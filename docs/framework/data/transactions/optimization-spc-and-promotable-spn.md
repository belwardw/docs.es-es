---
title: "Optimizaci&#243;n mediante el uso de la confirmaci&#243;n de fase &#250;nica y de la confirmaci&#243;n de fase &#250;nica promocionable  | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 57beaf1a-fb4d-441a-ab1d-bc0c14ce7899
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# Optimizaci&#243;n mediante el uso de la confirmaci&#243;n de fase &#250;nica y de la confirmaci&#243;n de fase &#250;nica promocionable 
En este tema se describen los mecanismos proporcionados por la infraestructura <xref:System.Transactions> para optimizar el rendimiento.  
  
## Inscripción de la fase única promocionable  
 La infraestructura <xref:System.Transactions> administra una transacción dentro de un dominio de aplicación único que implica a lo sumo un recurso durable único o varios recursos volátiles.Puesto que la infraestructura <xref:System.Transactions> solo utiliza las llamadas de dominio de intraaplicación, produce el mejor rendimiento.  
  
 Sin embargo, si la transacción se proporciona a otro objeto en otro dominio de aplicación \(incluso por el proceso y límites del equipo\) en el mismo equipo, o si fuera dar de alta otro administrador de recursos duradero, la infraestructura <xref:System.Transactions> realiza automáticamente una escalada de la transacción que va a ser administrada por MSDTC.Una transacción administrada por MSDTC no rinde tan eficazmente como uno administrado por la infraestructura <xref:System.Transactions>.  
  
 Para optimizar el rendimiento, la infraestructura <xref:System.Transactions> proporciona la Inscripción \(PSPE\) de Fase de Soltero promocionable que permite un recurso duradero remoto único, situado en un dominio de aplicación diferente, proceso o equipo, para participar en una transacción <xref:System.Transactions> sin producir una escalada a una transacción de MSDTC.Este administrador de recursos \(RM\) puede hospedar y "poseer" una transacción que puede realizar una escalada después de una transacción distribuida \(o transacción de MSDTC\) si es necesario.Esto reduce aún más la oportunidad de utilizar MSDTC.  
  
 Este administrador de recursos concreto normalmente tiene sus propias transacciones no\-distribuidas internas y necesita permitir convertir esas transacciones en las transacciones distribuidas en el tiempo de ejecución.Por ejemplo, SQL Server 2005 es este tipo de administrador de recursos.En tal caso, la infraestructura <xref:System.Transactions> toma un rol de administración pasiva simplemente supervisando la transacción para una necesidad de subida.Para admitir la interacción entre la infraestructura <xref:System.Transactions> y el administrador de recursos, este último necesita implementar la interfaz <xref:System.Transactions.IPromotableSinglePhaseNotification>.  
  
 El método <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> se utiliza para dar de alta un recurso duradero único que pueda realizar después una escalada.Este método asegurar que la inscripción puede realizar una escalada según sea necesario.Si la inscripción tiene éxito, RM crea su transacción interna y la asocia a la transacción <xref:System.Transactions>.En caso de error en la inscripción de PSPE, RM debería darse de alta utilizando en su lugar el método <xref:System.Transactions.Transaction.EnlistDurable%2A>.Los errores para dar de alta en PSPE podrían ocurrir cuando la transacción ya es una transacción distribuida, o cuando RM ya ha realizado una inscripción de PSPE  
  
 Cuando esté dada de alta, las llamadas por clientes para confirmar o anular la transacción <xref:System.Transactions> se convierten en las llamadas en el Recurso Administrador invocando el método <xref:System.Transactions.IPromotableSinglePhaseNotification.SinglePhaseCommit%2A> o <xref:System.Transactions.IPromotableSinglePhaseNotification.Rollback%2A> respectivamente.  
  
 Si la transacción <xref:System.Transactions> nunca requiere la subida, cuando se confirma la transacción, RM recibe una notificación <xref:System.Transactions.IPromotableSinglePhaseNotification.SinglePhaseCommit%2A>.Puede confirmar a continuación la transacción interna que se creó inicialmente.  
  
 Si la transacción <xref:System.Transactions> necesita realizar una escalada \(por ejemplo, admitir varios RMs\), <xref:System.Transactions> informa al administrador de recursos llamando al método <xref:System.Transactions.ITransactionPromoter.Promote%2A> en la interfaz <xref:System.Transactions.ITransactionPromoter>, de la que la interfaz <xref:System.Transactions.IPromotableSinglePhaseNotification> deriva.El administrador de recursos convierte a continuación internamente la transacción de una transacción local \(qué no requiere el registro\) en un objeto de transacción que es capaz de participar en una transacción de DTC y lo asocia al trabajo ya hecho.Cuando solicitan que la transacción se confirme, el administrador de transacciones todavía envía la notificación <xref:System.Transactions.IPromotableSinglePhaseNotification.SinglePhaseCommit%2A> al administrador de recursos, que confirma la transacción distribuida que creó durante la subida.  
  
