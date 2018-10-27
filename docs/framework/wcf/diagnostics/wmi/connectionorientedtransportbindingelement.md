---
title: ConnectionOrientedTransportBindingElement
ms.date: 03/30/2017
ms.assetid: c1308313-f0e2-49e6-977d-6b4ce9ad35d1
ms.openlocfilehash: 49f030c05f02280d483ac2a836cbe75716b7b5cc
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50185048"
---
# <a name="connectionorientedtransportbindingelement"></a><span data-ttu-id="d91db-102">ConnectionOrientedTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="d91db-102">ConnectionOrientedTransportBindingElement</span></span>
<span data-ttu-id="d91db-103">ConnectionOrientedTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="d91db-103">ConnectionOrientedTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d91db-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d91db-104">Syntax</span></span>  
  
```csharp
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
  
## <a name="methods"></a><span data-ttu-id="d91db-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="d91db-105">Methods</span></span>  
 <span data-ttu-id="d91db-106">A classe ConnectionOrientedTransportBindingElement não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="d91db-106">The ConnectionOrientedTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="d91db-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="d91db-107">Properties</span></span>  
 <span data-ttu-id="d91db-108">A classe ConnectionOrientedTransportBindingElement tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="d91db-108">The ConnectionOrientedTransportBindingElement class has the following properties:</span></span>  
  
### <a name="channelinitializationtimeout"></a><span data-ttu-id="d91db-109">channelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="d91db-109">ChannelInitializationTimeout</span></span>  
 <span data-ttu-id="d91db-110">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="d91db-110">Data type: datetime</span></span>  
  
 <span data-ttu-id="d91db-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="d91db-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d91db-112">O timespan que especifica quanto tempo a inicialização do canal tem para ser concluída antes do tempo limite.</span><span class="sxs-lookup"><span data-stu-id="d91db-112">The timespan that specifies how long the channel initialization has to complete before timing out.</span></span>  
  
### <a name="connectionbuffersize"></a><span data-ttu-id="d91db-113">connectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="d91db-113">ConnectionBufferSize</span></span>  
 <span data-ttu-id="d91db-114">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="d91db-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="d91db-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="d91db-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d91db-116">O tamanho do buffer usado para transmitir uma parte da mensagem serializada na conexão do cliente ou do serviço.</span><span class="sxs-lookup"><span data-stu-id="d91db-116">The size of the buffer used to transmit a chunk of the serialized message on the wire from the client or service.</span></span>  
  
### <a name="hostnamecomparisonmode"></a><span data-ttu-id="d91db-117">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="d91db-117">HostNameComparisonMode</span></span>  
 <span data-ttu-id="d91db-118">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="d91db-118">Data type: string</span></span>  
  
 <span data-ttu-id="d91db-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="d91db-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d91db-120">Um valor que indica se o nome do host é usado para alcançar o serviço ao fazer a correspondência no URI.</span><span class="sxs-lookup"><span data-stu-id="d91db-120">A value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>  
  
### <a name="maxbuffersize"></a><span data-ttu-id="d91db-121">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="d91db-121">MaxBufferSize</span></span>  
 <span data-ttu-id="d91db-122">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="d91db-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="d91db-123">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="d91db-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d91db-124">O tamanho máximo do buffer a usar.</span><span class="sxs-lookup"><span data-stu-id="d91db-124">The maximum size of the buffer to use.</span></span>  
  
### <a name="maxoutputdelay"></a><span data-ttu-id="d91db-125">maxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="d91db-125">MaxOutputDelay</span></span>  
 <span data-ttu-id="d91db-126">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="d91db-126">Data type: datetime</span></span>  
  
 <span data-ttu-id="d91db-127">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="d91db-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d91db-128">O intervalo máximo de tempo que uma parte de uma mensagem ou uma mensagem completa pode permanecer armazenada em buffer na memória antes de serem enviados.</span><span class="sxs-lookup"><span data-stu-id="d91db-128">The maximum interval of time that a chunk of a message or a full message can remain buffered in memory before being sent out.</span></span>  
  
### <a name="maxpendingaccepts"></a><span data-ttu-id="d91db-129">maxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="d91db-129">MaxPendingAccepts</span></span>  
 <span data-ttu-id="d91db-130">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="d91db-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="d91db-131">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="d91db-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d91db-132">O número máximo de pendente assíncrono aceita threads que estão disponíveis para processar conexões de entrada no serviço.</span><span class="sxs-lookup"><span data-stu-id="d91db-132">The maximum number of pending asynchronous accept threads that are available for processing incoming connections on the service.</span></span>  
  
### <a name="maxpendingconnections"></a><span data-ttu-id="d91db-133">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="d91db-133">MaxPendingConnections</span></span>  
 <span data-ttu-id="d91db-134">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="d91db-134">Data type: sint32</span></span>  
  
 <span data-ttu-id="d91db-135">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="d91db-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d91db-136">O número máximo de conexões pendentes.</span><span class="sxs-lookup"><span data-stu-id="d91db-136">The maximum number of pending connections.</span></span>  
  
### <a name="transfermode"></a><span data-ttu-id="d91db-137">transferMode</span><span class="sxs-lookup"><span data-stu-id="d91db-137">TransferMode</span></span>  
 <span data-ttu-id="d91db-138">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="d91db-138">Data type: string</span></span>  
  
 <span data-ttu-id="d91db-139">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="d91db-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d91db-140">Um valor que especifica se as mensagens são armazenadas em buffer ou transmitidas com o transporte orientado a conexão.</span><span class="sxs-lookup"><span data-stu-id="d91db-140">A value that specifies whether the messages are buffered or streamed with the connection-oriented transport.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d91db-141">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d91db-141">Requirements</span></span>  
  
|<span data-ttu-id="d91db-142">MOF</span><span class="sxs-lookup"><span data-stu-id="d91db-142">MOF</span></span>|<span data-ttu-id="d91db-143">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="d91db-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="d91db-144">Namespace</span><span class="sxs-lookup"><span data-stu-id="d91db-144">Namespace</span></span>|<span data-ttu-id="d91db-145">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="d91db-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d91db-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d91db-146">See Also</span></span>  
 <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>
