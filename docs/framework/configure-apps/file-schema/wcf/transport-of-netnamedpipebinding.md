---
title: '&lt;transporte&gt; de &lt;netNamedPipeBinding&gt;'
ms.date: 03/30/2017
ms.assetid: d9eff52d-4bde-4586-b56a-b0ec24611f8d
ms.openlocfilehash: 1624b93344e50b0406d314e285ce94786ba6dadc
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54148975"
---
# <a name="lttransportgt-of-ltnetnamedpipebindinggt"></a><span data-ttu-id="59ead-102">&lt;transporte&gt; de &lt;netNamedPipeBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="59ead-102">&lt;transport&gt; of &lt;netNamedPipeBinding&gt;</span></span>
<span data-ttu-id="59ead-103">Define as configurações de segurança de transporte para um pipe nomeado.</span><span class="sxs-lookup"><span data-stu-id="59ead-103">Defines the transport security settings for a named pipe.</span></span>  
  
 <span data-ttu-id="59ead-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="59ead-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="59ead-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="59ead-105">\<bindings></span></span>  
<span data-ttu-id="59ead-106">\<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="59ead-106">\<netNamedPipeBinding></span></span>  
<span data-ttu-id="59ead-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="59ead-107">\<binding></span></span>  
<span data-ttu-id="59ead-108">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="59ead-108">\<security></span></span>  
<span data-ttu-id="59ead-109">\<transporte ></span><span class="sxs-lookup"><span data-stu-id="59ead-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59ead-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="59ead-110">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>
  <binding>
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="59ead-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="59ead-111">Attributes and Elements</span></span>  
 <span data-ttu-id="59ead-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="59ead-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="59ead-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="59ead-113">Attributes</span></span>  
  
|<span data-ttu-id="59ead-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="59ead-114">Attribute</span></span>|<span data-ttu-id="59ead-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="59ead-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="59ead-116">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="59ead-116">protectionLevel</span></span>|<span data-ttu-id="59ead-117">Define o nível de proteção de pipe nomeado.</span><span class="sxs-lookup"><span data-stu-id="59ead-117">Defines protection level of the named pipe.</span></span> <span data-ttu-id="59ead-118">Assinar mensagens minimiza o risco de um terceiro violação da mensagem enquanto estão sendo transferidos.</span><span class="sxs-lookup"><span data-stu-id="59ead-118">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="59ead-119">A criptografia fornece privacidade de nível de dados durante o transporte.</span><span class="sxs-lookup"><span data-stu-id="59ead-119">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="59ead-120">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="59ead-120">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="59ead-121">-None: Sem proteção.</span><span class="sxs-lookup"><span data-stu-id="59ead-121">-   None: No protection.</span></span><br /><span data-ttu-id="59ead-122">-Sinal: As mensagens são assinadas.</span><span class="sxs-lookup"><span data-stu-id="59ead-122">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="59ead-123">-EncryptAndSign: As mensagens são criptografadas e assinadas.</span><span class="sxs-lookup"><span data-stu-id="59ead-123">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="59ead-124">O valor padrão é EncryptAndSign.</span><span class="sxs-lookup"><span data-stu-id="59ead-124">The default value is EncryptAndSign.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="59ead-125">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="59ead-125">Child Elements</span></span>  
 <span data-ttu-id="59ead-126">Nenhum</span><span class="sxs-lookup"><span data-stu-id="59ead-126">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="59ead-127">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="59ead-127">Parent Elements</span></span>  
  
|<span data-ttu-id="59ead-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="59ead-128">Element</span></span>|<span data-ttu-id="59ead-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="59ead-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="59ead-130">\<security></span><span class="sxs-lookup"><span data-stu-id="59ead-130">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netnamedpipebinding.md)|<span data-ttu-id="59ead-131">Define as configurações de segurança para uma associação.</span><span class="sxs-lookup"><span data-stu-id="59ead-131">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="59ead-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="59ead-132">See Also</span></span>  
 <xref:System.ServiceModel.NamedPipeTransportSecurity>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.NetNamedPipeSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>  
 [<span data-ttu-id="59ead-133">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="59ead-133">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="59ead-134">Associações</span><span class="sxs-lookup"><span data-stu-id="59ead-134">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="59ead-135">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="59ead-135">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="59ead-136">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="59ead-136">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="59ead-137">\<associação ></span><span class="sxs-lookup"><span data-stu-id="59ead-137">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
