---
title: "Cómo: Realizar escuchas de solicitudes de cancelación cuando tienen controladores de espera"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cancellation, waiting with wait handles
ms.assetid: 6e2aa49b-fc84-4bcf-962b-17db98b7edcb
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: a0998703ef5b27b4de725a2c2adcfc3d9a2135b9
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-listen-for-cancellation-requests-that-have-wait-handles"></a>Cómo: Realizar escuchas de solicitudes de cancelación cuando tienen controladores de espera
Si un método se bloquea mientras está en espera para que se señalice un evento, no se puede comprobar el valor del token de cancelación ni responder de manera oportuna. El primer ejemplo muestra cómo resolver este problema cuando se trabaja con eventos como <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> que no admiten de forma nativa el marco de cancelación unificada. El segundo ejemplo muestra un enfoque más sencillo que utiliza <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>, que es compatible con la cancelación unificada.  
  
> [!NOTE]
>  Cuando está habilitada la opción "Solo mi código", en algunos casos, Visual Studio se interrumpe en la línea que produce la excepción y muestra el mensaje de error "Excepción no controlada por el código de usuario". Este error es benigno. Puede presionar F5 para continuar y ver el comportamiento de control de excepciones que se muestra en estos ejemplos. Para evitar que Visual Studio se interrumpa con el primer error, desactive la casilla "Solo mi código" en **Herramientas, Opciones, Depurar, General**.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se usa <xref:System.Threading.ManualResetEvent> para mostrar cómo desbloquear identificadores de espera que no admiten la cancelación unificada.  
  
 [!code-csharp[Cancellation#9](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex9.cs#9)]
 [!code-vb[Cancellation#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex9.vb#9)]  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se usa <xref:System.Threading.ManualResetEventSlim> para mostrar cómo desbloquear primitivos de coordinación que no admiten la cancelación unificada. Puede utilizarse el mismo enfoque con otros primitivos de coordinación ligeros, como <xref:System.Threading.Semaphore>`Slim` y <xref:System.Threading.CountdownEvent>.  
  
 [!code-csharp[Cancellation#10](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex10.cs#10)]
 [!code-vb[Cancellation#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex10.vb#10)]  
  
## <a name="see-also"></a>Vea también  
 [Cancelación en subprocesos administrados](../../../docs/standard/threading/cancellation-in-managed-threads.md)
