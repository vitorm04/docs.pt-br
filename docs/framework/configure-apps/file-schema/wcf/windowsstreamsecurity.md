---
title: <windowsStreamSecurity>
ms.date: 03/30/2017
ms.assetid: 926bea29-90c7-4a26-9cf0-fb4aa44f6f70
ms.openlocfilehash: 32e8ed6b70a23462fac3c53d1bc353167ff67560
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59113627"
---
# <a name="windowsstreamsecurity"></a><span data-ttu-id="20dbc-101">\<windowsStreamSecurity></span><span class="sxs-lookup"><span data-stu-id="20dbc-101">\<windowsStreamSecurity></span></span>
<span data-ttu-id="20dbc-102">Especifica configurações de segurança de fluxo do Windows da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="20dbc-102">Specify Windows stream security settings of the custom binding.</span></span>  
  
 <span data-ttu-id="20dbc-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="20dbc-103">\<system.serviceModel></span></span>  
<span data-ttu-id="20dbc-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="20dbc-104">\<bindings></span></span>  
<span data-ttu-id="20dbc-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="20dbc-105">\<customBinding></span></span>  
<span data-ttu-id="20dbc-106">\<binding></span><span class="sxs-lookup"><span data-stu-id="20dbc-106">\<binding></span></span>  
<span data-ttu-id="20dbc-107">\<windowsStreamSecurity></span><span class="sxs-lookup"><span data-stu-id="20dbc-107">\<windowsStreamSecurity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20dbc-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="20dbc-108">Syntax</span></span>  
  
```xml  
<windowsStreamSecurity protectionLevel="None/Sign/EncryptAndSign" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="20dbc-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="20dbc-109">Attributes and Elements</span></span>  
 <span data-ttu-id="20dbc-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="20dbc-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="20dbc-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="20dbc-111">Attributes</span></span>  
  
|<span data-ttu-id="20dbc-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="20dbc-112">Attribute</span></span>|<span data-ttu-id="20dbc-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="20dbc-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="20dbc-114">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="20dbc-114">protectionLevel</span></span>|<span data-ttu-id="20dbc-115">Define a segurança em nível de mensagem.</span><span class="sxs-lookup"><span data-stu-id="20dbc-115">Defines message-level security.</span></span> <span data-ttu-id="20dbc-116">Assinar mensagens minimiza o risco de um terceiro violação da mensagem enquanto estão sendo transferidos.</span><span class="sxs-lookup"><span data-stu-id="20dbc-116">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="20dbc-117">A criptografia fornece privacidade de nível de dados durante o transporte.</span><span class="sxs-lookup"><span data-stu-id="20dbc-117">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="20dbc-118">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="20dbc-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="20dbc-119">-None: Sem proteção.</span><span class="sxs-lookup"><span data-stu-id="20dbc-119">-   None: No protection.</span></span><br /><span data-ttu-id="20dbc-120">-Sinal: As mensagens são assinadas.</span><span class="sxs-lookup"><span data-stu-id="20dbc-120">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="20dbc-121">-   EncryptAndSign: Mensagens assinadas e criptografadas.</span><span class="sxs-lookup"><span data-stu-id="20dbc-121">-   EncryptAndSign: Messages are signed and encrypted.</span></span><br /><br /> <span data-ttu-id="20dbc-122">O padrão é EncryptAndSign.</span><span class="sxs-lookup"><span data-stu-id="20dbc-122">The default is EncryptAndSign.</span></span><br /><br /> <span data-ttu-id="20dbc-123">Esse atributo é do tipo <xref:System.Net.Security.ProtectionLevel>.</span><span class="sxs-lookup"><span data-stu-id="20dbc-123">This attribute is of type <xref:System.Net.Security.ProtectionLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="20dbc-124">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="20dbc-124">Child Elements</span></span>  
 <span data-ttu-id="20dbc-125">Nenhum</span><span class="sxs-lookup"><span data-stu-id="20dbc-125">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="20dbc-126">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="20dbc-126">Parent Elements</span></span>  
  
|<span data-ttu-id="20dbc-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="20dbc-127">Element</span></span>|<span data-ttu-id="20dbc-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="20dbc-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="20dbc-129">\<binding></span><span class="sxs-lookup"><span data-stu-id="20dbc-129">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="20dbc-130">Define todos os recursos de associação de associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="20dbc-130">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="20dbc-131">Comentários</span><span class="sxs-lookup"><span data-stu-id="20dbc-131">Remarks</span></span>  
 <span data-ttu-id="20dbc-132">Transportes que usam um protocolo orientado a fluxo como TCP e pipes nomeados oferecem suporte a atualizações com base no fluxo de transporte.</span><span class="sxs-lookup"><span data-stu-id="20dbc-132">Transports that use a stream-oriented protocol such as TCP and named pipes support stream-based transport upgrades.</span></span> <span data-ttu-id="20dbc-133">Especificamente, o WCF fornece atualizações de segurança.</span><span class="sxs-lookup"><span data-stu-id="20dbc-133">Specifically, WCF provides security upgrades.</span></span> <span data-ttu-id="20dbc-134">A configuração dessa segurança de transporte é encapsulada por este elemento de configuração, bem como por [ \<sslStreamSecurity >](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md), que pode ser configurado e adicionado a uma associação personalizada</span><span class="sxs-lookup"><span data-stu-id="20dbc-134">The configuration of this transport security is encapsulated by this configuration element  as well as by [\<sslStreamSecurity>](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md), which can be configured and added to a custom binding</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20dbc-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="20dbc-135">See also</span></span>

- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>
- <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>
- [<span data-ttu-id="20dbc-136">Associações</span><span class="sxs-lookup"><span data-stu-id="20dbc-136">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="20dbc-137">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="20dbc-137">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="20dbc-138">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="20dbc-138">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="20dbc-139">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="20dbc-139">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
