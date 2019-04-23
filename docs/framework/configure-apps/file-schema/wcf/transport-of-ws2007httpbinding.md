---
title: <transport> de <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: 692befa3-8b0b-4ec5-b601-755874e98eb0
ms.openlocfilehash: a1540b53d4af76141c1daee60a6bddbbecd9d6da
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59153862"
---
# <a name="transport-of-ws2007httpbinding"></a><span data-ttu-id="3972a-102">\<transporte > de \<ws2007HttpBinding ></span><span class="sxs-lookup"><span data-stu-id="3972a-102">\<transport> of \<ws2007HttpBinding></span></span>
<span data-ttu-id="3972a-103">Define as configurações de autenticação para o transporte HTTP.</span><span class="sxs-lookup"><span data-stu-id="3972a-103">Defines authentication settings for the HTTP transport.</span></span>  
  
 <span data-ttu-id="3972a-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="3972a-104">\<system.serviceModel></span></span>  
<span data-ttu-id="3972a-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="3972a-105">\<bindings></span></span>  
<span data-ttu-id="3972a-106">\<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="3972a-106">\<ws2007HttpBinding></span></span>  
<span data-ttu-id="3972a-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="3972a-107">\<binding></span></span>  
<span data-ttu-id="3972a-108">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="3972a-108">\<security></span></span>  
<span data-ttu-id="3972a-109">\<transporte ></span><span class="sxs-lookup"><span data-stu-id="3972a-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3972a-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3972a-110">Syntax</span></span>  
  
```xml  
<transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
           proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
           realm="string" />
```  
  
## <a name="type"></a><span data-ttu-id="3972a-111">Tipo</span><span class="sxs-lookup"><span data-stu-id="3972a-111">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3972a-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="3972a-112">Attributes and Elements</span></span>  
 <span data-ttu-id="3972a-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="3972a-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3972a-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="3972a-114">Attributes</span></span>  
  
