---
title: 'Cómo: Configurar el seguimiento con WorkflowServiceHost'
ms.date: 03/30/2017
ms.assetid: ed1485fe-7529-4351-bca3-8bb915260b17
ms.openlocfilehash: 56b9f95019995cdb55ec36769ff179ce1125c4b6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-configure-tracking-with-workflowservicehost"></a>Cómo: Configurar el seguimiento con WorkflowServiceHost
En este tema, se explica cómo configurar el seguimiento para un flujo de trabajo [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] hospedado en <xref:System.ServiceModel.Activities.WorkflowServiceHost>. Se configura a través de un archivo Web.config especificando un comportamiento de servicio.  
  
### <a name="configure-tracking-in-configuration"></a>Configurar el seguimiento en la configuración  
  
1.  Agregue <xref:System.Activities.Tracking.EtwTrackingParticipant> mediante el elemento <`behavior`> en un archivo de configuración, como se muestra en el siguiente ejemplo.  
  
    ```xml  
    <behaviors>  
       <serviceBehaviors>  
         <behavior>  
           <etwTracking profileName="Sample Tracking Profile" />  
         </behavior>              
       </serviceBehaviors>  
    <behaviors>  
    ```  
  
    > [!NOTE]
    >  En el ejemplo de configuración anterior, se usa la configuración simplificada. Para obtener más información, consulte [configuración simplificada](../../../../docs/framework/wcf/simplified-configuration.md).  
  
     El ejemplo de configuración anterior agrega <xref:System.Activities.Tracking.EtwTrackingParticipant> y especifica un nombre del perfil de seguimiento. Se crean perfiles de seguimiento en un elemento <`trackingProfile`> dentro de un elemento<`tracking`>. El perfil de seguimiento contiene consultas de seguimiento que permiten a un participante de seguimiento suscribirse a eventos de flujo de trabajo que se emiten cuando el estado de una instancia de flujo de trabajo cambia en el tiempo de ejecución. En el siguiente ejemplo, se muestra cómo crear un perfil de seguimiento.  
  
    ```xml  
    <system.serviceModel>  
        <tracking>   
         <trackingProfile name="Sample Tracking Profile">  
            <workflow activityDefinitionId="*">  
               <workflowInstanceQueries>  
                 <workflowInstanceQuery>  
                    <states>  
                       <state name="Started"/>  
                       <state name="Completed"/>  
                    </states>  
                </workflowInstanceQuery>  
             </workflowInstanceQueries>  
           </workflow>  
         </trackingProfile>   
       </tracking>  
    </system.serviceModel>  
    ```  
  
     Para obtener más información acerca de los perfiles de seguimiento, vea [perfiles de seguimiento](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).  
  
     Para obtener más información acerca del seguimiento en general, vea [seguimiento y traza del flujo de trabajo](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).  
  
### <a name="configure-tracking-in-code"></a>Configurar el seguimiento en el código  
  
1.  Agregue el objeto <xref:System.Activities.Tracking.EtwTrackingParticipant> con el comportamiento <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior> en el código, según se muestra en el código siguiente.  
  
    ```csharp  
    host.Description.Behaviors.Add(new EtwTrackingBehavior { ProfileName = "Sample Tracking Profile" });  
    ```  
  
     El ejemplo de código anterior agrega un objeto <xref:System.Activities.Tracking.EtwTrackingParticipant> y especifica un nombre del perfil de seguimiento. Los perfiles de seguimiento se crean en un elemento <`trackingProfile`> dentro de un elemento <`tracking`> según se muestra en la sección anterior.  
  
     Para obtener más información acerca de los perfiles de seguimiento, vea [perfiles de seguimiento](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).  
  
     Para obtener más información acerca del seguimiento en general, vea [seguimiento y traza del flujo de trabajo](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md). Para obtener un ejemplo de configuración de seguimiento mediante programación, vea [configuración del seguimiento para un flujo de trabajo](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).  
  
## <a name="see-also"></a>Vea también  
 [Configuración simplificada de los servicios WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)  
 [Servicios de flujo de trabajo](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [Perfiles de seguimiento](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
