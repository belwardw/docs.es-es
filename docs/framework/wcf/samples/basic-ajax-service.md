---
title: Servicio AJAX básico
ms.date: 03/30/2017
ms.assetid: d66d0c91-0109-45a0-a901-f3e4667c2465
ms.openlocfilehash: a534e4eda1f95cd33d4429fda23b6187caaf58ae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="basic-ajax-service"></a>Servicio AJAX básico
Este ejemplo muestra cómo usar Windows Communication Foundation (WCF) para crear un servicio básico de ASP.NET Asynchronous JavaScript y XML (AJAX) (es decir, un servicio que se puede tener acceso mediante código JavaScript de un cliente del explorador Web). El servicio utiliza el atributo <xref:System.ServiceModel.Web.WebGetAttribute> para asegurarse de que el servicio responde a las solicitudes HTTP GET y de que está configurado para utilizar el formato de datos de Notación de objeto de JavaScript (JSON) para las respuestas.  
  
 La compatibilidad de AJAX en [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] se optimiza para su uso con ASP.NET AJAX a través del control `ScriptManager`. Para obtener un ejemplo del uso de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] con AJAX de ASP.NET, vea el [muestra AJAX](http://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).  
  
> [!NOTE]
>  El procedimiento de instalación y las instrucciones de compilación de este ejemplo se encuentran al final de este tema.  
  
 En el código siguiente, el atributo <xref:System.ServiceModel.Web.WebGetAttribute> se aplica a la operación `Add` para asegurarse de que el servicio responde a las solicitudes HTTP GET. El código usa GET por simplicidad (puede construir una solicitud HTTP GET desde cualquier explorador web). También puede utilizar GET para habilitar el almacenamiento en caché. HTTP POST es el valor predeterminado en la ausencia del atributo `WebGetAttribute`.  

```csharp
[ServiceContract(Namespace = "SimpleAjaxService")]
public interface ICalculator
{
    [WebGet]
    double Add(double n1, double n2);
    //Other operations omitted…
}
```

 El archivo .svc de ejemplo utiliza <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, que agrega un extremo estándar <xref:System.ServiceModel.Description.WebScriptEndpoint> al servicio. El punto de conexión se configura en una dirección vacía relativa al archivo .svc. Esto significa que la dirección del servicio es http://localhost/ServiceModelSamples/service.svc, sin ningún sufijo adicional que no sea el nombre de la operación.  

```svc
<%@ServiceHost language="C#" Debug="true" Service="Microsoft.Samples.SimpleAjaxService.CalculatorService" Factory="System.ServiceModel.Activation.WebScriptServiceHostFactory" %>
```

 <xref:System.ServiceModel.Description.WebScriptEndpoint> se preconfigura de modo que el servicio esté accesible desde una página de cliente AJAX de ASP.NET. La siguiente sección de Web.config se puede utilizar para realizar cambios de configuración adicionales en el extremo. Se puede quitar si no se necesita ningún cambio adicional.  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>  
    <webScriptEndpoint>  
      <!-- Use this element to configure the endpoint -->  
      <standardEndpoint name=""  />  
    </webScriptEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 <xref:System.ServiceModel.Description.WebScriptEndpoint> establece el formato de datos predeterminado para el servicio en JSON en lugar de XML. Para invocar el servicio, vaya a http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200 después de completar el conjunto de seguridad y se muestra más adelante en este tema de pasos de compilación. El uso de una solicitud HTTP GET habilita esta funcionalidad de la prueba.  
  
 La página web del cliente SimpleAjaxClientPage.aspx contiene el código de ASP.NET para invocar el servicio siempre que el usuario haga clic en uno de los botones de operación en la página. El control `ScriptManager` se utiliza para hacer que un proxy al servicio sea accesible a través de JavaScript.  

```aspx-csharp
<asp:ScriptManager ID="ScriptManager" runat="server">  
    <Services>  
        <asp:ServiceReference Path="service.svc" />  
    </Services>  
</asp:ScriptManager>  
```

 Se crean instancias del proxy local y las operaciones se invocan utilizando el siguiente código de JavaScript.  

```javascript
// Code for extracting arguments n1 and n2 omitted…  
// Instantiate a service proxy  
var proxy = new SimpleAjaxService.ICalculator();  
// Code for selecting operation omitted…  
proxy.Add(parseFloat(n1), parseFloat(n2), onSuccess, onFail, null);  
```

 Si la llamada del servicio es correcta, el código invoca el controlador `onSuccess` y el resultado de la operación se muestra en un cuadro de texto.  

```javascript
function onSuccess(mathResult){  
     document.getElementById("result").value = mathResult;  
}
```

> [!IMPORTANT]
>  Puede que los ejemplos ya estén instalados en su equipo. Compruebe el siguiente directorio (predeterminado) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si este directorio no existe, vaya a [Windows Communication Foundation (WCF) y ejemplos de Windows Workflow Foundation (WF) para .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para descargar todos los Windows Communication Foundation (WCF) y [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ejemplos. Este ejemplo se encuentra en el siguiente directorio.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\SimpleAjaxService`  
  
## <a name="see-also"></a>Vea también
