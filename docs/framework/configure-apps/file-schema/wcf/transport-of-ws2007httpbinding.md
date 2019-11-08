---
title: <transport> de <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: 692befa3-8b0b-4ec5-b601-755874e98eb0
ms.openlocfilehash: 0cd20c607b0c4ddd3ecfd806d38ba63b4a5c5a25
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73732767"
---
# <a name="transport-of-ws2007httpbinding"></a><span data-ttu-id="384f6-102">> de transporte de \<de \<ws2007HttpBinding ></span><span class="sxs-lookup"><span data-stu-id="384f6-102">\<transport> of \<ws2007HttpBinding></span></span>
<span data-ttu-id="384f6-103">Define as configurações de autenticação para o transporte HTTP.</span><span class="sxs-lookup"><span data-stu-id="384f6-103">Defines authentication settings for the HTTP transport.</span></span>  
  
<span data-ttu-id="384f6-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="384f6-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="384f6-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="384f6-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="384f6-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações**](bindings.md) ></span><span class="sxs-lookup"><span data-stu-id="384f6-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="384f6-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<ws2007HttpBinding >** ](ws2007httpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="384f6-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007HttpBinding>**](ws2007httpbinding.md)</span></span>\
<span data-ttu-id="384f6-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Binding** ></span><span class="sxs-lookup"><span data-stu-id="384f6-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="384f6-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<security >** ](security-of-ws2007httpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="384f6-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-ws2007httpbinding.md)</span></span>\
<span data-ttu-id="384f6-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**transporte >**</span><span class="sxs-lookup"><span data-stu-id="384f6-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="384f6-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="384f6-111">Syntax</span></span>  
  
```xml  
<transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
           proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
           realm="string" />
```  
  
## <a name="type"></a><span data-ttu-id="384f6-112">Digite</span><span class="sxs-lookup"><span data-stu-id="384f6-112">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="384f6-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="384f6-113">Attributes and Elements</span></span>  
 <span data-ttu-id="384f6-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="384f6-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="384f6-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="384f6-115">Attributes</span></span>  
  
