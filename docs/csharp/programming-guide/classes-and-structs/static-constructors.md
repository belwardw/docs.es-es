---
title: "Constructores est&#225;ticos (Gu&#237;a de programaci&#243;n de C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "constructores [C#], static"
  - "constructores estáticos [C#]"
ms.assetid: 151ec95e-3c4d-4ed7-885d-95b7a3be2e7d
caps.latest.revision: 23
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 23
---
# Constructores est&#225;ticos (Gu&#237;a de programaci&#243;n de C#)
Un constructor estático se utiliza para inicializar cualquier dato [estático](../../../csharp/language-reference/keywords/static.md) o realizar una acción determinada que solo debe realizarse una vez.  Es llamado automáticamente antes de crear la primera instancia o de hacer referencia a cualquier miembro estático.  
  
 [!code-cs[csProgGuideObjects#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-constructors_1.cs)]  
  
 Los constructores estáticos tienen las propiedades siguientes:  
  
-   Un constructor estático no permite modificadores de acceso ni tiene parámetros.  
  
-   Se le llama automáticamente para inicializar la [clase](../../../csharp/language-reference/keywords/class.md) antes de crear la primera instancia o de hacer referencia a cualquier miembro estático.  
  
-   El constructor estático no puede ser llamado directamente.  
  
-   El usuario no puede controlar cuando se ejecuta el constructor estático en el programa.  
  
-   Los constructores estáticos se utilizan normalmente cuando la clase hace uso de un archivo de registro y el constructor escribe entradas en dicho archivo.  
  
-   Los constructores estáticos también son útiles al crear clases contenedoras para código no administrado, cuando el constructor puede llamar al método `LoadLibrary`.  
  
-   Si un constructor estático inicia una excepción, el motor en tiempo de ejecución no lo invocará una segunda vez y el tipo seguirá sin inicializar durante el período de duración del dominio de aplicación donde se ejecuta el programa.  
  
## Ejemplo  
 En este ejemplo, la clase `Bus` tiene un constructor estático.  Cuando se crea la primera instancia de `Bus` \(`bus1`\), se invoca el constructor estático para inicializar la clase.  En el resultado del ejemplo, se comprueba que el constructor estático se ejecuta solo una vez, incluso si se crean dos instancias de `Bus`, y que se ejecuta antes de que se ejecute el constructor de instancia.  
  
 [!code-cs[csProgGuideObjects#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-constructors_2.cs)]  
  
## Vea también  
 [Guía de programación de C\#](../../../csharp/programming-guide/index.md)   
 [Clases y structs](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [Constructores](../../../csharp/programming-guide/classes-and-structs/constructors.md)   
 [Clases estáticas y sus miembros](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)   
 [Destructores](../../../csharp/programming-guide/classes-and-structs/destructors.md)