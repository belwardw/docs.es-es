---
title: 'Cómo: Crear un autenticador de tokens de seguridad personalizado'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, authentication
ms.assetid: 10e245f7-d31e-42e7-82a2-d5780325d372
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 41936b407dfdb3fecee80b2513b557016cdcfe5e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-custom-security-token-authenticator"></a>Cómo: Crear un autenticador de tokens de seguridad personalizado
En este tema se muestra cómo crear un autenticador de tokens de seguridad personalizado y cómo integrarlo con un administrador de tokens de seguridad personalizado. Un autenticador de tokens de seguridad valida el contenido de un token de seguridad proporcionado con un mensaje entrante. Si la validación es correcta, el autenticador devuelve una colección de instancias <xref:System.IdentityModel.Policy.IAuthorizationPolicy> que, cuando se evalúa, devuelve un conjunto de notificaciones.  
  
 Para utilizar un autenticador de tokens de seguridad personalizado en Windows Communication Foundation (WCF), primero debe crear credenciales personalizadas y seguridad de las implementaciones de administrador de tokens. Para obtener más información acerca de cómo crear credenciales personalizadas y seguridad Administrador de tokens, consulte [Tutorial: creación de cliente personalizada y las credenciales de servicio](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md). Para obtener más información sobre las credenciales, Administrador de tokens de seguridad y las clases de proveedor y el autenticador, vea [arquitectura de seguridad](http://msdn.microsoft.com/library/16593476-d36a-408d-808c-ae6fd483e28f).  
  
## <a name="procedures"></a>Procedimientos  
  
#### <a name="to-create-a-custom-security-token-authenticator"></a>Para crear un autenticador de token de seguridad personalizado  
  
1.  Defina una clase nueva derivada de la clase <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator>.  
  
2.  Invalide el método <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator.CanValidateTokenCore%2A>. El método devuelve `true` o `false` en función de si el autenticador personalizado puede validar el tipo de token entrante o no.  
  
3.  Invalide el método <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator.ValidateTokenCore%2A>. Este método necesita validar adecuadamente el contenido del token. Si el token pasa la fase de la validación, devuelve una colección de instancias <xref:System.IdentityModel.Policy.IAuthorizationPolicy>. El ejemplo siguiente utiliza una implementación de la directiva de autorización personalizada que se creará en el procedimiento siguiente.  
  
     [!code-csharp[C_CustomTokenAuthenticator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenauthenticator/cs/source.cs#1)]
     [!code-vb[C_CustomTokenAuthenticator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenauthenticator/vb/source.vb#1)]  
  
 El código anterior devuelve una colección de directivas de autorización en el método <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator.CanValidateToken%28System.IdentityModel.Tokens.SecurityToken%29>. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] no proporciona una implementación pública de esta interfaz. El procedimiento siguiente muestra cómo hacer esto para sus propios requisitos.  
  
#### <a name="to-create-a-custom-authorization-policy"></a>Para crear una directiva de autorización personalizada  
  
1.  Defina una nueva clase que implementa la interfaz <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.  
  
2.  Implemente la propiedad de solo lectura <xref:System.IdentityModel.Policy.IAuthorizationComponent.Id%2A>. Una manera de implementar esta propiedad es generar un identificador único global (GUID) en el constructor de clase y devolverlo cada vez que se solicita el valor para esta propiedad.  
  
3.  Implemente la propiedad de solo lectura <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Issuer%2A>. Esta propiedad necesita devolver un emisor de los conjuntos de notificaciones que se obtienen del token. Este emisor debería corresponderse con el emisor del token o con una autoridad que sea responsable de validar el contenido del token. El ejemplo siguiente utiliza la notificación del emisor que se pasó a esta clase desde el autenticador de tokens de seguridad personalizado creado en el procedimiento anterior. El autenticador de tokens de seguridad personalizado utiliza el conjunto de notificaciones proporcionado por el sistema (devuelto por la propiedad <xref:System.IdentityModel.Claims.ClaimSet.System%2A>) para representar el emisor del token del nombre de usuario.  
  
4.  Implemente el método <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%2A>. Este método rellena una instancia de la clase <xref:System.IdentityModel.Policy.EvaluationContext> (pasadas como argumento) con notificaciones basadas en el contenido del token de seguridad entrante. El método devuelve `true` cuando se hace con la evaluación. En los casos en los que la implementación confía en la presencia de otras directivas de autorización que proporcionan información adicional al contexto de la evaluación, este método puede devolver `false` si la información necesaria no se encuentra todavía en el contexto de la evaluación. En ese caso, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] llamará de nuevo al método después de evaluar el resto de las directivas de autorización generadas para el mensaje entrante si, por lo menos, una de esas directivas de autorización modificó el contexto de evaluación.  
  
     [!code-csharp[c_CustomTokenAuthenticator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenauthenticator/cs/source.cs#2)]
     [!code-vb[c_CustomTokenAuthenticator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenauthenticator/vb/source.vb#2)]  
  
 [Tutorial: Crear personalizado credenciales de cliente y servicio](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md) describe cómo crear credenciales personalizadas y seguridad personalizado, Administrador de tokens. Para utilizar el autenticador de tokens de seguridad personalizado creado aquí, se modificará una implementación del administrador de tokens de seguridad para devolver el autenticador personalizado desde el método <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenAuthenticator%2A>. El método devuelve un autenticador cuando se pasa un requisito de token de seguridad adecuado.  
  
#### <a name="to-integrate-a-custom-security-token-authenticator-with-a-custom-security-token-manager"></a>Para integrar un autenticador de tokens de seguridad personalizado con un administrador de tokens de seguridad personalizado  
  
1.  Invalide el método <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenAuthenticator%2A> en la implementación del administrador de tokens de seguridad personalizada.  
  
2.  Agregue la lógica al método para habilitarlo con objeto de devolver su autenticador de tokens de seguridad personalizado basado en el parámetro <xref:System.IdentityModel.Selectors.SecurityTokenRequirement>. El ejemplo siguiente devuelve un autenticador de tokens de seguridad personalizado si el tipo de token de requisitos de token es un nombre de usuario (representado por la propiedad <xref:System.IdentityModel.Tokens.SecurityTokenTypes.UserName%2A>) y la dirección del mensaje para la que se solicita el autenticador de tokens de seguridad es la entrada (representada por el campo <xref:System.ServiceModel.Description.MessageDirection.Input>).  
  
     [!code-csharp[c_CustomTokenAuthenticator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenauthenticator/cs/source.cs#3)]
     [!code-vb[c_CustomTokenAuthenticator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenauthenticator/vb/source.vb#3)]  
  
## <a name="see-also"></a>Vea también  
 <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator>  
 <xref:System.IdentityModel.Selectors.SecurityTokenRequirement>  
 <xref:System.IdentityModel.Selectors.SecurityTokenManager>  
 <xref:System.IdentityModel.Tokens.UserNameSecurityToken>  
 [Tutorial: Creación de credenciales de cliente y servicio personalizadas](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)  
 [Creación de un proveedor de tokens de seguridad personalizado](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)  
 [Arquitectura de seguridad](http://msdn.microsoft.com/library/16593476-d36a-408d-808c-ae6fd483e28f)
