---
title: <transport> de <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: 692befa3-8b0b-4ec5-b601-755874e98eb0
ms.openlocfilehash: 4ea60ccaba58bc0b3fa8f2263295bf1413d25e89
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399262"
---
# <a name="transport-of-ws2007httpbinding"></a><span data-ttu-id="2998f-102">\<> de transporte \<do ws2007HttpBinding ></span><span class="sxs-lookup"><span data-stu-id="2998f-102">\<transport> of \<ws2007HttpBinding></span></span>
<span data-ttu-id="2998f-103">Define as configurações de autenticação para o transporte HTTP.</span><span class="sxs-lookup"><span data-stu-id="2998f-103">Defines authentication settings for the HTTP transport.</span></span>  
  
<span data-ttu-id="2998f-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="2998f-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2998f-105">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="2998f-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="2998f-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="2998f-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="2998f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> ws2007HttpBinding**](ws2007httpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="2998f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007HttpBinding>**](ws2007httpbinding.md)</span></span>\
<span data-ttu-id="2998f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de associação**</span><span class="sxs-lookup"><span data-stu-id="2998f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="2998f-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de segurança**](security-of-ws2007httpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="2998f-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-ws2007httpbinding.md)</span></span>\
<span data-ttu-id="2998f-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de transporte**</span><span class="sxs-lookup"><span data-stu-id="2998f-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2998f-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2998f-111">Syntax</span></span>  
  
```xml  
<transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
           proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
           realm="string" />
```  
  
## <a name="type"></a><span data-ttu-id="2998f-112">Tipo</span><span class="sxs-lookup"><span data-stu-id="2998f-112">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2998f-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="2998f-113">Attributes and Elements</span></span>  
 <span data-ttu-id="2998f-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="2998f-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2998f-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="2998f-115">Attributes</span></span>  
  
