---
title: <webSocketSettings>
ms.date: 03/30/2017
ms.assetid: bbf97e02-8dd1-4922-acac-3cd33397b249
ms.openlocfilehash: 1101d021f3c7436c4f45a22a48e50f6d1553f753
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61769740"
---
# <a name="websocketsettings"></a><span data-ttu-id="35c31-101">\<webSocketSettings></span><span class="sxs-lookup"><span data-stu-id="35c31-101">\<webSocketSettings></span></span>
<span data-ttu-id="35c31-102">Um elemento de configuração usado para especificar configurações de soquete da Web.</span><span class="sxs-lookup"><span data-stu-id="35c31-102">A configuration element used to specify Web Socket settings.</span></span>  
  
<span data-ttu-id="35c31-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="35c31-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="35c31-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="35c31-104">\<bindings></span></span>  
<span data-ttu-id="35c31-105">\<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="35c31-105">\<netHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35c31-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="35c31-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="35c31-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="35c31-107">Attributes and Elements</span></span>  
 <span data-ttu-id="35c31-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="35c31-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="35c31-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="35c31-109">Attributes</span></span>  
  
|<span data-ttu-id="35c31-110">Atributo</span><span class="sxs-lookup"><span data-stu-id="35c31-110">Attribute</span></span>|<span data-ttu-id="35c31-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="35c31-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="35c31-112">createNotificationOnConnection</span><span class="sxs-lookup"><span data-stu-id="35c31-112">createNotificationOnConnection</span></span>|<span data-ttu-id="35c31-113">Especifica se uma notificação será enviada após a conexão.</span><span class="sxs-lookup"><span data-stu-id="35c31-113">Specifies whether a notification is sent upon connection.</span></span>|  
|<span data-ttu-id="35c31-114">disablePayloadMasking</span><span class="sxs-lookup"><span data-stu-id="35c31-114">disablePayloadMasking</span></span>|<span data-ttu-id="35c31-115">Especifica se o mascaramento de soquete da Web está desabilitado.</span><span class="sxs-lookup"><span data-stu-id="35c31-115">Specifies whether Web Socket masking is disabled.</span></span>|  
|<span data-ttu-id="35c31-116">keepAliveInterval</span><span class="sxs-lookup"><span data-stu-id="35c31-116">keepAliveInterval</span></span>|<span data-ttu-id="35c31-117">Especifica o intervalo de keep alive.</span><span class="sxs-lookup"><span data-stu-id="35c31-117">Specifies the keep alive interval.</span></span>|  
|<span data-ttu-id="35c31-118">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="35c31-118">maxPendingConnections</span></span>|<span data-ttu-id="35c31-119">Especifica o número máximo de conexões aguardando a expedição no serviço.</span><span class="sxs-lookup"><span data-stu-id="35c31-119">Specifies the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="35c31-120">receiveBufferSize</span><span class="sxs-lookup"><span data-stu-id="35c31-120">receiveBufferSize</span></span>|<span data-ttu-id="35c31-121">Especifica o tamanho do buffer de recepção.</span><span class="sxs-lookup"><span data-stu-id="35c31-121">Specifies the size of the receive buffer.</span></span>|  
|<span data-ttu-id="35c31-122">sendBufferSize</span><span class="sxs-lookup"><span data-stu-id="35c31-122">sendBufferSize</span></span>|<span data-ttu-id="35c31-123">Especifica o tamanho do buffer de envio.</span><span class="sxs-lookup"><span data-stu-id="35c31-123">Specifies the size of the send buffer.</span></span>|  
|<span data-ttu-id="35c31-124">subProtocol</span><span class="sxs-lookup"><span data-stu-id="35c31-124">subProtocol</span></span>|<span data-ttu-id="35c31-125">Especifica o subprotocolo do soquete da Web.</span><span class="sxs-lookup"><span data-stu-id="35c31-125">Specifies the Web Socket subprotocol.</span></span>|  
|<span data-ttu-id="35c31-126">transportUsage</span><span class="sxs-lookup"><span data-stu-id="35c31-126">transportUsage</span></span>|<span data-ttu-id="35c31-127">Especifica quando usar soquetes da Web.</span><span class="sxs-lookup"><span data-stu-id="35c31-127">Specifies when to use Web Sockets.</span></span>|  
  
## <a name="transportusage-attribute"></a><span data-ttu-id="35c31-128">transportUsage atributo</span><span class="sxs-lookup"><span data-stu-id="35c31-128">transportUsage Attribute</span></span>  
  
|<span data-ttu-id="35c31-129">Valor</span><span class="sxs-lookup"><span data-stu-id="35c31-129">Value</span></span>|<span data-ttu-id="35c31-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="35c31-130">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="35c31-131">WhenDuplex</span><span class="sxs-lookup"><span data-stu-id="35c31-131">WhenDuplex</span></span>|<span data-ttu-id="35c31-132">Use o protocolo de soquete da Web quando o contrato é duplex.</span><span class="sxs-lookup"><span data-stu-id="35c31-132">Use the Web Socket protocol when the contract is duplex.</span></span>|  
|<span data-ttu-id="35c31-133">Sempre</span><span class="sxs-lookup"><span data-stu-id="35c31-133">Always</span></span>|<span data-ttu-id="35c31-134">Sempre use o protocolo de soquete da Web, independentemente do contrato.</span><span class="sxs-lookup"><span data-stu-id="35c31-134">Always use the Web Socket protocol regardless of the contract.</span></span>|  
|<span data-ttu-id="35c31-135">Nunca</span><span class="sxs-lookup"><span data-stu-id="35c31-135">Never</span></span>|<span data-ttu-id="35c31-136">Nunca use o protocolo de soquete da Web.</span><span class="sxs-lookup"><span data-stu-id="35c31-136">Never use the Web Socket protocol.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="35c31-137">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="35c31-137">Child Elements</span></span>  
 <span data-ttu-id="35c31-138">Nenhum</span><span class="sxs-lookup"><span data-stu-id="35c31-138">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="35c31-139">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="35c31-139">Parent Elements</span></span>  
  
|<span data-ttu-id="35c31-140">Elemento</span><span class="sxs-lookup"><span data-stu-id="35c31-140">Element</span></span>|<span data-ttu-id="35c31-141">Descrição</span><span class="sxs-lookup"><span data-stu-id="35c31-141">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="35c31-142">\<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="35c31-142">\<netHttpBinding></span></span>|<span data-ttu-id="35c31-143">Especifica o NetHttpBinding</span><span class="sxs-lookup"><span data-stu-id="35c31-143">Specifies the NetHttpBinding</span></span>|  
  
## <a name="example"></a><span data-ttu-id="35c31-144">Exemplo</span><span class="sxs-lookup"><span data-stu-id="35c31-144">Example</span></span>  
 <span data-ttu-id="35c31-145">O exemplo a seguir mostra como usar o \<webSocketSettings > elemento.</span><span class="sxs-lookup"><span data-stu-id="35c31-145">The following example shows how to use the \<webSocketSettings> element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="35c31-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="35c31-146">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="35c31-147">Associações</span><span class="sxs-lookup"><span data-stu-id="35c31-147">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="35c31-148">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="35c31-148">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="35c31-149">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="35c31-149">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="35c31-150">\<binding></span><span class="sxs-lookup"><span data-stu-id="35c31-150">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
