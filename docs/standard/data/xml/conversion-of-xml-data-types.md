---
title: "Conversión de tipos de datos XML"
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
ms.assetid: a2aa99ba-8239-4818-9281-f1d72ee40bde
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d18b69c2d5baeac77cbdf45bebd6f0c9d5c94d9f
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/23/2017
---
# <a name="conversion-of-xml-data-types"></a>Conversión de tipos de datos XML
La mayor parte de los métodos que se encuentran en una clase **XmlConvert** se utilizan para convertir datos entre cadenas y formatos fuertemente tipados. Los métodos son independientes de la configuración regional. Esto significa que no la tienen en cuenta al realizar la conversión.  
  
## <a name="reading-string-as-types"></a>Leer cadenas como tipos  
 En el ejemplo siguiente se lee una cadena y se convierte en un tipo **DateTime**.  
  
 Dada la siguiente entrada XML:  
  
 **Entrada**  
  
```xml  
<Element>2001-02-27T11:13:23</Element>  
```  
  
 Este código convierte la cadena al formato **DateTime**:  
  
```vb  
reader.ReadStartElement()  
Dim vDateTime As DateTime = XmlConvert.ToDateTime(reader.ReadString())  
Console.WriteLine(vDateTime)  
```  
  
```csharp  
reader.ReadStartElement();  
DateTime vDateTime = XmlConvert.ToDateTime(reader.ReadString());  
Console.WriteLine(vDateTime);  
```  
  
## <a name="writing-strings-as-types"></a>Escribir cadenas como tipos  
 En el ejemplo siguiente se lee un valor **Int32** y se convierte en una cadena.  
  
 Dada la siguiente entrada XML:  
  
 **Entrada**  
  
```xml  
<TestInt32>-2147483648</TestInt32>  
```  
  
 Este código convierte el valor **Int32** en **String**:  
  
```vb  
Dim vInt32 As Int32 = -2147483648  
writer.WriteElementString("TestInt32", XmlConvert.ToString(vInt32))  
```  
  
```csharp  
Int32 vInt32=-2147483648;  
writer.WriteElementString("TestInt32",XmlConvert.ToString(vInt32));  
```  
  
## <a name="see-also"></a>Vea también  
 [Conversión de cadenas en tipos de datos de .NET Framework](../../../../docs/standard/data/xml/converting-strings-to-dotnet-data-types.md)  
 [Conversión de tipos de .NET Framework en cadenas](../../../../docs/standard/data/xml/converting-dotnet-types-to-strings.md)
