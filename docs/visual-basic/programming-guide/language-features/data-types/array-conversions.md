---
title: Conversión de matrices (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [Visual Basic], converting type
- type conversion [Visual Basic], arrays
- conversions [Visual Basic], type
- arrays [Visual Basic], data types
- conversions [Visual Basic], data type
- object arrays [Visual Basic], converting type
- data type conversion [Visual Basic], array conversions
- conversions [Visual Basic], array types
- object arrays
ms.assetid: fceff7d2-a1b7-44c7-b9aa-8bd831d8a444
ms.openlocfilehash: a179b7cf5b82132db88fb5412f0ca4be207f0987
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="array-conversions-visual-basic"></a>Conversión de matrices (Visual Basic)
Puede convertir un tipo de matriz en otro tipo de matriz siempre que se cumplan las condiciones siguientes:  
  
-   **Rango igual.** Los rangos de las dos matrices deben ser los mismos, es decir, deben tener el mismo número de dimensiones. Sin embargo, las longitudes de las dimensiones respectivas no es necesario ser el mismo.  
  
-   **Tipo de datos del elemento.** Los tipos de datos de los elementos de ambas matrices deben ser tipos de referencia. No se puede convertir un `Integer` de matriz a un `Long` de matriz, o incluso en un `Object` de matriz, porque al menos un tipo de valor está implicado. Para obtener más información, consulte [tipos de valor y tipos de referencia](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).  
  
-   **Convertibility.** Una conversión de ampliación o restricción, debe ser posible entre los tipos de elemento de las dos matrices. Un ejemplo que no cumple este requisito es un intento de conversión entre una `String` matriz y una matriz de una clase derivan de <xref:System.Attribute?displayProperty=nameWithType>. Estos dos tipos no tienen nada en común y no existe ninguna conversión de ningún tipo entre ellos.  
  
 Una conversión de tipo de matriz de uno a otro es de ampliación o restricción dependiendo de si la conversión de los respectivos elementos es de ampliación o restricción. Para obtener más información, consulta [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
## <a name="conversion-to-an-object-array"></a>Conversión a una matriz de objetos  
 Cuando se declara un `Object` matriz sin inicializarla, su tipo de elemento es `Object` mientras permanezca sin inicializar. Cuando se establece en una matriz de una clase específica, toma el tipo de esa clase. Sin embargo, su tipo subyacente sigue siendo `Object`, y posteriormente se puede establecer en otra matriz de una clase no relacionada. Dado que todas las clases que derivan de `Object`, puede cambiar el tipo de elemento de la matriz de cualquier clase a cualquier otra clase.  
  
 En el ejemplo siguiente, no existe ninguna conversión entre tipos `student` y `String`, pero ambos derivan de `Object`, por lo que todas las asignaciones son válidas.  
  
```  
' Assume student has already been defined as a class.  
Dim testArray() As Object  
' testArray is still an Object array at this point.  
Dim names() As String = New String(3) {"Name0", "Name1", "Name2", "Name3"}  
testArray = New student(3) {}  
' testArray is now of type student().  
testArray = names  
' testArray is now a String array.  
```  
  
### <a name="underlying-type-of-an-array"></a>El tipo subyacente de una matriz  
 Si originalmente se declara una matriz con una clase específica, su tipo de elemento subyacente es esa clase. Si posteriormente se establece en una matriz de otra clase, debe haber una conversión entre las dos clases.  
  
 En el ejemplo siguiente, `students` es un `student` matriz. Puesto que no existe ninguna conversión entre `String` y `student`, se produce un error en la última instrucción.  
  
```  
Dim students() As student  
Dim names() As String = New String(3) {"Name0", "Name1", "Name2", "Name3"}  
students = New Student(3) {}  
' The following statement fails at compile time.  
students = names  
```  
  
## <a name="see-also"></a>Vea también  
 [Tipos de datos](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [Conversiones de tipos en Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [Conversiones implícitas y explícitas](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [Conversiones entre cadenas y otros tipos](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)  
 [Cómo: convertir un objeto a otro tipo en Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)  
 [Tipos de datos](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Funciones de conversión de tipos](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Matrices](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
