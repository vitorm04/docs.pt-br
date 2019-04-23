---
title: <compositeDuplex>
ms.date: 03/30/2017
ms.assetid: 725004d1-ce88-4405-a220-78e89844f81f
ms.openlocfilehash: 1e5ecc2b937aa0cdb159a6cbd1222fe6d4af79fb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59159839"
---
# <a name="compositeduplex"></a><span data-ttu-id="add61-101">\<compositeDuplex></span><span class="sxs-lookup"><span data-stu-id="add61-101">\<compositeDuplex></span></span>
<span data-ttu-id="add61-102">Define o elemento de associação que é usado quando o cliente deve expor um ponto de extremidade para o serviço enviar mensagens de volta ao cliente.</span><span class="sxs-lookup"><span data-stu-id="add61-102">Defines the binding element that is used when the client must expose an endpoint for the service to send messages back to the client.</span></span>  
  
 <span data-ttu-id="add61-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="add61-103">\<system.serviceModel></span></span>  
<span data-ttu-id="add61-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="add61-104">\<bindings></span></span>  
<span data-ttu-id="add61-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="add61-105">\<customBinding></span></span>  
<span data-ttu-id="add61-106">\<binding></span><span class="sxs-lookup"><span data-stu-id="add61-106">\<binding></span></span>  
<span data-ttu-id="add61-107">\<compositeDuplex></span><span class="sxs-lookup"><span data-stu-id="add61-107">\<compositeDuplex></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="add61-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="add61-108">Syntax</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="URI" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="add61-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="add61-109">Attributes and Elements</span></span>  
 <span data-ttu-id="add61-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="add61-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="add61-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="add61-111">Attributes</span></span>  
  
|<span data-ttu-id="add61-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="add61-112">Attribute</span></span>|<span data-ttu-id="add61-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="add61-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="add61-114">clientBaseAddress</span><span class="sxs-lookup"><span data-stu-id="add61-114">clientBaseAddress</span></span>|<span data-ttu-id="add61-115">Um URI que define o endereço do canal de retorno no modo duplex.</span><span class="sxs-lookup"><span data-stu-id="add61-115">A URI that sets the address of the back channel in duplex mode.</span></span> <span data-ttu-id="add61-116">O serviço usa esse endereço para tornar o contato e estabelecer uma conexão com o cliente.</span><span class="sxs-lookup"><span data-stu-id="add61-116">The service uses this address to make contact and establish a connection with the client.</span></span><br /><br /> <span data-ttu-id="add61-117">Se esse atributo não é definido, um endereço padrão "`full qualified name+default port\TemporaryIndigoAddress\guid`" é gerado.</span><span class="sxs-lookup"><span data-stu-id="add61-117">If this attribute is not set, a default address "`full qualified name+default port\TemporaryIndigoAddress\guid`" is generated.</span></span> <span data-ttu-id="add61-118">O padrão é `null`.</span><span class="sxs-lookup"><span data-stu-id="add61-118">The default is `null`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="add61-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="add61-119">Child Elements</span></span>  
 <span data-ttu-id="add61-120">Nenhum</span><span class="sxs-lookup"><span data-stu-id="add61-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="add61-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="add61-121">Parent Elements</span></span>  
  
|<span data-ttu-id="add61-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="add61-122">Element</span></span>|<span data-ttu-id="add61-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="add61-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="add61-124">\<binding></span><span class="sxs-lookup"><span data-stu-id="add61-124">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="add61-125">Define todos os recursos de associação de associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="add61-125">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="add61-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="add61-126">Remarks</span></span>  
 <span data-ttu-id="add61-127">Este elemento de configuração é usado com os transportes que não permitem comunicações duplex nativamente, por exemplo, HTTP.</span><span class="sxs-lookup"><span data-stu-id="add61-127">This configuration element is used with transports that do not allow duplex communications natively, for example, HTTP.</span></span> <span data-ttu-id="add61-128">TCP, por outro lado, permite que as comunicações duplex nativamente e não requer o uso desse elemento de associação para o serviço enviar mensagens para um cliente.</span><span class="sxs-lookup"><span data-stu-id="add61-128">TCP, by contrast, allows duplex communications natively, and does not require the use of this binding element for the service to send messages back to a client.</span></span>  
  
 <span data-ttu-id="add61-129">O cliente deve expor um endereço para o serviço para que entre em contato com e estabelecer uma conexão.</span><span class="sxs-lookup"><span data-stu-id="add61-129">The client must expose an address for the service to make contact and establish a connection.</span></span> <span data-ttu-id="add61-130">Esse endereço de cliente é fornecido pelo `clientBaseAddress` atributo.</span><span class="sxs-lookup"><span data-stu-id="add61-130">This client address is provided by the `clientBaseAddress` attribute.</span></span> <span data-ttu-id="add61-131">Observe que Windows Communication Foundation (WCF) gera automaticamente um ClientBaseAddress se um não é explicitamente definido pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="add61-131">Note that Windows Communication Foundation (WCF) auto-generates a ClientBaseAddress if one is not explicitly set by the user.</span></span>  
  
## <a name="example"></a><span data-ttu-id="add61-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="add61-132">Example</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="http://www.contoso.com" />
```  
  
## <a name="see-also"></a><span data-ttu-id="add61-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="add61-133">See also</span></span>

- <xref:System.ServiceModel.Configuration.CompositeDuplexElement>
- <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="add61-134">Associações</span><span class="sxs-lookup"><span data-stu-id="add61-134">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="add61-135">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="add61-135">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="add61-136">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="add61-136">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="add61-137">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="add61-137">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
