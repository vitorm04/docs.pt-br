---
title: <transport> de <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: 692befa3-8b0b-4ec5-b601-755874e98eb0
ms.openlocfilehash: ce8b2acb7d87b094958e20ca0b6cca9fc8266a8d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911980"
---
# <a name="transport-of-ws2007httpbinding"></a><span data-ttu-id="4f467-102">\<> de transporte \<do ws2007HttpBinding ></span><span class="sxs-lookup"><span data-stu-id="4f467-102">\<transport> of \<ws2007HttpBinding></span></span>
<span data-ttu-id="4f467-103">Define as configurações de autenticação para o transporte HTTP.</span><span class="sxs-lookup"><span data-stu-id="4f467-103">Defines authentication settings for the HTTP transport.</span></span>  
  
 <span data-ttu-id="4f467-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="4f467-104">\<system.serviceModel></span></span>  
<span data-ttu-id="4f467-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="4f467-105">\<bindings></span></span>  
<span data-ttu-id="4f467-106">\<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="4f467-106">\<ws2007HttpBinding></span></span>  
<span data-ttu-id="4f467-107">\<> de associação</span><span class="sxs-lookup"><span data-stu-id="4f467-107">\<binding></span></span>  
<span data-ttu-id="4f467-108">\<> de segurança</span><span class="sxs-lookup"><span data-stu-id="4f467-108">\<security></span></span>  
<span data-ttu-id="4f467-109">\<> de transporte</span><span class="sxs-lookup"><span data-stu-id="4f467-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f467-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4f467-110">Syntax</span></span>  
  
```xml  
<transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
           proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
           realm="string" />
```  
  
## <a name="type"></a><span data-ttu-id="4f467-111">Tipo</span><span class="sxs-lookup"><span data-stu-id="4f467-111">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4f467-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="4f467-112">Attributes and Elements</span></span>  
 <span data-ttu-id="4f467-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="4f467-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4f467-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="4f467-114">Attributes</span></span>  
  
