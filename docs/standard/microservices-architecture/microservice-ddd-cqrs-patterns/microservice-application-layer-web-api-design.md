---
title: Diseñar el nivel de aplicación de microservicios y la API web
description: Arquitectura de microservicios de .NET para aplicaciones .NET en contenedor | Diseñar el nivel de aplicación de microservicios y la API web
keywords: Docker, microservicios, ASP.NET, contenedor
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/12/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d623a3bc542e0f044d73f405aa639bef0f6d1ec8
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
---
# <a name="designing-the-microservice-application-layer-and-web-api"></a>Diseñar el nivel de aplicación de microservicios y la API web

## <a name="using-solid-principles-and-dependency-injection"></a>Uso de principios SOLID e inserción de dependencias

Los principios SOLID son técnicas fundamentales para utilizar en cualquier aplicación moderna y crítica, como para el desarrollo de un microservicio con patrones DDD. En inglés, SOLID representa un acrónimo que agrupa cinco principios fundamentales:

-   Principio de responsabilidad única

-   Principio de abierto y cerrado

-   Principio de sustitución de Liskov

-   Principio de segregación de interfaces

-   Principio de inversión de dependencias

SOLID hace referencia a la forma de diseñar los niveles internos de una aplicación o de un microservicio, así como a separar las dependencias entre ellas. No está relacionado con el dominio, sino con el diseño técnico de la aplicación. El principio final, el de inversión de dependencias, le permite desacoplar el nivel de infraestructura del resto de niveles, lo que permite una mejor implementación desacoplada de los niveles de DDD.

La inversión de dependencias es una forma de implementar el principio de inversión de dependencias. Es una técnica para lograr el acoplamiento flexible entre los objetos y sus dependencias. En lugar de crear directamente instancias de colaboradores o de usar referencias estáticas, los objetos que una clase necesita para llevar a cabo sus acciones se proporcionan (o se "insertan") a dicha clase. A menudo, las clases declaran sus dependencias a través de su constructor, lo que les permite seguir el principio de dependencias explícitas. Normalmente la inversión de dependencias está basada en determinados contenedores de Inversión de control (IoC). ASP.NET Core proporciona un sencillo contenedor de IoC integrado. Aun así, usted puede usar el contenedor de IoC que prefiera, como Autofac o Ninject.

Siguiendo los principios SOLID, las clases tenderán naturalmente a ser pequeñas, a estar factorizadas correctamente y a poder probarse fácilmente. Pero, ¿cómo puede saber si se van a insertar demasiadas dependencias en sus clases? Si usa la inversión de dependencias a través del constructor, le resultará fácil saberlo con solo mirar el número de parámetros de su constructor. Si hay demasiadas dependencias, esto suele ser una señal (una [intuición de código](http://deviq.com/code-smells/)) de que su clase está intentando hacer demasiado y de que probablemente esté infringiendo el principio de responsabilidad única.

Necesitaríamos otra guía para tratar SOLID con detalle. Para esta guía solo necesita tener unos conocimientos mínimos de estos temas.

#### <a name="additional-resources"></a>Recursos adicionales

-   **SOLID: Fundamental OOP Principles**
    [*http://deviq.com/solid/*](http://deviq.com/solid/%20) (SOLID: principios fundamentales de OOP)

-   **Inversion of Control Containers and the Dependency Injection pattern**
    [*https://martinfowler.com/articles/injection.html*](https://martinfowler.com/articles/injection.html) (Inversión de los contenedores de control y el patrón de inserción de dependencias)

-   **Steve Smith. New is Glue**
    [*https://ardalis.com/new-is-glue*](https://ardalis.com/new-is-glue) (New es como pegamento)


>[!div class="step-by-step"]
[Anterior] (nosql-database-persistence-infrastructure.md) [Siguiente] (microservice-application-layer-implementation-web-api.md)