|<span data-ttu-id="2998f-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="2998f-116">Attribute</span></span>|<span data-ttu-id="2998f-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="2998f-117">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="2998f-118">Especifica a credencial usada para autenticar o cliente para o serviço.</span><span class="sxs-lookup"><span data-stu-id="2998f-118">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="2998f-119">Esse atributo é do tipo <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="2998f-119">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="2998f-120">Especifica a credencial usada para autenticar o cliente para um proxy de domínio.</span><span class="sxs-lookup"><span data-stu-id="2998f-120">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="2998f-121">Esse atributo é do tipo <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="2998f-121">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="2998f-122">O realm de autenticação para Digest ou autenticação básica.</span><span class="sxs-lookup"><span data-stu-id="2998f-122">The authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="2998f-123">O padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="2998f-123">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="2998f-124">Um realm de autenticação especifica pelo menos o nome do host que executa a autenticação.</span><span class="sxs-lookup"><span data-stu-id="2998f-124">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="2998f-125">Ele também pode especificar uma coleção de usuários que têm acesso.</span><span class="sxs-lookup"><span data-stu-id="2998f-125">It can also specify a collection of users who have access.</span></span> <span data-ttu-id="2998f-126">Um usuário pode consultar o realm de autenticação para determinar qual um dos vários nomes de usuário e senhas possíveis podem ser usados.</span><span class="sxs-lookup"><span data-stu-id="2998f-126">A user can query the authentication realm to determine which one of the several possible usernames and passwords can be used.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="2998f-127">Atributo clientCredentialtype</span><span class="sxs-lookup"><span data-stu-id="2998f-127">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="2998f-128">Valor</span><span class="sxs-lookup"><span data-stu-id="2998f-128">Value</span></span>|<span data-ttu-id="2998f-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="2998f-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2998f-130">Nenhum</span><span class="sxs-lookup"><span data-stu-id="2998f-130">None</span></span>|<span data-ttu-id="2998f-131">A segurança é desabilitada.</span><span class="sxs-lookup"><span data-stu-id="2998f-131">Security is disabled.</span></span>|  
|<span data-ttu-id="2998f-132">Basic</span><span class="sxs-lookup"><span data-stu-id="2998f-132">Basic</span></span>|<span data-ttu-id="2998f-133">Usa a autenticação básica.</span><span class="sxs-lookup"><span data-stu-id="2998f-133">Uses basic authentication.</span></span>|  
|<span data-ttu-id="2998f-134">Digest</span><span class="sxs-lookup"><span data-stu-id="2998f-134">Digest</span></span>|<span data-ttu-id="2998f-135">Usa a autenticação Digest.</span><span class="sxs-lookup"><span data-stu-id="2998f-135">Uses digest authentication.</span></span>|  
|<span data-ttu-id="2998f-136">NTLM</span><span class="sxs-lookup"><span data-stu-id="2998f-136">Ntlm</span></span>|<span data-ttu-id="2998f-137">Usa a autenticação NTLM como um fallback com um domínio do Windows.</span><span class="sxs-lookup"><span data-stu-id="2998f-137">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="2998f-138">Windows</span><span class="sxs-lookup"><span data-stu-id="2998f-138">Windows</span></span>|<span data-ttu-id="2998f-139">Usa a autenticação integrada do Windows.</span><span class="sxs-lookup"><span data-stu-id="2998f-139">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="2998f-140">Certificate</span><span class="sxs-lookup"><span data-stu-id="2998f-140">Certificate</span></span>|<span data-ttu-id="2998f-141">Usa certificados X. 509 para autenticar o cliente.</span><span class="sxs-lookup"><span data-stu-id="2998f-141">Uses X.509 certificates to authenticate the client.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="2998f-142">Atributo proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="2998f-142">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="2998f-143">Valor</span><span class="sxs-lookup"><span data-stu-id="2998f-143">Value</span></span>|<span data-ttu-id="2998f-144">Descrição</span><span class="sxs-lookup"><span data-stu-id="2998f-144">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2998f-145">Nenhum</span><span class="sxs-lookup"><span data-stu-id="2998f-145">None</span></span>|<span data-ttu-id="2998f-146">A segurança é desabilitada.</span><span class="sxs-lookup"><span data-stu-id="2998f-146">Security is disabled.</span></span>|  
|<span data-ttu-id="2998f-147">Basic</span><span class="sxs-lookup"><span data-stu-id="2998f-147">Basic</span></span>|<span data-ttu-id="2998f-148">Usa a autenticação básica.</span><span class="sxs-lookup"><span data-stu-id="2998f-148">Uses basic authentication.</span></span>|  
|<span data-ttu-id="2998f-149">Digest</span><span class="sxs-lookup"><span data-stu-id="2998f-149">Digest</span></span>|<span data-ttu-id="2998f-150">Usa a autenticação Digest.</span><span class="sxs-lookup"><span data-stu-id="2998f-150">Uses digest authentication.</span></span>|  
|<span data-ttu-id="2998f-151">NTLM</span><span class="sxs-lookup"><span data-stu-id="2998f-151">Ntlm</span></span>|<span data-ttu-id="2998f-152">Usa NTLM como um fallback com um domínio do Windows.</span><span class="sxs-lookup"><span data-stu-id="2998f-152">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="2998f-153">Windows</span><span class="sxs-lookup"><span data-stu-id="2998f-153">Windows</span></span>|<span data-ttu-id="2998f-154">Usa a autenticação integrada do Windows.</span><span class="sxs-lookup"><span data-stu-id="2998f-154">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="2998f-155">Certificate</span><span class="sxs-lookup"><span data-stu-id="2998f-155">Certificate</span></span>|<span data-ttu-id="2998f-156">Usa certificados X. 509 para autenticar o cliente.</span><span class="sxs-lookup"><span data-stu-id="2998f-156">Uses X.509 certificates to authenticate the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2998f-157">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="2998f-157">Child Elements</span></span>  
 <span data-ttu-id="2998f-158">Nenhum</span><span class="sxs-lookup"><span data-stu-id="2998f-158">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2998f-159">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="2998f-159">Parent Elements</span></span>  
  
|<span data-ttu-id="2998f-160">Elemento</span><span class="sxs-lookup"><span data-stu-id="2998f-160">Element</span></span>|<span data-ttu-id="2998f-161">Descrição</span><span class="sxs-lookup"><span data-stu-id="2998f-161">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2998f-162">\<security></span><span class="sxs-lookup"><span data-stu-id="2998f-162">\<security></span></span>](security-of-ws2007httpbinding.md)|<span data-ttu-id="2998f-163">Representa os recursos de segurança do [ \<elemento > ws2007HttpBinding](ws2007httpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="2998f-163">Represents the security capabilities of the [\<ws2007HttpBinding>](ws2007httpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2998f-164">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2998f-164">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.WSHttpTransportSecurityElement>
- [<span data-ttu-id="2998f-165">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="2998f-165">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="2998f-166">Associações</span><span class="sxs-lookup"><span data-stu-id="2998f-166">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="2998f-167">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="2998f-167">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="2998f-168">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="2998f-168">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="2998f-169">\<binding></span><span class="sxs-lookup"><span data-stu-id="2998f-169">\<binding></span></span>](../../../misc/binding.md)
