---
title: '&lt;issuedTokenParameters&gt;'
ms.date: 03/30/2017
ms.assetid: 120b3f37-7331-4816-b712-d6aab39655a4
ms.openlocfilehash: 550b3412b193b996b8de800856d6833369fc4bc7
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="ltissuedtokenparametersgt"></a>&lt;issuedTokenParameters&gt;
Especifica los parámetros para un token de seguridad emitido en un escenario de seguridad aliado.  
  
 \<system.serviceModel>  
\<enlaces >  
\<customBinding >  
\<enlace >  
\<seguridad >  
\<issuedTokenParameters >  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
<issuedTokenParameters   
      DefaultMessageSecurityVersion="System.ServiceModel.MessageSecurityVersion"  
      inclusionMode="AlwaysToInitiator/AlwaysToRecipient/Never/Once"  
      keySize="Integer"  
   keyType="AsymmetricKey/BearerKey/SymmetricKey"  
      tokenType="String" >  
   <additionalRequestParameters />  
      <claimTypeRequirements>  
            <add claimType="URI"  
           isOptional="Boolean" />  
      </claimTypeRequirements>  
      <issuer address="String"   
                      binding=" " />  
      <issuerMetadata address="String" />   
</issuedTokenParameters>  
```  
  
## <a name="type"></a>Tipo  
 `Type`  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|defaultMessageSecurityVersion|Especifica las versiones de las especificaciones de seguridad, (WS-Security, WS-Trust, WS-Secure Conversation y WS-Security Policy) que debe admitir el enlace. Este valor es del tipo <xref:System.ServiceModel.MessageSecurityVersion>.|  
|inclusionMode|Especifica los requisitos de inclusión del token. Este atributo es del tipo <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>.|  
|keySize|Un entero que especifica el tamaño de la clave del token. El valor predeterminado es 256.|  
|keyType|Una valor válido de <xref:System.IdentityModel.Tokens.SecurityKeyType> que especifica el tipo de clave. De manera predeterminada, es `SymmetricKey`.|  
|tokenType|Una cadena que representa el tipo de token. El valor predeterminado es "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML".|  
  
### <a name="child-elements"></a>Elementos secundarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[\<additionalRequestParameters >](../../../../../docs/framework/configure-apps/file-schema/wcf/additionalrequestparameters-element.md)|Una colección de elementos de configuración que especifican los parámetros de solicitud adicionales.|  
|[\<claimTypeRequirements >](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)|Especifica una colección de tipos de notificación requeridos.<br /><br /> En un escenario aliado, los servicios indican los requisitos de las credenciales de entrada. Por ejemplo, las credenciales de entrada deben poseer un determinado conjunto de tipos de notificación. Cada elemento de la colección especifica los tipos de notificaciones necesarias y opcionales que se espera que aparezcan en una credencial aliada.|  
|[\<emisor >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuer-of-issuedtokenparameters.md)|Un elemento de configuración que especifica el punto de conexión que emite el token actual.|  
|[\<issuerMetadata>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata-of-issuedtokenparameters.md)|Un elemento de configuración que especifica la dirección del punto de conexión de los metadatos del emisor del token.|  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[\<secureConversationBootstrap >](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)|Especifica los valores predeterminados usados para iniciar un servicio de conversación seguro.|  
|[\<seguridad >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)|Especifica las opciones de seguridad de un enlace personalizado.|  
  
## <a name="see-also"></a>Vea también  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>  
 <xref:System.ServiceModel.Configuration.SecurityElementBase.IssuedTokenParameters%2A>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [Enlaces](../../../../../docs/framework/wcf/bindings.md)  
 [Extensión de enlaces](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Enlaces personalizados](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [Creación de un enlace personalizado mediante SecurityBindingElement](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [Seguridad de enlace personalizado](../../../../../docs/framework/wcf/samples/custom-binding-security.md)  
 [Identidad del servicio y autenticación](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [Federación y tokens emitidos](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [Funcionalidades de seguridad con enlaces personalizados](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [Federación y tokens emitidos](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
