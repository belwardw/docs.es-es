---
title: Proveedor de EntityClient para Entity Framework
ms.date: 03/30/2017
ms.assetid: 8c5db787-78e6-4a34-8dc1-188bca0aca5e
ms.openlocfilehash: bf3bf6fe0d0013b3e5b05ec697ad4f6a57459a6f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="entityclient-provider-for-the-entity-framework"></a>Proveedor de EntityClient para Entity Framework
El proveedor de EntityClient es un proveedor de datos que usan las aplicaciones de Entity Framework para tener acceso a los datos descritos en un modelo conceptual. Para obtener información acerca de los modelos conceptuales, consulte [de modelado y asignación](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md). EntityClient utiliza otros proveedores de datos .NET Framework para tener acceso al origen de datos. Por ejemplo, EntityClient utiliza el Proveedor de datos .NET Framework para SQL Server (SqlClient) al tener acceso a una base de datos de SQL Server. Para obtener información sobre el proveedor SqlClient, vea [SqlClient para Entity Framework](../../../../../docs/framework/data/adonet/ef/sqlclient-for-the-entity-framework.md). El proveedor de EntityClient se implementa en el espacio de nombres <xref:System.Data.EntityClient>.  
  
## <a name="managing-connections"></a>Administrar conexiones  
 El [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] se basa en específicos del almacenamiento [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] proveedores de datos proporcionando un <xref:System.Data.EntityClient.EntityConnection> a un proveedor de datos subyacente y la base de datos relacional. Para construir un <xref:System.Data.EntityClient.EntityConnection> objeto, tiene que hacer referencia a un conjunto de metadatos que contiene los modelos necesarios y asignación así como una cadena de conexión y nombre de proveedor de datos específicos del almacenamiento. Después de la <xref:System.Data.EntityClient.EntityConnection> está en su lugar, las entidades son accesibles a través de las clases generadas desde el modelo conceptual.  
  
 Se puede especificar una cadena de conexión en el archivo app.config.  
  
 El espacio de nombres <xref:System.Data.EntityClient> también incluye la clase <xref:System.Data.EntityClient.EntityConnectionStringBuilder>. Esta clase permite que los programadores creen mediante programación cadenas de conexión sintácticamente correctas, y que analicen y recompilen las cadenas de conexión existentes, utilizando las propiedades y los métodos de la clase. Para obtener más información, consulte [Cómo: crear una cadena de conexión EntityConnection](../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md).  
  
## <a name="creating-queries"></a>Crear consultas  
 El [!INCLUDE[esql](../../../../../includes/esql-md.md)] lenguaje es un dialecto independiente del almacenamiento de SQL que trabaja directamente con esquemas de entidades conceptuales y admite conceptos de Entity Data Model, como la herencia y relaciones. El <xref:System.Data.EntityClient.EntityCommand> clase se usa para ejecutar un [!INCLUDE[esql](../../../../../includes/esql-md.md)] comando con un modelo de entidades. Cuando se crean objetos de <xref:System.Data.EntityClient.EntityCommand>, se puede especificar un nombre de procedimiento almacenado o un texto de consulta. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] trabaja con proveedores de datos específicos del almacenamiento para traducir el [!INCLUDE[esql](../../../../../includes/esql-md.md)] genérico en consultas específicas del almacenamiento. Para obtener más información acerca de la escritura [!INCLUDE[esql](../../../../../includes/esql-md.md)] de las consultas, vea [lenguaje Entity SQL](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md).  
  
 En el ejemplo siguiente se crea un <xref:System.Data.EntityClient.EntityCommand> objeto y asigna un [!INCLUDE[esql](../../../../../includes/esql-md.md)] consultar texto a su <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType> propiedad. Esto [!INCLUDE[esql](../../../../../includes/esql-md.md)] consulta solicita productos ordenados por el precio de venta del modelo conceptual. El código siguiente no tiene conocimiento alguno del modelo de almacenamiento.  
  
 `EntityCommand cmd = conn.CreateCommand();`  
  
 `cmd.CommandText = @"` `SELECT VALUE p`  
  
 `FROM AdventureWorksEntities.Product AS p`  
  
 `ORDER BY p.ListPrice ";`  
  
## <a name="executing-queries"></a>Ejecutar consultas  
 Cuando se ejecuta una consulta, se analiza y se convierte en un árbol de comandos canónico. Todo el procesamiento subsiguiente se realiza en el árbol de comandos. El árbol de comandos es el medio de comunicación entre el espacio de nombres <xref:System.Data.EntityClient> y el proveedor de datos [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] subyacente, como <xref:System.Data.SqlClient>.  
  
 <xref:System.Data.EntityClient.EntityDataReader> muestra los resultados de ejecutar <xref:System.Data.EntityClient.EntityCommand> en un modelo conceptual. Para ejecutar el comando que devuelve el <xref:System.Data.EntityClient.EntityDataReader>, llame a <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A>. <xref:System.Data.EntityClient.EntityDataReader> implementa <xref:System.Data.IExtendedDataRecord> para describir resultados estructurados enriquecidos.  
  
## <a name="managing-transactions"></a>Administrar transacciones  
 En Entity Framework, hay dos maneras de utilizar las transacciones: automática y explícita. Las transacciones automáticas usan el espacio de nombres <xref:System.Transactions> y las transacciones explícitas usan la clase <xref:System.Data.EntityClient.EntityTransaction>.  
  
 Para actualizar los datos que se exponen a través de un modelo conceptual; vea [Cómo: administrar transacciones en Entity Framework](http://msdn.microsoft.com/library/4a55eb7f-f826-4a48-9df1-aebe2352ebef).  
  
## <a name="in-this-section"></a>En esta sección  
 [Compilación de una cadena de conexión EntityConnection](../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md)  
  
 [Ejecución de una consulta que devuelve resultados PrimitiveType](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)  
  
 [Ejecución de una consulta que devuelve resultados StructuralType](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)  
  
 [Ejecución de una consulta que devuelve resultados RefType](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-reftype-results.md)  
  
 [Ejecución de una consulta que devuelve tipos complejos](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-complex-types.md)  
  
 [Ejecución de una consulta que devuelve colecciones anidadas](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-nested-collections.md)  
  
 [Ejecución de una consulta parametrizada de Entity SQL usando EntityCommand](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-entity-sql-query-using-entitycommand.md)  
  
 [Ejecución de un procedimiento almacenado parametrizado usando EntityCommand](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-stored-procedure-using-entitycommand.md)  
  
 [Ejecución de una consulta polimórfica](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-polymorphic-query.md)  
  
 [Navegación por las relaciones con el operador Navigate](../../../../../docs/framework/data/adonet/ef/how-to-navigate-relationships-with-the-navigate-operator.md)  
  
## <a name="see-also"></a>Vea también  
 [Administrar conexiones y transacciones](http://msdn.microsoft.com/library/b6659d2a-9a45-4e98-acaa-d7a8029e5b99)  
 [ADO.NET Entity Framework](../../../../../docs/framework/data/adonet/ef/index.md)  
 [Referencia del lenguaje](../../../../../docs/framework/data/adonet/ef/language-reference/index.md)
