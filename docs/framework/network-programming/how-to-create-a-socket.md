---
title: "Cómo crear un socket"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- Networking
- sending data, sockets
- data requests, sockets
- requesting data from Internet, sockets
- Socket class, creating sockets
- Network Resources
- receiving data, sockets
- protocols, sockets
- Internet, sockets
- sockets, creating
ms.assetid: c64a049c-5981-43bc-a2dc-1851473589c7
caps.latest.revision: "7"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 24ec39798f5f31cf20cc5c84714efaae6ccbed52
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-socket"></a>Cómo crear un socket
Para poder usar un socket a fin de comunicarse con dispositivos remotos, es necesario inicializarlo con la información del protocolo y de la dirección de red. El constructor para la clase <xref:System.Net.Sockets.Socket> tiene parámetros que especifican la familia de direcciones, el tipo de socket y el tipo de protocolo que el socket usa para establecer conexiones.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se crea un socket que se puede usar para comunicarse en una red basada en TCP/IP, como Internet.  
  
```csharp  
Socket s = new Socket(AddressFamily.InterNetwork,   
   SocketType.Stream, ProtocolType.Tcp);  
```  
  
```vb  
Dim s as New Socket(AddressFamily.InterNetwork, _  
   SocketType.Stream, ProtocolType.Tcp)  
```  
  
 Para usar UDP en lugar de TCP, cambie el tipo de protocolo, como en el ejemplo siguiente:  
  
```csharp  
Socket s = new Socket(AddressFamily.InterNetwork,   
   SocketType.Dgram, ProtocolType.Udp);  
```  
  
```vb  
Dim s as New Socket(AddressFamily.InterNetwork, _  
   SocketType.Dgram, ProtocolType.Udp)  
```  
  
 La enumeración <xref:System.Net.Sockets.AddressFamily> especifica las familias de direcciones estándar usadas por la clase **Socket** para resolver direcciones de red (por ejemplo, el miembro **AddressFamily.InterNetwork** especifica la familia de direcciones IP de versión 4).  
  
 La enumeración <xref:System.Net.Sockets.SocketType> especifica el tipo de socket (por ejemplo, el miembro **SocketType.Stream** indica un socket estándar para enviar y recibir datos con control de flujo).  
  
 La enumeración <xref:System.Net.Sockets.ProtocolType> especifica el protocolo de red que se va a usar al comunicarse en el **Socket** (por ejemplo, **ProtocolType.Tcp** indica que el socket usa TCP y **ProtocolType.Udp** indica que el socket usa UDP).  
  
 Una vez que se ha creado un **socket**, puede iniciar una conexión con un punto de conexión remoto o recibir conexiones procedentes de dispositivos remotos.  
  
## <a name="see-also"></a>Vea también  
 [Uso de sockets de cliente](../../../docs/framework/network-programming/using-client-sockets.md)  
 [Escuchas con sockets](../../../docs/framework/network-programming/listening-with-sockets.md)
