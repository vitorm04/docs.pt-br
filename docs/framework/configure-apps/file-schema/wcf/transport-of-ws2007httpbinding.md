---
title: <transport> de <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: 692befa3-8b0b-4ec5-b601-755874e98eb0
ms.openlocfilehash: 60e8758d653848176ca3f287e253bd7990e78470
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91162043"
---
# <a name="transport-of-ws2007httpbinding"></a><span data-ttu-id="83b04-102">\<transport> de \<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="83b04-102">\<transport> of \<ws2007HttpBinding></span></span>

<span data-ttu-id="83b04-103">Define as configurações de autenticação para o transporte HTTP.</span><span class="sxs-lookup"><span data-stu-id="83b04-103">Defines authentication settings for the HTTP transport.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007HttpBinding>**](ws2007httpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-ws2007httpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="83b04-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="83b04-104">Syntax</span></span>  
  
```xml  
<transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
           proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
           realm="string" />
```  
  
## <a name="type"></a><span data-ttu-id="83b04-105">Tipo</span><span class="sxs-lookup"><span data-stu-id="83b04-105">Type</span></span>  

 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="83b04-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="83b04-106">Attributes and Elements</span></span>  

 <span data-ttu-id="83b04-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="83b04-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="83b04-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="83b04-108">Attributes</span></span>  
  
|<span data-ttu-id="83b04-109">Atributo</span><span class="sxs-lookup"><span data-stu-id="83b04-109">Attribute</span></span>|<span data-ttu-id="83b04-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="83b04-110">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="83b04-111">Especifica a credencial usada para autenticar o cliente para o serviço.</span><span class="sxs-lookup"><span data-stu-id="83b04-111">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="83b04-112">Esse atributo é do tipo <xref:System.ServiceModel.HttpClientCredentialType> .</span><span class="sxs-lookup"><span data-stu-id="83b04-112">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="83b04-113">Especifica a credencial usada para autenticar o cliente para um proxy de domínio.</span><span class="sxs-lookup"><span data-stu-id="83b04-113">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="83b04-114">Esse atributo é do tipo <xref:System.ServiceModel.HttpProxyCredentialType> .</span><span class="sxs-lookup"><span data-stu-id="83b04-114">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="83b04-115">O realm de autenticação para Digest ou autenticação básica.</span><span class="sxs-lookup"><span data-stu-id="83b04-115">The authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="83b04-116">O padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="83b04-116">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="83b04-117">Um realm de autenticação especifica pelo menos o nome do host que executa a autenticação.</span><span class="sxs-lookup"><span data-stu-id="83b04-117">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="83b04-118">Ele também pode especificar uma coleção de usuários que têm acesso.</span><span class="sxs-lookup"><span data-stu-id="83b04-118">It can also specify a collection of users who have access.</span></span> <span data-ttu-id="83b04-119">Um usuário pode consultar o realm de autenticação para determinar qual um dos vários nomes de usuário e senhas possíveis podem ser usados.</span><span class="sxs-lookup"><span data-stu-id="83b04-119">A user can query the authentication realm to determine which one of the several possible usernames and passwords can be used.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="83b04-120">Atributo clientCredentialtype</span><span class="sxs-lookup"><span data-stu-id="83b04-120">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="83b04-121">Valor</span><span class="sxs-lookup"><span data-stu-id="83b04-121">Value</span></span>|<span data-ttu-id="83b04-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="83b04-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="83b04-123">Nenhum</span><span class="sxs-lookup"><span data-stu-id="83b04-123">None</span></span>|<span data-ttu-id="83b04-124">A segurança é desabilitada.</span><span class="sxs-lookup"><span data-stu-id="83b04-124">Security is disabled.</span></span>|  
|<span data-ttu-id="83b04-125">Basic</span><span class="sxs-lookup"><span data-stu-id="83b04-125">Basic</span></span>|<span data-ttu-id="83b04-126">Usa a autenticação básica.</span><span class="sxs-lookup"><span data-stu-id="83b04-126">Uses basic authentication.</span></span>|  
|<span data-ttu-id="83b04-127">Digest</span><span class="sxs-lookup"><span data-stu-id="83b04-127">Digest</span></span>|<span data-ttu-id="83b04-128">Usa a autenticação Digest.</span><span class="sxs-lookup"><span data-stu-id="83b04-128">Uses digest authentication.</span></span>|  
|<span data-ttu-id="83b04-129">Ntlm</span><span class="sxs-lookup"><span data-stu-id="83b04-129">Ntlm</span></span>|<span data-ttu-id="83b04-130">Usa a autenticação NTLM como um fallback com um domínio do Windows.</span><span class="sxs-lookup"><span data-stu-id="83b04-130">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="83b04-131">Windows</span><span class="sxs-lookup"><span data-stu-id="83b04-131">Windows</span></span>|<span data-ttu-id="83b04-132">Usa a autenticação integrada do Windows.</span><span class="sxs-lookup"><span data-stu-id="83b04-132">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="83b04-133">Certificado</span><span class="sxs-lookup"><span data-stu-id="83b04-133">Certificate</span></span>|<span data-ttu-id="83b04-134">Usa certificados X. 509 para autenticar o cliente.</span><span class="sxs-lookup"><span data-stu-id="83b04-134">Uses X.509 certificates to authenticate the client.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="83b04-135">Atributo proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="83b04-135">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="83b04-136">Valor</span><span class="sxs-lookup"><span data-stu-id="83b04-136">Value</span></span>|<span data-ttu-id="83b04-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="83b04-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="83b04-138">Nenhum</span><span class="sxs-lookup"><span data-stu-id="83b04-138">None</span></span>|<span data-ttu-id="83b04-139">A segurança é desabilitada.</span><span class="sxs-lookup"><span data-stu-id="83b04-139">Security is disabled.</span></span>|  
|<span data-ttu-id="83b04-140">Basic</span><span class="sxs-lookup"><span data-stu-id="83b04-140">Basic</span></span>|<span data-ttu-id="83b04-141">Usa a autenticação básica.</span><span class="sxs-lookup"><span data-stu-id="83b04-141">Uses basic authentication.</span></span>|  
|<span data-ttu-id="83b04-142">Digest</span><span class="sxs-lookup"><span data-stu-id="83b04-142">Digest</span></span>|<span data-ttu-id="83b04-143">Usa a autenticação Digest.</span><span class="sxs-lookup"><span data-stu-id="83b04-143">Uses digest authentication.</span></span>|  
|<span data-ttu-id="83b04-144">Ntlm</span><span class="sxs-lookup"><span data-stu-id="83b04-144">Ntlm</span></span>|<span data-ttu-id="83b04-145">Usa NTLM como um fallback com um domínio do Windows.</span><span class="sxs-lookup"><span data-stu-id="83b04-145">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="83b04-146">Windows</span><span class="sxs-lookup"><span data-stu-id="83b04-146">Windows</span></span>|<span data-ttu-id="83b04-147">Usa a autenticação integrada do Windows.</span><span class="sxs-lookup"><span data-stu-id="83b04-147">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="83b04-148">Certificado</span><span class="sxs-lookup"><span data-stu-id="83b04-148">Certificate</span></span>|<span data-ttu-id="83b04-149">Usa certificados X. 509 para autenticar o cliente.</span><span class="sxs-lookup"><span data-stu-id="83b04-149">Uses X.509 certificates to authenticate the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="83b04-150">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="83b04-150">Child Elements</span></span>  

 <span data-ttu-id="83b04-151">Nenhum</span><span class="sxs-lookup"><span data-stu-id="83b04-151">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="83b04-152">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="83b04-152">Parent Elements</span></span>  
  
|<span data-ttu-id="83b04-153">Elemento</span><span class="sxs-lookup"><span data-stu-id="83b04-153">Element</span></span>|<span data-ttu-id="83b04-154">Descrição</span><span class="sxs-lookup"><span data-stu-id="83b04-154">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-ws2007httpbinding.md)|<span data-ttu-id="83b04-155">Representa os recursos de segurança do [\<ws2007HttpBinding>](ws2007httpbinding.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="83b04-155">Represents the security capabilities of the [\<ws2007HttpBinding>](ws2007httpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="83b04-156">Confira também</span><span class="sxs-lookup"><span data-stu-id="83b04-156">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.WSHttpTransportSecurityElement>
- [<span data-ttu-id="83b04-157">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="83b04-157">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="83b04-158">Associações</span><span class="sxs-lookup"><span data-stu-id="83b04-158">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="83b04-159">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="83b04-159">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="83b04-160">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="83b04-160">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
