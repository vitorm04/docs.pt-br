---
title: <security> de <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: bb3cb022-637e-49fd-92e8-6766038affa7
ms.openlocfilehash: 31ea31ce6880a770c966350cd931e487396c4d63
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73736439"
---
# <a name="security-of-netnamedpipebinding"></a><span data-ttu-id="8b762-102">\<security> de \<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="8b762-102">\<security> of \<netNamedPipeBinding></span></span>
<span data-ttu-id="8b762-103">Define as configurações de segurança para uma associação.</span><span class="sxs-lookup"><span data-stu-id="8b762-103">Defines the security settings for a binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netNamedPipeBinding>**](netnamedpipebinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="8b762-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8b762-104">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>
  <binding>
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8b762-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="8b762-105">Attributes and Elements</span></span>  
 <span data-ttu-id="8b762-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="8b762-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8b762-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="8b762-107">Attributes</span></span>  
  
|<span data-ttu-id="8b762-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="8b762-108">Attribute</span></span>|<span data-ttu-id="8b762-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="8b762-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8b762-110">mode</span><span class="sxs-lookup"><span data-stu-id="8b762-110">mode</span></span>|<span data-ttu-id="8b762-111">Especifica o tipo de segurança que é aplicado a essa associação.</span><span class="sxs-lookup"><span data-stu-id="8b762-111">Specifies the type of security that is applied to this binding.</span></span> <span data-ttu-id="8b762-112">Os valores válidos incluem os seguintes:</span><span class="sxs-lookup"><span data-stu-id="8b762-112">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="8b762-113">-Nenhum: isso desabilita a segurança.</span><span class="sxs-lookup"><span data-stu-id="8b762-113">-   None: This disables security.</span></span><br /><span data-ttu-id="8b762-114">-Transport: a segurança é fornecida usando a segurança baseada em transporte subjacente.</span><span class="sxs-lookup"><span data-stu-id="8b762-114">-   Transport: Security is provided using underlying transport based security.</span></span> <span data-ttu-id="8b762-115">É possível controlar o nível de proteção com esse modo.</span><span class="sxs-lookup"><span data-stu-id="8b762-115">It is possible to control the protection level with this mode.</span></span><br /><span data-ttu-id="8b762-116">-O valor padrão é transporte.</span><span class="sxs-lookup"><span data-stu-id="8b762-116">-   The default value is Transport.</span></span> <span data-ttu-id="8b762-117">Esse atributo é do tipo <xref:System.ServiceModel.NetNamedPipeSecurityMode> .</span><span class="sxs-lookup"><span data-stu-id="8b762-117">This attribute is of type <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8b762-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="8b762-118">Child Elements</span></span>  
  
|<span data-ttu-id="8b762-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="8b762-119">Element</span></span>|<span data-ttu-id="8b762-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="8b762-120">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8b762-121">transporte</span><span class="sxs-lookup"><span data-stu-id="8b762-121">transport</span></span>|<span data-ttu-id="8b762-122">Define as configurações de segurança para o transporte.</span><span class="sxs-lookup"><span data-stu-id="8b762-122">Defines the security settings for the transport.</span></span> <span data-ttu-id="8b762-123">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="8b762-123">This element is of type <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8b762-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="8b762-124">Parent Elements</span></span>  
  
|<span data-ttu-id="8b762-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="8b762-125">Element</span></span>|<span data-ttu-id="8b762-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="8b762-126">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8b762-127">associação</span><span class="sxs-lookup"><span data-stu-id="8b762-127">binding</span></span>|<span data-ttu-id="8b762-128">O elemento Binding do [\<netNamedPipeBinding>](netnamedpipebinding.md) .</span><span class="sxs-lookup"><span data-stu-id="8b762-128">The binding element of the [\<netNamedPipeBinding>](netnamedpipebinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8b762-129">Confira também</span><span class="sxs-lookup"><span data-stu-id="8b762-129">See also</span></span>

- <xref:System.ServiceModel.NetNamedPipeSecurity>
- <xref:System.ServiceModel.NetNamedPipeBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement>
- [<span data-ttu-id="8b762-130">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="8b762-130">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="8b762-131">Selecionando um tipo de credencial</span><span class="sxs-lookup"><span data-stu-id="8b762-131">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="8b762-132">Associações</span><span class="sxs-lookup"><span data-stu-id="8b762-132">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="8b762-133">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="8b762-133">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="8b762-134">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="8b762-134">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
