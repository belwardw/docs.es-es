---
title: "Tipos conocidos de contratos de datos | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "contratos de datos [WCF], tipos conocidos"
  - "KnownTypeAttribute [WCF]"
  - "KnownTypes [WCF]"
ms.assetid: 1a0baea1-27b7-470d-9136-5bbad86c4337
caps.latest.revision: 42
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 42
---
# Tipos conocidos de contratos de datos
La clase <xref:System.Runtime.Serialization.KnownTypeAttribute> le permite especificar, de antemano, los tipos que deberían tenerse en cuenta durante la deserialización. Para ver un ejemplo ilustrativo, consulte el ejemplo [Tipos conocidos](../../../../docs/framework/wcf/samples/known-types.md).  
  
 Normalmente, al pasar parámetros y valores devueltos entre un cliente y un servicio, ambos extremos comparten todos los contratos de datos de los datos que se van a transmitir. Sin embargo, éste no es el caso en las siguientes circunstancias:  
  
-   El contrato de datos enviados se deriva del contrato de datos esperados.[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] la sección sobre herencia en [Equivalencia del contrato de datos](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)\). En ese caso, los datos transmitidos no tienen el mismo contrato de datos que espera el extremo receptor.  
  
-   El tipo declarado de la información que se va a transmitir es una interfaz, en lugar de una clase, estructura o enumeración. En consecuencia, no se puede saber por adelantado qué tipo que implementa la interfaz se envía realmente y, por consiguiente, el extremo receptor no puede determinar de antemano el contrato de datos para los datos transmitidos.  
  
-   El tipo declarado de la información que se va a transmitir es <xref:System.Object>. Puesto que cada tipo hereda de <xref:System.Object>, y no se puede conocer de antemano qué tipo se envía realmente, el extremo receptor no puede determinar de antemano el contrato de datos para los datos transmitidos. Éste es un caso especial del primer elemento: cada contrato de datos se deriva del valor predeterminado, un contrato de datos en blanco que se genera para <xref:System.Object>.  
  
-   Algunos tipos, entre los que se incluyen los tipos [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], tienen miembros que se encuentran en una de las tres categorías anteriores. Por ejemplo, <xref:System.Collections.Hashtable> utiliza <xref:System.Object> para almacenar los objetos reales en la tabla hash. Al serializar estos tipos, el lado receptor no puede determinar de antemano el contrato de datos de estos miembros.  
  
## La clase KnownTypeAttribute  
 Cuando los datos llegan a un extremo receptor, el tiempo de ejecución de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] intenta deserializar los datos en una instancia de un tipo de Common Language Runtime \(CLR\). El tipo del que se crea una instancia para la deserialización se elige inspeccionando primero el mensaje entrante para determinar el contrato de datos al que se ajusta el contenido del mensaje. El motor de deserialización intenta a continuación encontrar un tipo CLR que implemente un contrato de datos compatible con el contenido del mensaje. El conjunto de tipos de candidatos que admite el motor de deserialización durante este proceso se conoce como el conjunto del deserializador de "tipos conocidos."  
  
 Una manera de permitir al motor de deserialización saber sobre un tipo consiste en utilizar el <xref:System.Runtime.Serialization.KnownTypeAttribute>. El atributo no se puede aplicar a miembros de datos individuales, solo a tipos de contrato de datos enteros. El atributo se aplica a un *tipo exterior* que puede ser una clase o una estructura. En su uso más básico, al aplicar el atributo, se especifica un tipo como "tipo conocido". Esto hace que el tipo conocido forme parte del conjunto de tipos conocidos siempre que se deserialice un objeto del tipo exterior o cualquier objeto al que se hace referencia a través de sus miembros. Se puede aplicar más de un atributo <xref:System.Runtime.Serialization.KnownTypeAttribute> al mismo tipo.  
  
## Tipos conocidos y primitivos  
 Los tipos primitivos, así como ciertos tipos tratados como primitivos \(como, por ejemplo, <xref:System.DateTime> y <xref:System.Xml.XmlElement>\) son siempre “conocidos” y nunca tienen que agregarse mediante este mecanismo. Sin embargo, las matrices de tipos primitivos tienen que agregarse explícitamente. La mayoría de las colecciones se consideran equivalentes a las matrices. \(Las colecciones no genéricas se consideran equivalentes a las matrices de <xref:System.Object>\). Para obtener un ejemplo del uso de primitivos, matrices de primitivos y colecciones de primitivos, vea el Ejemplo 4.  
  
