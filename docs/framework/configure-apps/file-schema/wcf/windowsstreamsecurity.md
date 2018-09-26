---
title: '&lt;windowsStreamSecurity&gt;'
ms.date: 03/30/2017
ms.assetid: 926bea29-90c7-4a26-9cf0-fb4aa44f6f70
author: BrucePerlerMS
ms.openlocfilehash: 6c1253e6f402da6b818a4438142e122f8b31809c
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47193155"
---
# <a name="ltwindowsstreamsecuritygt"></a><span data-ttu-id="3c97e-102">&lt;windowsStreamSecurity&gt;</span><span class="sxs-lookup"><span data-stu-id="3c97e-102">&lt;windowsStreamSecurity&gt;</span></span>
<span data-ttu-id="3c97e-103">Especifica configurações de segurança de fluxo do Windows da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="3c97e-103">Specify Windows stream security settings of the custom binding.</span></span>  
  
 <span data-ttu-id="3c97e-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="3c97e-104">\<system.serviceModel></span></span>  
<span data-ttu-id="3c97e-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="3c97e-105">\<bindings></span></span>  
<span data-ttu-id="3c97e-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="3c97e-106">\<customBinding></span></span>  
<span data-ttu-id="3c97e-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="3c97e-107">\<binding></span></span>  
<span data-ttu-id="3c97e-108">\<windowsStreamSecurity ></span><span class="sxs-lookup"><span data-stu-id="3c97e-108">\<windowsStreamSecurity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c97e-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3c97e-109">Syntax</span></span>  
  
```xml  
<windowsStreamSecurity protectionLevel="None/Sign/EncryptAndSign"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3c97e-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="3c97e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="3c97e-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="3c97e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3c97e-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="3c97e-112">Attributes</span></span>  
  
|<span data-ttu-id="3c97e-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="3c97e-113">Attribute</span></span>|<span data-ttu-id="3c97e-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="3c97e-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3c97e-115">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="3c97e-115">protectionLevel</span></span>|<span data-ttu-id="3c97e-116">Define a segurança em nível de mensagem.</span><span class="sxs-lookup"><span data-stu-id="3c97e-116">Defines message-level security.</span></span> <span data-ttu-id="3c97e-117">Assinar mensagens minimiza o risco de um terceiro violação da mensagem enquanto estão sendo transferidos.</span><span class="sxs-lookup"><span data-stu-id="3c97e-117">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="3c97e-118">A criptografia fornece privacidade de nível de dados durante o transporte.</span><span class="sxs-lookup"><span data-stu-id="3c97e-118">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="3c97e-119">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="3c97e-119">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="3c97e-120">-None: Nenhuma proteção.</span><span class="sxs-lookup"><span data-stu-id="3c97e-120">-   None: No protection.</span></span><br /><span data-ttu-id="3c97e-121">-Sinal: As mensagens são assinadas.</span><span class="sxs-lookup"><span data-stu-id="3c97e-121">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="3c97e-122">-EncryptAndSign: Mensagens assinadas e criptografadas.</span><span class="sxs-lookup"><span data-stu-id="3c97e-122">-   EncryptAndSign: Messages are signed and encrypted.</span></span><br /><br /> <span data-ttu-id="3c97e-123">O padrão é EncryptAndSign.</span><span class="sxs-lookup"><span data-stu-id="3c97e-123">The default is EncryptAndSign.</span></span><br /><br /> <span data-ttu-id="3c97e-124">Esse atributo é do tipo <xref:System.Net.Security.ProtectionLevel>.</span><span class="sxs-lookup"><span data-stu-id="3c97e-124">This attribute is of type <xref:System.Net.Security.ProtectionLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3c97e-125">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="3c97e-125">Child Elements</span></span>  
 <span data-ttu-id="3c97e-126">Nenhum</span><span class="sxs-lookup"><span data-stu-id="3c97e-126">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3c97e-127">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="3c97e-127">Parent Elements</span></span>  
  
|<span data-ttu-id="3c97e-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="3c97e-128">Element</span></span>|<span data-ttu-id="3c97e-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="3c97e-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3c97e-130">\<associação ></span><span class="sxs-lookup"><span data-stu-id="3c97e-130">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="3c97e-131">Define todos os recursos de associação de associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="3c97e-131">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3c97e-132">Comentários</span><span class="sxs-lookup"><span data-stu-id="3c97e-132">Remarks</span></span>  
 <span data-ttu-id="3c97e-133">Transportes que usam um protocolo orientado a fluxo como TCP e pipes nomeados oferecem suporte a atualizações com base no fluxo de transporte.</span><span class="sxs-lookup"><span data-stu-id="3c97e-133">Transports that use a stream-oriented protocol such as TCP and named pipes support stream-based transport upgrades.</span></span> <span data-ttu-id="3c97e-134">Especificamente, o WCF fornece atualizações de segurança.</span><span class="sxs-lookup"><span data-stu-id="3c97e-134">Specifically, WCF provides security upgrades.</span></span> <span data-ttu-id="3c97e-135">A configuração dessa segurança de transporte é encapsulada por este elemento de configuração, bem como por [ \<sslStreamSecurity >](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md), que pode ser configurado e adicionado a uma associação personalizada</span><span class="sxs-lookup"><span data-stu-id="3c97e-135">The configuration of this transport security is encapsulated by this configuration element  as well as by [\<sslStreamSecurity>](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md), which can be configured and added to a custom binding</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c97e-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3c97e-136">See Also</span></span>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>  
 <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
 [<span data-ttu-id="3c97e-137">Associações</span><span class="sxs-lookup"><span data-stu-id="3c97e-137">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="3c97e-138">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="3c97e-138">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="3c97e-139">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="3c97e-139">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="3c97e-140">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="3c97e-140">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
