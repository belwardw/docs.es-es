---
title: "C&#243;mo: Eliminar almacenes de almacenamiento aislado | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "almacenes, eliminar"
  - "almacenes de datos, eliminar"
  - "eliminar almacenes"
  - "quitar almacenes"
  - "almacenamiento aislado, eliminar almacenes"
  - "almacenar datos mediante el almacenamiento aislado, eliminar almacenes"
  - "almacenamiento de datos mediante el almacenamiento aislado, eliminar almacenes"
ms.assetid: 3947e333-5af6-4601-b2f1-24d4d6129cf3
caps.latest.revision: 14
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 14
---
# C&#243;mo: Eliminar almacenes de almacenamiento aislado
La clase <xref:System.IO.IsolatedStorage.IsolatedStorageFile> proporciona dos métodos para eliminar archivos de almacenamiento aislado:  
  
-   El método de instancia <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> no toma ningún argumento y elimina el almacén que lo llama. No se requieren permisos para realizar esta operación. Cualquier código que pueda acceder al almacén puede eliminar alguno o todos los datos que contenga.  
  
-   El método estático <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29> toma el valor de enumeración <xref:System.IO.IsolatedStorage.IsolatedStorageScope> y elimina todos los almacenes del usuario que está ejecutando el código. Esta operación requiere permiso <xref:System.Security.Permissions.IsolatedStorageFilePermission> para el valor <xref:System.Security.Permissions.IsolatedStorageContainment>.  
  
## Ejemplo  
 En el ejemplo de código siguiente se muestra el uso de los métodos <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%2A> estático y de instancia. La clase obtiene dos almacenes; uno está aislado de usuario y ensamblado, y el otro está aislado de usuario, dominio y ensamblado. El almacén de usuario, dominio y ensamblado se elimina con una llamada al método <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> del archivo de almacenamiento aislado `isoStore1`. A continuación, se eliminan todos los demás almacenes del usuario con una llamada al método estático <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29>.  
  
 [!code-cpp[Conceptual.IsolatedStorage#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source3.cpp#3)]
 [!code-csharp[Conceptual.IsolatedStorage#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source3.cs#3)]
 [!code-vb[Conceptual.IsolatedStorage#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source3.vb#3)]  
  
## Vea también  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>   
 [Almacenamiento aislado](../../../docs/standard/io/isolated-storage.md)