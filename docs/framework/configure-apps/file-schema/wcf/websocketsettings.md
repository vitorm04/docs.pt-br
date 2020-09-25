---
title: <webSocketSettings>
ms.date: 03/30/2017
ms.assetid: bbf97e02-8dd1-4922-acac-3cd33397b249
ms.openlocfilehash: 6cfddfb9ebfc7c3447af977e14738baabebc8fe9
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177838"
---
# \<webSocketSettings>

<span data-ttu-id="08104-101">Um elemento de configuração usado para especificar as configurações de soquete da Web.</span><span class="sxs-lookup"><span data-stu-id="08104-101">A configuration element used to specify Web Socket settings.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netHttpBinding>**](nethttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webSocketSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="08104-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="08104-102">Syntax</span></span>  
  
```xml  
<netHttpBinding>
  <binding>
    <webSocketSettings createNotificationOnConnection="Boolean"
                       disablePayloadMasking="Boolean"
                       keepAliveInterval="TimeSpan"
                       maxPendingConnections="Integer"
                       receiveBufferSize="Integer"
                       sendBufferSize="Integer"
                       subProtocol="String"
                       transportUsage="WhenDuplex/Always/Never" />
  </binding>
</netHttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="08104-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="08104-103">Attributes and Elements</span></span>  

 <span data-ttu-id="08104-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="08104-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="08104-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="08104-105">Attributes</span></span>  
  
|<span data-ttu-id="08104-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="08104-106">Attribute</span></span>|<span data-ttu-id="08104-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="08104-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="08104-108">createNotificationOnConnection</span><span class="sxs-lookup"><span data-stu-id="08104-108">createNotificationOnConnection</span></span>|<span data-ttu-id="08104-109">Especifica se uma notificação é enviada na conexão.</span><span class="sxs-lookup"><span data-stu-id="08104-109">Specifies whether a notification is sent upon connection.</span></span>|  
|<span data-ttu-id="08104-110">disablePayloadMasking</span><span class="sxs-lookup"><span data-stu-id="08104-110">disablePayloadMasking</span></span>|<span data-ttu-id="08104-111">Especifica se o mascaramento de soquete da Web está desabilitado.</span><span class="sxs-lookup"><span data-stu-id="08104-111">Specifies whether Web Socket masking is disabled.</span></span>|  
|<span data-ttu-id="08104-112">keepAliveInterval</span><span class="sxs-lookup"><span data-stu-id="08104-112">keepAliveInterval</span></span>|<span data-ttu-id="08104-113">Especifica o intervalo de Keep Alive.</span><span class="sxs-lookup"><span data-stu-id="08104-113">Specifies the keep alive interval.</span></span>|  
|<span data-ttu-id="08104-114">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="08104-114">maxPendingConnections</span></span>|<span data-ttu-id="08104-115">Especifica o número máximo de conexões que estão aguardando despacho no serviço.</span><span class="sxs-lookup"><span data-stu-id="08104-115">Specifies the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="08104-116">receiveBufferSize</span><span class="sxs-lookup"><span data-stu-id="08104-116">receiveBufferSize</span></span>|<span data-ttu-id="08104-117">Especifica o tamanho do buffer de recebimento.</span><span class="sxs-lookup"><span data-stu-id="08104-117">Specifies the size of the receive buffer.</span></span>|  
|<span data-ttu-id="08104-118">sendBufferSize</span><span class="sxs-lookup"><span data-stu-id="08104-118">sendBufferSize</span></span>|<span data-ttu-id="08104-119">Especifica o tamanho do buffer de envio.</span><span class="sxs-lookup"><span data-stu-id="08104-119">Specifies the size of the send buffer.</span></span>|  
|<span data-ttu-id="08104-120">subprotocolo</span><span class="sxs-lookup"><span data-stu-id="08104-120">subProtocol</span></span>|<span data-ttu-id="08104-121">Especifica o subprotocolo de soquete da Web.</span><span class="sxs-lookup"><span data-stu-id="08104-121">Specifies the Web Socket subprotocol.</span></span>|  
|<span data-ttu-id="08104-122">transportUsage</span><span class="sxs-lookup"><span data-stu-id="08104-122">transportUsage</span></span>|<span data-ttu-id="08104-123">Especifica quando usar soquetes da Web.</span><span class="sxs-lookup"><span data-stu-id="08104-123">Specifies when to use Web Sockets.</span></span>|  
  
## <a name="transportusage-attribute"></a><span data-ttu-id="08104-124">Atributo transportUsage</span><span class="sxs-lookup"><span data-stu-id="08104-124">transportUsage Attribute</span></span>  
  
|<span data-ttu-id="08104-125">Valor</span><span class="sxs-lookup"><span data-stu-id="08104-125">Value</span></span>|<span data-ttu-id="08104-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="08104-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="08104-127">WhenDuplex</span><span class="sxs-lookup"><span data-stu-id="08104-127">WhenDuplex</span></span>|<span data-ttu-id="08104-128">Use o protocolo de soquete da Web quando o contrato for duplex.</span><span class="sxs-lookup"><span data-stu-id="08104-128">Use the Web Socket protocol when the contract is duplex.</span></span>|  
|<span data-ttu-id="08104-129">Sempre</span><span class="sxs-lookup"><span data-stu-id="08104-129">Always</span></span>|<span data-ttu-id="08104-130">Sempre use o protocolo de soquete da Web, independentemente do contrato.</span><span class="sxs-lookup"><span data-stu-id="08104-130">Always use the Web Socket protocol regardless of the contract.</span></span>|  
|<span data-ttu-id="08104-131">Nunca</span><span class="sxs-lookup"><span data-stu-id="08104-131">Never</span></span>|<span data-ttu-id="08104-132">Nunca use o protocolo de soquete da Web.</span><span class="sxs-lookup"><span data-stu-id="08104-132">Never use the Web Socket protocol.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="08104-133">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="08104-133">Child Elements</span></span>  

 <span data-ttu-id="08104-134">Nenhum</span><span class="sxs-lookup"><span data-stu-id="08104-134">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="08104-135">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="08104-135">Parent Elements</span></span>  
  
|<span data-ttu-id="08104-136">Elemento</span><span class="sxs-lookup"><span data-stu-id="08104-136">Element</span></span>|<span data-ttu-id="08104-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="08104-137">Description</span></span>|  
|-------------|-----------------|  
|\<netHttpBinding>|<span data-ttu-id="08104-138">Especifica o NetHttpBinding</span><span class="sxs-lookup"><span data-stu-id="08104-138">Specifies the NetHttpBinding</span></span>|  
  
## <a name="example"></a><span data-ttu-id="08104-139">Exemplo</span><span class="sxs-lookup"><span data-stu-id="08104-139">Example</span></span>  

 <span data-ttu-id="08104-140">O exemplo a seguir mostra como usar o elemento \<webSocketSettings>.</span><span class="sxs-lookup"><span data-stu-id="08104-140">The following example shows how to use the \<webSocketSettings> element.</span></span>  
  
```xml  
<netHttpBinding>
  <binding>
    <webSocketSettings createNotificationOnConnection="true"
                       disablePayloadMasking="false"
                       keepAliveInterval="00:10:00"
                       maxPendingConnections="100"
                       receiveBufferSize="1000"
                       sendBufferSize="1000"
                       subProtocol="Soap"
                       transportUsage="WhenDuplex/Always/Never" />
  </binding>
</netHttpBinding>
```  
  
## <a name="see-also"></a><span data-ttu-id="08104-141">Veja também</span><span class="sxs-lookup"><span data-stu-id="08104-141">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="08104-142">Associações</span><span class="sxs-lookup"><span data-stu-id="08104-142">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="08104-143">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="08104-143">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="08104-144">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="08104-144">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
