---
title: <webSocketSettings>
ms.date: 03/30/2017
ms.assetid: bbf97e02-8dd1-4922-acac-3cd33397b249
ms.openlocfilehash: 298bf27b171772bb039b11b5e5de70e7d45b061d
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55258430"
---
# <a name="websocketsettings"></a><span data-ttu-id="bf373-101">\<webSocketSettings></span><span class="sxs-lookup"><span data-stu-id="bf373-101">\<webSocketSettings></span></span>
<span data-ttu-id="bf373-102">Um elemento de configuração usado para especificar configurações de soquete da Web.</span><span class="sxs-lookup"><span data-stu-id="bf373-102">A configuration element used to specify Web Socket settings.</span></span>  
  
<span data-ttu-id="bf373-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="bf373-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="bf373-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="bf373-104">\<bindings></span></span>  
<span data-ttu-id="bf373-105">\<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="bf373-105">\<netHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf373-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bf373-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bf373-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="bf373-107">Attributes and Elements</span></span>  
 <span data-ttu-id="bf373-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="bf373-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bf373-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="bf373-109">Attributes</span></span>  
  
|<span data-ttu-id="bf373-110">Atributo</span><span class="sxs-lookup"><span data-stu-id="bf373-110">Attribute</span></span>|<span data-ttu-id="bf373-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="bf373-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bf373-112">createNotificationOnConnection</span><span class="sxs-lookup"><span data-stu-id="bf373-112">createNotificationOnConnection</span></span>|<span data-ttu-id="bf373-113">Especifica se uma notificação será enviada após a conexão.</span><span class="sxs-lookup"><span data-stu-id="bf373-113">Specifies whether a notification is sent upon connection.</span></span>|  
|<span data-ttu-id="bf373-114">disablePayloadMasking</span><span class="sxs-lookup"><span data-stu-id="bf373-114">disablePayloadMasking</span></span>|<span data-ttu-id="bf373-115">Especifica se o mascaramento de soquete da Web está desabilitado.</span><span class="sxs-lookup"><span data-stu-id="bf373-115">Specifies whether Web Socket masking is disabled.</span></span>|  
|<span data-ttu-id="bf373-116">keepAliveInterval</span><span class="sxs-lookup"><span data-stu-id="bf373-116">keepAliveInterval</span></span>|<span data-ttu-id="bf373-117">Especifica o intervalo de keep alive.</span><span class="sxs-lookup"><span data-stu-id="bf373-117">Specifies the keep alive interval.</span></span>|  
|<span data-ttu-id="bf373-118">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="bf373-118">maxPendingConnections</span></span>|<span data-ttu-id="bf373-119">Especifica o número máximo de conexões aguardando a expedição no serviço.</span><span class="sxs-lookup"><span data-stu-id="bf373-119">Specifies the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="bf373-120">receiveBufferSize</span><span class="sxs-lookup"><span data-stu-id="bf373-120">receiveBufferSize</span></span>|<span data-ttu-id="bf373-121">Especifica o tamanho do buffer de recepção.</span><span class="sxs-lookup"><span data-stu-id="bf373-121">Specifies the size of the receive buffer.</span></span>|  
|<span data-ttu-id="bf373-122">sendBufferSize</span><span class="sxs-lookup"><span data-stu-id="bf373-122">sendBufferSize</span></span>|<span data-ttu-id="bf373-123">Especifica o tamanho do buffer de envio.</span><span class="sxs-lookup"><span data-stu-id="bf373-123">Specifies the size of the send buffer.</span></span>|  
|<span data-ttu-id="bf373-124">subProtocol</span><span class="sxs-lookup"><span data-stu-id="bf373-124">subProtocol</span></span>|<span data-ttu-id="bf373-125">Especifica o subprotocolo do soquete da Web.</span><span class="sxs-lookup"><span data-stu-id="bf373-125">Specifies the Web Socket subprotocol.</span></span>|  
|<span data-ttu-id="bf373-126">transportUsage</span><span class="sxs-lookup"><span data-stu-id="bf373-126">transportUsage</span></span>|<span data-ttu-id="bf373-127">Especifica quando usar soquetes da Web.</span><span class="sxs-lookup"><span data-stu-id="bf373-127">Specifies when to use Web Sockets.</span></span>|  
  
## <a name="transportusage-attribute"></a><span data-ttu-id="bf373-128">transportUsage atributo</span><span class="sxs-lookup"><span data-stu-id="bf373-128">transportUsage Attribute</span></span>  
  
|<span data-ttu-id="bf373-129">Valor</span><span class="sxs-lookup"><span data-stu-id="bf373-129">Value</span></span>|<span data-ttu-id="bf373-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="bf373-130">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="bf373-131">WhenDuplex</span><span class="sxs-lookup"><span data-stu-id="bf373-131">WhenDuplex</span></span>|<span data-ttu-id="bf373-132">Use o protocolo de soquete da Web quando o contrato é duplex.</span><span class="sxs-lookup"><span data-stu-id="bf373-132">Use the Web Socket protocol when the contract is duplex.</span></span>|  
|<span data-ttu-id="bf373-133">Sempre</span><span class="sxs-lookup"><span data-stu-id="bf373-133">Always</span></span>|<span data-ttu-id="bf373-134">Sempre use o protocolo de soquete da Web, independentemente do contrato.</span><span class="sxs-lookup"><span data-stu-id="bf373-134">Always use the Web Socket protocol regardless of the contract.</span></span>|  
|<span data-ttu-id="bf373-135">Nunca</span><span class="sxs-lookup"><span data-stu-id="bf373-135">Never</span></span>|<span data-ttu-id="bf373-136">Nunca use o protocolo de soquete da Web.</span><span class="sxs-lookup"><span data-stu-id="bf373-136">Never use the Web Socket protocol.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bf373-137">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="bf373-137">Child Elements</span></span>  
 <span data-ttu-id="bf373-138">Nenhum</span><span class="sxs-lookup"><span data-stu-id="bf373-138">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bf373-139">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="bf373-139">Parent Elements</span></span>  
  
|<span data-ttu-id="bf373-140">Elemento</span><span class="sxs-lookup"><span data-stu-id="bf373-140">Element</span></span>|<span data-ttu-id="bf373-141">Descrição</span><span class="sxs-lookup"><span data-stu-id="bf373-141">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bf373-142">\<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="bf373-142">\<netHttpBinding></span></span>|<span data-ttu-id="bf373-143">Especifica o NetHttpBinding</span><span class="sxs-lookup"><span data-stu-id="bf373-143">Specifies the NetHttpBinding</span></span>|  
  
## <a name="example"></a><span data-ttu-id="bf373-144">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bf373-144">Example</span></span>  
 <span data-ttu-id="bf373-145">O exemplo a seguir mostra como usar o \<webSocketSettings > elemento.</span><span class="sxs-lookup"><span data-stu-id="bf373-145">The following example shows how to use the \<webSocketSettings> element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bf373-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bf373-146">See also</span></span>
- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="bf373-147">Associações</span><span class="sxs-lookup"><span data-stu-id="bf373-147">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="bf373-148">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="bf373-148">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="bf373-149">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="bf373-149">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="bf373-150">\<binding></span><span class="sxs-lookup"><span data-stu-id="bf373-150">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
