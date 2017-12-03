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
# <a name="using-multiple-authentication-schemes-with-wcf"></a><span data-ttu-id="9233a-102">Using Multiple Authentication Schemes with WCF</span><span class="sxs-lookup"><span data-stu-id="9233a-102">Using Multiple Authentication Schemes with WCF</span></span>
<span data-ttu-id="9233a-103">WCF agora permite que você especifique vários esquemas de autenticação em um único ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="9233a-103">WCF now allows you to specify multiple authentication schemes on a single endpoint.</span></span> <span data-ttu-id="9233a-104">Além disso serviços da web hospedado podem herdar as configurações de autenticação diretamente no IIS.</span><span class="sxs-lookup"><span data-stu-id="9233a-104">Furthermore web hosted services can inherit their authentication settings directly from IIS.</span></span> <span data-ttu-id="9233a-105">Serviços de hospedagem interna podem especificar qual autenticação esquemas podem ser usadas.</span><span class="sxs-lookup"><span data-stu-id="9233a-105">Self-hosted services can specify what authentication schemes can be used.</span></span> <span data-ttu-id="9233a-106">Para obter mais informações sobre como definir configurações de autenticação no IIS, consulte [autenticação IIS](http://go.microsoft.com/fwlink/?LinkId=232458)</span><span class="sxs-lookup"><span data-stu-id="9233a-106">For more information about setting authentication settings in IIS, see [IIS Authentication](http://go.microsoft.com/fwlink/?LinkId=232458)</span></span>  
  
## <a name="iis-hosted-services"></a><span data-ttu-id="9233a-107">Serviços hospedados no IIS</span><span class="sxs-lookup"><span data-stu-id="9233a-107">IIS-Hosted Services</span></span>  
 <span data-ttu-id="9233a-108">Para serviços hospedados no IIS, defina os esquemas de autenticação que você deseja usar no IIS.</span><span class="sxs-lookup"><span data-stu-id="9233a-108">For IIS-hosted services, set the authentication schemes you wish to use in IIS.</span></span> <span data-ttu-id="9233a-109">Em seguida, no arquivo de Web. config do seu serviço, em sua configuração de associação especifica tipo clientCredential como "InheritedFromHost" conforme mostrado no seguinte trecho de XML:</span><span class="sxs-lookup"><span data-stu-id="9233a-109">Then in your service’s web.config file, in your binding configuration specify clientCredential type as "InheritedFromHost" as shown in the following XML snippet:</span></span>  
  
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
  
 <span data-ttu-id="9233a-110">Você pode especificar que você deseja que apenas um subconjunto dos esquemas de autenticação a ser usado com o serviço usando o ServiceAuthenticationBehavior ou o \<serviceAuthenticationManager > elemento.</span><span class="sxs-lookup"><span data-stu-id="9233a-110">You can specify that you only want a subset of authentication schemes to be used with your service using the ServiceAuthenticationBehavior or the \<serviceAuthenticationManager> element.</span></span> <span data-ttu-id="9233a-111">Quando essa configuração no código use o ServiceAuthenticationBehavior, conforme mostrado no seguinte trecho de código.</span><span class="sxs-lookup"><span data-stu-id="9233a-111">When configuring this in code use the ServiceAuthenticationBehavior as shown in the following code snippet.</span></span>  
  
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
  
 <span data-ttu-id="9233a-112">Quando essa configuração em um arquivo de configuração, use o \<serviceAuthenticationManager > elemento conforme mostrado no seguinte trecho de XML.</span><span class="sxs-lookup"><span data-stu-id="9233a-112">When configuring this in a config file, use the \<serviceAuthenticationManager> element as shown in the following XML snippet.</span></span>  
  
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
  
 <span data-ttu-id="9233a-113">Isso irá garantir que apenas um subconjunto dos esquemas de autenticação listados aqui será considerado para a aplicação do ponto de extremidade de serviço, dependendo do que está selecionado no IIS.</span><span class="sxs-lookup"><span data-stu-id="9233a-113">This will ensure that only a subset of the authentication schemes listed here will be considered for applying on the service endpoint, depending on what is selected in the IIS.</span></span> <span data-ttu-id="9233a-114">Isso significa que um desenvolvedor pode excluir diga a autenticação básica da lista ao omiti-lo da listagem serviceAuthenticationManager e mesmo que ele esteja habilitado no IIS, ela não será aplicada no ponto de extremidade de serviço</span><span class="sxs-lookup"><span data-stu-id="9233a-114">This means that a developer can exclude say Basic auth from the list by omitting it from the serviceAuthenticationManager listing and even if it is enabled in IIS, it will not be applied on the service endpoint</span></span>  
  
## <a name="self-hosted-services"></a><span data-ttu-id="9233a-115">Serviços de hospedagem interna</span><span class="sxs-lookup"><span data-stu-id="9233a-115">Self-Hosted Services</span></span>  
 <span data-ttu-id="9233a-116">Serviços de hospedagem interna são configurados de forma um pouco diferente porque não há nenhum IIS para herdar as definições de.</span><span class="sxs-lookup"><span data-stu-id="9233a-116">Self-hosted services are configured a bit differently since there is no IIS to inherit settings from.</span></span> <span data-ttu-id="9233a-117">Aqui você vai usar o \<serviceAuthenticationManager > elemento ou ServiceAuthenticationBehavior para especificar as configurações de autenticação que serão herdadas.</span><span class="sxs-lookup"><span data-stu-id="9233a-117">Here you use the \<serviceAuthenticationManager> element or ServiceAuthenticationBehavior to specify the authentication settings that will be inherited.</span></span> <span data-ttu-id="9233a-118">No código que fique assim:</span><span class="sxs-lookup"><span data-stu-id="9233a-118">In code it looks like this:</span></span>  
  
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
  
 <span data-ttu-id="9233a-119">Na configuração, ele fica assim:</span><span class="sxs-lookup"><span data-stu-id="9233a-119">In config, it looks like this:</span></span>  
  
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
  
 <span data-ttu-id="9233a-120">E, em seguida, você pode especificar InheritFromHost em suas configurações de associação, conforme mostrado no seguinte trecho de XML.</span><span class="sxs-lookup"><span data-stu-id="9233a-120">And then you can specify InheritFromHost in your binding settings as shown in the following XML snippet.</span></span>  
  
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
  
 <span data-ttu-id="9233a-121">Como alternativa, você pode especificar os esquemas de autenticação em uma associação personalizada, definindo os esquemas de autenticação HTTP transporte elemento de associação, conforme mostrado no seguinte trecho de configuração.</span><span class="sxs-lookup"><span data-stu-id="9233a-121">Alternatively, you can specify the authentication schemes in a custom binding, by setting the authentication schemes on the HTTP transport binding element, as shown in the following config snippet.</span></span>  
  
```xml  
<binding name="multipleBinding">  
      <textMessageEncoding/>  
      <httpTransport authenticationScheme="Negotiate, Ntlm, Digest, Basic" />  
    </binding>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9233a-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9233a-122">See Also</span></span>  
 [<span data-ttu-id="9233a-123">Associações e segurança</span><span class="sxs-lookup"><span data-stu-id="9233a-123">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
 [<span data-ttu-id="9233a-124">Pontos de extremidade: Endereços, associações e contratos</span><span class="sxs-lookup"><span data-stu-id="9233a-124">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)  
 [<span data-ttu-id="9233a-125">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="9233a-125">Configuring System-Provided Bindings</span></span>](../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="9233a-126">Recursos de segurança com associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="9233a-126">Security Capabilities with Custom Bindings</span></span>](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 <span data-ttu-id="9233a-127">[Bindings](../../../../docs/framework/wcf/feature-details/bindings.md) (Associações)</span><span class="sxs-lookup"><span data-stu-id="9233a-127">[Bindings](../../../../docs/framework/wcf/feature-details/bindings.md)</span></span>  
 <span data-ttu-id="9233a-128">[Bindings](../../../../docs/framework/wcf/feature-details/bindings.md) (Associações)</span><span class="sxs-lookup"><span data-stu-id="9233a-128">[Bindings](../../../../docs/framework/wcf/feature-details/bindings.md)</span></span>  
 [<span data-ttu-id="9233a-129">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="9233a-129">Custom Bindings</span></span>](../../../../docs/framework/wcf/extending/custom-bindings.md)
