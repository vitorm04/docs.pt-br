---
title: '&lt;transporte&gt; de &lt;ws2007HttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 692befa3-8b0b-4ec5-b601-755874e98eb0
ms.openlocfilehash: 35af47551f742b0e48220611a874605fb752b626
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43396791"
---
# <a name="lttransportgt-of-ltws2007httpbindinggt"></a><span data-ttu-id="8164c-102">&lt;transporte&gt; de &lt;ws2007HttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="8164c-102">&lt;transport&gt; of &lt;ws2007HttpBinding&gt;</span></span>
<span data-ttu-id="8164c-103">Define as configurações de autenticação para o transporte HTTP.</span><span class="sxs-lookup"><span data-stu-id="8164c-103">Defines authentication settings for the HTTP transport.</span></span>  
  
 <span data-ttu-id="8164c-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="8164c-104">\<system.serviceModel></span></span>  
<span data-ttu-id="8164c-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="8164c-105">\<bindings></span></span>  
<span data-ttu-id="8164c-106">\<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="8164c-106">\<ws2007HttpBinding></span></span>  
<span data-ttu-id="8164c-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="8164c-107">\<binding></span></span>  
<span data-ttu-id="8164c-108">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="8164c-108">\<security></span></span>  
<span data-ttu-id="8164c-109">\<transporte ></span><span class="sxs-lookup"><span data-stu-id="8164c-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8164c-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8164c-110">Syntax</span></span>  
  
```  
transport clientCredentialType =   
       "Basic/Certificate/Digest/None/Ntlm/Windows"  
       proxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
       realm="string"   
```  
  
## <a name="type"></a><span data-ttu-id="8164c-111">Tipo</span><span class="sxs-lookup"><span data-stu-id="8164c-111">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8164c-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="8164c-112">Attributes and Elements</span></span>  
 <span data-ttu-id="8164c-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="8164c-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8164c-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="8164c-114">Attributes</span></span>  
  
