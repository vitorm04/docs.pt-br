---
title: <webSocketSettings>
ms.date: 03/30/2017
ms.assetid: bbf97e02-8dd1-4922-acac-3cd33397b249
ms.openlocfilehash: 5c9dbec13dd0d71ba1b92ea971d067540013b6f9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940315"
---
# <a name="websocketsettings"></a><span data-ttu-id="0cf8c-101">\<webSocketSettings></span><span class="sxs-lookup"><span data-stu-id="0cf8c-101">\<webSocketSettings></span></span>
<span data-ttu-id="0cf8c-102">Um elemento de configuração usado para especificar as configurações de soquete da Web.</span><span class="sxs-lookup"><span data-stu-id="0cf8c-102">A configuration element used to specify Web Socket settings.</span></span>  
  
<span data-ttu-id="0cf8c-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="0cf8c-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="0cf8c-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="0cf8c-104">\<bindings></span></span>  
<span data-ttu-id="0cf8c-105">\<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="0cf8c-105">\<netHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0cf8c-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0cf8c-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0cf8c-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="0cf8c-107">Attributes and Elements</span></span>  
 <span data-ttu-id="0cf8c-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="0cf8c-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0cf8c-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="0cf8c-109">Attributes</span></span>  
  
|<span data-ttu-id="0cf8c-110">Atributo</span><span class="sxs-lookup"><span data-stu-id="0cf8c-110">Attribute</span></span>|<span data-ttu-id="0cf8c-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="0cf8c-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0cf8c-112">createNotificationOnConnection</span><span class="sxs-lookup"><span data-stu-id="0cf8c-112">createNotificationOnConnection</span></span>|<span data-ttu-id="0cf8c-113">Especifica se uma notificação é enviada na conexão.</span><span class="sxs-lookup"><span data-stu-id="0cf8c-113">Specifies whether a notification is sent upon connection.</span></span>|  
|<span data-ttu-id="0cf8c-114">disablePayloadMasking</span><span class="sxs-lookup"><span data-stu-id="0cf8c-114">disablePayloadMasking</span></span>|<span data-ttu-id="0cf8c-115">Especifica se o mascaramento de soquete da Web está desabilitado.</span><span class="sxs-lookup"><span data-stu-id="0cf8c-115">Specifies whether Web Socket masking is disabled.</span></span>|  
|<span data-ttu-id="0cf8c-116">keepAliveInterval</span><span class="sxs-lookup"><span data-stu-id="0cf8c-116">keepAliveInterval</span></span>|<span data-ttu-id="0cf8c-117">Especifica o intervalo de Keep Alive.</span><span class="sxs-lookup"><span data-stu-id="0cf8c-117">Specifies the keep alive interval.</span></span>|  
|<span data-ttu-id="0cf8c-118">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="0cf8c-118">maxPendingConnections</span></span>|<span data-ttu-id="0cf8c-119">Especifica o número máximo de conexões que estão aguardando despacho no serviço.</span><span class="sxs-lookup"><span data-stu-id="0cf8c-119">Specifies the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="0cf8c-120">receiveBufferSize</span><span class="sxs-lookup"><span data-stu-id="0cf8c-120">receiveBufferSize</span></span>|<span data-ttu-id="0cf8c-121">Especifica o tamanho do buffer de recebimento.</span><span class="sxs-lookup"><span data-stu-id="0cf8c-121">Specifies the size of the receive buffer.</span></span>|  
|<span data-ttu-id="0cf8c-122">sendBufferSize</span><span class="sxs-lookup"><span data-stu-id="0cf8c-122">sendBufferSize</span></span>|<span data-ttu-id="0cf8c-123">Especifica o tamanho do buffer de envio.</span><span class="sxs-lookup"><span data-stu-id="0cf8c-123">Specifies the size of the send buffer.</span></span>|  
|<span data-ttu-id="0cf8c-124">subProtocol</span><span class="sxs-lookup"><span data-stu-id="0cf8c-124">subProtocol</span></span>|<span data-ttu-id="0cf8c-125">Especifica o subprotocolo de soquete da Web.</span><span class="sxs-lookup"><span data-stu-id="0cf8c-125">Specifies the Web Socket subprotocol.</span></span>|  
|<span data-ttu-id="0cf8c-126">transportUsage</span><span class="sxs-lookup"><span data-stu-id="0cf8c-126">transportUsage</span></span>|<span data-ttu-id="0cf8c-127">Especifica quando usar soquetes da Web.</span><span class="sxs-lookup"><span data-stu-id="0cf8c-127">Specifies when to use Web Sockets.</span></span>|  
  
