---
title: "Cómo: Cancelar un bucle Parallel.For o ForEach"
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
- parallel foreach loop, how to cancel
- parallel for loops, how to cancel
ms.assetid: 9d19b591-ea95-4418-8ea7-b6266af9905b
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: e3d2ba6776a46573599e581cbfdeb62d181b81e0
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-cancel-a-parallelfor-or-foreach-loop"></a>Cómo: Cancelar un bucle Parallel.For o ForEach
Los métodos <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> y <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> admiten la cancelación mediante tokens de cancelación. Para obtener más información sobre la cancelación, vea [Cancelación](../../../docs/standard/threading/cancellation-in-managed-threads.md). En un bucle paralelo, se proporciona <xref:System.Threading.CancellationToken> al método en el parámetro <xref:System.Threading.Tasks.ParallelOptions> y, a continuación, incluye la llamada paralela en un bloque try-catch.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo cancelar una llamada a <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>. Puede aplicar el mismo enfoque a una llamada <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>.  
  
 [!code-csharp[TPL_Parallel#29](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallel_cancel.cs#29)]
 [!code-vb[TPL_Parallel#29](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/cancelloop.vb#29)]  
  
 Si el token que señala la cancelación es el mismo token que se especifica en la instancia <xref:System.Threading.Tasks.ParallelOptions>, el bucle paralelo producirá una sola clase <xref:System.OperationCanceledException> en la cancelación. Si algún otro token produce la cancelación, el bucle producirá una clase <xref:System.AggregateException> con una clase <xref:System.OperationCanceledException> como una excepción interna.  
  
## <a name="see-also"></a>Vea también  
 [Data Parallelism](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md) (Paralelismo de datos)  
 [Expresiones lambda en PLINQ y TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