|<span data-ttu-id="8164c-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="8164c-115">Attribute</span></span>|<span data-ttu-id="8164c-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="8164c-116">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="8164c-117">Especifica a credencial usada para autenticar o cliente para o serviço.</span><span class="sxs-lookup"><span data-stu-id="8164c-117">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="8164c-118">Esse atributo é do tipo <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="8164c-118">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="8164c-119">Especifica a credencial usada para autenticar o cliente para um proxy do domínio.</span><span class="sxs-lookup"><span data-stu-id="8164c-119">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="8164c-120">Esse atributo é do tipo <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="8164c-120">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="8164c-121">O realm de autenticação para a autenticação básica ou digest.</span><span class="sxs-lookup"><span data-stu-id="8164c-121">The authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="8164c-122">O padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="8164c-122">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="8164c-123">Pelo menos, um realm de autenticação especifica o nome do host que executa a autenticação.</span><span class="sxs-lookup"><span data-stu-id="8164c-123">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="8164c-124">Ele também pode especificar uma coleção de usuários que têm acesso.</span><span class="sxs-lookup"><span data-stu-id="8164c-124">It can also specify a collection of users who have access.</span></span> <span data-ttu-id="8164c-125">Um usuário pode consultar o realm de autenticação para determinar qual dos vários possíveis nomes de usuário e senhas pode ser usado.</span><span class="sxs-lookup"><span data-stu-id="8164c-125">A user can query the authentication realm to determine which one of the several possible usernames and passwords can be used.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="8164c-126">clientCredentialType de atributo</span><span class="sxs-lookup"><span data-stu-id="8164c-126">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="8164c-127">Valor</span><span class="sxs-lookup"><span data-stu-id="8164c-127">Value</span></span>|<span data-ttu-id="8164c-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="8164c-128">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8164c-129">Nenhum</span><span class="sxs-lookup"><span data-stu-id="8164c-129">None</span></span>|<span data-ttu-id="8164c-130">A segurança é desabilitada.</span><span class="sxs-lookup"><span data-stu-id="8164c-130">Security is disabled.</span></span>|  
|<span data-ttu-id="8164c-131">Basic</span><span class="sxs-lookup"><span data-stu-id="8164c-131">Basic</span></span>|<span data-ttu-id="8164c-132">Usa a autenticação básica.</span><span class="sxs-lookup"><span data-stu-id="8164c-132">Uses basic authentication.</span></span>|  
|<span data-ttu-id="8164c-133">Digest</span><span class="sxs-lookup"><span data-stu-id="8164c-133">Digest</span></span>|<span data-ttu-id="8164c-134">Usa autenticação digest.</span><span class="sxs-lookup"><span data-stu-id="8164c-134">Uses digest authentication.</span></span>|  
|<span data-ttu-id="8164c-135">NTLM</span><span class="sxs-lookup"><span data-stu-id="8164c-135">Ntlm</span></span>|<span data-ttu-id="8164c-136">Usa a autenticação NTLM como um fallback com um domínio do Windows.</span><span class="sxs-lookup"><span data-stu-id="8164c-136">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="8164c-137">Windows</span><span class="sxs-lookup"><span data-stu-id="8164c-137">Windows</span></span>|<span data-ttu-id="8164c-138">Usa integrada a autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="8164c-138">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="8164c-139">Certificado</span><span class="sxs-lookup"><span data-stu-id="8164c-139">Certificate</span></span>|<span data-ttu-id="8164c-140">Usa certificados x. 509 para autenticar o cliente.</span><span class="sxs-lookup"><span data-stu-id="8164c-140">Uses X.509 certificates to authenticate the client.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="8164c-141">proxyCredentialType atributo</span><span class="sxs-lookup"><span data-stu-id="8164c-141">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="8164c-142">Valor</span><span class="sxs-lookup"><span data-stu-id="8164c-142">Value</span></span>|<span data-ttu-id="8164c-143">Descrição</span><span class="sxs-lookup"><span data-stu-id="8164c-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8164c-144">Nenhum</span><span class="sxs-lookup"><span data-stu-id="8164c-144">None</span></span>|<span data-ttu-id="8164c-145">A segurança é desabilitada.</span><span class="sxs-lookup"><span data-stu-id="8164c-145">Security is disabled.</span></span>|  
|<span data-ttu-id="8164c-146">Basic</span><span class="sxs-lookup"><span data-stu-id="8164c-146">Basic</span></span>|<span data-ttu-id="8164c-147">Usa a autenticação básica.</span><span class="sxs-lookup"><span data-stu-id="8164c-147">Uses basic authentication.</span></span>|  
|<span data-ttu-id="8164c-148">Digest</span><span class="sxs-lookup"><span data-stu-id="8164c-148">Digest</span></span>|<span data-ttu-id="8164c-149">Usa autenticação digest.</span><span class="sxs-lookup"><span data-stu-id="8164c-149">Uses digest authentication.</span></span>|  
|<span data-ttu-id="8164c-150">NTLM</span><span class="sxs-lookup"><span data-stu-id="8164c-150">Ntlm</span></span>|<span data-ttu-id="8164c-151">Usa NTLM como um fallback com um domínio do Windows.</span><span class="sxs-lookup"><span data-stu-id="8164c-151">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="8164c-152">Windows</span><span class="sxs-lookup"><span data-stu-id="8164c-152">Windows</span></span>|<span data-ttu-id="8164c-153">Usa integrada a autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="8164c-153">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="8164c-154">Certificado</span><span class="sxs-lookup"><span data-stu-id="8164c-154">Certificate</span></span>|<span data-ttu-id="8164c-155">Usa certificados x. 509 para autenticar o cliente.</span><span class="sxs-lookup"><span data-stu-id="8164c-155">Uses X.509 certificates to authenticate the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8164c-156">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="8164c-156">Child Elements</span></span>  
 <span data-ttu-id="8164c-157">Nenhum</span><span class="sxs-lookup"><span data-stu-id="8164c-157">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8164c-158">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="8164c-158">Parent Elements</span></span>  
  
|<span data-ttu-id="8164c-159">Elemento</span><span class="sxs-lookup"><span data-stu-id="8164c-159">Element</span></span>|<span data-ttu-id="8164c-160">Descrição</span><span class="sxs-lookup"><span data-stu-id="8164c-160">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8164c-161">\<security></span><span class="sxs-lookup"><span data-stu-id="8164c-161">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-ws2007httpbinding.md)|<span data-ttu-id="8164c-162">Representa os recursos de segurança de [ \<ws2007HttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="8164c-162">Represents the security capabilities of the [\<ws2007HttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8164c-163">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8164c-163">See Also</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
 <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpTransportSecurityElement>  
 [<span data-ttu-id="8164c-164">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="8164c-164">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="8164c-165">Associações</span><span class="sxs-lookup"><span data-stu-id="8164c-165">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="8164c-166">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="8164c-166">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="8164c-167">Usando associações para configurar clientes e serviços do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="8164c-167">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="8164c-168">\<associação ></span><span class="sxs-lookup"><span data-stu-id="8164c-168">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
