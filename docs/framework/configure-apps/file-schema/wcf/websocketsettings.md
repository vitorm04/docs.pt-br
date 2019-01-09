---
title: '&lt;webSocketSettings&gt;'
ms.date: 03/30/2017
ms.assetid: bbf97e02-8dd1-4922-acac-3cd33397b249
ms.openlocfilehash: 134a233a337c40d21f7547fe385ec788cef2165b
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54150052"
---
# <a name="ltwebsocketsettingsgt"></a><span data-ttu-id="948f6-102">&lt;webSocketSettings&gt;</span><span class="sxs-lookup"><span data-stu-id="948f6-102">&lt;webSocketSettings&gt;</span></span>
<span data-ttu-id="948f6-103">Um elemento de configuração usado para especificar configurações de soquete da Web.</span><span class="sxs-lookup"><span data-stu-id="948f6-103">A configuration element used to specify Web Socket settings.</span></span>  
  
<span data-ttu-id="948f6-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="948f6-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="948f6-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="948f6-105">\<bindings></span></span>  
<span data-ttu-id="948f6-106">\<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="948f6-106">\<netHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="948f6-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="948f6-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="948f6-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="948f6-108">Attributes and Elements</span></span>  
 <span data-ttu-id="948f6-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="948f6-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="948f6-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="948f6-110">Attributes</span></span>  
  
|<span data-ttu-id="948f6-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="948f6-111">Attribute</span></span>|<span data-ttu-id="948f6-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="948f6-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="948f6-113">createNotificationOnConnection</span><span class="sxs-lookup"><span data-stu-id="948f6-113">createNotificationOnConnection</span></span>|<span data-ttu-id="948f6-114">Especifica se uma notificação será enviada após a conexão.</span><span class="sxs-lookup"><span data-stu-id="948f6-114">Specifies whether a notification is sent upon connection.</span></span>|  
|<span data-ttu-id="948f6-115">disablePayloadMasking</span><span class="sxs-lookup"><span data-stu-id="948f6-115">disablePayloadMasking</span></span>|<span data-ttu-id="948f6-116">Especifica se o mascaramento de soquete da Web está desabilitado.</span><span class="sxs-lookup"><span data-stu-id="948f6-116">Specifies whether Web Socket masking is disabled.</span></span>|  
|<span data-ttu-id="948f6-117">keepAliveInterval</span><span class="sxs-lookup"><span data-stu-id="948f6-117">keepAliveInterval</span></span>|<span data-ttu-id="948f6-118">Especifica o intervalo de keep alive.</span><span class="sxs-lookup"><span data-stu-id="948f6-118">Specifies the keep alive interval.</span></span>|  
|<span data-ttu-id="948f6-119">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="948f6-119">maxPendingConnections</span></span>|<span data-ttu-id="948f6-120">Especifica o número máximo de conexões aguardando a expedição no serviço.</span><span class="sxs-lookup"><span data-stu-id="948f6-120">Specifies the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="948f6-121">receiveBufferSize</span><span class="sxs-lookup"><span data-stu-id="948f6-121">receiveBufferSize</span></span>|<span data-ttu-id="948f6-122">Especifica o tamanho do buffer de recepção.</span><span class="sxs-lookup"><span data-stu-id="948f6-122">Specifies the size of the receive buffer.</span></span>|  
|<span data-ttu-id="948f6-123">sendBufferSize</span><span class="sxs-lookup"><span data-stu-id="948f6-123">sendBufferSize</span></span>|<span data-ttu-id="948f6-124">Especifica o tamanho do buffer de envio.</span><span class="sxs-lookup"><span data-stu-id="948f6-124">Specifies the size of the send buffer.</span></span>|  
|<span data-ttu-id="948f6-125">subProtocol</span><span class="sxs-lookup"><span data-stu-id="948f6-125">subProtocol</span></span>|<span data-ttu-id="948f6-126">Especifica o subprotocolo do soquete da Web.</span><span class="sxs-lookup"><span data-stu-id="948f6-126">Specifies the Web Socket subprotocol.</span></span>|  
|<span data-ttu-id="948f6-127">transportUsage</span><span class="sxs-lookup"><span data-stu-id="948f6-127">transportUsage</span></span>|<span data-ttu-id="948f6-128">Especifica quando usar soquetes da Web.</span><span class="sxs-lookup"><span data-stu-id="948f6-128">Specifies when to use Web Sockets.</span></span>|  
  
## <a name="transportusage-attribute"></a><span data-ttu-id="948f6-129">transportUsage atributo</span><span class="sxs-lookup"><span data-stu-id="948f6-129">transportUsage Attribute</span></span>  
  
|<span data-ttu-id="948f6-130">Valor</span><span class="sxs-lookup"><span data-stu-id="948f6-130">Value</span></span>|<span data-ttu-id="948f6-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="948f6-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="948f6-132">WhenDuplex</span><span class="sxs-lookup"><span data-stu-id="948f6-132">WhenDuplex</span></span>|<span data-ttu-id="948f6-133">Use o protocolo de soquete da Web quando o contrato é duplex.</span><span class="sxs-lookup"><span data-stu-id="948f6-133">Use the Web Socket protocol when the contract is duplex.</span></span>|  
|<span data-ttu-id="948f6-134">Sempre</span><span class="sxs-lookup"><span data-stu-id="948f6-134">Always</span></span>|<span data-ttu-id="948f6-135">Sempre use o protocolo de soquete da Web, independentemente do contrato.</span><span class="sxs-lookup"><span data-stu-id="948f6-135">Always use the Web Socket protocol regardless of the contract.</span></span>|  
|<span data-ttu-id="948f6-136">Nunca</span><span class="sxs-lookup"><span data-stu-id="948f6-136">Never</span></span>|<span data-ttu-id="948f6-137">Nunca use o protocolo de soquete da Web.</span><span class="sxs-lookup"><span data-stu-id="948f6-137">Never use the Web Socket protocol.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="948f6-138">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="948f6-138">Child Elements</span></span>  
 <span data-ttu-id="948f6-139">Nenhum</span><span class="sxs-lookup"><span data-stu-id="948f6-139">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="948f6-140">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="948f6-140">Parent Elements</span></span>  
  
|<span data-ttu-id="948f6-141">Elemento</span><span class="sxs-lookup"><span data-stu-id="948f6-141">Element</span></span>|<span data-ttu-id="948f6-142">Descrição</span><span class="sxs-lookup"><span data-stu-id="948f6-142">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="948f6-143">\<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="948f6-143">\<netHttpBinding></span></span>|<span data-ttu-id="948f6-144">Especifica o NetHttpBinding</span><span class="sxs-lookup"><span data-stu-id="948f6-144">Specifies the NetHttpBinding</span></span>|  
  
## <a name="example"></a><span data-ttu-id="948f6-145">Exemplo</span><span class="sxs-lookup"><span data-stu-id="948f6-145">Example</span></span>  
 <span data-ttu-id="948f6-146">O exemplo a seguir mostra como usar o \<webSocketSettings > elemento.</span><span class="sxs-lookup"><span data-stu-id="948f6-146">The following example shows how to use the \<webSocketSettings> element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="948f6-147">Consulte também</span><span class="sxs-lookup"><span data-stu-id="948f6-147">See Also</span></span>  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 <xref:System.ServiceModel.BasicHttpBinding>  
 <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>  
 [<span data-ttu-id="948f6-148">Associações</span><span class="sxs-lookup"><span data-stu-id="948f6-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="948f6-149">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="948f6-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="948f6-150">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="948f6-150">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="948f6-151">\<associação ></span><span class="sxs-lookup"><span data-stu-id="948f6-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