|<span data-ttu-id="3972a-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="3972a-115">Attribute</span></span>|<span data-ttu-id="3972a-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="3972a-116">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="3972a-117">Especifica a credencial usada para autenticar o cliente para o serviço.</span><span class="sxs-lookup"><span data-stu-id="3972a-117">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="3972a-118">Esse atributo é do tipo <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="3972a-118">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="3972a-119">Especifica a credencial usada para autenticar o cliente para um proxy do domínio.</span><span class="sxs-lookup"><span data-stu-id="3972a-119">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="3972a-120">Esse atributo é do tipo <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="3972a-120">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="3972a-121">O realm de autenticação para a autenticação básica ou digest.</span><span class="sxs-lookup"><span data-stu-id="3972a-121">The authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="3972a-122">O padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="3972a-122">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="3972a-123">Pelo menos, um realm de autenticação especifica o nome do host que executa a autenticação.</span><span class="sxs-lookup"><span data-stu-id="3972a-123">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="3972a-124">Ele também pode especificar uma coleção de usuários que têm acesso.</span><span class="sxs-lookup"><span data-stu-id="3972a-124">It can also specify a collection of users who have access.</span></span> <span data-ttu-id="3972a-125">Um usuário pode consultar o realm de autenticação para determinar qual dos vários possíveis nomes de usuário e senhas pode ser usado.</span><span class="sxs-lookup"><span data-stu-id="3972a-125">A user can query the authentication realm to determine which one of the several possible usernames and passwords can be used.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="3972a-126">clientCredentialType de atributo</span><span class="sxs-lookup"><span data-stu-id="3972a-126">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="3972a-127">Valor</span><span class="sxs-lookup"><span data-stu-id="3972a-127">Value</span></span>|<span data-ttu-id="3972a-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="3972a-128">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3972a-129">Nenhum</span><span class="sxs-lookup"><span data-stu-id="3972a-129">None</span></span>|<span data-ttu-id="3972a-130">A segurança é desabilitada.</span><span class="sxs-lookup"><span data-stu-id="3972a-130">Security is disabled.</span></span>|  
|<span data-ttu-id="3972a-131">Basic</span><span class="sxs-lookup"><span data-stu-id="3972a-131">Basic</span></span>|<span data-ttu-id="3972a-132">Usa a autenticação básica.</span><span class="sxs-lookup"><span data-stu-id="3972a-132">Uses basic authentication.</span></span>|  
|<span data-ttu-id="3972a-133">Digest</span><span class="sxs-lookup"><span data-stu-id="3972a-133">Digest</span></span>|<span data-ttu-id="3972a-134">Usa autenticação digest.</span><span class="sxs-lookup"><span data-stu-id="3972a-134">Uses digest authentication.</span></span>|  
|<span data-ttu-id="3972a-135">NTLM</span><span class="sxs-lookup"><span data-stu-id="3972a-135">Ntlm</span></span>|<span data-ttu-id="3972a-136">Usa a autenticação NTLM como um fallback com um domínio do Windows.</span><span class="sxs-lookup"><span data-stu-id="3972a-136">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="3972a-137">Windows</span><span class="sxs-lookup"><span data-stu-id="3972a-137">Windows</span></span>|<span data-ttu-id="3972a-138">Usa integrada a autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="3972a-138">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="3972a-139">Certificado</span><span class="sxs-lookup"><span data-stu-id="3972a-139">Certificate</span></span>|<span data-ttu-id="3972a-140">Usa certificados x. 509 para autenticar o cliente.</span><span class="sxs-lookup"><span data-stu-id="3972a-140">Uses X.509 certificates to authenticate the client.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="3972a-141">proxyCredentialType atributo</span><span class="sxs-lookup"><span data-stu-id="3972a-141">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="3972a-142">Valor</span><span class="sxs-lookup"><span data-stu-id="3972a-142">Value</span></span>|<span data-ttu-id="3972a-143">Descrição</span><span class="sxs-lookup"><span data-stu-id="3972a-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3972a-144">Nenhum</span><span class="sxs-lookup"><span data-stu-id="3972a-144">None</span></span>|<span data-ttu-id="3972a-145">A segurança é desabilitada.</span><span class="sxs-lookup"><span data-stu-id="3972a-145">Security is disabled.</span></span>|  
|<span data-ttu-id="3972a-146">Basic</span><span class="sxs-lookup"><span data-stu-id="3972a-146">Basic</span></span>|<span data-ttu-id="3972a-147">Usa a autenticação básica.</span><span class="sxs-lookup"><span data-stu-id="3972a-147">Uses basic authentication.</span></span>|  
|<span data-ttu-id="3972a-148">Digest</span><span class="sxs-lookup"><span data-stu-id="3972a-148">Digest</span></span>|<span data-ttu-id="3972a-149">Usa autenticação digest.</span><span class="sxs-lookup"><span data-stu-id="3972a-149">Uses digest authentication.</span></span>|  
|<span data-ttu-id="3972a-150">NTLM</span><span class="sxs-lookup"><span data-stu-id="3972a-150">Ntlm</span></span>|<span data-ttu-id="3972a-151">Usa NTLM como um fallback com um domínio do Windows.</span><span class="sxs-lookup"><span data-stu-id="3972a-151">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="3972a-152">Windows</span><span class="sxs-lookup"><span data-stu-id="3972a-152">Windows</span></span>|<span data-ttu-id="3972a-153">Usa integrada a autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="3972a-153">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="3972a-154">Certificado</span><span class="sxs-lookup"><span data-stu-id="3972a-154">Certificate</span></span>|<span data-ttu-id="3972a-155">Usa certificados x. 509 para autenticar o cliente.</span><span class="sxs-lookup"><span data-stu-id="3972a-155">Uses X.509 certificates to authenticate the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3972a-156">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="3972a-156">Child Elements</span></span>  
 <span data-ttu-id="3972a-157">Nenhum</span><span class="sxs-lookup"><span data-stu-id="3972a-157">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3972a-158">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="3972a-158">Parent Elements</span></span>  
  
|<span data-ttu-id="3972a-159">Elemento</span><span class="sxs-lookup"><span data-stu-id="3972a-159">Element</span></span>|<span data-ttu-id="3972a-160">Descrição</span><span class="sxs-lookup"><span data-stu-id="3972a-160">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3972a-161">\<security></span><span class="sxs-lookup"><span data-stu-id="3972a-161">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-ws2007httpbinding.md)|<span data-ttu-id="3972a-162">Representa os recursos de segurança de [ \<ws2007HttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="3972a-162">Represents the security capabilities of the [\<ws2007HttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3972a-163">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3972a-163">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.WSHttpTransportSecurityElement>
- [<span data-ttu-id="3972a-164">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="3972a-164">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="3972a-165">Associações</span><span class="sxs-lookup"><span data-stu-id="3972a-165">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="3972a-166">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="3972a-166">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="3972a-167">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="3972a-167">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="3972a-168">\<binding></span><span class="sxs-lookup"><span data-stu-id="3972a-168">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
