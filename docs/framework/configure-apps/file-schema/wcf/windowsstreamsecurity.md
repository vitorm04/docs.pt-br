---
title: '&lt;windowsStreamSecurity&gt;'
ms.date: 03/30/2017
ms.assetid: 926bea29-90c7-4a26-9cf0-fb4aa44f6f70
ms.openlocfilehash: 4218072f63cabe511ca9d30c77395f734d961eca
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54745175"
---
# <a name="ltwindowsstreamsecuritygt"></a><span data-ttu-id="24277-102">&lt;windowsStreamSecurity&gt;</span><span class="sxs-lookup"><span data-stu-id="24277-102">&lt;windowsStreamSecurity&gt;</span></span>
<span data-ttu-id="24277-103">Especifica configurações de segurança de fluxo do Windows da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="24277-103">Specify Windows stream security settings of the custom binding.</span></span>  
  
 <span data-ttu-id="24277-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="24277-104">\<system.serviceModel></span></span>  
<span data-ttu-id="24277-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="24277-105">\<bindings></span></span>  
<span data-ttu-id="24277-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="24277-106">\<customBinding></span></span>  
<span data-ttu-id="24277-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="24277-107">\<binding></span></span>  
<span data-ttu-id="24277-108">\<windowsStreamSecurity></span><span class="sxs-lookup"><span data-stu-id="24277-108">\<windowsStreamSecurity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24277-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="24277-109">Syntax</span></span>  
  
```xml  
<windowsStreamSecurity protectionLevel="None/Sign/EncryptAndSign" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="24277-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="24277-110">Attributes and Elements</span></span>  
 <span data-ttu-id="24277-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="24277-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="24277-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="24277-112">Attributes</span></span>  
  
|<span data-ttu-id="24277-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="24277-113">Attribute</span></span>|<span data-ttu-id="24277-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="24277-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="24277-115">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="24277-115">protectionLevel</span></span>|<span data-ttu-id="24277-116">Define a segurança em nível de mensagem.</span><span class="sxs-lookup"><span data-stu-id="24277-116">Defines message-level security.</span></span> <span data-ttu-id="24277-117">Assinar mensagens minimiza o risco de um terceiro violação da mensagem enquanto estão sendo transferidos.</span><span class="sxs-lookup"><span data-stu-id="24277-117">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="24277-118">A criptografia fornece privacidade de nível de dados durante o transporte.</span><span class="sxs-lookup"><span data-stu-id="24277-118">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="24277-119">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="24277-119">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="24277-120">-None: Sem proteção.</span><span class="sxs-lookup"><span data-stu-id="24277-120">-   None: No protection.</span></span><br /><span data-ttu-id="24277-121">-Sinal: As mensagens são assinadas.</span><span class="sxs-lookup"><span data-stu-id="24277-121">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="24277-122">-   EncryptAndSign: Mensagens assinadas e criptografadas.</span><span class="sxs-lookup"><span data-stu-id="24277-122">-   EncryptAndSign: Messages are signed and encrypted.</span></span><br /><br /> <span data-ttu-id="24277-123">O padrão é EncryptAndSign.</span><span class="sxs-lookup"><span data-stu-id="24277-123">The default is EncryptAndSign.</span></span><br /><br /> <span data-ttu-id="24277-124">Esse atributo é do tipo <xref:System.Net.Security.ProtectionLevel>.</span><span class="sxs-lookup"><span data-stu-id="24277-124">This attribute is of type <xref:System.Net.Security.ProtectionLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="24277-125">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="24277-125">Child Elements</span></span>  
 <span data-ttu-id="24277-126">Nenhum</span><span class="sxs-lookup"><span data-stu-id="24277-126">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="24277-127">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="24277-127">Parent Elements</span></span>  
  
|<span data-ttu-id="24277-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="24277-128">Element</span></span>|<span data-ttu-id="24277-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="24277-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="24277-130">\<binding></span><span class="sxs-lookup"><span data-stu-id="24277-130">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="24277-131">Define todos os recursos de associação de associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="24277-131">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="24277-132">Comentários</span><span class="sxs-lookup"><span data-stu-id="24277-132">Remarks</span></span>  
 <span data-ttu-id="24277-133">Transportes que usam um protocolo orientado a fluxo como TCP e pipes nomeados oferecem suporte a atualizações com base no fluxo de transporte.</span><span class="sxs-lookup"><span data-stu-id="24277-133">Transports that use a stream-oriented protocol such as TCP and named pipes support stream-based transport upgrades.</span></span> <span data-ttu-id="24277-134">Especificamente, o WCF fornece atualizações de segurança.</span><span class="sxs-lookup"><span data-stu-id="24277-134">Specifically, WCF provides security upgrades.</span></span> <span data-ttu-id="24277-135">A configuração dessa segurança de transporte é encapsulada por este elemento de configuração, bem como por [ \<sslStreamSecurity >](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md), que pode ser configurado e adicionado a uma associação personalizada</span><span class="sxs-lookup"><span data-stu-id="24277-135">The configuration of this transport security is encapsulated by this configuration element  as well as by [\<sslStreamSecurity>](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md), which can be configured and added to a custom binding</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24277-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="24277-136">See also</span></span>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>
- <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>
- [<span data-ttu-id="24277-137">Associações</span><span class="sxs-lookup"><span data-stu-id="24277-137">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="24277-138">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="24277-138">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="24277-139">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="24277-139">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="24277-140">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="24277-140">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
