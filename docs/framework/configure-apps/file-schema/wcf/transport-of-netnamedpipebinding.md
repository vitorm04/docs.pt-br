---
title: '&lt;transporte&gt; de &lt;netNamedPipeBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d9eff52d-4bde-4586-b56a-b0ec24611f8d
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 00f4ddfd218e8797aa2089a21081ee711be316d2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="lttransportgt-of-ltnetnamedpipebindinggt"></a><span data-ttu-id="fc8c6-102">&lt;transporte&gt; de &lt;netNamedPipeBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="fc8c6-102">&lt;transport&gt; of &lt;netNamedPipeBinding&gt;</span></span>
<span data-ttu-id="fc8c6-103">Define as configurações de segurança de transporte para um pipe nomeado.</span><span class="sxs-lookup"><span data-stu-id="fc8c6-103">Defines the transport security settings for a named pipe.</span></span>  
  
 <span data-ttu-id="fc8c6-104">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="fc8c6-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="fc8c6-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="fc8c6-105">\<bindings></span></span>  
<span data-ttu-id="fc8c6-106">\<netNamedPipeBinding ></span><span class="sxs-lookup"><span data-stu-id="fc8c6-106">\<netNamedPipeBinding></span></span>  
<span data-ttu-id="fc8c6-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="fc8c6-107">\<binding></span></span>  
<span data-ttu-id="fc8c6-108">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="fc8c6-108">\<security></span></span>  
<span data-ttu-id="fc8c6-109">\<transporte ></span><span class="sxs-lookup"><span data-stu-id="fc8c6-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc8c6-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fc8c6-110">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>  
   <binding>  
      <security mode="None/Transport">  
            <transport protectionLevel="None/Sign/EncryptAndSign" />  
      </security>  
   </binding>  
</netNamedPipeBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fc8c6-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="fc8c6-111">Attributes and Elements</span></span>  
 <span data-ttu-id="fc8c6-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="fc8c6-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fc8c6-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="fc8c6-113">Attributes</span></span>  
  
|<span data-ttu-id="fc8c6-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="fc8c6-114">Attribute</span></span>|<span data-ttu-id="fc8c6-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="fc8c6-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fc8c6-116">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="fc8c6-116">protectionLevel</span></span>|<span data-ttu-id="fc8c6-117">Define o nível de proteção de pipe nomeado.</span><span class="sxs-lookup"><span data-stu-id="fc8c6-117">Defines protection level of the named pipe.</span></span> <span data-ttu-id="fc8c6-118">Assinatura de mensagens reduz o risco de um terceiro que viole a mensagem enquanto eles estão sendo transferidos.</span><span class="sxs-lookup"><span data-stu-id="fc8c6-118">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="fc8c6-119">A criptografia fornece privacidade de nível de dados durante o transporte.</span><span class="sxs-lookup"><span data-stu-id="fc8c6-119">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="fc8c6-120">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="fc8c6-120">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="fc8c6-121">-Nenhum: Sem proteção.</span><span class="sxs-lookup"><span data-stu-id="fc8c6-121">-   None: No protection.</span></span><br /><span data-ttu-id="fc8c6-122">-Sign: Mensagens são assinadas.</span><span class="sxs-lookup"><span data-stu-id="fc8c6-122">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="fc8c6-123">-EncryptAndSign: Mensagens são criptografadas e assinadas.</span><span class="sxs-lookup"><span data-stu-id="fc8c6-123">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="fc8c6-124">O valor padrão é EncryptAndSign.</span><span class="sxs-lookup"><span data-stu-id="fc8c6-124">The default value is EncryptAndSign.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fc8c6-125">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="fc8c6-125">Child Elements</span></span>  
 <span data-ttu-id="fc8c6-126">Nenhum</span><span class="sxs-lookup"><span data-stu-id="fc8c6-126">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fc8c6-127">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="fc8c6-127">Parent Elements</span></span>  
  
|<span data-ttu-id="fc8c6-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="fc8c6-128">Element</span></span>|<span data-ttu-id="fc8c6-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="fc8c6-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fc8c6-130">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="fc8c6-130">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netnamedpipebinding.md)|<span data-ttu-id="fc8c6-131">Define as configurações de segurança para uma associação.</span><span class="sxs-lookup"><span data-stu-id="fc8c6-131">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fc8c6-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fc8c6-132">See Also</span></span>  
 <xref:System.ServiceModel.NamedPipeTransportSecurity>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.NetNamedPipeSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>  
 [<span data-ttu-id="fc8c6-133">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="fc8c6-133">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 <span data-ttu-id="fc8c6-134">[Bindings](../../../../../docs/framework/wcf/bindings.md) (Associações)</span><span class="sxs-lookup"><span data-stu-id="fc8c6-134">[Bindings](../../../../../docs/framework/wcf/bindings.md)</span></span>  
 [<span data-ttu-id="fc8c6-135">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="fc8c6-135">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="fc8c6-136">Usando associações para configurar clientes e serviços do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="fc8c6-136">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="fc8c6-137">\<associação ></span><span class="sxs-lookup"><span data-stu-id="fc8c6-137">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
