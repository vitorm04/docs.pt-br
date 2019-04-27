---
title: <compositeDuplex>
ms.date: 03/30/2017
ms.assetid: 725004d1-ce88-4405-a220-78e89844f81f
ms.openlocfilehash: 1e5ecc2b937aa0cdb159a6cbd1222fe6d4af79fb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704167"
---
# <a name="compositeduplex"></a><span data-ttu-id="74631-101">\<compositeDuplex></span><span class="sxs-lookup"><span data-stu-id="74631-101">\<compositeDuplex></span></span>
<span data-ttu-id="74631-102">Define o elemento de associação que é usado quando o cliente deve expor um ponto de extremidade para o serviço enviar mensagens de volta ao cliente.</span><span class="sxs-lookup"><span data-stu-id="74631-102">Defines the binding element that is used when the client must expose an endpoint for the service to send messages back to the client.</span></span>  
  
 <span data-ttu-id="74631-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="74631-103">\<system.serviceModel></span></span>  
<span data-ttu-id="74631-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="74631-104">\<bindings></span></span>  
<span data-ttu-id="74631-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="74631-105">\<customBinding></span></span>  
<span data-ttu-id="74631-106">\<binding></span><span class="sxs-lookup"><span data-stu-id="74631-106">\<binding></span></span>  
<span data-ttu-id="74631-107">\<compositeDuplex></span><span class="sxs-lookup"><span data-stu-id="74631-107">\<compositeDuplex></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74631-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="74631-108">Syntax</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="URI" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="74631-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="74631-109">Attributes and Elements</span></span>  
 <span data-ttu-id="74631-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="74631-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="74631-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="74631-111">Attributes</span></span>  
  
|<span data-ttu-id="74631-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="74631-112">Attribute</span></span>|<span data-ttu-id="74631-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="74631-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="74631-114">clientBaseAddress</span><span class="sxs-lookup"><span data-stu-id="74631-114">clientBaseAddress</span></span>|<span data-ttu-id="74631-115">Um URI que define o endereço do canal de retorno no modo duplex.</span><span class="sxs-lookup"><span data-stu-id="74631-115">A URI that sets the address of the back channel in duplex mode.</span></span> <span data-ttu-id="74631-116">O serviço usa esse endereço para tornar o contato e estabelecer uma conexão com o cliente.</span><span class="sxs-lookup"><span data-stu-id="74631-116">The service uses this address to make contact and establish a connection with the client.</span></span><br /><br /> <span data-ttu-id="74631-117">Se esse atributo não é definido, um endereço padrão "`full qualified name+default port\TemporaryIndigoAddress\guid`" é gerado.</span><span class="sxs-lookup"><span data-stu-id="74631-117">If this attribute is not set, a default address "`full qualified name+default port\TemporaryIndigoAddress\guid`" is generated.</span></span> <span data-ttu-id="74631-118">O padrão é `null`.</span><span class="sxs-lookup"><span data-stu-id="74631-118">The default is `null`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="74631-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="74631-119">Child Elements</span></span>  
 <span data-ttu-id="74631-120">Nenhum</span><span class="sxs-lookup"><span data-stu-id="74631-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="74631-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="74631-121">Parent Elements</span></span>  
  
|<span data-ttu-id="74631-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="74631-122">Element</span></span>|<span data-ttu-id="74631-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="74631-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="74631-124">\<binding></span><span class="sxs-lookup"><span data-stu-id="74631-124">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="74631-125">Define todos os recursos de associação de associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="74631-125">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="74631-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="74631-126">Remarks</span></span>  
 <span data-ttu-id="74631-127">Este elemento de configuração é usado com os transportes que não permitem comunicações duplex nativamente, por exemplo, HTTP.</span><span class="sxs-lookup"><span data-stu-id="74631-127">This configuration element is used with transports that do not allow duplex communications natively, for example, HTTP.</span></span> <span data-ttu-id="74631-128">TCP, por outro lado, permite que as comunicações duplex nativamente e não requer o uso desse elemento de associação para o serviço enviar mensagens para um cliente.</span><span class="sxs-lookup"><span data-stu-id="74631-128">TCP, by contrast, allows duplex communications natively, and does not require the use of this binding element for the service to send messages back to a client.</span></span>  
  
 <span data-ttu-id="74631-129">O cliente deve expor um endereço para o serviço para que entre em contato com e estabelecer uma conexão.</span><span class="sxs-lookup"><span data-stu-id="74631-129">The client must expose an address for the service to make contact and establish a connection.</span></span> <span data-ttu-id="74631-130">Esse endereço de cliente é fornecido pelo `clientBaseAddress` atributo.</span><span class="sxs-lookup"><span data-stu-id="74631-130">This client address is provided by the `clientBaseAddress` attribute.</span></span> <span data-ttu-id="74631-131">Observe que Windows Communication Foundation (WCF) gera automaticamente um ClientBaseAddress se um não é explicitamente definido pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="74631-131">Note that Windows Communication Foundation (WCF) auto-generates a ClientBaseAddress if one is not explicitly set by the user.</span></span>  
  
## <a name="example"></a><span data-ttu-id="74631-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="74631-132">Example</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="http://www.contoso.com" />
```  
  
## <a name="see-also"></a><span data-ttu-id="74631-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="74631-133">See also</span></span>

- <xref:System.ServiceModel.Configuration.CompositeDuplexElement>
- <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="74631-134">Associações</span><span class="sxs-lookup"><span data-stu-id="74631-134">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="74631-135">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="74631-135">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="74631-136">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="74631-136">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="74631-137">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="74631-137">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
