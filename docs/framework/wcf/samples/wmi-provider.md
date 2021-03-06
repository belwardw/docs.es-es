---
title: Proveedor WMI
ms.date: 03/30/2017
ms.assetid: 462f0db3-f4a4-4a4b-ac26-41fc25c670a4
ms.openlocfilehash: 202923ab1d09b0ce836dbfce7360dd22a479a900
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="wmi-provider"></a>Proveedor WMI
Este ejemplo muestra cómo recopilar los datos de servicios de Windows Communication Foundation (WCF) en tiempo de ejecución mediante el proveedor de Instrumental de administración de Windows (WMI) que está integrado en [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Asimismo, este ejemplo muestra cómo agregar un objeto WMI definido por el usuario a un servicio. El ejemplo activa el proveedor WMI para la [Introducción](../../../../docs/framework/wcf/samples/getting-started-sample.md) y muestra cómo recopilar datos de la `ICalculator` servicio en tiempo de ejecución.  
  
 WMI es la implementación de Microsoft del estándar Web-Based Enterprise Management (WBEM). Para obtener más información sobre el SDK de WMI, consulte [Windows Management Instrumentation](https://msdn.microsoft.com/library/aa394582.aspx). WBEM es un estándar de la industria para saber cómo exponen las aplicaciones la instrumentación de administración a las herramientas de administración externas.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementa un proveedor de WMI, un componente que expone la instrumentación en el tiempo de ejecución a través de una interfaz compatible con WBEM. Las herramientas de administración pueden conectarse a los servicios a través de la interfaz en tiempo de ejecución. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] expone atributos de servicios como direcciones, enlaces, comportamientos y agentes de escucha.  
  
 El proveedor de WMI integrado se activa en el archivo de configuración de la aplicación. Esto se realiza a través de la `wmiProviderEnabled` atributo de la [ \<diagnóstico >](../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md) en el [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) sección, como se muestra en el ejemplo siguiente configuración:  
  
```xml  
<system.serviceModel>  
    ...  
    <diagnostics wmiProviderEnabled="true" />  
    ...  
</system.serviceModel>  
```  
  
 Esta entrada de configuración expone una interfaz WMI. Ahora, las aplicaciones de administración pueden establecer la conexión a través de esta interfaz y obtener acceso a la instrumentación de administración de la aplicación.  
  
## <a name="custom-wmi-object"></a>Objeto WMI personalizado  
 Agregar objetos WMI a un servicio permite revelar la información definida por el usuario junto con la información de proveedor WMI integrada. Esto se logra publicando el esquema del servicio en WMI mediante la aplicación Installutil.exe. Las instrucciones para conseguirlo, además de más información, se pueden encontrar en las instrucciones de configuración al final del tema.  
  
## <a name="accessing-wmi-information"></a>Acceso a la información de WMI  
 Se puede tener acceso a los datos de WMI de maneras muy distintas. Microsoft proporciona las API de WMI para scripts, aplicaciones de Visual Basic, aplicaciones de C++ y la [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] (http://msdn.microsoft.com/library/default.asp?url=/library/wmisdk/wmi/using_wmi.asp).  
  
 Este ejemplo utiliza dos scripts Java: uno para enumerar los servicios que se ejecutan en el equipo junto con algunas de sus propiedades y otro para ver los datos de WMI definidos por el usuario. El script abre una conexión con el proveedor WMI, analiza los datos y muestra los datos recopilados.  
  
 Inicie el ejemplo para crear una instancia en ejecución de un servicio [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Mientras el servicio se está ejecutando, ejecute cada script de Java usando el comando siguiente en el símbolo del sistema:  
  
```  
cscript EnumerateServices.js  
```  
  
 El script obtiene acceso al instrumental contenido en el servicio y genera la salida siguiente:  
  
```  
Microsoft (R) Windows Script Host Version 5.6  
Copyright © Microsoft Corporation 1996-2001. All rights reserved.  
  
1 service(s) found.  
|-PID:           5776  
|-DistinguishedName:  CalculatorService@http://localhost/ServiceModelSamples/service.svc  
|-Endpoints:     1 endpoints  
  |-CalculatorService.ICalculator@http://localhost/ServiceModelSamples/service.svc  
    |-Address:                        http://localhost/ServiceModelSamples/service.svc  
    |-CounterInstanceName:  
    |-AddressHeaders:                 0  
    |-ContractType:                   Contract.Name='ICalculator'  
    |-BindingElements:                4 bindings  
      |-BindingElements[0]  
        |-Type:                       TransactionFlowBindingElement  
      |-BindingElements[1]  
        |-Type:                       SymmetricSecurityBindingElement  
      |-BindingElements[2]  
        |-Type:                       TextMessageEncodingBindingElement  
        |-MaxReadPoolSize:            64  
        |-MaxWritePoolSize:           16  
      |-BindingElements[3]  
        |-Type:                       HttpTransportBindingElement  
        |-ManualAddressing:           false  
        |-MaxBufferSize:              65536  
        |-AllowCookies:               false  
        |-AuthenticationScheme:       Anonymous  
        |-BypassProxyOnLocal:         false  
        |-HostNameComparisonMode:     StrongWildcard  
        |-ProxyAddress:               null  
        |-ProxyAuthenticationScheme:  Anonymous  
        |-Realm:  
        |-TransferMode:               Buffered  
        |-UseDefaultWebProxy:         true  
|-Behaviors:     5 behaviors  
      |-Behavior[0]  
      |-Type:                       ServiceBehaviorAttribute  
        |-AddressFilterMode:               Exact  
        |-AutomaticSessionShutdown:        true  
        |-ConcurrencyMode:                 Single  
        |-IncludeExceptionDetailInFaults:  false  
        |-InstanceContextMode:             PerSession  
        |-TransactionIsolationLevel:       Unspecified  
        |-TransactionTimeout:              null  
        |-ValidateMustUnderstand:          true  
      |-Behavior[1]  
      |-Type:                       AspNetCompatibilityRequirementsAttribute  
      |-Behavior[2]  
      |-Type:                       ServiceDebugBehavior  
      |-Behavior[3]  
      |-Type:                       ServiceAuthorizationBehavior  
      |-Behavior[4]  
      |-Type:                       Behavior  
```  
  
 Después, ejecute el segundo script de Java para mostrar los datos de WMI definidos por el usuario:  
  
```  
cscript EnumerateCustomObjects.js  
```  
  
 El script tiene acceso al instrumental definido por el usuario contenido en los servicios y genera el resultado siguiente:  
  
```  
1 WMIObject(s) found.  
|-PID:           30285bfd-9d66-4c4e-9be2-310499c5cef5  
|-InstanceId:    3839  
|-WMIInfo:       User Defined WMI Information.  
```  
  
 El resultado muestra que hay un único servicio que se ejecuta en el equipo. El servicio expone un extremo que implementa el contrato `ICalculator`. Los valores del comportamiento y el extremo que el extremo implementa se muestran como la suma de elementos individuales de la pila de mensajería.  
  
 WMI no se limita a exponer el instrumental de administración de la infraestructura [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. La aplicación puede exponer sus propios elementos de datos específicos del dominio a través del mismo mecanismo. WMI es un mecanismo unificado para la inspección y control de un servicio Web.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Configurar, compilar y ejecutar el ejemplo  
  
1.  Asegúrese de que ha llevado a cabo la [procedimiento de instalación de un solo uso para los ejemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para compilar el código C# o Visual Basic .NET Edition de la solución, siga las instrucciones de [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Publique el esquema de los servicios en WMI ejecutando InstallUtil.exe (las ubicaciones predeterminadas para Installutil.exe son "%WINDIR%\Microsoft.NET\Framework\v4.0.30319") en el archivo service.dll del directorio de hospedaje. Este paso solo debe ejecutarse cuando se hayan realizado cambios en el archivo service.dll. Para obtener más información, vea proporcionar información de administración mediante la instrumentación de aplicaciones en: http://msdn2.microsoft.com/library/ms186147.aspx en la sección "Cómo para: publicar el esquema a WMI para una aplicación instrumentada".  
  
4.  Para ejecutar el ejemplo en una configuración de equipo único o varios, siga las instrucciones de [ejecutando los ejemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
    > [!NOTE]
    >  Si instaló [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] después de instalar ASP.NET, es posible que necesite ejecutar "%WINDIR%\ Microsoft.Net\Framework\v3.0\Windows Communication Foundation\servicemodelreg.exe " -r -x para proporcionar a la cuenta de ASPNET permiso para publicar objetos WMI.  
  
5.  Vea los datos del ejemplo que aparece mediante WMI con los comandos: `cscript EnumerateServices.js` o `cscript EnumerateCustomObjects.js`.  
  
> [!IMPORTANT]
>  Puede que los ejemplos ya estén instalados en su equipo. Compruebe el siguiente directorio (predeterminado) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si este directorio no existe, vaya a [Windows Communication Foundation (WCF) y ejemplos de Windows Workflow Foundation (WF) para .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para descargar todos los Windows Communication Foundation (WCF) y [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ejemplos. Este ejemplo se encuentra en el siguiente directorio.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\WMIProvider`  
  
## <a name="see-also"></a>Vea también  
 [Ejemplos de supervisión de AppFabric](http://go.microsoft.com/fwlink/?LinkId=193959)
