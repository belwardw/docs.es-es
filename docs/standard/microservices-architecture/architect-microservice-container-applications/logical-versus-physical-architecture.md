---
title: "Arquitectura lógica frente a arquitectura física"
description: "Arquitectura de microservicios de .NET para aplicaciones .NET en contenedores | Arquitectura lógica frente a arquitectura física"
keywords: Docker, microservicios, ASP.NET, contenedor
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: b08a5b8fb8f9df8a9a0a821fa85f1f6a94fce2d3
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/23/2017
---
# <a name="logical-architecture-versus-physical-architecture"></a>Arquitectura lógica frente a arquitectura física

Es útil en este momento detenerse y analizar la diferencia entre la arquitectura lógica y la arquitectura física y cómo se aplica al diseño de aplicaciones basadas en microservicios.

Para empezar, para generar microservicios no es necesario usar ninguna tecnología específica. Por ejemplo, los contenedores de Docker no son obligatorios para crear una arquitectura basada en microservicios. Esos microservicios también se pueden ejecutar como procesos sin formato. Los microservicios son una arquitectura lógica.

Además, incluso cuando un microservicio podría implementarse físicamente como un servicio, proceso o contenedor único (para simplificar, es el enfoque adoptado en la versión inicial de [eShopOnContainers](http://aka.ms/MicroservicesArchitecture)), esta paridad entre microservicio empresarial y servicio o contenedor físico no es necesaria en todos los casos al compilar una aplicación grande y compleja formada por muchas docenas o incluso cientos de servicios.

Aquí es donde hay una diferencia entre la arquitectura lógica y la arquitectura física de una aplicación. La arquitectura lógica y los límites lógicos de un sistema no se asignan necesariamente uno a uno a la arquitectura física o de implementación. Esto puede suceder, pero a menudo no es así.

Aunque pueda haber identificado determinados microservicios o contextos limitados empresariales, esto no significa que la mejor manera de implementarlos sea siempre mediante la creación de un servicio único (como una ASP.NET Web API) o un contenedor de Docker único para cada microservicio empresarial. Tener una regla que indique que cada microservicio empresarial debe implementarse mediante un único servicio o contenedor es demasiado rígido.

Por tanto, un microservicio o contexto limitado empresarial es una arquitectura lógica que podría coincidir (o no) con la arquitectura física. Lo importante es que un microservicio o contexto limitado empresarial debe ser autónomo y permitir que el código y el estado se versioneen, implementen y escalen de forma independiente.

Como se muestra en la figura 4-8, el microservicio empresarial de catálogo podría estar compuesto de varios servicios o procesos. Estos podrían ser varios servicios de ASP.NET Web API o cualquier otro tipo de servicio que use HTTP o cualquier otro protocolo. Lo más importante es que los servicios puedan compartir los mismos datos, siempre y cuando estos servicios sean cohesivos con relación al mismo dominio empresarial.

![](./media/image8.png)

**Figura 4-8**. Microservicio empresarial con varios servicios físicos

Los servicios del ejemplo comparten el mismo modelo de datos porque el servicio Web API tiene como destino los mismos datos que el servicio Search. Por tanto, en la implementación física del microservicio empresarial, debe dividir esa función de manera que pueda escalar cada uno de esos servicios internos horizontal o verticalmente según sea necesario. Quizá el servicio Web API normalmente necesita más instancias que el servicio Search, o viceversa.

En resumen, la arquitectura lógica de los microservicios no siempre tiene que coincidir con la arquitectura de implementación física. En esta guía, siempre que se mencione un microservicio, se entiende que es un microservicio empresarial o lógico que se puede asignar a uno o más servicios. En la mayoría de los casos, se trata de un servicio único, pero puede que sean más.


>[!div class="step-by-step"]
[Previous] (data-sovereignty-per-microservice.md) [Next] (distributed-data-management.md)
