---
title: "&lt;returns&gt; (Guía de programación de C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- returns
- <returns>
helpviewer_keywords:
- <returns> C# XML tag
- returns C# XML tag
ms.assetid: bb2d9958-62fc-47c7-9511-6311171f119f
caps.latest.revision: "11"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0313e9584ae6a94469db17e15f8b6b509b8aebd5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2017
---
# <a name="ltreturnsgt-c-programming-guide"></a>&lt;returns&gt; (Guía de programación de C#)
## <a name="syntax"></a>Sintaxis  
  
```xml  
<returns>description</returns>  
```  
  
#### <a name="parameters"></a>Parámetros  
 `description`  
 Descripción del valor devuelto.  
  
## <a name="remarks"></a>Comentarios  
 La etiqueta \<returns> debe usarse en el comentario de una declaración de método para describir el valor devuelto.  
  
 Compile con el parámetro [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) para procesar los comentarios de documentación y generar un archivo con ellos.  
  
## <a name="example"></a>Ejemplo  
 [!code-csharp[csProgGuideDocComments#10](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/returns_1.cs)]  
  
## <a name="see-also"></a>Vea también  
 [Guía de programación de C#](../../../csharp/programming-guide/index.md)  
 [Etiquetas recomendadas para los comentarios de documentación](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
