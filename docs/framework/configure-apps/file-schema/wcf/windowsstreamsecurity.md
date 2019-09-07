---
title: <windowsStreamSecurity>
ms.date: 03/30/2017
ms.assetid: 926bea29-90c7-4a26-9cf0-fb4aa44f6f70
ms.openlocfilehash: cddd9f0c1dda982c1795500723c21546bd58c92b
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399091"
---
# <a name="windowsstreamsecurity"></a><span data-ttu-id="4f9a3-101">\<windowsStreamSecurity></span><span class="sxs-lookup"><span data-stu-id="4f9a3-101">\<windowsStreamSecurity></span></span>
<span data-ttu-id="4f9a3-102">Especifique as configurações de segurança de fluxo do Windows da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="4f9a3-102">Specify Windows stream security settings of the custom binding.</span></span>  
  
<span data-ttu-id="4f9a3-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="4f9a3-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="4f9a3-104">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="4f9a3-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="4f9a3-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="4f9a3-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="4f9a3-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de CustomBinding**](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="4f9a3-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="4f9a3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de associação**</span><span class="sxs-lookup"><span data-stu-id="4f9a3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="4f9a3-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> Windowsstreamsecurity está**</span><span class="sxs-lookup"><span data-stu-id="4f9a3-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<windowsStreamSecurity>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f9a3-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4f9a3-109">Syntax</span></span>  
  
```xml  
<windowsStreamSecurity protectionLevel="None/Sign/EncryptAndSign" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4f9a3-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="4f9a3-110">Attributes and Elements</span></span>  
 <span data-ttu-id="4f9a3-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="4f9a3-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4f9a3-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="4f9a3-112">Attributes</span></span>  
  
|<span data-ttu-id="4f9a3-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="4f9a3-113">Attribute</span></span>|<span data-ttu-id="4f9a3-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="4f9a3-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4f9a3-115">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="4f9a3-115">protectionLevel</span></span>|<span data-ttu-id="4f9a3-116">Define a segurança em nível de mensagem.</span><span class="sxs-lookup"><span data-stu-id="4f9a3-116">Defines message-level security.</span></span> <span data-ttu-id="4f9a3-117">A assinatura de mensagens reduz o risco de violação de terceiros com a mensagem enquanto ela está sendo transferida.</span><span class="sxs-lookup"><span data-stu-id="4f9a3-117">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="4f9a3-118">A criptografia fornece privacidade no nível de dados durante o transporte.</span><span class="sxs-lookup"><span data-stu-id="4f9a3-118">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="4f9a3-119">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="4f9a3-119">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="4f9a3-120">None Sem proteção.</span><span class="sxs-lookup"><span data-stu-id="4f9a3-120">-   None: No protection.</span></span><br /><span data-ttu-id="4f9a3-121">Assine As mensagens são assinadas.</span><span class="sxs-lookup"><span data-stu-id="4f9a3-121">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="4f9a3-122">EncryptAndSign As mensagens são assinadas e criptografadas.</span><span class="sxs-lookup"><span data-stu-id="4f9a3-122">-   EncryptAndSign: Messages are signed and encrypted.</span></span><br /><br /> <span data-ttu-id="4f9a3-123">O padrão é EncryptAndSign.</span><span class="sxs-lookup"><span data-stu-id="4f9a3-123">The default is EncryptAndSign.</span></span><br /><br /> <span data-ttu-id="4f9a3-124">Esse atributo é do tipo <xref:System.Net.Security.ProtectionLevel>.</span><span class="sxs-lookup"><span data-stu-id="4f9a3-124">This attribute is of type <xref:System.Net.Security.ProtectionLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4f9a3-125">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="4f9a3-125">Child Elements</span></span>  
 <span data-ttu-id="4f9a3-126">Nenhum</span><span class="sxs-lookup"><span data-stu-id="4f9a3-126">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4f9a3-127">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="4f9a3-127">Parent Elements</span></span>  
  
|<span data-ttu-id="4f9a3-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="4f9a3-128">Element</span></span>|<span data-ttu-id="4f9a3-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="4f9a3-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4f9a3-130">\<binding></span><span class="sxs-lookup"><span data-stu-id="4f9a3-130">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="4f9a3-131">Define todos os recursos de associação da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="4f9a3-131">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4f9a3-132">Comentários</span><span class="sxs-lookup"><span data-stu-id="4f9a3-132">Remarks</span></span>  
 <span data-ttu-id="4f9a3-133">Os transportes que usam um protocolo orientado a fluxo, como TCP e pipes nomeados, dão suporte a atualizações de transporte baseadas em fluxo.</span><span class="sxs-lookup"><span data-stu-id="4f9a3-133">Transports that use a stream-oriented protocol such as TCP and named pipes support stream-based transport upgrades.</span></span> <span data-ttu-id="4f9a3-134">Especificamente, o WCF fornece atualizações de segurança.</span><span class="sxs-lookup"><span data-stu-id="4f9a3-134">Specifically, WCF provides security upgrades.</span></span> <span data-ttu-id="4f9a3-135">A configuração dessa segurança de transporte é encapsulada por esse elemento de configuração, bem como pelo [ \<sslStreamSecurity >](sslstreamsecurity.md), que pode ser configurado e adicionado a uma associação personalizada</span><span class="sxs-lookup"><span data-stu-id="4f9a3-135">The configuration of this transport security is encapsulated by this configuration element  as well as by [\<sslStreamSecurity>](sslstreamsecurity.md), which can be configured and added to a custom binding</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f9a3-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4f9a3-136">See also</span></span>

- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>
- <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>
- [<span data-ttu-id="4f9a3-137">Associações</span><span class="sxs-lookup"><span data-stu-id="4f9a3-137">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="4f9a3-138">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="4f9a3-138">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="4f9a3-139">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="4f9a3-139">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="4f9a3-140">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="4f9a3-140">\<customBinding></span></span>](custombinding.md)
