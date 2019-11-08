---
title: <security> de <wsDualHttpBinding>
ms.date: 03/30/2017
ms.assetid: 869c05e7-4ebe-467d-95ab-c8f8de4e6b9e
ms.openlocfilehash: 4969c041678bbf3490975bc0ec53507b6cf762bb
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738611"
---
# <a name="security-of-wsdualhttpbinding"></a><span data-ttu-id="5471e-102">\<> de segurança do \<wsDualHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="5471e-102">\<security> of \<wsDualHttpBinding></span></span>
<span data-ttu-id="5471e-103">Define os recursos de segurança do [> de\<WSDualHttpBinding](wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="5471e-103">Defines the security capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>  
  
<span data-ttu-id="5471e-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5471e-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5471e-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="5471e-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="5471e-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações**](bindings.md) ></span><span class="sxs-lookup"><span data-stu-id="5471e-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="5471e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<wsDualHttpBinding >** ](wsdualhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="5471e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsDualHttpBinding>**](wsdualhttpbinding.md)</span></span>\
<span data-ttu-id="5471e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Binding** ></span><span class="sxs-lookup"><span data-stu-id="5471e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="5471e-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**security >**</span><span class="sxs-lookup"><span data-stu-id="5471e-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5471e-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5471e-110">Syntax</span></span>  
  
```xml  
<security mode="Message/None">
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"
           negotiateServiceCredential="Boolean"/>
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5471e-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5471e-111">Attributes and Elements</span></span>  
 <span data-ttu-id="5471e-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="5471e-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5471e-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="5471e-113">Attributes</span></span>  
  
|<span data-ttu-id="5471e-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="5471e-114">Attribute</span></span>|<span data-ttu-id="5471e-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="5471e-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5471e-116">modo</span><span class="sxs-lookup"><span data-stu-id="5471e-116">mode</span></span>|<span data-ttu-id="5471e-117">Adicional.</span><span class="sxs-lookup"><span data-stu-id="5471e-117">-   Optional.</span></span> <span data-ttu-id="5471e-118">Especifica o tipo de segurança que é aplicado.</span><span class="sxs-lookup"><span data-stu-id="5471e-118">Specifies the type of security that is applied.</span></span> <span data-ttu-id="5471e-119">O valor padrão é `Message`.</span><span class="sxs-lookup"><span data-stu-id="5471e-119">The default value is `Message`.</span></span> <span data-ttu-id="5471e-120">Este atributo é do tipo <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="5471e-120">This attribute is of type <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="5471e-121">Atributo de modo</span><span class="sxs-lookup"><span data-stu-id="5471e-121">Mode Attribute</span></span>  
  
|<span data-ttu-id="5471e-122">Valor</span><span class="sxs-lookup"><span data-stu-id="5471e-122">Value</span></span>|<span data-ttu-id="5471e-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="5471e-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5471e-124">Nenhum</span><span class="sxs-lookup"><span data-stu-id="5471e-124">None</span></span>|<span data-ttu-id="5471e-125">A segurança é desabilitada.</span><span class="sxs-lookup"><span data-stu-id="5471e-125">Security is disabled.</span></span>|  
|<span data-ttu-id="5471e-126">Mensagem</span><span class="sxs-lookup"><span data-stu-id="5471e-126">Message</span></span>|<span data-ttu-id="5471e-127">A segurança é fornecida usando a segurança de mensagem SOAP.</span><span class="sxs-lookup"><span data-stu-id="5471e-127">Security is provided using SOAP message security.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5471e-128">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5471e-128">Child Elements</span></span>  
  
|<span data-ttu-id="5471e-129">Elemento</span><span class="sxs-lookup"><span data-stu-id="5471e-129">Element</span></span>|<span data-ttu-id="5471e-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="5471e-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5471e-131">\<message ></span><span class="sxs-lookup"><span data-stu-id="5471e-131">\<message></span></span>](message-of-wsdualhttpbinding.md)|<span data-ttu-id="5471e-132">Define as configurações para a segurança em nível de mensagem.</span><span class="sxs-lookup"><span data-stu-id="5471e-132">Defines the settings for the message-level security.</span></span> <span data-ttu-id="5471e-133">Este elemento é do tipo <xref:System.ServiceModel.MessageSecurityOverHttp>.</span><span class="sxs-lookup"><span data-stu-id="5471e-133">This element is of type <xref:System.ServiceModel.MessageSecurityOverHttp>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5471e-134">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="5471e-134">Parent Elements</span></span>  
  
|<span data-ttu-id="5471e-135">Elemento</span><span class="sxs-lookup"><span data-stu-id="5471e-135">Element</span></span>|<span data-ttu-id="5471e-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="5471e-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5471e-137">\<binding ></span><span class="sxs-lookup"><span data-stu-id="5471e-137">\<binding></span></span>](bindings.md)|<span data-ttu-id="5471e-138">Define todos os recursos de associação do [\<wsDualHttpBinding >](wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="5471e-138">Defines all binding capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5471e-139">Comentários</span><span class="sxs-lookup"><span data-stu-id="5471e-139">Remarks</span></span>  
 <span data-ttu-id="5471e-140">Uma associação dupla expõe o endereço IP do cliente para o serviço.</span><span class="sxs-lookup"><span data-stu-id="5471e-140">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="5471e-141">O cliente deve usar a segurança para garantir que ele se conecte apenas aos serviços que confia.</span><span class="sxs-lookup"><span data-stu-id="5471e-141">The client should use security to ensure that it only connects to services it trusts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5471e-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5471e-142">See also</span></span>

- <xref:System.ServiceModel.WSDualHttpSecurity>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [<span data-ttu-id="5471e-143">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="5471e-143">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="5471e-144">Associações</span><span class="sxs-lookup"><span data-stu-id="5471e-144">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="5471e-145">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="5471e-145">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="5471e-146">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="5471e-146">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="5471e-147">\<binding ></span><span class="sxs-lookup"><span data-stu-id="5471e-147">\<binding></span></span>](bindings.md)
