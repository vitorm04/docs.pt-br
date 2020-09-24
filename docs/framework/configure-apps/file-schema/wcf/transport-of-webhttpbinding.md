---
title: <transport> de <webHttpBinding>
ms.date: 03/30/2017
ms.assetid: f150fb19-7de1-44af-81f4-86cad881cd05
ms.openlocfilehash: b9efc732832a8862373b14f657796a59fb52c1a1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91162108"
---
# <a name="transport-of-webhttpbinding"></a><span data-ttu-id="6590f-102">\<transport> de \<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="6590f-102">\<transport> of \<webHttpBinding></span></span>

<span data-ttu-id="6590f-103">Define as configurações de segurança no nível de transporte para um ponto de extremidade de serviço configurado para receber solicitações HTTP.</span><span class="sxs-lookup"><span data-stu-id="6590f-103">Defines the transport-level security settings for a service endpoint configured to receive HTTP requests.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<webHttpBinding>**](webhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-webhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="6590f-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="6590f-104">Syntax</span></span>  
  
```xml  
<webHttpBinding>
  <binding>
    <security mode="None|Transport|Message|TransportWithMessageCredential|TransportCredentialOnly">
      <transport clientCredentialType="None|Basic|Digest|Ntlm|Windows"
                 proxyCredentialType="None|Basic|Digest|Ntlm|Windows"
                 realm="string">
        <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always"
                                  protectionScenario="TransportSelected|TrustedProxy">
          <customServiceNames>
          </customServiceNames>
        </extendedProtectionPolicy>
      </transport>
    </security>
  </binding>
</webHttpBinding>
```  
  
## <a name="type"></a><span data-ttu-id="6590f-105">Tipo</span><span class="sxs-lookup"><span data-stu-id="6590f-105">Type</span></span>  

 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6590f-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="6590f-106">Attributes and Elements</span></span>  

 <span data-ttu-id="6590f-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="6590f-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6590f-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="6590f-108">Attributes</span></span>  
  
|<span data-ttu-id="6590f-109">Atributo</span><span class="sxs-lookup"><span data-stu-id="6590f-109">Attribute</span></span>|<span data-ttu-id="6590f-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="6590f-110">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="6590f-111">Especifica a credencial usada para autenticar o cliente para o serviço.</span><span class="sxs-lookup"><span data-stu-id="6590f-111">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="6590f-112">Esse atributo é do tipo <xref:System.ServiceModel.HttpClientCredentialType> .</span><span class="sxs-lookup"><span data-stu-id="6590f-112">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="6590f-113">Especifica a credencial usada para autenticar o cliente para um proxy de domínio.</span><span class="sxs-lookup"><span data-stu-id="6590f-113">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="6590f-114">Esse atributo é do tipo <xref:System.ServiceModel.HttpProxyCredentialType> .</span><span class="sxs-lookup"><span data-stu-id="6590f-114">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="6590f-115">Uma cadeia de caracteres que especifica o realm de autenticação para Digest ou autenticação básica.</span><span class="sxs-lookup"><span data-stu-id="6590f-115">A string that specifies the authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="6590f-116">O padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="6590f-116">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="6590f-117">Um realm de autenticação especifica pelo menos o nome do host que executa a autenticação.</span><span class="sxs-lookup"><span data-stu-id="6590f-117">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="6590f-118">Ele também pode especificar uma coleção de usuários que tem acesso.</span><span class="sxs-lookup"><span data-stu-id="6590f-118">It can also specify a collection of users that has access.</span></span> <span data-ttu-id="6590f-119">Um usuário pode consultar o realm de autenticação para determinar que um dos vários nomes de usuário e senhas possíveis podem ser usados.</span><span class="sxs-lookup"><span data-stu-id="6590f-119">A user can query the authentication realm to ascertain which one of the several possible usernames and passwords can be used.</span></span>|  
|`policyEnforcement`|<span data-ttu-id="6590f-120">Essa enumeração especifica quando o <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> deve ser imposto.</span><span class="sxs-lookup"><span data-stu-id="6590f-120">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="6590f-121">1. nunca – a política nunca é imposta (a proteção estendida está desabilitada).</span><span class="sxs-lookup"><span data-stu-id="6590f-121">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="6590f-122">2. WhenSupported – a política será imposta somente se o cliente oferecer suporte à proteção estendida.</span><span class="sxs-lookup"><span data-stu-id="6590f-122">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="6590f-123">3. sempre – a política é sempre imposta.</span><span class="sxs-lookup"><span data-stu-id="6590f-123">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="6590f-124">Os clientes que não dão suporte à proteção estendida não serão autenticados.</span><span class="sxs-lookup"><span data-stu-id="6590f-124">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="6590f-125">Atributo clientCredentialtype</span><span class="sxs-lookup"><span data-stu-id="6590f-125">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="6590f-126">Valor</span><span class="sxs-lookup"><span data-stu-id="6590f-126">Value</span></span>|<span data-ttu-id="6590f-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="6590f-127">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="6590f-128">A segurança é desabilitada.</span><span class="sxs-lookup"><span data-stu-id="6590f-128">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="6590f-129">Usa a autenticação básica.</span><span class="sxs-lookup"><span data-stu-id="6590f-129">Uses basic authentication.</span></span>|  
|`Certificate`|<span data-ttu-id="6590f-130">Usa certificados X. 509 para autenticar o cliente.</span><span class="sxs-lookup"><span data-stu-id="6590f-130">Uses X.509 certificates to authenticate the client.</span></span>|  
|`Digest`|<span data-ttu-id="6590f-131">Usa a autenticação Digest.</span><span class="sxs-lookup"><span data-stu-id="6590f-131">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="6590f-132">Usa a autenticação NTLM como um fallback com um domínio do Windows.</span><span class="sxs-lookup"><span data-stu-id="6590f-132">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="6590f-133">Usa a autenticação integrada do Windows.</span><span class="sxs-lookup"><span data-stu-id="6590f-133">Uses integrated Windows authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="6590f-134">Atributo proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="6590f-134">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="6590f-135">Valor</span><span class="sxs-lookup"><span data-stu-id="6590f-135">Value</span></span>|<span data-ttu-id="6590f-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="6590f-136">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="6590f-137">A segurança é desabilitada.</span><span class="sxs-lookup"><span data-stu-id="6590f-137">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="6590f-138">Usa a autenticação básica.</span><span class="sxs-lookup"><span data-stu-id="6590f-138">Uses basic authentication.</span></span>|  
|`Digest`|<span data-ttu-id="6590f-139">Usa a autenticação Digest.</span><span class="sxs-lookup"><span data-stu-id="6590f-139">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="6590f-140">Usa NTLM como um fallback com um domínio do Windows.</span><span class="sxs-lookup"><span data-stu-id="6590f-140">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="6590f-141">Usa a autenticação integrada do Windows.</span><span class="sxs-lookup"><span data-stu-id="6590f-141">Uses integrated Windows authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6590f-142">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="6590f-142">Child Elements</span></span>  

 <span data-ttu-id="6590f-143">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="6590f-143">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6590f-144">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="6590f-144">Parent Elements</span></span>  
  
|<span data-ttu-id="6590f-145">Elemento</span><span class="sxs-lookup"><span data-stu-id="6590f-145">Element</span></span>|<span data-ttu-id="6590f-146">Descrição</span><span class="sxs-lookup"><span data-stu-id="6590f-146">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-webhttpbinding.md)|<span data-ttu-id="6590f-147">Representa os recursos de segurança do [\<wsHttpBinding>](wshttpbinding.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="6590f-147">Represents the security capabilities of the [\<wsHttpBinding>](wshttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6590f-148">Confira também</span><span class="sxs-lookup"><span data-stu-id="6590f-148">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.Configuration.WebHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.WebHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- [<span data-ttu-id="6590f-149">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="6590f-149">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="6590f-150">Associações</span><span class="sxs-lookup"><span data-stu-id="6590f-150">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="6590f-151">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="6590f-151">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="6590f-152">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="6590f-152">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
- [<span data-ttu-id="6590f-153">Modelo de programação WCF Web HTTP</span><span class="sxs-lookup"><span data-stu-id="6590f-153">WCF Web HTTP Programming Model</span></span>](../../../wcf/feature-details/wcf-web-http-programming-model.md)