|<span data-ttu-id="4f467-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="4f467-115">Attribute</span></span>|<span data-ttu-id="4f467-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="4f467-116">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="4f467-117">Especifica a credencial usada para autenticar o cliente para o serviço.</span><span class="sxs-lookup"><span data-stu-id="4f467-117">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="4f467-118">Esse atributo é do tipo <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="4f467-118">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="4f467-119">Especifica a credencial usada para autenticar o cliente para um proxy de domínio.</span><span class="sxs-lookup"><span data-stu-id="4f467-119">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="4f467-120">Esse atributo é do tipo <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="4f467-120">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="4f467-121">O realm de autenticação para Digest ou autenticação básica.</span><span class="sxs-lookup"><span data-stu-id="4f467-121">The authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="4f467-122">O padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="4f467-122">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="4f467-123">Um realm de autenticação especifica pelo menos o nome do host que executa a autenticação.</span><span class="sxs-lookup"><span data-stu-id="4f467-123">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="4f467-124">Ele também pode especificar uma coleção de usuários que têm acesso.</span><span class="sxs-lookup"><span data-stu-id="4f467-124">It can also specify a collection of users who have access.</span></span> <span data-ttu-id="4f467-125">Um usuário pode consultar o realm de autenticação para determinar qual um dos vários nomes de usuário e senhas possíveis podem ser usados.</span><span class="sxs-lookup"><span data-stu-id="4f467-125">A user can query the authentication realm to determine which one of the several possible usernames and passwords can be used.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="4f467-126">Atributo clientCredentialtype</span><span class="sxs-lookup"><span data-stu-id="4f467-126">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="4f467-127">Valor</span><span class="sxs-lookup"><span data-stu-id="4f467-127">Value</span></span>|<span data-ttu-id="4f467-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="4f467-128">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4f467-129">Nenhum</span><span class="sxs-lookup"><span data-stu-id="4f467-129">None</span></span>|<span data-ttu-id="4f467-130">A segurança é desabilitada.</span><span class="sxs-lookup"><span data-stu-id="4f467-130">Security is disabled.</span></span>|  
|<span data-ttu-id="4f467-131">Basic</span><span class="sxs-lookup"><span data-stu-id="4f467-131">Basic</span></span>|<span data-ttu-id="4f467-132">Usa a autenticação básica.</span><span class="sxs-lookup"><span data-stu-id="4f467-132">Uses basic authentication.</span></span>|  
|<span data-ttu-id="4f467-133">Digest</span><span class="sxs-lookup"><span data-stu-id="4f467-133">Digest</span></span>|<span data-ttu-id="4f467-134">Usa a autenticação Digest.</span><span class="sxs-lookup"><span data-stu-id="4f467-134">Uses digest authentication.</span></span>|  
|<span data-ttu-id="4f467-135">NTLM</span><span class="sxs-lookup"><span data-stu-id="4f467-135">Ntlm</span></span>|<span data-ttu-id="4f467-136">Usa a autenticação NTLM como um fallback com um domínio do Windows.</span><span class="sxs-lookup"><span data-stu-id="4f467-136">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="4f467-137">Windows</span><span class="sxs-lookup"><span data-stu-id="4f467-137">Windows</span></span>|<span data-ttu-id="4f467-138">Usa a autenticação integrada do Windows.</span><span class="sxs-lookup"><span data-stu-id="4f467-138">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="4f467-139">Certificate</span><span class="sxs-lookup"><span data-stu-id="4f467-139">Certificate</span></span>|<span data-ttu-id="4f467-140">Usa certificados X. 509 para autenticar o cliente.</span><span class="sxs-lookup"><span data-stu-id="4f467-140">Uses X.509 certificates to authenticate the client.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="4f467-141">Atributo proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="4f467-141">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="4f467-142">Valor</span><span class="sxs-lookup"><span data-stu-id="4f467-142">Value</span></span>|<span data-ttu-id="4f467-143">Descrição</span><span class="sxs-lookup"><span data-stu-id="4f467-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4f467-144">Nenhum</span><span class="sxs-lookup"><span data-stu-id="4f467-144">None</span></span>|<span data-ttu-id="4f467-145">A segurança é desabilitada.</span><span class="sxs-lookup"><span data-stu-id="4f467-145">Security is disabled.</span></span>|  
|<span data-ttu-id="4f467-146">Basic</span><span class="sxs-lookup"><span data-stu-id="4f467-146">Basic</span></span>|<span data-ttu-id="4f467-147">Usa a autenticação básica.</span><span class="sxs-lookup"><span data-stu-id="4f467-147">Uses basic authentication.</span></span>|  
|<span data-ttu-id="4f467-148">Digest</span><span class="sxs-lookup"><span data-stu-id="4f467-148">Digest</span></span>|<span data-ttu-id="4f467-149">Usa a autenticação Digest.</span><span class="sxs-lookup"><span data-stu-id="4f467-149">Uses digest authentication.</span></span>|  
|<span data-ttu-id="4f467-150">NTLM</span><span class="sxs-lookup"><span data-stu-id="4f467-150">Ntlm</span></span>|<span data-ttu-id="4f467-151">Usa NTLM como um fallback com um domínio do Windows.</span><span class="sxs-lookup"><span data-stu-id="4f467-151">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="4f467-152">Windows</span><span class="sxs-lookup"><span data-stu-id="4f467-152">Windows</span></span>|<span data-ttu-id="4f467-153">Usa a autenticação integrada do Windows.</span><span class="sxs-lookup"><span data-stu-id="4f467-153">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="4f467-154">Certificate</span><span class="sxs-lookup"><span data-stu-id="4f467-154">Certificate</span></span>|<span data-ttu-id="4f467-155">Usa certificados X. 509 para autenticar o cliente.</span><span class="sxs-lookup"><span data-stu-id="4f467-155">Uses X.509 certificates to authenticate the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4f467-156">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="4f467-156">Child Elements</span></span>  
 <span data-ttu-id="4f467-157">Nenhum</span><span class="sxs-lookup"><span data-stu-id="4f467-157">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4f467-158">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="4f467-158">Parent Elements</span></span>  
  
|<span data-ttu-id="4f467-159">Elemento</span><span class="sxs-lookup"><span data-stu-id="4f467-159">Element</span></span>|<span data-ttu-id="4f467-160">Descrição</span><span class="sxs-lookup"><span data-stu-id="4f467-160">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4f467-161">\<security></span><span class="sxs-lookup"><span data-stu-id="4f467-161">\<security></span></span>](security-of-ws2007httpbinding.md)|<span data-ttu-id="4f467-162">Representa os recursos de segurança do [ \<elemento > ws2007HttpBinding](ws2007httpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="4f467-162">Represents the security capabilities of the [\<ws2007HttpBinding>](ws2007httpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4f467-163">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4f467-163">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.WSHttpTransportSecurityElement>
- [<span data-ttu-id="4f467-164">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="4f467-164">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="4f467-165">Associações</span><span class="sxs-lookup"><span data-stu-id="4f467-165">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="4f467-166">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="4f467-166">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="4f467-167">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="4f467-167">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="4f467-168">\<binding></span><span class="sxs-lookup"><span data-stu-id="4f467-168">\<binding></span></span>](../../../misc/binding.md)
