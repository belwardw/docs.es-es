---
title: "Realizar operaciones de combinación personalizadas"
description: "Cómo realizar operaciones de combinación personalizadas."
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: 56a2a4a5-7299-497d-b3c3-23c848678911
ms.openlocfilehash: fef146c92a5cbbf21f8f1688f221c2bd45c99de7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2017
---
# <a name="perform-custom-join-operations"></a>Realizar operaciones de combinación personalizadas

En este ejemplo se muestra cómo realizar operaciones de combinación que no son posibles con la cláusula `join`. En una expresión de consulta, la cláusula `join` se limita a combinaciones de igualdad (y se optimiza para estas), que son con diferencia el tipo más común de operación de combinación. Al realizar una combinación de igualdad, probablemente obtendrá siempre el mejor rendimiento con la cláusula `join`.  
  
 En cambio, la cláusula `join` no se puede usar en los siguientes casos:  
  
-   Cuando la combinación se basa en una expresión de desigualdad (una combinación que no es de igualdad).  
  
-   Cuando la combinación se basa en más de una expresión de igualdad o desigualdad.  
  
-   Cuando tenga que introducir una variable de rango temporal para la secuencia de la derecha (interior) antes de la operación de combinación.  
  
 Para realizar combinaciones que no son de igualdad, puede usar varias cláusulas `from` para presentar cada origen de datos de forma independiente. Después, aplique una expresión de predicado de una cláusula `where` a la variable de rango para cada origen. La expresión también puede adoptar la forma de una llamada de método.  
  
> [!NOTE]
>  No confunda este tipo de operación de combinación personalizada con el uso de varias cláusulas `from` para acceder a colecciones internas. Para obtener más información, consulte [join (Cláusula, Referencia de C#)](../language-reference/keywords/join-clause.md).  
  
## <a name="example"></a>Ejemplo  
 En el primer método del siguiente ejemplo se muestra una combinación cruzada sencilla. Las combinaciones cruzadas se deben usar con precaución porque pueden generar conjuntos de resultados muy grandes. En cambio, pueden resultar útiles en algunos escenarios para crear secuencias de origen en las que se ejecutan consultas adicionales.  
  
 El segundo método genera una secuencia de todos los productos cuyo identificador de categoría aparece en la lista de categorías en el lado izquierdo. Observe el uso de la cláusula `let` y el método `Contains` para crear una matriz temporal. También se puede crear la matriz antes de la consulta y eliminar la primera cláusula `from`.  
  
 [!code-csharp[csProgGuideLINQ#64](../../../samples/snippets/csharp/concepts/linq/how-to-perform-custom-join-operations_1.cs)]  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente, la consulta debe combinar dos secuencias basándose en las claves coincidentes que, en el caso de la secuencia interna (lado derecho), no se pueden obtener antes de la propia cláusula de combinación. Si esta combinación se realizara con una cláusula `join`, se tendría que llamar al método `Split` para cada elemento. El uso de varias cláusulas `from` permite a la consulta evitar la sobrecarga que supone la llamada al método repetida. En cambio, puesto que `join` está optimizada, en este caso particular puede que siga resultando más rápido que usar varias cláusulas `from`. Los resultados variarán dependiendo principalmente de cuántos recursos requiera la llamada de método.  
  
 [!code-csharp[csProgGuideLINQ#13](../../../samples/snippets/csharp/concepts/linq/how-to-perform-custom-join-operations_2.cs)]  
  
## <a name="see-also"></a>Vea también  
 [Expresiones de consulta LINQ](index.md)  
 [join (cláusula)](../language-reference/keywords/join-clause.md)  
 [Ordenar los resultados de una cláusula join](order-the-results-of-a-join-clause.md)
