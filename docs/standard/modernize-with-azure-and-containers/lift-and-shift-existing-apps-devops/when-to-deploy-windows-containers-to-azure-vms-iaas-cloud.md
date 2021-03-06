---
title: Cuándo se debe implementar contenedores de Windows en máquinas virtuales de Azure (IaaS nube)
description: Arquitectura de Microservicios de .NET para aplicaciones .NET en contenedores | Cuándo se debe implementar contenedores de Windows en máquinas virtuales de Azure (IaaS nube)
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.prod: .net
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d1a9f0593b4b84cbe25da9e4164f4ecbe8513831
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
---
# <a name="when-to-deploy-windows-containers-to-azure-vms-iaas-cloud"></a>Cuándo se debe implementar contenedores de Windows en máquinas virtuales de Azure (IaaS nube)

Si su organización está usando máquinas virtuales de Azure, incluso si también usa contenedores de Windows, siguen siendo ocuparse de IaaS. Esto significa que tratar con las operaciones de infraestructura, revisiones del sistema operativo de la máquina virtual y complejidad de la infraestructura para aplicaciones muy escalables cuando necesite implementar en varias máquinas virtuales en una infraestructura con equilibrio de carga. Los escenarios principales para usar los contenedores de Windows en una máquina virtual de Azure son:

-   **Entorno de desarrollo/pruebas**: una VM en la nube es ideal para desarrollo y pruebas en la nube. Puede crear rápidamente o detener el entorno según sus necesidades.

-   **Escalabilidad pequeña y mediana necesita**: en escenarios donde podría necesitar un par de máquinas virtuales para su entorno de producción, administra un pequeño número de máquinas virtuales podría estar asequible hasta que puede mover a los entornos de PaaS más avanzados, como orchestrators.

-   **Entorno de producción con las herramientas de implementación existentes**: pueden mover desde un entorno local en el que se ha invertido en herramientas para realizar las implementaciones complejas en las máquinas virtuales o servidores de reconstrucción completa (por ejemplo, Puppet o herramientas similares). Para mover a la nube con unos cambios mínimos en los procedimientos de implementación del entorno de producción, puede continuar usar estas herramientas para implementar en máquinas virtuales de Azure. Sin embargo, conviene utilizar contenedores de Windows como la unidad de implementación para mejorar la experiencia de implementación.

>[!div class="step-by-step"]
[Anterior](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
[Siguiente](when-to-deploy-windows-containers-to-service-fabric.md)
