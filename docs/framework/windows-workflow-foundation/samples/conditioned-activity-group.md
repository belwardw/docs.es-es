---
title: Grupo de actividad condicionado
ms.date: 03/30/2017
ms.assetid: f76ef924-34ce-48ae-8c8d-48faf9697754
ms.openlocfilehash: 3560542b912f9697ec2e77c8d5c82e148a41d485
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="conditioned-activity-group"></a>Grupo de actividad condicionado
En el ejemplo se muestra una aplicación de reservas de viajes. La actividad <xref:System.Workflow.Activities.ConditionedActivityGroup> (CAG) tiene dos actividades de código: una actividad Car y una actividad Airline. En el constructor `SimpleCAGWorkflow`, el objeto de ArrayList "travelNeedType" se rellena con los tipos de reserva de viajes que se requieren. Si se escribe un comentario en una de las instrucciones `travelNeeds.Add`, o en las dos, se modifica el comportamiento de CAG en consecuencia. Las actividades Car y Airline tienen la condición <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty> con detalles de <xref:System.Workflow.Activities.CodeCondition>. La actividad Car solo se ejecuta si la colección `travelNeeds` tiene una entrada `TravelNeeds.Car`, y la actividad Airline solo se ejecuta si la colección `travelNeeds` tiene una entrada `TravelNeeds.Airline`.  
  
 La ejecución de cada actividad quita la entrada correspondiente de la colección. La condición <xref:System.Workflow.Activities.ConditionedActivityGroup.UntilCondition%2A> predeterminada especifica que CAG se debe cerrar cuando no se está ejecutando ningún elemento secundario ni están listos para la ejecución (en función de sus condiciones <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty>). En este ejemplo, esto significa que CAG se cierra cuando la colección `travelNeeds` está vacía.  
  
### <a name="to-build-the-sample"></a>Para compilar el ejemplo  
  
1.  Abra la solución en [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Compile la solución presionando CTRL+MAYÚS+B.  
  
3.  Ejecute la solución sin depuración presionando CTRL+F5.  
  
### <a name="to-run-the-sample"></a>Para ejecutar el ejemplo  
  
-   En la ventana del símbolo del sistema del SDK, ejecute el archivo .exe de la carpeta SimpleCAG\bin\debug (o la carpeta SimpleCAG\bin para la versión de Visual Basic del ejemplo), que se encuentra debajo de la carpeta principal del ejemplo.  
  
> [!IMPORTANT]
>  Puede que los ejemplos ya estén instalados en su equipo. Compruebe el siguiente directorio (predeterminado) antes de continuar:  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si este directorio no existe, vaya a [Windows Communication Foundation (WCF) y ejemplos de Windows Workflow Foundation (WF) para .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para descargar todos los Windows Communication Foundation (WCF) y [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ejemplos. Este ejemplo se encuentra en el siguiente directorio:  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\SimpleCAG`  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Workflow.Activities.ConditionedActivityGroup>  
 <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty>  
 <xref:System.Workflow.Activities.CodeCondition>  
 <xref:System.Workflow.Activities.ConditionedActivityGroup.UntilCondition%2A>
