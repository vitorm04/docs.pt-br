---
title: <security> de <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: fdda0ff7-b462-4e26-af52-e87ddab71945
ms.openlocfilehash: e88f55f3651d1ccd55631dce13a0349ac2772624
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73736396"
---
# <a name="security-of-ws2007httpbinding"></a><span data-ttu-id="06c57-102">\<security> de \<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="06c57-102">\<security> of \<ws2007HttpBinding></span></span>
<span data-ttu-id="06c57-103">Representa as configurações de segurança usadas com o [\<ws2007HttpBinding>](ws2007httpbinding.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="06c57-103">Represents the security settings used with the [\<ws2007HttpBinding>](ws2007httpbinding.md) element.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007HttpBinding>**](ws2007httpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="06c57-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="06c57-104">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <bindings>
    <ws2007HttpBinding>
      <binding name = "String">
        <security mode="None/Message/Transport/TransportWithMessageCredential">
          <transport>
          </transport>
          <message>
          </message>
        </security>
      </binding>
    </ws2007HttpBinding>
  </bindings>
</system.ServiceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="06c57-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="06c57-105">Attributes and Elements</span></span>  
 <span data-ttu-id="06c57-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="06c57-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="06c57-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="06c57-107">Attributes</span></span>  
  
|<span data-ttu-id="06c57-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="06c57-108">Attribute</span></span>|<span data-ttu-id="06c57-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="06c57-109">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="06c57-110">Adicional.</span><span class="sxs-lookup"><span data-stu-id="06c57-110">-   Optional.</span></span> <span data-ttu-id="06c57-111">Especifica o tipo de segurança que é aplicado.</span><span class="sxs-lookup"><span data-stu-id="06c57-111">Specifies the type of security that is applied.</span></span> <span data-ttu-id="06c57-112">O padrão é `Message`.</span><span class="sxs-lookup"><span data-stu-id="06c57-112">The default is `Message`.</span></span><br /><br /> <span data-ttu-id="06c57-113">Esse atributo é do tipo <xref:System.ServiceModel.SecurityMode> .</span><span class="sxs-lookup"><span data-stu-id="06c57-113">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="06c57-114">Atributo Mode</span><span class="sxs-lookup"><span data-stu-id="06c57-114">Mode Attribute</span></span>  
  
|<span data-ttu-id="06c57-115">Valor</span><span class="sxs-lookup"><span data-stu-id="06c57-115">Value</span></span>|<span data-ttu-id="06c57-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="06c57-116">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="06c57-117">A segurança é desabilitada.</span><span class="sxs-lookup"><span data-stu-id="06c57-117">Security is disabled.</span></span>|  
|`Transport`|<span data-ttu-id="06c57-118">A proteção é fornecida usando HTTPS.</span><span class="sxs-lookup"><span data-stu-id="06c57-118">Security is provided using HTTPS.</span></span> <span data-ttu-id="06c57-119">O serviço deve ser configurado com certificados de protocolo SSL (SSL).</span><span class="sxs-lookup"><span data-stu-id="06c57-119">The service must be configured with Secure Sockets Layer (SSL) certificates.</span></span> <span data-ttu-id="06c57-120">A mensagem é totalmente protegida usando HTTPS e o serviço é autenticado pelo cliente usando o certificado SSL do serviço.</span><span class="sxs-lookup"><span data-stu-id="06c57-120">The message is entirely secured using HTTPS and the service is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="06c57-121">A autenticação do cliente é controlada por meio do `ClientCredentials` atributo do [\<transport>](transport-of-ws2007httpbinding.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="06c57-121">The client authentication is controlled through the `ClientCredentials` attribute of the [\<transport>](transport-of-ws2007httpbinding.md) element.</span></span>|  
|`Message`|<span data-ttu-id="06c57-122">A segurança é fornecida usando a segurança de mensagem SOAP.</span><span class="sxs-lookup"><span data-stu-id="06c57-122">Security is provided using SOAP message security.</span></span> <span data-ttu-id="06c57-123">Por padrão, o corpo SOAP é criptografado e assinado.</span><span class="sxs-lookup"><span data-stu-id="06c57-123">By default, the SOAP body is encrypted and signed.</span></span> <span data-ttu-id="06c57-124">Esse modo oferece uma variedade de recursos, como se as credenciais de serviço estão disponíveis no cliente fora da banda, o pacote de algoritmos a ser usado e qual nível de proteção aplicar ao corpo da mensagem por meio do <xref:System.ServiceModel.Security.SecurityMessageProperty> .</span><span class="sxs-lookup"><span data-stu-id="06c57-124">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body through the <xref:System.ServiceModel.Security.SecurityMessageProperty>.</span></span> <span data-ttu-id="06c57-125">A autenticação do cliente é executada uma vez para cada sessão e os resultados da autenticação são armazenados em cache durante a sessão.</span><span class="sxs-lookup"><span data-stu-id="06c57-125">Client authentication is performed once for each session and the results of authentication are cached for the duration of the session.</span></span>|  
|`TransportWithMessageCredential`|<span data-ttu-id="06c57-126">Nesse modo, o HTTPS fornece integridade, confidencialidade e autenticação de servidor, e a segurança de mensagem SOAP fornece autenticação de cliente.</span><span class="sxs-lookup"><span data-stu-id="06c57-126">In this mode, HTTPS provides integrity, confidentiality, and server authentication, and SOAP message security provides client authentication.</span></span> <span data-ttu-id="06c57-127">Por padrão, a autenticação do cliente é executada uma vez para cada sessão e os resultados da autenticação são armazenados em cache durante a sessão.</span><span class="sxs-lookup"><span data-stu-id="06c57-127">By default, client authentication is performed once for each session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="06c57-128">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="06c57-128">Child Elements</span></span>  
  
|<span data-ttu-id="06c57-129">Elemento</span><span class="sxs-lookup"><span data-stu-id="06c57-129">Element</span></span>|<span data-ttu-id="06c57-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="06c57-130">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-ws2007httpbinding.md)|<span data-ttu-id="06c57-131">Define as configurações de segurança de transporte.</span><span class="sxs-lookup"><span data-stu-id="06c57-131">Defines the transport security settings.</span></span> <span data-ttu-id="06c57-132">Este elemento corresponde ao <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> tipo.</span><span class="sxs-lookup"><span data-stu-id="06c57-132">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span> <span data-ttu-id="06c57-133">Essas configurações são aplicadas somente quando o modo é definido como transporte.</span><span class="sxs-lookup"><span data-stu-id="06c57-133">These settings are applied only when the mode is set to Transport.</span></span>|  
|[\<message>](message-of-ws2007httpbinding.md)|<span data-ttu-id="06c57-134">Define as configurações de segurança para a mensagem.</span><span class="sxs-lookup"><span data-stu-id="06c57-134">Defines the security settings for the message.</span></span> <span data-ttu-id="06c57-135">Este elemento corresponde ao <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> tipo.</span><span class="sxs-lookup"><span data-stu-id="06c57-135">This element corresponds to the <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> type.</span></span> <span data-ttu-id="06c57-136">Essas configurações não são aplicadas quando o modo é definido como transporte.</span><span class="sxs-lookup"><span data-stu-id="06c57-136">These settings are not applied when the mode is set to Transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="06c57-137">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="06c57-137">Parent Elements</span></span>  
  
|<span data-ttu-id="06c57-138">Elemento</span><span class="sxs-lookup"><span data-stu-id="06c57-138">Element</span></span>|<span data-ttu-id="06c57-139">Descrição</span><span class="sxs-lookup"><span data-stu-id="06c57-139">Description</span></span>|  
|-------------|-----------------|  
|[\<ws2007HttpBinding>](ws2007httpbinding.md)|<span data-ttu-id="06c57-140">Uma associação segura para aplicativos de transporte HTTP.</span><span class="sxs-lookup"><span data-stu-id="06c57-140">A secure binding for HTTP transport applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="06c57-141">Comentários</span><span class="sxs-lookup"><span data-stu-id="06c57-141">Remarks</span></span>  
 <span data-ttu-id="06c57-142">Esse elemento foi projetado para interoperação com serviços que implementam especificações WS-\*.</span><span class="sxs-lookup"><span data-stu-id="06c57-142">This element is designed for interoperation with services that implement WS-\* specifications.</span></span> <span data-ttu-id="06c57-143">A segurança de transporte para essa associação é protocolo SSL (SSL) sobre HTTP ou HTTPS.</span><span class="sxs-lookup"><span data-stu-id="06c57-143">The transport security for this binding is Secure Sockets Layer (SSL) over HTTP, or HTTPS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06c57-144">Confira também</span><span class="sxs-lookup"><span data-stu-id="06c57-144">See also</span></span>

- <xref:System.ServiceModel.WSHttpSecurity>
- <xref:System.ServiceModel.WSHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [<span data-ttu-id="06c57-145">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="06c57-145">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="06c57-146">Associações</span><span class="sxs-lookup"><span data-stu-id="06c57-146">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="06c57-147">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="06c57-147">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="06c57-148">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="06c57-148">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
