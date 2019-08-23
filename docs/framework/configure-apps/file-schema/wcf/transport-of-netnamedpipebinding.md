---
title: <transport> de <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: d9eff52d-4bde-4586-b56a-b0ec24611f8d
ms.openlocfilehash: 1e76d0962ea7b4714ef6ca1f9d4c4c3e23df5b6f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934680"
---
# <a name="transport-of-netnamedpipebinding"></a><span data-ttu-id="16bfa-102">\<> de transporte \<do NetNamedPipeBinding ></span><span class="sxs-lookup"><span data-stu-id="16bfa-102">\<transport> of \<netNamedPipeBinding></span></span>
<span data-ttu-id="16bfa-103">Define as configurações de segurança de transporte para um pipe nomeado.</span><span class="sxs-lookup"><span data-stu-id="16bfa-103">Defines the transport security settings for a named pipe.</span></span>  
  
 <span data-ttu-id="16bfa-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="16bfa-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="16bfa-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="16bfa-105">\<bindings></span></span>  
<span data-ttu-id="16bfa-106">\<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="16bfa-106">\<netNamedPipeBinding></span></span>  
<span data-ttu-id="16bfa-107">\<> de associação</span><span class="sxs-lookup"><span data-stu-id="16bfa-107">\<binding></span></span>  
<span data-ttu-id="16bfa-108">\<> de segurança</span><span class="sxs-lookup"><span data-stu-id="16bfa-108">\<security></span></span>  
<span data-ttu-id="16bfa-109">\<> de transporte</span><span class="sxs-lookup"><span data-stu-id="16bfa-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16bfa-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="16bfa-110">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>
  <binding>
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="16bfa-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="16bfa-111">Attributes and Elements</span></span>  
 <span data-ttu-id="16bfa-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="16bfa-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="16bfa-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="16bfa-113">Attributes</span></span>  
  
|<span data-ttu-id="16bfa-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="16bfa-114">Attribute</span></span>|<span data-ttu-id="16bfa-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="16bfa-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="16bfa-116">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="16bfa-116">protectionLevel</span></span>|<span data-ttu-id="16bfa-117">Define o nível de proteção do pipe nomeado.</span><span class="sxs-lookup"><span data-stu-id="16bfa-117">Defines protection level of the named pipe.</span></span> <span data-ttu-id="16bfa-118">A assinatura de mensagens reduz o risco de violação de terceiros com a mensagem enquanto ela está sendo transferida.</span><span class="sxs-lookup"><span data-stu-id="16bfa-118">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="16bfa-119">A criptografia fornece privacidade no nível de dados durante o transporte.</span><span class="sxs-lookup"><span data-stu-id="16bfa-119">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="16bfa-120">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="16bfa-120">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="16bfa-121">None Sem proteção.</span><span class="sxs-lookup"><span data-stu-id="16bfa-121">-   None: No protection.</span></span><br /><span data-ttu-id="16bfa-122">Assine As mensagens são assinadas.</span><span class="sxs-lookup"><span data-stu-id="16bfa-122">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="16bfa-123">EncryptAndSign As mensagens são criptografadas e assinadas.</span><span class="sxs-lookup"><span data-stu-id="16bfa-123">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="16bfa-124">O valor padrão é EncryptAndSign.</span><span class="sxs-lookup"><span data-stu-id="16bfa-124">The default value is EncryptAndSign.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="16bfa-125">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="16bfa-125">Child Elements</span></span>  
 <span data-ttu-id="16bfa-126">Nenhum</span><span class="sxs-lookup"><span data-stu-id="16bfa-126">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="16bfa-127">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="16bfa-127">Parent Elements</span></span>  
  
|<span data-ttu-id="16bfa-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="16bfa-128">Element</span></span>|<span data-ttu-id="16bfa-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="16bfa-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="16bfa-130">\<security></span><span class="sxs-lookup"><span data-stu-id="16bfa-130">\<security></span></span>](security-of-netnamedpipebinding.md)|<span data-ttu-id="16bfa-131">Define as configurações de segurança para uma associação.</span><span class="sxs-lookup"><span data-stu-id="16bfa-131">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="16bfa-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="16bfa-132">See also</span></span>

- <xref:System.ServiceModel.NamedPipeTransportSecurity>
- <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetNamedPipeSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>
- [<span data-ttu-id="16bfa-133">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="16bfa-133">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="16bfa-134">Associações</span><span class="sxs-lookup"><span data-stu-id="16bfa-134">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="16bfa-135">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="16bfa-135">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="16bfa-136">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="16bfa-136">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="16bfa-137">\<binding></span><span class="sxs-lookup"><span data-stu-id="16bfa-137">\<binding></span></span>](../../../misc/binding.md)
