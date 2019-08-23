---
title: <windowsStreamSecurity>
ms.date: 03/30/2017
ms.assetid: 926bea29-90c7-4a26-9cf0-fb4aa44f6f70
ms.openlocfilehash: 0f1dfd523e593c82727354db7ce39ffc992bdfb4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932799"
---
# <a name="windowsstreamsecurity"></a><span data-ttu-id="77299-101">\<windowsStreamSecurity></span><span class="sxs-lookup"><span data-stu-id="77299-101">\<windowsStreamSecurity></span></span>
<span data-ttu-id="77299-102">Especifique as configurações de segurança de fluxo do Windows da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="77299-102">Specify Windows stream security settings of the custom binding.</span></span>  
  
 <span data-ttu-id="77299-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="77299-103">\<system.serviceModel></span></span>  
<span data-ttu-id="77299-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="77299-104">\<bindings></span></span>  
<span data-ttu-id="77299-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="77299-105">\<customBinding></span></span>  
<span data-ttu-id="77299-106">\<> de associação</span><span class="sxs-lookup"><span data-stu-id="77299-106">\<binding></span></span>  
<span data-ttu-id="77299-107">\<windowsStreamSecurity></span><span class="sxs-lookup"><span data-stu-id="77299-107">\<windowsStreamSecurity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77299-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="77299-108">Syntax</span></span>  
  
```xml  
<windowsStreamSecurity protectionLevel="None/Sign/EncryptAndSign" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="77299-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="77299-109">Attributes and Elements</span></span>  
 <span data-ttu-id="77299-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="77299-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="77299-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="77299-111">Attributes</span></span>  
  
|<span data-ttu-id="77299-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="77299-112">Attribute</span></span>|<span data-ttu-id="77299-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="77299-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="77299-114">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="77299-114">protectionLevel</span></span>|<span data-ttu-id="77299-115">Define a segurança em nível de mensagem.</span><span class="sxs-lookup"><span data-stu-id="77299-115">Defines message-level security.</span></span> <span data-ttu-id="77299-116">A assinatura de mensagens reduz o risco de violação de terceiros com a mensagem enquanto ela está sendo transferida.</span><span class="sxs-lookup"><span data-stu-id="77299-116">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="77299-117">A criptografia fornece privacidade no nível de dados durante o transporte.</span><span class="sxs-lookup"><span data-stu-id="77299-117">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="77299-118">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="77299-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="77299-119">None Sem proteção.</span><span class="sxs-lookup"><span data-stu-id="77299-119">-   None: No protection.</span></span><br /><span data-ttu-id="77299-120">Assine As mensagens são assinadas.</span><span class="sxs-lookup"><span data-stu-id="77299-120">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="77299-121">EncryptAndSign As mensagens são assinadas e criptografadas.</span><span class="sxs-lookup"><span data-stu-id="77299-121">-   EncryptAndSign: Messages are signed and encrypted.</span></span><br /><br /> <span data-ttu-id="77299-122">O padrão é EncryptAndSign.</span><span class="sxs-lookup"><span data-stu-id="77299-122">The default is EncryptAndSign.</span></span><br /><br /> <span data-ttu-id="77299-123">Esse atributo é do tipo <xref:System.Net.Security.ProtectionLevel>.</span><span class="sxs-lookup"><span data-stu-id="77299-123">This attribute is of type <xref:System.Net.Security.ProtectionLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="77299-124">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="77299-124">Child Elements</span></span>  
 <span data-ttu-id="77299-125">Nenhum</span><span class="sxs-lookup"><span data-stu-id="77299-125">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="77299-126">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="77299-126">Parent Elements</span></span>  
  
|<span data-ttu-id="77299-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="77299-127">Element</span></span>|<span data-ttu-id="77299-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="77299-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="77299-129">\<binding></span><span class="sxs-lookup"><span data-stu-id="77299-129">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="77299-130">Define todos os recursos de associação da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="77299-130">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="77299-131">Comentários</span><span class="sxs-lookup"><span data-stu-id="77299-131">Remarks</span></span>  
 <span data-ttu-id="77299-132">Os transportes que usam um protocolo orientado a fluxo, como TCP e pipes nomeados, dão suporte a atualizações de transporte baseadas em fluxo.</span><span class="sxs-lookup"><span data-stu-id="77299-132">Transports that use a stream-oriented protocol such as TCP and named pipes support stream-based transport upgrades.</span></span> <span data-ttu-id="77299-133">Especificamente, o WCF fornece atualizações de segurança.</span><span class="sxs-lookup"><span data-stu-id="77299-133">Specifically, WCF provides security upgrades.</span></span> <span data-ttu-id="77299-134">A configuração dessa segurança de transporte é encapsulada por esse elemento de configuração, bem como pelo [ \<sslStreamSecurity >](sslstreamsecurity.md), que pode ser configurado e adicionado a uma associação personalizada</span><span class="sxs-lookup"><span data-stu-id="77299-134">The configuration of this transport security is encapsulated by this configuration element  as well as by [\<sslStreamSecurity>](sslstreamsecurity.md), which can be configured and added to a custom binding</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77299-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="77299-135">See also</span></span>

- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>
- <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>
- [<span data-ttu-id="77299-136">Associações</span><span class="sxs-lookup"><span data-stu-id="77299-136">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="77299-137">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="77299-137">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="77299-138">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="77299-138">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="77299-139">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="77299-139">\<customBinding></span></span>](custombinding.md)
