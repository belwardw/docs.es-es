---
title: 'Personalizar operaciones: Información general'
ms.date: 03/30/2017
ms.assetid: a3546296-1443-4b88-aa6e-d41011041ba7
ms.openlocfilehash: d495632faf2f57df21d07e0be85244d7ba9d9da7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="customizing-operations-overview"></a>Personalizar operaciones: Información general
De forma predeterminada, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] genera SQL dinámico para las operaciones de inserción, actualización y eliminación por asignación. Sin embargo, en la práctica, normalmente se agrega lógica empresarial propia para proporcionar seguridad, validación, etc.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] las técnicas para personalizar estas operaciones incluyen lo siguiente.  
  
## <a name="loading-options"></a>Opciones de carga  
 En las consultas es posible controlar la cantidad de datos relacionados con el destino principal que se recuperan al establecer una conexión con la base de datos. Esta funcionalidad se implementa en gran medida mediante el uso de <xref:System.Data.Linq.DataLoadOptions>. Para obtener más información, consulte [ejecución diferida frente a carga inmediata](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).  
  
## <a name="partial-methods"></a>Métodos Partial  
 En su asignación predeterminada, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] proporciona métodos parciales para ayudar a implementar lógica empresarial propia. Para obtener más información, consulte [agregar Business lógica por utilizando métodos parciales](../../../../../../docs/framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md).  
  
## <a name="stored-procedures-and-user-defined-functions"></a>Procedimientos almacenados y funciones definidas por el usuario  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] admite el uso de procedimientos almacenados y funciones definidas por el usuario. Los procedimientos almacenados se utilizan con frecuencia para personalizar operaciones. Para obtener más información, vea [Procedimientos almacenados](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md).  
  
## <a name="see-also"></a>Vea también  
 [Personalización de operaciones de actualización, inserción y eliminación](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)
