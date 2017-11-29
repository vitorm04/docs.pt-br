---
title: ConnectionOrientedTransportBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c1308313-f0e2-49e6-977d-6b4ce9ad35d1
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d28bedb67850b9bb77c25c8d29c6e39b056770a5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="connectionorientedtransportbindingelement"></a><span data-ttu-id="339e4-102">ConnectionOrientedTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="339e4-102">ConnectionOrientedTransportBindingElement</span></span>
<span data-ttu-id="339e4-103">ConnectionOrientedTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="339e4-103">ConnectionOrientedTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="339e4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="339e4-104">Syntax</span></span>  
  
```  
class ConnectionOrientedTransportBindingElement : TransportBindingElement  
{  
  datetime ChannelInitializationTimeout;  
  sint32 ConnectionBufferSize;  
  string HostNameComparisonMode;  
  sint32 MaxBufferSize;  
  datetime MaxOutputDelay;  
  sint32 MaxPendingAccepts;  
  sint32 MaxPendingConnections;  
  string TransferMode;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="339e4-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="339e4-105">Methods</span></span>  
 <span data-ttu-id="339e4-106">A classe ConnectionOrientedTransportBindingElement não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="339e4-106">The ConnectionOrientedTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="339e4-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="339e4-107">Properties</span></span>  
 <span data-ttu-id="339e4-108">A classe ConnectionOrientedTransportBindingElement tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="339e4-108">The ConnectionOrientedTransportBindingElement class has the following properties:</span></span>  
  
### <a name="channelinitializationtimeout"></a><span data-ttu-id="339e4-109">ChannelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="339e4-109">ChannelInitializationTimeout</span></span>  
 <span data-ttu-id="339e4-110">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="339e4-110">Data type: datetime</span></span>  
  
 <span data-ttu-id="339e4-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="339e4-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="339e4-112">O timespan que especifica quanto tempo a inicialização do canal tem para concluir antes do tempo limite.</span><span class="sxs-lookup"><span data-stu-id="339e4-112">The timespan that specifies how long the channel initialization has to complete before timing out.</span></span>  
  
### <a name="connectionbuffersize"></a><span data-ttu-id="339e4-113">connectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="339e4-113">ConnectionBufferSize</span></span>  
 <span data-ttu-id="339e4-114">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="339e4-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="339e4-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="339e4-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="339e4-116">O tamanho do buffer usado para transmitir um bloco da mensagem serializada na conexão do cliente ou serviço.</span><span class="sxs-lookup"><span data-stu-id="339e4-116">The size of the buffer used to transmit a chunk of the serialized message on the wire from the client or service.</span></span>  
  
### <a name="hostnamecomparisonmode"></a><span data-ttu-id="339e4-117">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="339e4-117">HostNameComparisonMode</span></span>  
 <span data-ttu-id="339e4-118">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="339e4-118">Data type: string</span></span>  
  
 <span data-ttu-id="339e4-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="339e4-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="339e4-120">Um valor que indica se o nome do host é usado para acessar o serviço ao fazer correspondência no URI.</span><span class="sxs-lookup"><span data-stu-id="339e4-120">A value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>  
  
### <a name="maxbuffersize"></a><span data-ttu-id="339e4-121">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="339e4-121">MaxBufferSize</span></span>  
 <span data-ttu-id="339e4-122">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="339e4-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="339e4-123">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="339e4-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="339e4-124">O tamanho máximo do buffer a ser usado.</span><span class="sxs-lookup"><span data-stu-id="339e4-124">The maximum size of the buffer to use.</span></span>  
  
### <a name="maxoutputdelay"></a><span data-ttu-id="339e4-125">maxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="339e4-125">MaxOutputDelay</span></span>  
 <span data-ttu-id="339e4-126">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="339e4-126">Data type: datetime</span></span>  
  
 <span data-ttu-id="339e4-127">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="339e4-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="339e4-128">O intervalo máximo de tempo que uma parte de uma mensagem ou uma mensagem completa pode permanecer armazenada em buffer na memória antes de ser enviada.</span><span class="sxs-lookup"><span data-stu-id="339e4-128">The maximum interval of time that a chunk of a message or a full message can remain buffered in memory before being sent out.</span></span>  
  
### <a name="maxpendingaccepts"></a><span data-ttu-id="339e4-129">MaxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="339e4-129">MaxPendingAccepts</span></span>  
 <span data-ttu-id="339e4-130">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="339e4-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="339e4-131">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="339e4-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="339e4-132">O número máximo de pendente assíncrono aceita threads que estão disponíveis para processar conexões de entrada no serviço.</span><span class="sxs-lookup"><span data-stu-id="339e4-132">The maximum number of pending asynchronous accept threads that are available for processing incoming connections on the service.</span></span>  
  
### <a name="maxpendingconnections"></a><span data-ttu-id="339e4-133">MaxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="339e4-133">MaxPendingConnections</span></span>  
 <span data-ttu-id="339e4-134">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="339e4-134">Data type: sint32</span></span>  
  
 <span data-ttu-id="339e4-135">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="339e4-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="339e4-136">O número máximo de conexões pendentes.</span><span class="sxs-lookup"><span data-stu-id="339e4-136">The maximum number of pending connections.</span></span>  
  
### <a name="transfermode"></a><span data-ttu-id="339e4-137">transferMode</span><span class="sxs-lookup"><span data-stu-id="339e4-137">TransferMode</span></span>  
 <span data-ttu-id="339e4-138">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="339e4-138">Data type: string</span></span>  
  
 <span data-ttu-id="339e4-139">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="339e4-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="339e4-140">Um valor que especifica se as mensagens são armazenadas em buffer ou transmitidas em fluxo com o transporte orientado à conexão.</span><span class="sxs-lookup"><span data-stu-id="339e4-140">A value that specifies whether the messages are buffered or streamed with the connection-oriented transport.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="339e4-141">Requisitos</span><span class="sxs-lookup"><span data-stu-id="339e4-141">Requirements</span></span>  
  
|<span data-ttu-id="339e4-142">MOF</span><span class="sxs-lookup"><span data-stu-id="339e4-142">MOF</span></span>|<span data-ttu-id="339e4-143">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="339e4-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="339e4-144">Namespace</span><span class="sxs-lookup"><span data-stu-id="339e4-144">Namespace</span></span>|<span data-ttu-id="339e4-145">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="339e4-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="339e4-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="339e4-146">See Also</span></span>  
 <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>
