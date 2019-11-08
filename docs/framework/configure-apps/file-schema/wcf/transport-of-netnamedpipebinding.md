---
title: <transport> de <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: d9eff52d-4bde-4586-b56a-b0ec24611f8d
ms.openlocfilehash: d40178e59b89c2912123e1927e9e960f6d880871
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73735965"
---
# <a name="transport-of-netnamedpipebinding"></a><span data-ttu-id="b2861-102">> de transporte de \<de \<netNamedPipeBinding ></span><span class="sxs-lookup"><span data-stu-id="b2861-102">\<transport> of \<netNamedPipeBinding></span></span>
<span data-ttu-id="b2861-103">Define as configurações de segurança de transporte para um pipe nomeado.</span><span class="sxs-lookup"><span data-stu-id="b2861-103">Defines the transport security settings for a named pipe.</span></span>  
  
<span data-ttu-id="b2861-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b2861-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b2861-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="b2861-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="b2861-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações**](bindings.md) ></span><span class="sxs-lookup"><span data-stu-id="b2861-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="b2861-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netNamedPipeBinding >** ](netnamedpipebinding.md)</span><span class="sxs-lookup"><span data-stu-id="b2861-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netNamedPipeBinding>**](netnamedpipebinding.md)</span></span>\
<span data-ttu-id="b2861-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Binding** ></span><span class="sxs-lookup"><span data-stu-id="b2861-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="b2861-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<security >** ](security-of-netnamedpipebinding.md)</span><span class="sxs-lookup"><span data-stu-id="b2861-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-netnamedpipebinding.md)</span></span>\
<span data-ttu-id="b2861-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**transporte >**</span><span class="sxs-lookup"><span data-stu-id="b2861-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2861-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b2861-111">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>
  <binding>
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b2861-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b2861-112">Attributes and Elements</span></span>  
 <span data-ttu-id="b2861-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b2861-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b2861-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="b2861-114">Attributes</span></span>  
  
|<span data-ttu-id="b2861-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="b2861-115">Attribute</span></span>|<span data-ttu-id="b2861-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="b2861-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b2861-117">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="b2861-117">protectionLevel</span></span>|<span data-ttu-id="b2861-118">Define o nível de proteção do pipe nomeado.</span><span class="sxs-lookup"><span data-stu-id="b2861-118">Defines protection level of the named pipe.</span></span> <span data-ttu-id="b2861-119">A assinatura de mensagens reduz o risco de violação de terceiros com a mensagem enquanto ela está sendo transferida.</span><span class="sxs-lookup"><span data-stu-id="b2861-119">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="b2861-120">A criptografia fornece privacidade no nível de dados durante o transporte.</span><span class="sxs-lookup"><span data-stu-id="b2861-120">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="b2861-121">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="b2861-121">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="b2861-122">-Nenhum: sem proteção.</span><span class="sxs-lookup"><span data-stu-id="b2861-122">-   None: No protection.</span></span><br /><span data-ttu-id="b2861-123">-Sign: as mensagens são assinadas.</span><span class="sxs-lookup"><span data-stu-id="b2861-123">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="b2861-124">-EncryptAndSign: as mensagens são criptografadas e assinadas.</span><span class="sxs-lookup"><span data-stu-id="b2861-124">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="b2861-125">O valor padrão é EncryptAndSign.</span><span class="sxs-lookup"><span data-stu-id="b2861-125">The default value is EncryptAndSign.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b2861-126">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b2861-126">Child Elements</span></span>  
 <span data-ttu-id="b2861-127">Nenhum</span><span class="sxs-lookup"><span data-stu-id="b2861-127">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b2861-128">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b2861-128">Parent Elements</span></span>  
  
|<span data-ttu-id="b2861-129">Elemento</span><span class="sxs-lookup"><span data-stu-id="b2861-129">Element</span></span>|<span data-ttu-id="b2861-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="b2861-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b2861-131">\<Security ></span><span class="sxs-lookup"><span data-stu-id="b2861-131">\<security></span></span>](security-of-netnamedpipebinding.md)|<span data-ttu-id="b2861-132">Define as configurações de segurança para uma associação.</span><span class="sxs-lookup"><span data-stu-id="b2861-132">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b2861-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b2861-133">See also</span></span>

- <xref:System.ServiceModel.NamedPipeTransportSecurity>
- <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetNamedPipeSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>
- [<span data-ttu-id="b2861-134">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="b2861-134">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="b2861-135">Associações</span><span class="sxs-lookup"><span data-stu-id="b2861-135">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="b2861-136">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="b2861-136">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="b2861-137">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="b2861-137">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="b2861-138">\<binding ></span><span class="sxs-lookup"><span data-stu-id="b2861-138">\<binding></span></span>](bindings.md)
