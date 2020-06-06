---
title: <security> de <wsDualHttpBinding>
ms.date: 03/30/2017
ms.assetid: 869c05e7-4ebe-467d-95ab-c8f8de4e6b9e
ms.openlocfilehash: 4969c041678bbf3490975bc0ec53507b6cf762bb
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738611"
---
# <a name="security-of-wsdualhttpbinding"></a><span data-ttu-id="17939-102">\<security> de \<wsDualHttpBinding></span><span class="sxs-lookup"><span data-stu-id="17939-102">\<security> of \<wsDualHttpBinding></span></span>
<span data-ttu-id="17939-103">Define os recursos de segurança do [\<wsDualHttpBinding>](wsdualhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="17939-103">Defines the security capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsDualHttpBinding>**](wsdualhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="17939-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="17939-104">Syntax</span></span>  
  
```xml  
<security mode="Message/None">
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"
           negotiateServiceCredential="Boolean"/>
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="17939-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="17939-105">Attributes and Elements</span></span>  
 <span data-ttu-id="17939-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="17939-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="17939-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="17939-107">Attributes</span></span>  
  
|<span data-ttu-id="17939-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="17939-108">Attribute</span></span>|<span data-ttu-id="17939-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="17939-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="17939-110">mode</span><span class="sxs-lookup"><span data-stu-id="17939-110">mode</span></span>|<span data-ttu-id="17939-111">Adicional.</span><span class="sxs-lookup"><span data-stu-id="17939-111">-   Optional.</span></span> <span data-ttu-id="17939-112">Especifica o tipo de segurança que é aplicado.</span><span class="sxs-lookup"><span data-stu-id="17939-112">Specifies the type of security that is applied.</span></span> <span data-ttu-id="17939-113">O valor padrão é `Message`.</span><span class="sxs-lookup"><span data-stu-id="17939-113">The default value is `Message`.</span></span> <span data-ttu-id="17939-114">Esse atributo é do tipo <xref:System.ServiceModel.WSDualHttpSecurityMode> .</span><span class="sxs-lookup"><span data-stu-id="17939-114">This attribute is of type <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="17939-115">Atributo Mode</span><span class="sxs-lookup"><span data-stu-id="17939-115">Mode Attribute</span></span>  
  
|<span data-ttu-id="17939-116">Valor</span><span class="sxs-lookup"><span data-stu-id="17939-116">Value</span></span>|<span data-ttu-id="17939-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="17939-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="17939-118">Nenhum</span><span class="sxs-lookup"><span data-stu-id="17939-118">None</span></span>|<span data-ttu-id="17939-119">A segurança é desabilitada.</span><span class="sxs-lookup"><span data-stu-id="17939-119">Security is disabled.</span></span>|  
|<span data-ttu-id="17939-120">Mensagem</span><span class="sxs-lookup"><span data-stu-id="17939-120">Message</span></span>|<span data-ttu-id="17939-121">A segurança é fornecida usando a segurança de mensagem SOAP.</span><span class="sxs-lookup"><span data-stu-id="17939-121">Security is provided using SOAP message security.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="17939-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="17939-122">Child Elements</span></span>  
  
|<span data-ttu-id="17939-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="17939-123">Element</span></span>|<span data-ttu-id="17939-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="17939-124">Description</span></span>|  
|-------------|-----------------|  
|[\<message>](message-of-wsdualhttpbinding.md)|<span data-ttu-id="17939-125">Define as configurações para a segurança em nível de mensagem.</span><span class="sxs-lookup"><span data-stu-id="17939-125">Defines the settings for the message-level security.</span></span> <span data-ttu-id="17939-126">Esse elemento é do tipo <xref:System.ServiceModel.MessageSecurityOverHttp> .</span><span class="sxs-lookup"><span data-stu-id="17939-126">This element is of type <xref:System.ServiceModel.MessageSecurityOverHttp>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="17939-127">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="17939-127">Parent Elements</span></span>  
  
|<span data-ttu-id="17939-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="17939-128">Element</span></span>|<span data-ttu-id="17939-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="17939-129">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="17939-130">Define todos os recursos de associação do [\<wsDualHttpBinding>](wsdualhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="17939-130">Defines all binding capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="17939-131">Comentários</span><span class="sxs-lookup"><span data-stu-id="17939-131">Remarks</span></span>  
 <span data-ttu-id="17939-132">Uma associação dupla expõe o endereço IP do cliente para o serviço.</span><span class="sxs-lookup"><span data-stu-id="17939-132">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="17939-133">O cliente deve usar a segurança para garantir que ele se conecte apenas aos serviços que confia.</span><span class="sxs-lookup"><span data-stu-id="17939-133">The client should use security to ensure that it only connects to services it trusts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17939-134">Confira também</span><span class="sxs-lookup"><span data-stu-id="17939-134">See also</span></span>

- <xref:System.ServiceModel.WSDualHttpSecurity>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [<span data-ttu-id="17939-135">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="17939-135">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="17939-136">Associações</span><span class="sxs-lookup"><span data-stu-id="17939-136">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="17939-137">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="17939-137">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="17939-138">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="17939-138">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
