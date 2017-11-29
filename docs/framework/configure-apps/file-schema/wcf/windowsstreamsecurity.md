---
title: "&lt;windowsstreamsecurity está&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 926bea29-90c7-4a26-9cf0-fb4aa44f6f70
caps.latest.revision: "10"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 5a0d3b61f473b49abdb2470a9fa5381dc9929274
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltwindowsstreamsecuritygt"></a><span data-ttu-id="1b46a-102">&lt;windowsstreamsecurity está&gt;</span><span class="sxs-lookup"><span data-stu-id="1b46a-102">&lt;windowsStreamSecurity&gt;</span></span>
<span data-ttu-id="1b46a-103">Especifica configurações de segurança de fluxo do Windows da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="1b46a-103">Specify Windows stream security settings of the custom binding.</span></span>  
  
 <span data-ttu-id="1b46a-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="1b46a-104">\<system.serviceModel></span></span>  
<span data-ttu-id="1b46a-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="1b46a-105">\<bindings></span></span>  
<span data-ttu-id="1b46a-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="1b46a-106">\<customBinding></span></span>  
<span data-ttu-id="1b46a-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="1b46a-107">\<binding></span></span>  
<span data-ttu-id="1b46a-108">\<windowsstreamsecurity está ></span><span class="sxs-lookup"><span data-stu-id="1b46a-108">\<windowsStreamSecurity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b46a-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1b46a-109">Syntax</span></span>  
  
```xml  
<windowsStreamSecurity protectionLevel="None/Sign/EncryptAndSign"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1b46a-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="1b46a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="1b46a-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="1b46a-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1b46a-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="1b46a-112">Attributes</span></span>  
  
|<span data-ttu-id="1b46a-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="1b46a-113">Attribute</span></span>|<span data-ttu-id="1b46a-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="1b46a-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1b46a-115">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="1b46a-115">protectionLevel</span></span>|<span data-ttu-id="1b46a-116">Define a segurança em nível de mensagem.</span><span class="sxs-lookup"><span data-stu-id="1b46a-116">Defines message-level security.</span></span> <span data-ttu-id="1b46a-117">Assinatura de mensagens reduz o risco de um terceiro que viole a mensagem enquanto eles estão sendo transferidos.</span><span class="sxs-lookup"><span data-stu-id="1b46a-117">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="1b46a-118">A criptografia fornece privacidade de nível de dados durante o transporte.</span><span class="sxs-lookup"><span data-stu-id="1b46a-118">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="1b46a-119">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="1b46a-119">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="1b46a-120">-Nenhum: Sem proteção.</span><span class="sxs-lookup"><span data-stu-id="1b46a-120">-   None: No protection.</span></span><br /><span data-ttu-id="1b46a-121">-Sign: Mensagens são assinadas.</span><span class="sxs-lookup"><span data-stu-id="1b46a-121">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="1b46a-122">-EncryptAndSign: Mensagens são assinadas e criptografadas.</span><span class="sxs-lookup"><span data-stu-id="1b46a-122">-   EncryptAndSign: Messages are signed and encrypted.</span></span><br /><br /> <span data-ttu-id="1b46a-123">O padrão é EncryptAndSign.</span><span class="sxs-lookup"><span data-stu-id="1b46a-123">The default is EncryptAndSign.</span></span><br /><br /> <span data-ttu-id="1b46a-124">Esse atributo é do tipo <xref:System.Net.Security.ProtectionLevel>.</span><span class="sxs-lookup"><span data-stu-id="1b46a-124">This attribute is of type <xref:System.Net.Security.ProtectionLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1b46a-125">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="1b46a-125">Child Elements</span></span>  
 <span data-ttu-id="1b46a-126">Nenhum</span><span class="sxs-lookup"><span data-stu-id="1b46a-126">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1b46a-127">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="1b46a-127">Parent Elements</span></span>  
  
|<span data-ttu-id="1b46a-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="1b46a-128">Element</span></span>|<span data-ttu-id="1b46a-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="1b46a-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1b46a-130">\<associação ></span><span class="sxs-lookup"><span data-stu-id="1b46a-130">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="1b46a-131">Define todos os recursos de associação da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="1b46a-131">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1b46a-132">Comentários</span><span class="sxs-lookup"><span data-stu-id="1b46a-132">Remarks</span></span>  
 <span data-ttu-id="1b46a-133">Transportes que usam um protocolo orientado por fluxo como TCP e pipes nomeados oferecem suporte a atualizações com base em fluxo de transporte.</span><span class="sxs-lookup"><span data-stu-id="1b46a-133">Transports that use a stream-oriented protocol such as TCP and named pipes support stream-based transport upgrades.</span></span> <span data-ttu-id="1b46a-134">Especificamente, o WCF fornece atualizações de segurança.</span><span class="sxs-lookup"><span data-stu-id="1b46a-134">Specifically, WCF provides security upgrades.</span></span> <span data-ttu-id="1b46a-135">A configuração de segurança de transporte é encapsulada por este elemento de configuração, bem como por [ \<sslStreamSecurity >](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md), que pode ser configurado e adicionado a uma associação personalizada</span><span class="sxs-lookup"><span data-stu-id="1b46a-135">The configuration of this transport security is encapsulated by this configuration element  as well as by [\<sslStreamSecurity>](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md), which can be configured and added to a custom binding</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b46a-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1b46a-136">See Also</span></span>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>  
 <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
 <span data-ttu-id="1b46a-137">[Bindings](../../../../../docs/framework/wcf/bindings.md) (Associações)</span><span class="sxs-lookup"><span data-stu-id="1b46a-137">[Bindings](../../../../../docs/framework/wcf/bindings.md)</span></span>  
 [<span data-ttu-id="1b46a-138">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="1b46a-138">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="1b46a-139">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="1b46a-139">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="1b46a-140">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="1b46a-140">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
