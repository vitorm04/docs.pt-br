---
title: <webSocketSettings>
ms.date: 03/30/2017
ms.assetid: bbf97e02-8dd1-4922-acac-3cd33397b249
ms.openlocfilehash: 80784f40130e572ae374bd9b26e701360dbfcaa5
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399140"
---
# <a name="websocketsettings"></a><span data-ttu-id="6db22-101">\<webSocketSettings></span><span class="sxs-lookup"><span data-stu-id="6db22-101">\<webSocketSettings></span></span>
<span data-ttu-id="6db22-102">Um elemento de configuração usado para especificar as configurações de soquete da Web.</span><span class="sxs-lookup"><span data-stu-id="6db22-102">A configuration element used to specify Web Socket settings.</span></span>  
  
<span data-ttu-id="6db22-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="6db22-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="6db22-104">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="6db22-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="6db22-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="6db22-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="6db22-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> NetHttpBinding**](nethttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="6db22-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netHttpBinding>**](nethttpbinding.md)</span></span>\
<span data-ttu-id="6db22-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de associação**</span><span class="sxs-lookup"><span data-stu-id="6db22-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="6db22-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> webSocketSettings**</span><span class="sxs-lookup"><span data-stu-id="6db22-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webSocketSettings>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6db22-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6db22-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6db22-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="6db22-110">Attributes and Elements</span></span>  
 <span data-ttu-id="6db22-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="6db22-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6db22-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="6db22-112">Attributes</span></span>  
  
|<span data-ttu-id="6db22-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="6db22-113">Attribute</span></span>|<span data-ttu-id="6db22-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="6db22-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6db22-115">createNotificationOnConnection</span><span class="sxs-lookup"><span data-stu-id="6db22-115">createNotificationOnConnection</span></span>|<span data-ttu-id="6db22-116">Especifica se uma notificação é enviada na conexão.</span><span class="sxs-lookup"><span data-stu-id="6db22-116">Specifies whether a notification is sent upon connection.</span></span>|  
|<span data-ttu-id="6db22-117">disablePayloadMasking</span><span class="sxs-lookup"><span data-stu-id="6db22-117">disablePayloadMasking</span></span>|<span data-ttu-id="6db22-118">Especifica se o mascaramento de soquete da Web está desabilitado.</span><span class="sxs-lookup"><span data-stu-id="6db22-118">Specifies whether Web Socket masking is disabled.</span></span>|  
|<span data-ttu-id="6db22-119">keepAliveInterval</span><span class="sxs-lookup"><span data-stu-id="6db22-119">keepAliveInterval</span></span>|<span data-ttu-id="6db22-120">Especifica o intervalo de Keep Alive.</span><span class="sxs-lookup"><span data-stu-id="6db22-120">Specifies the keep alive interval.</span></span>|  
|<span data-ttu-id="6db22-121">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="6db22-121">maxPendingConnections</span></span>|<span data-ttu-id="6db22-122">Especifica o número máximo de conexões que estão aguardando despacho no serviço.</span><span class="sxs-lookup"><span data-stu-id="6db22-122">Specifies the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="6db22-123">receiveBufferSize</span><span class="sxs-lookup"><span data-stu-id="6db22-123">receiveBufferSize</span></span>|<span data-ttu-id="6db22-124">Especifica o tamanho do buffer de recebimento.</span><span class="sxs-lookup"><span data-stu-id="6db22-124">Specifies the size of the receive buffer.</span></span>|  
|<span data-ttu-id="6db22-125">sendBufferSize</span><span class="sxs-lookup"><span data-stu-id="6db22-125">sendBufferSize</span></span>|<span data-ttu-id="6db22-126">Especifica o tamanho do buffer de envio.</span><span class="sxs-lookup"><span data-stu-id="6db22-126">Specifies the size of the send buffer.</span></span>|  
|<span data-ttu-id="6db22-127">subProtocol</span><span class="sxs-lookup"><span data-stu-id="6db22-127">subProtocol</span></span>|<span data-ttu-id="6db22-128">Especifica o subprotocolo de soquete da Web.</span><span class="sxs-lookup"><span data-stu-id="6db22-128">Specifies the Web Socket subprotocol.</span></span>|  
|<span data-ttu-id="6db22-129">transportUsage</span><span class="sxs-lookup"><span data-stu-id="6db22-129">transportUsage</span></span>|<span data-ttu-id="6db22-130">Especifica quando usar soquetes da Web.</span><span class="sxs-lookup"><span data-stu-id="6db22-130">Specifies when to use Web Sockets.</span></span>|  
  
## <a name="transportusage-attribute"></a><span data-ttu-id="6db22-131">Atributo transportUsage</span><span class="sxs-lookup"><span data-stu-id="6db22-131">transportUsage Attribute</span></span>  
  
|<span data-ttu-id="6db22-132">Valor</span><span class="sxs-lookup"><span data-stu-id="6db22-132">Value</span></span>|<span data-ttu-id="6db22-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="6db22-133">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6db22-134">WhenDuplex</span><span class="sxs-lookup"><span data-stu-id="6db22-134">WhenDuplex</span></span>|<span data-ttu-id="6db22-135">Use o protocolo de soquete da Web quando o contrato for duplex.</span><span class="sxs-lookup"><span data-stu-id="6db22-135">Use the Web Socket protocol when the contract is duplex.</span></span>|  
|<span data-ttu-id="6db22-136">Sempre</span><span class="sxs-lookup"><span data-stu-id="6db22-136">Always</span></span>|<span data-ttu-id="6db22-137">Sempre use o protocolo de soquete da Web, independentemente do contrato.</span><span class="sxs-lookup"><span data-stu-id="6db22-137">Always use the Web Socket protocol regardless of the contract.</span></span>|  
|<span data-ttu-id="6db22-138">Nunca</span><span class="sxs-lookup"><span data-stu-id="6db22-138">Never</span></span>|<span data-ttu-id="6db22-139">Nunca use o protocolo de soquete da Web.</span><span class="sxs-lookup"><span data-stu-id="6db22-139">Never use the Web Socket protocol.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6db22-140">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="6db22-140">Child Elements</span></span>  
 <span data-ttu-id="6db22-141">Nenhum</span><span class="sxs-lookup"><span data-stu-id="6db22-141">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6db22-142">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="6db22-142">Parent Elements</span></span>  
  
|<span data-ttu-id="6db22-143">Elemento</span><span class="sxs-lookup"><span data-stu-id="6db22-143">Element</span></span>|<span data-ttu-id="6db22-144">Descrição</span><span class="sxs-lookup"><span data-stu-id="6db22-144">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6db22-145">\<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="6db22-145">\<netHttpBinding></span></span>|<span data-ttu-id="6db22-146">Especifica o NetHttpBinding</span><span class="sxs-lookup"><span data-stu-id="6db22-146">Specifies the NetHttpBinding</span></span>|  
  
## <a name="example"></a><span data-ttu-id="6db22-147">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6db22-147">Example</span></span>  
 <span data-ttu-id="6db22-148">O exemplo a seguir mostra como usar o \<elemento > webSocketSettings.</span><span class="sxs-lookup"><span data-stu-id="6db22-148">The following example shows how to use the \<webSocketSettings> element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6db22-149">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6db22-149">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="6db22-150">Associações</span><span class="sxs-lookup"><span data-stu-id="6db22-150">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="6db22-151">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="6db22-151">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="6db22-152">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="6db22-152">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="6db22-153">\<binding></span><span class="sxs-lookup"><span data-stu-id="6db22-153">\<binding></span></span>](../../../misc/binding.md)
