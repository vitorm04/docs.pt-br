---
title: <windowsStreamSecurity>
ms.date: 03/30/2017
ms.assetid: 926bea29-90c7-4a26-9cf0-fb4aa44f6f70
ms.openlocfilehash: dab8505a9ddb348a6f7fe16ae9acb3a0119a8b06
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73735889"
---
# \<windowsStreamSecurity>
<span data-ttu-id="fec80-101">Especifique as configurações de segurança de fluxo do Windows da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="fec80-101">Specify Windows stream security settings of the custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<windowsStreamSecurity>**  
  
## <a name="syntax"></a><span data-ttu-id="fec80-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fec80-102">Syntax</span></span>  
  
```xml  
<windowsStreamSecurity protectionLevel="None/Sign/EncryptAndSign" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fec80-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="fec80-103">Attributes and Elements</span></span>  
 <span data-ttu-id="fec80-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="fec80-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fec80-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="fec80-105">Attributes</span></span>  
  
|<span data-ttu-id="fec80-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="fec80-106">Attribute</span></span>|<span data-ttu-id="fec80-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="fec80-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fec80-108">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="fec80-108">protectionLevel</span></span>|<span data-ttu-id="fec80-109">Define a segurança em nível de mensagem.</span><span class="sxs-lookup"><span data-stu-id="fec80-109">Defines message-level security.</span></span> <span data-ttu-id="fec80-110">A assinatura de mensagens reduz o risco de violação de terceiros com a mensagem enquanto ela está sendo transferida.</span><span class="sxs-lookup"><span data-stu-id="fec80-110">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="fec80-111">A criptografia fornece privacidade no nível de dados durante o transporte.</span><span class="sxs-lookup"><span data-stu-id="fec80-111">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="fec80-112">Os valores válidos incluem os seguintes:</span><span class="sxs-lookup"><span data-stu-id="fec80-112">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="fec80-113">-Nenhum: sem proteção.</span><span class="sxs-lookup"><span data-stu-id="fec80-113">-   None: No protection.</span></span><br /><span data-ttu-id="fec80-114">-Sign: as mensagens são assinadas.</span><span class="sxs-lookup"><span data-stu-id="fec80-114">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="fec80-115">-EncryptAndSign: as mensagens são assinadas e criptografadas.</span><span class="sxs-lookup"><span data-stu-id="fec80-115">-   EncryptAndSign: Messages are signed and encrypted.</span></span><br /><br /> <span data-ttu-id="fec80-116">O padrão é EncryptAndSign.</span><span class="sxs-lookup"><span data-stu-id="fec80-116">The default is EncryptAndSign.</span></span><br /><br /> <span data-ttu-id="fec80-117">Esse atributo é do tipo <xref:System.Net.Security.ProtectionLevel> .</span><span class="sxs-lookup"><span data-stu-id="fec80-117">This attribute is of type <xref:System.Net.Security.ProtectionLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fec80-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="fec80-118">Child Elements</span></span>  
 <span data-ttu-id="fec80-119">Nenhum</span><span class="sxs-lookup"><span data-stu-id="fec80-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fec80-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="fec80-120">Parent Elements</span></span>  
  
|<span data-ttu-id="fec80-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="fec80-121">Element</span></span>|<span data-ttu-id="fec80-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="fec80-122">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="fec80-123">Define todos os recursos de associação da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="fec80-123">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fec80-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="fec80-124">Remarks</span></span>  
 <span data-ttu-id="fec80-125">Os transportes que usam um protocolo orientado a fluxo, como TCP e pipes nomeados, dão suporte a atualizações de transporte baseadas em fluxo.</span><span class="sxs-lookup"><span data-stu-id="fec80-125">Transports that use a stream-oriented protocol such as TCP and named pipes support stream-based transport upgrades.</span></span> <span data-ttu-id="fec80-126">Especificamente, o WCF fornece atualizações de segurança.</span><span class="sxs-lookup"><span data-stu-id="fec80-126">Specifically, WCF provides security upgrades.</span></span> <span data-ttu-id="fec80-127">A configuração dessa segurança de transporte é encapsulada por esse elemento de configuração, bem como pelo [\<sslStreamSecurity>](sslstreamsecurity.md) , que pode ser configurado e adicionado a uma associação personalizada</span><span class="sxs-lookup"><span data-stu-id="fec80-127">The configuration of this transport security is encapsulated by this configuration element  as well as by [\<sslStreamSecurity>](sslstreamsecurity.md), which can be configured and added to a custom binding</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fec80-128">Confira também</span><span class="sxs-lookup"><span data-stu-id="fec80-128">See also</span></span>

- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>
- <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>
- [<span data-ttu-id="fec80-129">Associações</span><span class="sxs-lookup"><span data-stu-id="fec80-129">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="fec80-130">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="fec80-130">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="fec80-131">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="fec80-131">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
