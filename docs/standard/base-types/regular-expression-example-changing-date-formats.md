---
title: 'Ejemplo de expresiones regulares: Cambiar formatos de fecha'
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
- searching with regular expressions, examples
- parsing text with regular expressions, examples
- regular expressions, examples
- .NET Framework regular expressions, examples
- regular expressions [.NET Framework], examples
- pattern-matching with regular expressions, examples
ms.assetid: 5fcc75a5-09d7-45ae-a4c0-9ad6085ac83d
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 93c526e87f7aba650cce397962c7262b6fd2f085
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/23/2017
---
# <a name="regular-expression-example-changing-date-formats"></a>Ejemplo de expresiones regulares: Cambiar formatos de fecha
En el siguiente ejemplo de código, se usa el método <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> para reemplazar las fechas con el formato *mm*/*dd*/*aa* con fechas que tienen el formato *dd*-*mm*-*aa*.  
  
## <a name="example"></a>Ejemplo  
 [!code-csharp[RegularExpressions.Examples.ChangeDateFormats#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/cs/Example_ChangeDateFormats1.cs#1)]
 [!code-vb[RegularExpressions.Examples.ChangeDateFormats#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/vb/Example_ChangeDateFormats1.vb#1)]  
  
 El código siguiente muestra cómo se puede llamar al método `MDYToDMY` en una aplicación.  
  
 [!code-csharp[RegularExpressions.Examples.ChangeDateFormats#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/cs/Example_ChangeDateFormats1.cs#2)]
 [!code-vb[RegularExpressions.Examples.ChangeDateFormats#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/vb/Example_ChangeDateFormats1.vb#2)]  
  
## <a name="comments"></a>Comentarios  
 El patrón de la expresión regular `\b(?<month>\d{1,2})/(?<day>\d{1,2})/(?<year>\d{2,4})\b` se interpreta como se muestra en la tabla siguiente.  
  
|Modelo|Description|  
|-------------|-----------------|  
|`\b`|Iniciar la búsqueda de coincidencias en un límite de palabras.|  
|`(?<month>\d{1,2})`|Buscar coincidencias con uno o dos dígitos decimales. Es el grupo `month` capturado.|  
|`/`|Buscar coincidencias con la barra diagonal.|  
|`(?<day>\d{1,2})`|Buscar coincidencias con uno o dos dígitos decimales. Es el grupo `day` capturado.|  
|`/`|Buscar coincidencias con la barra diagonal.|  
|`(?<year>\d{2,4})`|Buscar coincidencias de dos a cuatro dígitos decimales. Es el grupo `year` capturado.|  
|`\b`|Finalizar la búsqueda de coincidencias en un límite de palabras.|  
  
 El patrón `${day}-${month}-${year}` define la cadena de reemplazo como se muestra en la siguiente tabla.  
  
|Modelo|Description|  
|-------------|-----------------|  
|`$(day)`|Agregar la cadena capturada por el grupo de captura `day`.|  
|`-`|Agregar un guión.|  
|`$(month)`|Agregar la cadena capturada por el grupo de captura `month`.|  
|`-`|Agregar un guión.|  
|`$(year)`|Agregar la cadena capturada por el grupo de captura `year`.|  
  
## <a name="see-also"></a>Vea también  
 [Expresiones regulares de .NET](../../../docs/standard/base-types/regular-expressions.md)
