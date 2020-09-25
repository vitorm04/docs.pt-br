---
title: <compositeDuplex>
ms.date: 03/30/2017
ms.assetid: 725004d1-ce88-4405-a220-78e89844f81f
ms.openlocfilehash: a5209efddd489f8cb04b3266e6ba0bb033eeae6c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91176013"
---
# \<compositeDuplex>

<span data-ttu-id="65633-101">Define o elemento de associação que é usado quando o cliente deve expor um ponto de extremidade para que o serviço envie mensagens de volta ao cliente.</span><span class="sxs-lookup"><span data-stu-id="65633-101">Defines the binding element that is used when the client must expose an endpoint for the service to send messages back to the client.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<compositeDuplex>**  
  
## <a name="syntax"></a><span data-ttu-id="65633-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="65633-102">Syntax</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="URI" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="65633-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="65633-103">Attributes and Elements</span></span>  

 <span data-ttu-id="65633-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="65633-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="65633-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="65633-105">Attributes</span></span>  
  
|<span data-ttu-id="65633-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="65633-106">Attribute</span></span>|<span data-ttu-id="65633-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="65633-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="65633-108">clientBaseAddress</span><span class="sxs-lookup"><span data-stu-id="65633-108">clientBaseAddress</span></span>|<span data-ttu-id="65633-109">Um URI que define o endereço do canal traseiro no modo duplex.</span><span class="sxs-lookup"><span data-stu-id="65633-109">A URI that sets the address of the back channel in duplex mode.</span></span> <span data-ttu-id="65633-110">O serviço usa esse endereço para fazer contato e estabelecer uma conexão com o cliente.</span><span class="sxs-lookup"><span data-stu-id="65633-110">The service uses this address to make contact and establish a connection with the client.</span></span><br /><br /> <span data-ttu-id="65633-111">Se esse atributo não estiver definido, um endereço padrão " `full qualified name+default port\TemporaryIndigoAddress\guid` " será gerado.</span><span class="sxs-lookup"><span data-stu-id="65633-111">If this attribute is not set, a default address "`full qualified name+default port\TemporaryIndigoAddress\guid`" is generated.</span></span> <span data-ttu-id="65633-112">O padrão é `null`.</span><span class="sxs-lookup"><span data-stu-id="65633-112">The default is `null`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="65633-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="65633-113">Child Elements</span></span>  

 <span data-ttu-id="65633-114">Nenhum</span><span class="sxs-lookup"><span data-stu-id="65633-114">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="65633-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="65633-115">Parent Elements</span></span>  
  
|<span data-ttu-id="65633-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="65633-116">Element</span></span>|<span data-ttu-id="65633-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="65633-117">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="65633-118">Define todos os recursos de associação da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="65633-118">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="65633-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="65633-119">Remarks</span></span>  

 <span data-ttu-id="65633-120">Esse elemento de configuração é usado com transportes que não permitem comunicações de duplex nativamente, por exemplo, HTTP.</span><span class="sxs-lookup"><span data-stu-id="65633-120">This configuration element is used with transports that do not allow duplex communications natively, for example, HTTP.</span></span> <span data-ttu-id="65633-121">O TCP, por outro lado, permite comunicações duplex nativamente e não requer o uso desse elemento de ligação para que o serviço envie mensagens de volta para um cliente.</span><span class="sxs-lookup"><span data-stu-id="65633-121">TCP, by contrast, allows duplex communications natively, and does not require the use of this binding element for the service to send messages back to a client.</span></span>  
  
 <span data-ttu-id="65633-122">O cliente deve expor um endereço para que o serviço faça contato e estabeleça uma conexão.</span><span class="sxs-lookup"><span data-stu-id="65633-122">The client must expose an address for the service to make contact and establish a connection.</span></span> <span data-ttu-id="65633-123">Esse endereço de cliente é fornecido pelo `clientBaseAddress` atributo.</span><span class="sxs-lookup"><span data-stu-id="65633-123">This client address is provided by the `clientBaseAddress` attribute.</span></span> <span data-ttu-id="65633-124">Observe que Windows Communication Foundation (WCF) gera automaticamente um ClientBaseAddress se um não é definido explicitamente pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="65633-124">Note that Windows Communication Foundation (WCF) auto-generates a ClientBaseAddress if one is not explicitly set by the user.</span></span>  
  
## <a name="example"></a><span data-ttu-id="65633-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="65633-125">Example</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="http://www.contoso.com" />
```  
  
## <a name="see-also"></a><span data-ttu-id="65633-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="65633-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.CompositeDuplexElement>
- <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="65633-127">Associações</span><span class="sxs-lookup"><span data-stu-id="65633-127">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="65633-128">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="65633-128">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="65633-129">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="65633-129">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