|<span data-ttu-id="384f6-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="384f6-116">Attribute</span></span>|<span data-ttu-id="384f6-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="384f6-117">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="384f6-118">Especifica a credencial usada para autenticar o cliente para o serviço.</span><span class="sxs-lookup"><span data-stu-id="384f6-118">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="384f6-119">Este atributo é do tipo <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="384f6-119">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="384f6-120">Especifica a credencial usada para autenticar o cliente para um proxy de domínio.</span><span class="sxs-lookup"><span data-stu-id="384f6-120">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="384f6-121">Este atributo é do tipo <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="384f6-121">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="384f6-122">O realm de autenticação para Digest ou autenticação básica.</span><span class="sxs-lookup"><span data-stu-id="384f6-122">The authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="384f6-123">O padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="384f6-123">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="384f6-124">Um realm de autenticação especifica pelo menos o nome do host que executa a autenticação.</span><span class="sxs-lookup"><span data-stu-id="384f6-124">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="384f6-125">Ele também pode especificar uma coleção de usuários que têm acesso.</span><span class="sxs-lookup"><span data-stu-id="384f6-125">It can also specify a collection of users who have access.</span></span> <span data-ttu-id="384f6-126">Um usuário pode consultar o realm de autenticação para determinar qual um dos vários nomes de usuário e senhas possíveis podem ser usados.</span><span class="sxs-lookup"><span data-stu-id="384f6-126">A user can query the authentication realm to determine which one of the several possible usernames and passwords can be used.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="384f6-127">Atributo clientCredentialtype</span><span class="sxs-lookup"><span data-stu-id="384f6-127">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="384f6-128">Valor</span><span class="sxs-lookup"><span data-stu-id="384f6-128">Value</span></span>|<span data-ttu-id="384f6-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="384f6-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="384f6-130">Nenhum</span><span class="sxs-lookup"><span data-stu-id="384f6-130">None</span></span>|<span data-ttu-id="384f6-131">A segurança é desabilitada.</span><span class="sxs-lookup"><span data-stu-id="384f6-131">Security is disabled.</span></span>|  
|<span data-ttu-id="384f6-132">Basic</span><span class="sxs-lookup"><span data-stu-id="384f6-132">Basic</span></span>|<span data-ttu-id="384f6-133">Usa a autenticação básica.</span><span class="sxs-lookup"><span data-stu-id="384f6-133">Uses basic authentication.</span></span>|  
|<span data-ttu-id="384f6-134">Digest</span><span class="sxs-lookup"><span data-stu-id="384f6-134">Digest</span></span>|<span data-ttu-id="384f6-135">Usa a autenticação Digest.</span><span class="sxs-lookup"><span data-stu-id="384f6-135">Uses digest authentication.</span></span>|  
|<span data-ttu-id="384f6-136">NTLM</span><span class="sxs-lookup"><span data-stu-id="384f6-136">Ntlm</span></span>|<span data-ttu-id="384f6-137">Usa a autenticação NTLM como um fallback com um domínio do Windows.</span><span class="sxs-lookup"><span data-stu-id="384f6-137">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="384f6-138">Windows</span><span class="sxs-lookup"><span data-stu-id="384f6-138">Windows</span></span>|<span data-ttu-id="384f6-139">Usa a autenticação integrada do Windows.</span><span class="sxs-lookup"><span data-stu-id="384f6-139">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="384f6-140">Certificate</span><span class="sxs-lookup"><span data-stu-id="384f6-140">Certificate</span></span>|<span data-ttu-id="384f6-141">Usa certificados X. 509 para autenticar o cliente.</span><span class="sxs-lookup"><span data-stu-id="384f6-141">Uses X.509 certificates to authenticate the client.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="384f6-142">Atributo proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="384f6-142">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="384f6-143">Valor</span><span class="sxs-lookup"><span data-stu-id="384f6-143">Value</span></span>|<span data-ttu-id="384f6-144">Descrição</span><span class="sxs-lookup"><span data-stu-id="384f6-144">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="384f6-145">Nenhum</span><span class="sxs-lookup"><span data-stu-id="384f6-145">None</span></span>|<span data-ttu-id="384f6-146">A segurança é desabilitada.</span><span class="sxs-lookup"><span data-stu-id="384f6-146">Security is disabled.</span></span>|  
|<span data-ttu-id="384f6-147">Basic</span><span class="sxs-lookup"><span data-stu-id="384f6-147">Basic</span></span>|<span data-ttu-id="384f6-148">Usa a autenticação básica.</span><span class="sxs-lookup"><span data-stu-id="384f6-148">Uses basic authentication.</span></span>|  
|<span data-ttu-id="384f6-149">Digest</span><span class="sxs-lookup"><span data-stu-id="384f6-149">Digest</span></span>|<span data-ttu-id="384f6-150">Usa a autenticação Digest.</span><span class="sxs-lookup"><span data-stu-id="384f6-150">Uses digest authentication.</span></span>|  
|<span data-ttu-id="384f6-151">NTLM</span><span class="sxs-lookup"><span data-stu-id="384f6-151">Ntlm</span></span>|<span data-ttu-id="384f6-152">Usa NTLM como um fallback com um domínio do Windows.</span><span class="sxs-lookup"><span data-stu-id="384f6-152">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="384f6-153">Windows</span><span class="sxs-lookup"><span data-stu-id="384f6-153">Windows</span></span>|<span data-ttu-id="384f6-154">Usa a autenticação integrada do Windows.</span><span class="sxs-lookup"><span data-stu-id="384f6-154">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="384f6-155">Certificate</span><span class="sxs-lookup"><span data-stu-id="384f6-155">Certificate</span></span>|<span data-ttu-id="384f6-156">Usa certificados X. 509 para autenticar o cliente.</span><span class="sxs-lookup"><span data-stu-id="384f6-156">Uses X.509 certificates to authenticate the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="384f6-157">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="384f6-157">Child Elements</span></span>  
 <span data-ttu-id="384f6-158">Nenhum</span><span class="sxs-lookup"><span data-stu-id="384f6-158">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="384f6-159">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="384f6-159">Parent Elements</span></span>  
  
|<span data-ttu-id="384f6-160">Elemento</span><span class="sxs-lookup"><span data-stu-id="384f6-160">Element</span></span>|<span data-ttu-id="384f6-161">Descrição</span><span class="sxs-lookup"><span data-stu-id="384f6-161">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="384f6-162">\<Security ></span><span class="sxs-lookup"><span data-stu-id="384f6-162">\<security></span></span>](security-of-ws2007httpbinding.md)|<span data-ttu-id="384f6-163">Representa os recursos de segurança do elemento [\<ws2007HttpBinding >](ws2007httpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="384f6-163">Represents the security capabilities of the [\<ws2007HttpBinding>](ws2007httpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="384f6-164">Consulte também</span><span class="sxs-lookup"><span data-stu-id="384f6-164">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.WSHttpTransportSecurityElement>
- [<span data-ttu-id="384f6-165">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="384f6-165">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="384f6-166">Associações</span><span class="sxs-lookup"><span data-stu-id="384f6-166">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="384f6-167">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="384f6-167">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="384f6-168">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="384f6-168">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="384f6-169">\<binding ></span><span class="sxs-lookup"><span data-stu-id="384f6-169">\<binding></span></span>](bindings.md)