## <a name="transportusage-attribute"></a><span data-ttu-id="0cf8c-128">Atributo transportUsage</span><span class="sxs-lookup"><span data-stu-id="0cf8c-128">transportUsage Attribute</span></span>  
  
|<span data-ttu-id="0cf8c-129">Valor</span><span class="sxs-lookup"><span data-stu-id="0cf8c-129">Value</span></span>|<span data-ttu-id="0cf8c-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="0cf8c-130">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0cf8c-131">WhenDuplex</span><span class="sxs-lookup"><span data-stu-id="0cf8c-131">WhenDuplex</span></span>|<span data-ttu-id="0cf8c-132">Use o protocolo de soquete da Web quando o contrato for duplex.</span><span class="sxs-lookup"><span data-stu-id="0cf8c-132">Use the Web Socket protocol when the contract is duplex.</span></span>|  
|<span data-ttu-id="0cf8c-133">Sempre</span><span class="sxs-lookup"><span data-stu-id="0cf8c-133">Always</span></span>|<span data-ttu-id="0cf8c-134">Sempre use o protocolo de soquete da Web, independentemente do contrato.</span><span class="sxs-lookup"><span data-stu-id="0cf8c-134">Always use the Web Socket protocol regardless of the contract.</span></span>|  
|<span data-ttu-id="0cf8c-135">Nunca</span><span class="sxs-lookup"><span data-stu-id="0cf8c-135">Never</span></span>|<span data-ttu-id="0cf8c-136">Nunca use o protocolo de soquete da Web.</span><span class="sxs-lookup"><span data-stu-id="0cf8c-136">Never use the Web Socket protocol.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0cf8c-137">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="0cf8c-137">Child Elements</span></span>  
 <span data-ttu-id="0cf8c-138">Nenhum</span><span class="sxs-lookup"><span data-stu-id="0cf8c-138">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0cf8c-139">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="0cf8c-139">Parent Elements</span></span>  
  
|<span data-ttu-id="0cf8c-140">Elemento</span><span class="sxs-lookup"><span data-stu-id="0cf8c-140">Element</span></span>|<span data-ttu-id="0cf8c-141">Descrição</span><span class="sxs-lookup"><span data-stu-id="0cf8c-141">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0cf8c-142">\<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="0cf8c-142">\<netHttpBinding></span></span>|<span data-ttu-id="0cf8c-143">Especifica o NetHttpBinding</span><span class="sxs-lookup"><span data-stu-id="0cf8c-143">Specifies the NetHttpBinding</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0cf8c-144">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0cf8c-144">Example</span></span>  
 <span data-ttu-id="0cf8c-145">O exemplo a seguir mostra como usar o \<elemento > webSocketSettings.</span><span class="sxs-lookup"><span data-stu-id="0cf8c-145">The following example shows how to use the \<webSocketSettings> element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0cf8c-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0cf8c-146">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="0cf8c-147">Associações</span><span class="sxs-lookup"><span data-stu-id="0cf8c-147">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="0cf8c-148">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="0cf8c-148">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="0cf8c-149">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="0cf8c-149">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="0cf8c-150">\<binding></span><span class="sxs-lookup"><span data-stu-id="0cf8c-150">\<binding></span></span>](../../../misc/binding.md)
