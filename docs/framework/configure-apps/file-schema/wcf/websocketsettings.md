---
title: '&lt;webSocketSettings&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bbf97e02-8dd1-4922-acac-3cd33397b249
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7ee0f555fc1e3412032e0a7dda3a747bbfef6f4d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltwebsocketsettingsgt"></a><span data-ttu-id="c4209-102">&lt;webSocketSettings&gt;</span><span class="sxs-lookup"><span data-stu-id="c4209-102">&lt;webSocketSettings&gt;</span></span>
<span data-ttu-id="c4209-103">Um elemento de configuração usado para especificar configurações de soquete da Web.</span><span class="sxs-lookup"><span data-stu-id="c4209-103">A configuration element used to specify Web Socket settings.</span></span>  
  
<span data-ttu-id="c4209-104">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="c4209-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="c4209-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="c4209-105">\<bindings></span></span>  
<span data-ttu-id="c4209-106">\<netHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="c4209-106">\<netHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4209-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c4209-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c4209-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c4209-108">Attributes and Elements</span></span>  
 <span data-ttu-id="c4209-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c4209-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c4209-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="c4209-110">Attributes</span></span>  
  
|<span data-ttu-id="c4209-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="c4209-111">Attribute</span></span>|<span data-ttu-id="c4209-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="c4209-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c4209-113">createNotificationOnConnection</span><span class="sxs-lookup"><span data-stu-id="c4209-113">createNotificationOnConnection</span></span>|<span data-ttu-id="c4209-114">Especifica se uma notificação será enviada após a conexão.</span><span class="sxs-lookup"><span data-stu-id="c4209-114">Specifies whether a notification is sent upon connection.</span></span>|  
|<span data-ttu-id="c4209-115">disablePayloadMasking</span><span class="sxs-lookup"><span data-stu-id="c4209-115">disablePayloadMasking</span></span>|<span data-ttu-id="c4209-116">Especifica se o mascaramento de soquete da Web está desabilitado.</span><span class="sxs-lookup"><span data-stu-id="c4209-116">Specifies whether Web Socket masking is disabled.</span></span>|  
|<span data-ttu-id="c4209-117">keepAliveInterval</span><span class="sxs-lookup"><span data-stu-id="c4209-117">keepAliveInterval</span></span>|<span data-ttu-id="c4209-118">Especifica o intervalo de keep alive.</span><span class="sxs-lookup"><span data-stu-id="c4209-118">Specifies the keep alive interval.</span></span>|  
|<span data-ttu-id="c4209-119">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="c4209-119">maxPendingConnections</span></span>|<span data-ttu-id="c4209-120">Especifica o número máximo de conexões que estão aguardando envio no serviço.</span><span class="sxs-lookup"><span data-stu-id="c4209-120">Specifies the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="c4209-121">receiveBufferSize</span><span class="sxs-lookup"><span data-stu-id="c4209-121">receiveBufferSize</span></span>|<span data-ttu-id="c4209-122">Especifica o tamanho do buffer de recepção.</span><span class="sxs-lookup"><span data-stu-id="c4209-122">Specifies the size of the receive buffer.</span></span>|  
|<span data-ttu-id="c4209-123">sendBufferSize</span><span class="sxs-lookup"><span data-stu-id="c4209-123">sendBufferSize</span></span>|<span data-ttu-id="c4209-124">Especifica o tamanho do buffer de envio.</span><span class="sxs-lookup"><span data-stu-id="c4209-124">Specifies the size of the send buffer.</span></span>|  
|<span data-ttu-id="c4209-125">subprotocolo</span><span class="sxs-lookup"><span data-stu-id="c4209-125">subProtocol</span></span>|<span data-ttu-id="c4209-126">Especifica o subprotocolo de soquete da Web.</span><span class="sxs-lookup"><span data-stu-id="c4209-126">Specifies the Web Socket subprotocol.</span></span>|  
|<span data-ttu-id="c4209-127">transportUsage</span><span class="sxs-lookup"><span data-stu-id="c4209-127">transportUsage</span></span>|<span data-ttu-id="c4209-128">Especifica quando usar soquetes da Web.</span><span class="sxs-lookup"><span data-stu-id="c4209-128">Specifies when to use Web Sockets.</span></span>|  
  
## <a name="transportusage-attribute"></a><span data-ttu-id="c4209-129">transportUsage atributo</span><span class="sxs-lookup"><span data-stu-id="c4209-129">transportUsage Attribute</span></span>  
  
|<span data-ttu-id="c4209-130">Valor</span><span class="sxs-lookup"><span data-stu-id="c4209-130">Value</span></span>|<span data-ttu-id="c4209-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="c4209-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c4209-132">WhenDuplex</span><span class="sxs-lookup"><span data-stu-id="c4209-132">WhenDuplex</span></span>|<span data-ttu-id="c4209-133">Use o protocolo de soquete da Web quando o contrato é duplex.</span><span class="sxs-lookup"><span data-stu-id="c4209-133">Use the Web Socket protocol when the contract is duplex.</span></span>|  
|<span data-ttu-id="c4209-134">Sempre</span><span class="sxs-lookup"><span data-stu-id="c4209-134">Always</span></span>|<span data-ttu-id="c4209-135">Sempre use o protocolo de soquete da Web, independentemente do contrato.</span><span class="sxs-lookup"><span data-stu-id="c4209-135">Always use the Web Socket protocol regardless of the contract.</span></span>|  
|<span data-ttu-id="c4209-136">Nunca</span><span class="sxs-lookup"><span data-stu-id="c4209-136">Never</span></span>|<span data-ttu-id="c4209-137">Nunca use o protocolo de soquete da Web.</span><span class="sxs-lookup"><span data-stu-id="c4209-137">Never use the Web Socket protocol.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c4209-138">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c4209-138">Child Elements</span></span>  
 <span data-ttu-id="c4209-139">Nenhum</span><span class="sxs-lookup"><span data-stu-id="c4209-139">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c4209-140">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c4209-140">Parent Elements</span></span>  
  
|<span data-ttu-id="c4209-141">Elemento</span><span class="sxs-lookup"><span data-stu-id="c4209-141">Element</span></span>|<span data-ttu-id="c4209-142">Descrição</span><span class="sxs-lookup"><span data-stu-id="c4209-142">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c4209-143">\<netHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="c4209-143">\<netHttpBinding></span></span>|<span data-ttu-id="c4209-144">Especifica o NetHttpBinding</span><span class="sxs-lookup"><span data-stu-id="c4209-144">Specifies the NetHttpBinding</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c4209-145">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c4209-145">Example</span></span>  
 <span data-ttu-id="c4209-146">O exemplo a seguir mostra como usar o \<webSocketSettings > elemento.</span><span class="sxs-lookup"><span data-stu-id="c4209-146">The following example shows how to use the \<webSocketSettings> element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c4209-147">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c4209-147">See Also</span></span>  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 <xref:System.ServiceModel.BasicHttpBinding>  
 <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>  
 [<span data-ttu-id="c4209-148">Associações</span><span class="sxs-lookup"><span data-stu-id="c4209-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="c4209-149">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="c4209-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="c4209-150">Usando associações para configurar clientes e serviços do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="c4209-150">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="c4209-151">\<associação ></span><span class="sxs-lookup"><span data-stu-id="c4209-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
