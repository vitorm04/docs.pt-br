---
title: '&lt;webSocketSettings&gt;'
ms.date: 03/30/2017
ms.assetid: bbf97e02-8dd1-4922-acac-3cd33397b249
ms.openlocfilehash: e5f34dca83c8d3d08d27fb72bee5af2a89ac6b9f
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43511908"
---
# <a name="ltwebsocketsettingsgt"></a><span data-ttu-id="224c4-102">&lt;webSocketSettings&gt;</span><span class="sxs-lookup"><span data-stu-id="224c4-102">&lt;webSocketSettings&gt;</span></span>
<span data-ttu-id="224c4-103">Um elemento de configuração usado para especificar configurações de soquete da Web.</span><span class="sxs-lookup"><span data-stu-id="224c4-103">A configuration element used to specify Web Socket settings.</span></span>  
  
<span data-ttu-id="224c4-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="224c4-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="224c4-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="224c4-105">\<bindings></span></span>  
<span data-ttu-id="224c4-106">\<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="224c4-106">\<netHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="224c4-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="224c4-107">Syntax</span></span>  
  
```xml  
<netHttpBinding>  
  <binding>   
    <webSocketSettings createNotificationOnConnection="boolean" 
                       disablePayloadMasking="boolean" 
                       keepAliveInterval="TimeSpan" 
                       maxPendingConnections="Integer" 
                       receiveBufferSize="Integer" 
                       sendBufferSize="Integer" 
                       subProtocol="String" 
                       transportUsage="WhenDuplex/Always/Never"/>
  </binding>  
</netHttpBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="224c4-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="224c4-108">Attributes and Elements</span></span>  
 <span data-ttu-id="224c4-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="224c4-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="224c4-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="224c4-110">Attributes</span></span>  
  
|<span data-ttu-id="224c4-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="224c4-111">Attribute</span></span>|<span data-ttu-id="224c4-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="224c4-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="224c4-113">createNotificationOnConnection</span><span class="sxs-lookup"><span data-stu-id="224c4-113">createNotificationOnConnection</span></span>|<span data-ttu-id="224c4-114">Especifica se uma notificação será enviada após a conexão.</span><span class="sxs-lookup"><span data-stu-id="224c4-114">Specifies whether a notification is sent upon connection.</span></span>|  
|<span data-ttu-id="224c4-115">disablePayloadMasking</span><span class="sxs-lookup"><span data-stu-id="224c4-115">disablePayloadMasking</span></span>|<span data-ttu-id="224c4-116">Especifica se o mascaramento de soquete da Web está desabilitado.</span><span class="sxs-lookup"><span data-stu-id="224c4-116">Specifies whether Web Socket masking is disabled.</span></span>|  
|<span data-ttu-id="224c4-117">keepAliveInterval</span><span class="sxs-lookup"><span data-stu-id="224c4-117">keepAliveInterval</span></span>|<span data-ttu-id="224c4-118">Especifica o intervalo de keep alive.</span><span class="sxs-lookup"><span data-stu-id="224c4-118">Specifies the keep alive interval.</span></span>|  
|<span data-ttu-id="224c4-119">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="224c4-119">maxPendingConnections</span></span>|<span data-ttu-id="224c4-120">Especifica o número máximo de conexões aguardando a expedição no serviço.</span><span class="sxs-lookup"><span data-stu-id="224c4-120">Specifies the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="224c4-121">receiveBufferSize</span><span class="sxs-lookup"><span data-stu-id="224c4-121">receiveBufferSize</span></span>|<span data-ttu-id="224c4-122">Especifica o tamanho do buffer de recepção.</span><span class="sxs-lookup"><span data-stu-id="224c4-122">Specifies the size of the receive buffer.</span></span>|  
|<span data-ttu-id="224c4-123">sendBufferSize</span><span class="sxs-lookup"><span data-stu-id="224c4-123">sendBufferSize</span></span>|<span data-ttu-id="224c4-124">Especifica o tamanho do buffer de envio.</span><span class="sxs-lookup"><span data-stu-id="224c4-124">Specifies the size of the send buffer.</span></span>|  
|<span data-ttu-id="224c4-125">subProtocol</span><span class="sxs-lookup"><span data-stu-id="224c4-125">subProtocol</span></span>|<span data-ttu-id="224c4-126">Especifica o subprotocolo do soquete da Web.</span><span class="sxs-lookup"><span data-stu-id="224c4-126">Specifies the Web Socket subprotocol.</span></span>|  
|<span data-ttu-id="224c4-127">transportUsage</span><span class="sxs-lookup"><span data-stu-id="224c4-127">transportUsage</span></span>|<span data-ttu-id="224c4-128">Especifica quando usar soquetes da Web.</span><span class="sxs-lookup"><span data-stu-id="224c4-128">Specifies when to use Web Sockets.</span></span>|  
  
## <a name="transportusage-attribute"></a><span data-ttu-id="224c4-129">transportUsage atributo</span><span class="sxs-lookup"><span data-stu-id="224c4-129">transportUsage Attribute</span></span>  
  
|<span data-ttu-id="224c4-130">Valor</span><span class="sxs-lookup"><span data-stu-id="224c4-130">Value</span></span>|<span data-ttu-id="224c4-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="224c4-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="224c4-132">WhenDuplex</span><span class="sxs-lookup"><span data-stu-id="224c4-132">WhenDuplex</span></span>|<span data-ttu-id="224c4-133">Use o protocolo de soquete da Web quando o contrato é duplex.</span><span class="sxs-lookup"><span data-stu-id="224c4-133">Use the Web Socket protocol when the contract is duplex.</span></span>|  
|<span data-ttu-id="224c4-134">Sempre</span><span class="sxs-lookup"><span data-stu-id="224c4-134">Always</span></span>|<span data-ttu-id="224c4-135">Sempre use o protocolo de soquete da Web, independentemente do contrato.</span><span class="sxs-lookup"><span data-stu-id="224c4-135">Always use the Web Socket protocol regardless of the contract.</span></span>|  
|<span data-ttu-id="224c4-136">Nunca</span><span class="sxs-lookup"><span data-stu-id="224c4-136">Never</span></span>|<span data-ttu-id="224c4-137">Nunca use o protocolo de soquete da Web.</span><span class="sxs-lookup"><span data-stu-id="224c4-137">Never use the Web Socket protocol.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="224c4-138">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="224c4-138">Child Elements</span></span>  
 <span data-ttu-id="224c4-139">Nenhum</span><span class="sxs-lookup"><span data-stu-id="224c4-139">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="224c4-140">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="224c4-140">Parent Elements</span></span>  
  
|<span data-ttu-id="224c4-141">Elemento</span><span class="sxs-lookup"><span data-stu-id="224c4-141">Element</span></span>|<span data-ttu-id="224c4-142">Descrição</span><span class="sxs-lookup"><span data-stu-id="224c4-142">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="224c4-143">\<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="224c4-143">\<netHttpBinding></span></span>|<span data-ttu-id="224c4-144">Especifica o NetHttpBinding</span><span class="sxs-lookup"><span data-stu-id="224c4-144">Specifies the NetHttpBinding</span></span>|  
  
## <a name="example"></a><span data-ttu-id="224c4-145">Exemplo</span><span class="sxs-lookup"><span data-stu-id="224c4-145">Example</span></span>  
 <span data-ttu-id="224c4-146">O exemplo a seguir mostra como usar o \<webSocketSettings > elemento.</span><span class="sxs-lookup"><span data-stu-id="224c4-146">The following example shows how to use the \<webSocketSettings> element.</span></span>  
  
```xml  
<netHttpBinding>  
        <binding>  
          <webSocketSettings createNotificationOnConnection="true"  
                              disablePayloadMasking="false  
                              keepAliveInterval="00:10:00"  
                              maxPendingConnections="100"  
                              receiveBufferSize="1000"  
                              sendBufferSize="1000"  
                              subProtocol="Soap"  
                              transportUsage="WhenDuplex/Always/Never"/>  
  
        </binding>  
      </netHttpBinding>  
```  
  
## <a name="see-also"></a><span data-ttu-id="224c4-147">Consulte também</span><span class="sxs-lookup"><span data-stu-id="224c4-147">See Also</span></span>  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 <xref:System.ServiceModel.BasicHttpBinding>  
 <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>  
 [<span data-ttu-id="224c4-148">Associações</span><span class="sxs-lookup"><span data-stu-id="224c4-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="224c4-149">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="224c4-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="224c4-150">Usando associações para configurar clientes e serviços do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="224c4-150">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="224c4-151">\<associação ></span><span class="sxs-lookup"><span data-stu-id="224c4-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
