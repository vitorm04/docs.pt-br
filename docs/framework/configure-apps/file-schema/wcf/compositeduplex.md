---
title: <compositeDuplex>
ms.date: 03/30/2017
ms.assetid: 725004d1-ce88-4405-a220-78e89844f81f
ms.openlocfilehash: e79b3e1aeecc52bf41ae759dc15ebf1c8211beb2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926063"
---
# <a name="compositeduplex"></a><span data-ttu-id="38e85-101">\<compositeDuplex></span><span class="sxs-lookup"><span data-stu-id="38e85-101">\<compositeDuplex></span></span>
<span data-ttu-id="38e85-102">Define o elemento de associação que é usado quando o cliente deve expor um ponto de extremidade para que o serviço envie mensagens de volta ao cliente.</span><span class="sxs-lookup"><span data-stu-id="38e85-102">Defines the binding element that is used when the client must expose an endpoint for the service to send messages back to the client.</span></span>  
  
 <span data-ttu-id="38e85-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="38e85-103">\<system.serviceModel></span></span>  
<span data-ttu-id="38e85-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="38e85-104">\<bindings></span></span>  
<span data-ttu-id="38e85-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="38e85-105">\<customBinding></span></span>  
<span data-ttu-id="38e85-106">\<> de associação</span><span class="sxs-lookup"><span data-stu-id="38e85-106">\<binding></span></span>  
<span data-ttu-id="38e85-107">\<compositeDuplex></span><span class="sxs-lookup"><span data-stu-id="38e85-107">\<compositeDuplex></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38e85-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="38e85-108">Syntax</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="URI" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="38e85-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="38e85-109">Attributes and Elements</span></span>  
 <span data-ttu-id="38e85-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="38e85-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="38e85-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="38e85-111">Attributes</span></span>  
  
|<span data-ttu-id="38e85-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="38e85-112">Attribute</span></span>|<span data-ttu-id="38e85-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="38e85-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="38e85-114">clientBaseAddress</span><span class="sxs-lookup"><span data-stu-id="38e85-114">clientBaseAddress</span></span>|<span data-ttu-id="38e85-115">Um URI que define o endereço do canal traseiro no modo duplex.</span><span class="sxs-lookup"><span data-stu-id="38e85-115">A URI that sets the address of the back channel in duplex mode.</span></span> <span data-ttu-id="38e85-116">O serviço usa esse endereço para fazer contato e estabelecer uma conexão com o cliente.</span><span class="sxs-lookup"><span data-stu-id="38e85-116">The service uses this address to make contact and establish a connection with the client.</span></span><br /><br /> <span data-ttu-id="38e85-117">Se esse atributo não estiver definido, um endereço padrão "`full qualified name+default port\TemporaryIndigoAddress\guid`" será gerado.</span><span class="sxs-lookup"><span data-stu-id="38e85-117">If this attribute is not set, a default address "`full qualified name+default port\TemporaryIndigoAddress\guid`" is generated.</span></span> <span data-ttu-id="38e85-118">O padrão é `null`.</span><span class="sxs-lookup"><span data-stu-id="38e85-118">The default is `null`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="38e85-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="38e85-119">Child Elements</span></span>  
 <span data-ttu-id="38e85-120">Nenhum</span><span class="sxs-lookup"><span data-stu-id="38e85-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="38e85-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="38e85-121">Parent Elements</span></span>  
  
|<span data-ttu-id="38e85-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="38e85-122">Element</span></span>|<span data-ttu-id="38e85-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="38e85-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="38e85-124">\<binding></span><span class="sxs-lookup"><span data-stu-id="38e85-124">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="38e85-125">Define todos os recursos de associação da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="38e85-125">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="38e85-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="38e85-126">Remarks</span></span>  
 <span data-ttu-id="38e85-127">Esse elemento de configuração é usado com transportes que não permitem comunicações de duplex nativamente, por exemplo, HTTP.</span><span class="sxs-lookup"><span data-stu-id="38e85-127">This configuration element is used with transports that do not allow duplex communications natively, for example, HTTP.</span></span> <span data-ttu-id="38e85-128">O TCP, por outro lado, permite comunicações duplex nativamente e não requer o uso desse elemento de ligação para que o serviço envie mensagens de volta para um cliente.</span><span class="sxs-lookup"><span data-stu-id="38e85-128">TCP, by contrast, allows duplex communications natively, and does not require the use of this binding element for the service to send messages back to a client.</span></span>  
  
 <span data-ttu-id="38e85-129">O cliente deve expor um endereço para que o serviço faça contato e estabeleça uma conexão.</span><span class="sxs-lookup"><span data-stu-id="38e85-129">The client must expose an address for the service to make contact and establish a connection.</span></span> <span data-ttu-id="38e85-130">Esse endereço de `clientBaseAddress` cliente é fornecido pelo atributo.</span><span class="sxs-lookup"><span data-stu-id="38e85-130">This client address is provided by the `clientBaseAddress` attribute.</span></span> <span data-ttu-id="38e85-131">Observe que Windows Communication Foundation (WCF) gera automaticamente um ClientBaseAddress se um não é definido explicitamente pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="38e85-131">Note that Windows Communication Foundation (WCF) auto-generates a ClientBaseAddress if one is not explicitly set by the user.</span></span>  
  
## <a name="example"></a><span data-ttu-id="38e85-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="38e85-132">Example</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="http://www.contoso.com" />
```  
  
## <a name="see-also"></a><span data-ttu-id="38e85-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="38e85-133">See also</span></span>

- <xref:System.ServiceModel.Configuration.CompositeDuplexElement>
- <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="38e85-134">Associações</span><span class="sxs-lookup"><span data-stu-id="38e85-134">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="38e85-135">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="38e85-135">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="38e85-136">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="38e85-136">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="38e85-137">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="38e85-137">\<customBinding></span></span>](custombinding.md)
