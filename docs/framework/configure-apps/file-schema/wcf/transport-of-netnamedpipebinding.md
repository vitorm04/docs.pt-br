---
title: '&lt;transporte&gt; de &lt;netNamedPipeBinding&gt;'
ms.date: 03/30/2017
ms.assetid: d9eff52d-4bde-4586-b56a-b0ec24611f8d
ms.openlocfilehash: c42132f774257589b9020248188ee8d972eb92ba
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48779238"
---
# <a name="lttransportgt-of-ltnetnamedpipebindinggt"></a><span data-ttu-id="5404a-102">&lt;transporte&gt; de &lt;netNamedPipeBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="5404a-102">&lt;transport&gt; of &lt;netNamedPipeBinding&gt;</span></span>
<span data-ttu-id="5404a-103">Define as configurações de segurança de transporte para um pipe nomeado.</span><span class="sxs-lookup"><span data-stu-id="5404a-103">Defines the transport security settings for a named pipe.</span></span>  
  
 <span data-ttu-id="5404a-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="5404a-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="5404a-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="5404a-105">\<bindings></span></span>  
<span data-ttu-id="5404a-106">\<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="5404a-106">\<netNamedPipeBinding></span></span>  
<span data-ttu-id="5404a-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="5404a-107">\<binding></span></span>  
<span data-ttu-id="5404a-108">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="5404a-108">\<security></span></span>  
<span data-ttu-id="5404a-109">\<transporte ></span><span class="sxs-lookup"><span data-stu-id="5404a-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5404a-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5404a-110">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>  
   <binding>  
      <security mode="None/Transport">  
            <transport protectionLevel="None/Sign/EncryptAndSign" />  
      </security>  
   </binding>  
</netNamedPipeBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5404a-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5404a-111">Attributes and Elements</span></span>  
 <span data-ttu-id="5404a-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="5404a-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5404a-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="5404a-113">Attributes</span></span>  
  
|<span data-ttu-id="5404a-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="5404a-114">Attribute</span></span>|<span data-ttu-id="5404a-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="5404a-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5404a-116">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="5404a-116">protectionLevel</span></span>|<span data-ttu-id="5404a-117">Define o nível de proteção de pipe nomeado.</span><span class="sxs-lookup"><span data-stu-id="5404a-117">Defines protection level of the named pipe.</span></span> <span data-ttu-id="5404a-118">Assinar mensagens minimiza o risco de um terceiro violação da mensagem enquanto estão sendo transferidos.</span><span class="sxs-lookup"><span data-stu-id="5404a-118">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="5404a-119">A criptografia fornece privacidade de nível de dados durante o transporte.</span><span class="sxs-lookup"><span data-stu-id="5404a-119">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="5404a-120">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="5404a-120">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="5404a-121">-None: Nenhuma proteção.</span><span class="sxs-lookup"><span data-stu-id="5404a-121">-   None: No protection.</span></span><br /><span data-ttu-id="5404a-122">-Sinal: As mensagens são assinadas.</span><span class="sxs-lookup"><span data-stu-id="5404a-122">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="5404a-123">-EncryptAndSign: As mensagens são criptografadas e assinadas.</span><span class="sxs-lookup"><span data-stu-id="5404a-123">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="5404a-124">O valor padrão é EncryptAndSign.</span><span class="sxs-lookup"><span data-stu-id="5404a-124">The default value is EncryptAndSign.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5404a-125">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5404a-125">Child Elements</span></span>  
 <span data-ttu-id="5404a-126">Nenhum</span><span class="sxs-lookup"><span data-stu-id="5404a-126">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5404a-127">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="5404a-127">Parent Elements</span></span>  
  
|<span data-ttu-id="5404a-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="5404a-128">Element</span></span>|<span data-ttu-id="5404a-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="5404a-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5404a-130">\<security></span><span class="sxs-lookup"><span data-stu-id="5404a-130">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netnamedpipebinding.md)|<span data-ttu-id="5404a-131">Define as configurações de segurança para uma associação.</span><span class="sxs-lookup"><span data-stu-id="5404a-131">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5404a-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5404a-132">See Also</span></span>  
 <xref:System.ServiceModel.NamedPipeTransportSecurity>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.NetNamedPipeSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>  
 [<span data-ttu-id="5404a-133">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="5404a-133">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="5404a-134">Associações</span><span class="sxs-lookup"><span data-stu-id="5404a-134">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="5404a-135">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="5404a-135">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="5404a-136">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="5404a-136">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="5404a-137">\<associação ></span><span class="sxs-lookup"><span data-stu-id="5404a-137">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
