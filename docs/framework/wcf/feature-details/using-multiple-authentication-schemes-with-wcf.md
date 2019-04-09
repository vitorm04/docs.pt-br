---
title: Using Multiple Authentication Schemes with WCF
ms.date: 03/30/2017
ms.assetid: f32a56a0-e2b2-46bf-a302-29e1275917f9
ms.openlocfilehash: b0f5da9a4c6fdfede9a86434f49f9e9821778176
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59102304"
---
# <a name="using-multiple-authentication-schemes-with-wcf"></a>Using Multiple Authentication Schemes with WCF
O WCF agora permite que você especifique vários esquemas de autenticação em um único ponto de extremidade. Além disso serviços da web hospedado podem herdar as configurações de autenticação diretamente do IIS. Serviços de hospedagem interna podem especificar qual autenticação esquemas podem ser usados. Para obter mais informações sobre como definir as configurações de autenticação no IIS, consulte [autenticação IIS](https://go.microsoft.com/fwlink/?LinkId=232458)  
  
## <a name="iis-hosted-services"></a>Serviços hospedados no IIS  
 Para serviços hospedados no IIS, defina os esquemas de autenticação que você deseja usar no IIS. Em seguida, no arquivo de Web. config do seu serviço, em sua configuração de associação especifique clientCredential tipo como "InheritedFromHost" conforme mostrado no trecho XML a seguir:  
  
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
  
 Você pode especificar que você deseja apenas um subconjunto dos esquemas de autenticação a ser usado com seu serviço usando o ServiceAuthenticationBehavior ou o \<serviceAuthenticationManager > elemento. Ao configurar isso no código use a ServiceAuthenticationBehavior conforme mostrado no trecho de código a seguir.  
  
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
  
 Ao configurar isso em um arquivo de configuração, use o \<serviceAuthenticationManager > elemento, conforme mostrado no seguinte trecho XML.  
  
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
  
 Isso garantirá que apenas um subconjunto dos esquemas de autenticação listadas aqui será considerado para a aplicação do ponto de extremidade de serviço, dependendo do que está selecionado no IIS. Isso significa que um desenvolvedor pode excluir digamos que a autenticação básica na lista ao omiti-lo na listagem serviceAuthenticationManager e mesmo se ela estiver habilitada no IIS, ela não será aplicada no ponto de extremidade de serviço  
  
## <a name="self-hosted-services"></a>Serviços de hospedagem interna  
 Serviços são hospedados são configurados de forma um pouco diferente, pois não há nenhum IIS para herdar as definições de. Aqui você vai usar o \<serviceAuthenticationManager > elemento ou ServiceAuthenticationBehavior para especificar as configurações de autenticação que serão herdadas. No código, ele parece com isto:  
  
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
  
 Na configuração, ela fica assim:  
  
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
  
 E, em seguida, você pode especificar InheritFromHost em suas configurações de associação, conforme mostrado no seguinte trecho XML.  
  
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
  
 Como alternativa, você pode especificar os esquemas de autenticação em uma associação personalizada, definindo os esquemas de autenticação em HTTP transportar o elemento de associação, conforme mostrado no seguinte trecho de config.  
  
```xml  
<binding name="multipleBinding">  
      <textMessageEncoding/>  
      <httpTransport authenticationScheme="Negotiate, Ntlm, Digest, Basic" />  
    </binding>  
```  
  
## <a name="see-also"></a>Consulte também

- [Associações e segurança](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)
- [Pontos de extremidade: endereços, associações e contratos](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
- [Configurando associações fornecidas pelo sistema](../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [Recursos de segurança com associações personalizadas](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [Associações](../../../../docs/framework/wcf/feature-details/bindings.md)
- [Associações personalizadas](../../../../docs/framework/wcf/extending/custom-bindings.md)
