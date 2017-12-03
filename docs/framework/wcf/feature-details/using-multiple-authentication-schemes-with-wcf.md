---
title: Using Multiple Authentication Schemes with WCF
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f32a56a0-e2b2-46bf-a302-29e1275917f9
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cf74b38c15cf8dc68218c39246c8999c4ec44493
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="using-multiple-authentication-schemes-with-wcf"></a>Using Multiple Authentication Schemes with WCF
WCF agora permite que você especifique vários esquemas de autenticação em um único ponto de extremidade. Além disso serviços da web hospedado podem herdar as configurações de autenticação diretamente no IIS. Serviços de hospedagem interna podem especificar qual autenticação esquemas podem ser usadas. Para obter mais informações sobre como definir configurações de autenticação no IIS, consulte [autenticação IIS](http://go.microsoft.com/fwlink/?LinkId=232458)  
  
## <a name="iis-hosted-services"></a>Serviços hospedados no IIS  
 Para serviços hospedados no IIS, defina os esquemas de autenticação que você deseja usar no IIS. Em seguida, no arquivo de Web. config do seu serviço, em sua configuração de associação especifica tipo clientCredential como "InheritedFromHost" conforme mostrado no seguinte trecho de XML:  
  
```xml  
<bindings>  
      <basicHttpBinding>  
        <binding name="secureBinding">  
          <security mode="Transport">  
            <transport clientCredentialType="InheritedFromHost" />  
          </security>  
        </binding>  
      </basicHttpBinding>  
    </bindings>  
```  
  
 Você pode especificar que você deseja que apenas um subconjunto dos esquemas de autenticação a ser usado com o serviço usando o ServiceAuthenticationBehavior ou o \<serviceAuthenticationManager > elemento. Quando essa configuração no código use o ServiceAuthenticationBehavior, conforme mostrado no seguinte trecho de código.  
  
```csharp  
// ...  
ServiceAuthenticationBehavior sab = null;  
sab = serviceHost.Description.Behaviors.Find<ServiceAuthenticationBehavior>();  
  
if (sab == null)  
{  
    sab = new ServiceAuthenticationBehavior();  
    sab.AuthenticationSchemes = AuthenticationSchemes.Basic | AuthenticationSchemes.Negotiate | AuthenticationSchemes.Digest;  
    serviceHost.Description.Behaviors.Add(sab);  
}  
else  
{  
     sab.AuthenticationSchemes = AuthenticationSchemes.Basic | AuthenticationSchemes.Negotiate | AuthenticationSchemes.Digest;  
}  
// ...  
```  
  
 Quando essa configuração em um arquivo de configuração, use o \<serviceAuthenticationManager > elemento conforme mostrado no seguinte trecho de XML.  
  
```xml  
<behaviors>  
      <serviceBehaviors>  
        <behavior name="limitedAuthBehavior">  
          <serviceAuthenticationManager authenticationSchemes="Negotiate, Digest, Basic"/>  
          <!-- ... -->  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
```  
  
 Isso irá garantir que apenas um subconjunto dos esquemas de autenticação listados aqui será considerado para a aplicação do ponto de extremidade de serviço, dependendo do que está selecionado no IIS. Isso significa que um desenvolvedor pode excluir diga a autenticação básica da lista ao omiti-lo da listagem serviceAuthenticationManager e mesmo que ele esteja habilitado no IIS, ela não será aplicada no ponto de extremidade de serviço  
  
## <a name="self-hosted-services"></a>Serviços de hospedagem interna  
 Serviços de hospedagem interna são configurados de forma um pouco diferente porque não há nenhum IIS para herdar as definições de. Aqui você vai usar o \<serviceAuthenticationManager > elemento ou ServiceAuthenticationBehavior para especificar as configurações de autenticação que serão herdadas. No código que fique assim:  
  
```csharp  
// ...  
ServiceAuthenticationBehavior sab = null;  
sab = serviceHost.Description.Behaviors.Find<ServiceAuthenticationBehavior>();  
  
if (sab == null)  
{  
    sab = new ServiceAuthenticationBehavior();  
    sab.AuthenticationSchemes = AuthenticationSchemes.Basic | AuthenticationSchemes.Negotiate | AuthenticationSchemes.Digest;  
    serviceHost.Description.Behaviors.Add(sab);  
}  
else  
{  
     sab.AuthenticationSchemes = AuthenticationSchemes.Basic | AuthenticationSchemes.Negotiate | AuthenticationSchemes.Digest;  
}  
// ...  
```  
  
 Na configuração, ele fica assim:  
  
```xml  
<behaviors>  
      <serviceBehaviors>  
        <behavior name="limitedAuthBehavior">  
          <serviceAuthenticationManager authenticationSchemes="Negotiate, Digest, Basic"/>  
          <!-- ... -->  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
```  
  
 E, em seguida, você pode especificar InheritFromHost em suas configurações de associação, conforme mostrado no seguinte trecho de XML.  
  
```xml  
<bindings>  
      <basicHttpBinding>  
        <binding name="secureBinding">  
          <security mode="Transport">  
            <transport clientCredentialType="InheritedFromHost" />  
          </security>  
        </binding>  
      </basicHttpBinding>  
    </bindings>  
```  
  
 Como alternativa, você pode especificar os esquemas de autenticação em uma associação personalizada, definindo os esquemas de autenticação HTTP transporte elemento de associação, conforme mostrado no seguinte trecho de configuração.  
  
```xml  
<binding name="multipleBinding">  
      <textMessageEncoding/>  
      <httpTransport authenticationScheme="Negotiate, Ntlm, Digest, Basic" />  
    </binding>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Associações e segurança](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
 [Pontos de extremidade: Endereços, associações e contratos](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)  
 [Configurando associações fornecidas pelo sistema](../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Recursos de segurança com associações personalizadas](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [Bindings](../../../../docs/framework/wcf/feature-details/bindings.md) (Associações)  
 [Bindings](../../../../docs/framework/wcf/feature-details/bindings.md) (Associações)  
 [Associações personalizadas](../../../../docs/framework/wcf/extending/custom-bindings.md)
