---
title: <transport> de <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: 692befa3-8b0b-4ec5-b601-755874e98eb0
ms.openlocfilehash: 0cd20c607b0c4ddd3ecfd806d38ba63b4a5c5a25
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73732767"
---
# <a name="transport-of-ws2007httpbinding"></a><span data-ttu-id="a9dbf-102">\<transport> de \<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="a9dbf-102">\<transport> of \<ws2007HttpBinding></span></span>
<span data-ttu-id="a9dbf-103">Define as configurações de autenticação para o transporte HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9dbf-103">Defines authentication settings for the HTTP transport.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007HttpBinding>**](ws2007httpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-ws2007httpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="a9dbf-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a9dbf-104">Syntax</span></span>  
  
```xml  
<transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
           proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
           realm="string" />
```  
  
## <a name="type"></a><span data-ttu-id="a9dbf-105">Type</span><span class="sxs-lookup"><span data-stu-id="a9dbf-105">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a9dbf-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a9dbf-106">Attributes and Elements</span></span>  
 <span data-ttu-id="a9dbf-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a9dbf-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a9dbf-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="a9dbf-108">Attributes</span></span>  
  
|<span data-ttu-id="a9dbf-109">Atributo</span><span class="sxs-lookup"><span data-stu-id="a9dbf-109">Attribute</span></span>|<span data-ttu-id="a9dbf-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="a9dbf-110">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="a9dbf-111">Especifica a credencial usada para autenticar o cliente para o serviço.</span><span class="sxs-lookup"><span data-stu-id="a9dbf-111">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="a9dbf-112">Esse atributo é do tipo <xref:System.ServiceModel.HttpClientCredentialType> .</span><span class="sxs-lookup"><span data-stu-id="a9dbf-112">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="a9dbf-113">Especifica a credencial usada para autenticar o cliente para um proxy de domínio.</span><span class="sxs-lookup"><span data-stu-id="a9dbf-113">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="a9dbf-114">Esse atributo é do tipo <xref:System.ServiceModel.HttpProxyCredentialType> .</span><span class="sxs-lookup"><span data-stu-id="a9dbf-114">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="a9dbf-115">O realm de autenticação para Digest ou autenticação básica.</span><span class="sxs-lookup"><span data-stu-id="a9dbf-115">The authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="a9dbf-116">O padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="a9dbf-116">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="a9dbf-117">Um realm de autenticação especifica pelo menos o nome do host que executa a autenticação.</span><span class="sxs-lookup"><span data-stu-id="a9dbf-117">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="a9dbf-118">Ele também pode especificar uma coleção de usuários que têm acesso.</span><span class="sxs-lookup"><span data-stu-id="a9dbf-118">It can also specify a collection of users who have access.</span></span> <span data-ttu-id="a9dbf-119">Um usuário pode consultar o realm de autenticação para determinar qual um dos vários nomes de usuário e senhas possíveis podem ser usados.</span><span class="sxs-lookup"><span data-stu-id="a9dbf-119">A user can query the authentication realm to determine which one of the several possible usernames and passwords can be used.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="a9dbf-120">Atributo clientCredentialtype</span><span class="sxs-lookup"><span data-stu-id="a9dbf-120">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="a9dbf-121">Valor</span><span class="sxs-lookup"><span data-stu-id="a9dbf-121">Value</span></span>|<span data-ttu-id="a9dbf-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="a9dbf-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a9dbf-123">Nenhum</span><span class="sxs-lookup"><span data-stu-id="a9dbf-123">None</span></span>|<span data-ttu-id="a9dbf-124">A segurança é desabilitada.</span><span class="sxs-lookup"><span data-stu-id="a9dbf-124">Security is disabled.</span></span>|  
|<span data-ttu-id="a9dbf-125">Basic</span><span class="sxs-lookup"><span data-stu-id="a9dbf-125">Basic</span></span>|<span data-ttu-id="a9dbf-126">Usa a autenticação básica.</span><span class="sxs-lookup"><span data-stu-id="a9dbf-126">Uses basic authentication.</span></span>|  
|<span data-ttu-id="a9dbf-127">Digest</span><span class="sxs-lookup"><span data-stu-id="a9dbf-127">Digest</span></span>|<span data-ttu-id="a9dbf-128">Usa a autenticação Digest.</span><span class="sxs-lookup"><span data-stu-id="a9dbf-128">Uses digest authentication.</span></span>|  
|<span data-ttu-id="a9dbf-129">Ntlm</span><span class="sxs-lookup"><span data-stu-id="a9dbf-129">Ntlm</span></span>|<span data-ttu-id="a9dbf-130">Usa a autenticação NTLM como um fallback com um domínio do Windows.</span><span class="sxs-lookup"><span data-stu-id="a9dbf-130">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="a9dbf-131">Windows</span><span class="sxs-lookup"><span data-stu-id="a9dbf-131">Windows</span></span>|<span data-ttu-id="a9dbf-132">Usa a autenticação integrada do Windows.</span><span class="sxs-lookup"><span data-stu-id="a9dbf-132">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="a9dbf-133">Certificado</span><span class="sxs-lookup"><span data-stu-id="a9dbf-133">Certificate</span></span>|<span data-ttu-id="a9dbf-134">Usa certificados X. 509 para autenticar o cliente.</span><span class="sxs-lookup"><span data-stu-id="a9dbf-134">Uses X.509 certificates to authenticate the client.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="a9dbf-135">Atributo proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="a9dbf-135">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="a9dbf-136">Valor</span><span class="sxs-lookup"><span data-stu-id="a9dbf-136">Value</span></span>|<span data-ttu-id="a9dbf-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="a9dbf-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a9dbf-138">Nenhum</span><span class="sxs-lookup"><span data-stu-id="a9dbf-138">None</span></span>|<span data-ttu-id="a9dbf-139">A segurança é desabilitada.</span><span class="sxs-lookup"><span data-stu-id="a9dbf-139">Security is disabled.</span></span>|  
|<span data-ttu-id="a9dbf-140">Basic</span><span class="sxs-lookup"><span data-stu-id="a9dbf-140">Basic</span></span>|<span data-ttu-id="a9dbf-141">Usa a autenticação básica.</span><span class="sxs-lookup"><span data-stu-id="a9dbf-141">Uses basic authentication.</span></span>|  
|<span data-ttu-id="a9dbf-142">Digest</span><span class="sxs-lookup"><span data-stu-id="a9dbf-142">Digest</span></span>|<span data-ttu-id="a9dbf-143">Usa a autenticação Digest.</span><span class="sxs-lookup"><span data-stu-id="a9dbf-143">Uses digest authentication.</span></span>|  
|<span data-ttu-id="a9dbf-144">Ntlm</span><span class="sxs-lookup"><span data-stu-id="a9dbf-144">Ntlm</span></span>|<span data-ttu-id="a9dbf-145">Usa NTLM como um fallback com um domínio do Windows.</span><span class="sxs-lookup"><span data-stu-id="a9dbf-145">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="a9dbf-146">Windows</span><span class="sxs-lookup"><span data-stu-id="a9dbf-146">Windows</span></span>|<span data-ttu-id="a9dbf-147">Usa a autenticação integrada do Windows.</span><span class="sxs-lookup"><span data-stu-id="a9dbf-147">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="a9dbf-148">Certificado</span><span class="sxs-lookup"><span data-stu-id="a9dbf-148">Certificate</span></span>|<span data-ttu-id="a9dbf-149">Usa certificados X. 509 para autenticar o cliente.</span><span class="sxs-lookup"><span data-stu-id="a9dbf-149">Uses X.509 certificates to authenticate the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a9dbf-150">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a9dbf-150">Child Elements</span></span>  
 <span data-ttu-id="a9dbf-151">Nenhum</span><span class="sxs-lookup"><span data-stu-id="a9dbf-151">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a9dbf-152">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a9dbf-152">Parent Elements</span></span>  
  
|<span data-ttu-id="a9dbf-153">Elemento</span><span class="sxs-lookup"><span data-stu-id="a9dbf-153">Element</span></span>|<span data-ttu-id="a9dbf-154">Descrição</span><span class="sxs-lookup"><span data-stu-id="a9dbf-154">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-ws2007httpbinding.md)|<span data-ttu-id="a9dbf-155">Representa os recursos de segurança do [\<ws2007HttpBinding>](ws2007httpbinding.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="a9dbf-155">Represents the security capabilities of the [\<ws2007HttpBinding>](ws2007httpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a9dbf-156">Confira também</span><span class="sxs-lookup"><span data-stu-id="a9dbf-156">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.WSHttpTransportSecurityElement>
- [<span data-ttu-id="a9dbf-157">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="a9dbf-157">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="a9dbf-158">Associações</span><span class="sxs-lookup"><span data-stu-id="a9dbf-158">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="a9dbf-159">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="a9dbf-159">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="a9dbf-160">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="a9dbf-160">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