> [!NOTE]
>  A diferencia de otros tipos primitivos, la estructura <xref:System.DateTimeOffset> no es un tipo conocido de forma predeterminada, por lo que debe agregarse manualmente a la lista de tipos conocidos.  
  
## Ejemplos  
 En los siguientes ejemplos se muestra la clase <xref:System.Runtime.Serialization.KnownTypeAttribute> en uso.  
  
#### Ejemplo 1  
 Hay tres clases con una relación de herencia.  
  
 [!code-csharp[C_KnownTypeAttribute#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#1)]
 [!code-vb[C_KnownTypeAttribute#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#1)]  
  
 Se puede serializar la siguiente clase `CompanyLogo`, pero no se puede deserializar si el miembro `ShapeOfLogo` está establecido en un objeto `CircleType` o `TriangleType`, porque el motor de deserialización no reconoce ningún tipo con nombres de contrato de datos "Circle" o "Triangle".  
  
 [!code-csharp[C_KnownTypeAttribute#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#2)]
 [!code-vb[C_KnownTypeAttribute#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#2)]  
  
 La forma correcta de escribir el tipo `CompanyLogo` se muestra en el siguiente código.  
  
 [!code-csharp[C_KnownTypeAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#3)]
 [!code-vb[C_KnownTypeAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#3)]  
  
 Cuando quiera que se deserializa el tipo exterior `CompanyLogo2`, el motor de deserialización sabe de `CircleType` y `TriangleType` y, por consiguiente, puede encontrar tipos coincidentes para los contratos de datos "Circle" y "Triangle".  
  
#### Ejemplo 2  
 En el siguiente ejemplo , aunque `CustomerTypeA` y `CustomerTypeB` tienen el contrato de datos `Customer`, se crea una instancia de `CustomerTypeB` siempre que se deserializa una `PurchaseOrder`, porque el motor de deserialización solo conoce al `CustomerTypeB`.  
  
 [!code-csharp[C_KnownTypeAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#4)]
 [!code-vb[C_KnownTypeAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#4)]  
  
#### Ejemplo 3  
 En el siguiente ejemplo, una <xref:System.Collections.Hashtable> almacena internamente su contenido como <xref:System.Object>. Para deserializar correctamente una tabla hash, el motor de deserialización debe conocer el conjunto de tipos posibles que se pueden dar. En este caso, conocemos de antemano que solo los objetos `Book` y `Magazine` se almacenan en `Catalog`, por lo que aquellos se agregan utilizando el atributo <xref:System.Runtime.Serialization.KnownTypeAttribute>.  
  
 [!code-csharp[C_KnownTypeAttribute#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#5)]
 [!code-vb[C_KnownTypeAttribute#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#5)]  
  
#### Ejemplo 4  
 En el siguiente ejemplo, un contrato de datos almacena un número y una operación que se va a realizar sobre el número. El miembro de datos `Numbers` puede ser un entero, una matriz de enteros, o una <xref:System.Collections.Generic.List%601> que contenga enteros.  
  
> [!CAUTION]
>  Esto solo funcionará en el lado del cliente si se usa SVCUTIL.EXE para generar un proxy WCF. SVCUTIL.EXE recupera metadatos del servicio, incluyendo los tipos conocidos. Sin esta información, un cliente no podrá deserializar los tipos.  
  
 [!code-csharp[C_KnownTypeAttribute#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#6)]
 [!code-vb[C_KnownTypeAttribute#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#6)]  
  
 Éste es el código de aplicación.  
  
 [!code-csharp[C_KnownTypeAttribute#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#7)]
 [!code-vb[C_KnownTypeAttribute#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#7)]  
  
## Herencia, interfaces y tipos conocidos  
 Cuando un tipo conocido está asociado a un tipo determinado mediante el atributo `KnownTypeAttribute`, el tipo conocido también está asociado a todos los tipos derivados de ese tipo. Por ejemplo, vea el siguiente código:  
  
 [!code-csharp[C_KnownTypeAttribute#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#8)]
 [!code-vb[C_KnownTypeAttribute#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#8)]  
  
 La clase `DoubleDrawing` no exige al atributo `KnownTypeAttribute` que utilice `Square` y `Circle` en el campo `AdditionalShape`, porque ya se han aplicado esos atributos a la clase base \(`Drawing`\).  
  
 Los tipos conocidos solo pueden estar asociados a clases y estructuras, no a interfaces.  
  
## Tipos conocidos utilizando métodos genéricos abiertos  
 Puede que sea necesario agregar un tipo genérico como un tipo conocido. Sin embargo, un tipo genérico abierto no se puede pasar como un parámetro al atributo `KnownTypeAttribute`.  
  
 Este problema se puede resolver utilizando un mecanismo alternativo: Escriba un método que devuelva una lista de tipos que se han de agregar a la colección de tipos conocidos. El nombre del método se especifica a continuación como un argumento de cadena al atributo `KnownTypeAttribute` debido a algunas restricciones.  
  
 El método debe existir en el tipo al que se aplica el atributo `KnownTypeAttribute`, debe ser estático, no debe aceptar parámetros y debe devolver un objeto que se pueda asignar a <xref:System.Collections.IEnumerable> de <xref:System.Type>.  
  
 No puede combinar el atributo `KnownTypeAttribute` con un nombre de método y atributos `KnownTypeAttribute` con tipos reales en el mismo tipo. Es más, no puede aplicar más de un `KnownTypeAttribute` con un nombre de método al mismo tipo.  
  
 Vea la siguiente clase.  
  
 [!code-csharp[C_KnownTypeAttribute#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#9)]
 [!code-vb[C_KnownTypeAttribute#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#9)]  
  
 El campo `theDrawing` contiene instancias de una clase genérica `ColorDrawing` y una clase genérica `BlackAndWhiteDrawing`, las cuales heredan de una clase genérica `Drawing`. Normalmente, ambos se deben agregar a los tipos conocidos, pero la siguiente sintaxis no es una sintaxis válida para atributos.  
  
```csharp  
// Invalid syntax for attributes:  
// [KnownType(typeof(ColorDrawing<T>))]  
// [KnownType(typeof(BlackAndWhiteDrawing<T>))]  
```  
  
```vb  
' Invalid syntax for attributes:  
' <KnownType(GetType(ColorDrawing(Of T))), _  
' KnownType(GetType(BlackAndWhiteDrawing(Of T)))>  
```  
  
 De este modo, se debe crear un método para devolver estos tipos. La forma correcta de escribir este tipo, entonces, se muestra en el siguiente código.  
  
 [!code-csharp[C_KnownTypeAttribute#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#10)]
 [!code-vb[C_KnownTypeAttribute#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#10)]  
  
## Maneras adicionales de agregar tipos conocidos  
 Además, los tipos conocidos se pueden agregar a través de un archivo de configuración. Esto es útil cuando no se controla el tipo que requiere tipos conocidos para la correcta deserialización, como cuando se usan bibliotecas de tipos de terceros con [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].  
  
 En el archivo de configuración siguiente se observa cómo se especifica un tipo conocido en un archivo de configuración.  
  
 `<configuration>`  
  
 `<system.runtime.serialization>`  
  
 `<dataContractSerializer>`  
  
 `<declaredTypes>`  
  
 `<add type="MyCompany.Library.Shape,`  
  
 `MyAssembly, Version=2.0.0.0, Culture=neutral,`  
  
 `PublicKeyToken=XXXXXX, processorArchitecture=MSIL">`  
  
 `<knownType type="MyCompany.Library.Circle,`  
  
 `MyAssembly, Version=2.0.0.0, Culture=neutral,`  
  
 `PublicKeyToken=XXXXXX, processorArchitecture=MSIL"/>`  
  
 `</add>`  
  
 `</declaredTypes>`  
  
 `</dataContractSerializer>`  
  
 `</system.runtime.serialization>`  
  
 `</configuration>`  
  
 En el archivo de configuración anterior, se declara que un tipo de contrato de datos denominado `MyCompany.Library.Shape` tiene `MyCompany.Library.Circle` como tipo conocido.  
  
## Vea también  
 <xref:System.Runtime.Serialization.KnownTypeAttribute>   
 <xref:System.Collections.Hashtable>   
 <xref:System.Object>   
 <xref:System.Runtime.Serialization.DataContractSerializer>   
 <xref:System.Runtime.Serialization.DataContractSerializer.KnownTypes%2A>   
 [Tipos conocidos](../../../../docs/framework/wcf/samples/known-types.md)   
 [Equivalencia del contrato de datos](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)   
 [Diseño de contratos de servicios](../../../../docs/framework/wcf/designing-service-contracts.md)