> [!NOTE]
>  Los rastros **TransactionCommitted** \(que se generan cuando una confirmación se invoca en la transacción escalada\) contienen el id. de la actividad de la transacción de DTC.  
  
 Para obtener más información sobre la elevación de la administración vea [Extensión de administración de transacciones ](../../../../docs/framework/data/transactions/transaction-management-escalation.md).  
  
## Escenario de subida de administración de la transacción  
 El escenario siguiente muestra una subida a una transacción distribuida utilizando el espacio de nombres <xref:System.Data> como el 'proxy' para el administrador de recursos.Este escenario supone que es ya una conexión <xref:System.Data> a la base de datos, CN1, envuelto en la transacción y la aplicación desea implicar otra conexión <xref:System.Data>, CN2.La transacción debe realizar una escalada a DTC, como una transacción completa de la confirmación distribuida en dos fases.  
  
 En este escenario  
  
1.  CN1 llama al método <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> para dar de alta en la transacción.A continuación, la transacción es todavía local y no es ningún otro alistamiento promocional en la transacción, por lo que la llamada <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> tiene éxito.  
  
2.  Cuando la segunda conexión, CN2 llama <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A>, se da un error en la llamada,  porque hay implicada otra inscripción promocional.Debido a esto, CN2 debe obtener una transacción de DTC para pasarlo a SQL.Utiliza uno de los métodos proporcionado por la clase <xref:System.Transactions.TransactionInterop> para generar un formato de la transacción que se puede dar a SQL para ello.  
  
3.  <xref:System.Transactions> llama al método <xref:System.Transactions.ITransactionPromoter.Promote%2A> en la interfaz <xref:System.Transactions.ITransactionPromoter> implementada por CN1.  
  
4.  En este punto, CN1 realiza una escalada de la transacción, utilizando algún mecanismo concreto a SQL 2005 y <xref:System.Data>.  
  
5.  El valor devuelto del método <xref:System.Transactions.ITransactionPromoter.Promote%2A> es una matriz de bytes que contiene un token de propagación para la transacción.<xref:System.Transactions> usa este token de propagación para crear una transacción de DTC que puede participar en la transacción local.  
  
6.  En este punto, CN2 puede utilizar los datos recibidos de llamar a uno de los métodos por <xref:System.Transactions.TransactionInterop> para pasar la transacción a SQL.  
  
7.  Ahora, ambos se dan de alta en una transacción distribuida de DTC.  
  
## Optimización de confirmación de fase única  
 La fase única el protocolo de confirmación es más eficaz en el tiempo de ejecución cuando todas las actualizaciones se hacen sin ninguna coordinación explícita.Para aprovecharse de esta optimización, debería implementar un administrador de recursos utilizando la interfaz <xref:System.Transactions.ISinglePhaseNotification> para el recurso y dar de alta en una transacción utilizando <xref:System.Transactions.Transaction.EnlistDurable%2A> o el método <xref:System.Transactions.Transaction.EnlistVolatile%2A>.En concreto, el parámetro *EnlistmentOptions* debería ser igual a <xref:System.Transactions.EnlistmentOptions> para garantizar que se realiza una confirmación en una fase.  
  
 Puesto que la interfaz <xref:System.Transactions.ISinglePhaseNotification> deriva de la interfaz <xref:System.Transactions.IEnlistmentNotification>, si RM no es elegible para la confirmación de la fase única, todavía puede recibir las dos notificaciones de confirmación de fase.Si RM recibe una notificación <xref:System.Transactions.ISinglePhaseNotification.SinglePhaseCommit%2A> de la TM, debería intentar hacer el trabajo necesario para confirmar y correspondientemente informar al administrador de transacciones si la transacción será confirmada o revertirla llamando al método <xref:System.Transactions.SinglePhaseEnlistment.Committed%2A>, <xref:System.Transactions.SinglePhaseEnlistment.Aborted%2A>o <xref:System.Transactions.SinglePhaseEnlistment.InDoubt%2A> en el parámetro <xref:System.Transactions.SinglePhaseEnlistment>.Una respuesta de <xref:System.Transactions.Enlistment.Done%2A> en la inscripción en esta copia intermedia implica la semántica ReadOnly.Por consiguiente, no debería contestar <xref:System.Transactions.Enlistment.Done%2A> sumándose a cualquiera de los otros métodos.  
  
 Si solo se da una inscripción volátil y ninguna inscripción duradera, la inscripción volátil recibe una notificación SPC. Si hay varias inscripciones volátiles y solo una duradera, las inscripciones volátiles reciben una notificación SPC.Cuando se completa, la inscripción duradera recibe SPC.  
  
## Vea también  
 [Dar de alta recursos como participantes en una transacción ](../../../../docs/framework/data/transactions/enlisting-resources-as-participants-in-a-transaction.md)   
 [Confirmar una transacción en fase única y fase múltiple ](../../../../docs/framework/data/transactions/committing-a-transaction-in-single-phase-and-multi-phase.md)