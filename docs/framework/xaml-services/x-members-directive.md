---
title: Directiva de x:Members
ms.date: 03/30/2017
ms.assetid: 155b393d-3b49-4c5a-8c9e-b3d9893af4e4
ms.openlocfilehash: 2c273fce1f15d9a5af72bc3f5a530d3c26dfc77e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="xmembers-directive"></a>Directiva de x:Members
Contiene un conjunto de miembros que se definen en el marcado, que se aplican para el atributo x: Class del elemento primario.  
  
## <a name="xaml-attribute-usage"></a>Uso de atributos XAML  
  
```  
<object x:Class="className">  
  <x:Members>  
    oneOrMoreMembers  
  </x:Members  
</object>  
```  
  
## <a name="xaml-values"></a>Valores XAML  
  
|||  
|-|-|  
|`className`|Nombre de la clase de respaldo o clase parcial para la producción de XAML. Vea la sección Comentarios.|  
|`oneOrMoreMembers`|Uno o más elementos de objeto que representan las definiciones de miembro. Normalmente, estos son `x:Property` elementos de objeto. Vea la sección Comentarios.|  
  
## <a name="remarks"></a>Comentarios  
 En la implementación de servicios XAML de .NET Framework, no hay ninguna clase de respaldo o la implementación subyacente de un miembro para `x:Members`. `x:Members` es un miembro XAML especiales que puede existir como un miembro de cualquier tipo. En un flujo de nodo XAML, `x:Members` se representa como un miembro denominado `Members`, desde el espacio de nombres XAML de lenguaje XAML. El miembro `Members` contiene una lista genérica de solo lectura de `Member` objetos. En el marcado típica se especifican los miembros individuales como `x:Property` elementos de propiedad. `x:Property` es un tipo más preciso específicamente para las propiedades de tipos y se puede asignar a `x:Member`. Para obtener más información, consulte [Directiva x: Property](../../../docs/framework/xaml-services/x-property-directive.md).  
  
 Para admitir un uso práctico de `x:Members` como medio para especificar definiciones de miembros en el marcado, los miembros deben asociarse con una clase que se pueda modificar. El modelo previsto es que `x:Members` exista como miembro de un tipo que especifica una `x:Class`. Sin embargo, el mecanismo para asociar tipos y miembros o para generar definiciones de miembros dinámicas no se admite en el nivel de los servicios XAML de .NET Framework. De esto se encargan los marcos individuales que tienen modelos de aplicación compatibles con las definiciones de miembro de XAML. Normalmente, para admitir esta característica se necesitan acciones de compilación de MSBUILD que compilan XAML por marcado y, o bien lo integran con código subyacente o producen ensamblados puros a partir de XAML.  
  
## <a name="xmembers-for-windows-workflow-foundation"></a>x: Members para Windows Workflow Foundation  
 Para Windows Workflow Foundation, `x:Members` contiene los miembros de una actividad personalizada compuesta completamente en XAML o XAML: miembros dinámicos definidos para un diseñador de actividades con código subyacente. `x:Class` también se debe especificar en el elemento raíz de la producción de XAML. Esto no es un requisito de los servicios XAML de .NET Framework, pero es obligatorio cuando la producción de XAML se carga mediante las acciones de compilación de MSBUILD que admiten actividades personalizadas y XAML en Windows Workflow Foundation en general. `x:Members` debe ser el primer elemento secundario en el marcado del elemento de objeto que declara el `x:Class`.
