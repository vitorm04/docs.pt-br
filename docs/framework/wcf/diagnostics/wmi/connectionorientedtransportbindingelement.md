---
title: ConnectionOrientedTransportBindingElement
ms.date: 03/30/2017
ms.assetid: c1308313-f0e2-49e6-977d-6b4ce9ad35d1
ms.openlocfilehash: 04e6abc5941ec99769ff2c15d47881b60e81d2e0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62048387"
---
# <a name="connectionorientedtransportbindingelement"></a><span data-ttu-id="c7be7-102">ConnectionOrientedTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="c7be7-102">ConnectionOrientedTransportBindingElement</span></span>
<span data-ttu-id="c7be7-103">ConnectionOrientedTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="c7be7-103">ConnectionOrientedTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7be7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c7be7-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="c7be7-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="c7be7-105">Methods</span></span>  
 <span data-ttu-id="c7be7-106">A classe ConnectionOrientedTransportBindingElement não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="c7be7-106">The ConnectionOrientedTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="c7be7-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="c7be7-107">Properties</span></span>  
 <span data-ttu-id="c7be7-108">A classe ConnectionOrientedTransportBindingElement tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="c7be7-108">The ConnectionOrientedTransportBindingElement class has the following properties:</span></span>  
  
### <a name="channelinitializationtimeout"></a><span data-ttu-id="c7be7-109">ChannelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="c7be7-109">ChannelInitializationTimeout</span></span>  
 <span data-ttu-id="c7be7-110">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="c7be7-110">Data type: datetime</span></span>  
  
 <span data-ttu-id="c7be7-111">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="c7be7-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c7be7-112">O timespan que especifica quanto tempo a inicialização do canal tem para ser concluída antes do tempo limite.</span><span class="sxs-lookup"><span data-stu-id="c7be7-112">The timespan that specifies how long the channel initialization has to complete before timing out.</span></span>  
  
### <a name="connectionbuffersize"></a><span data-ttu-id="c7be7-113">ConnectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="c7be7-113">ConnectionBufferSize</span></span>  
 <span data-ttu-id="c7be7-114">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="c7be7-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="c7be7-115">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="c7be7-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c7be7-116">O tamanho do buffer usado para transmitir uma parte da mensagem serializada na conexão do cliente ou do serviço.</span><span class="sxs-lookup"><span data-stu-id="c7be7-116">The size of the buffer used to transmit a chunk of the serialized message on the wire from the client or service.</span></span>  
  
### <a name="hostnamecomparisonmode"></a><span data-ttu-id="c7be7-117">HostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="c7be7-117">HostNameComparisonMode</span></span>  
 <span data-ttu-id="c7be7-118">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="c7be7-118">Data type: string</span></span>  
  
 <span data-ttu-id="c7be7-119">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="c7be7-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c7be7-120">Um valor que indica se o nome do host é usado para alcançar o serviço ao fazer a correspondência no URI.</span><span class="sxs-lookup"><span data-stu-id="c7be7-120">A value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>  
  
### <a name="maxbuffersize"></a><span data-ttu-id="c7be7-121">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="c7be7-121">MaxBufferSize</span></span>  
 <span data-ttu-id="c7be7-122">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="c7be7-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="c7be7-123">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="c7be7-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c7be7-124">O tamanho máximo do buffer a usar.</span><span class="sxs-lookup"><span data-stu-id="c7be7-124">The maximum size of the buffer to use.</span></span>  
  
### <a name="maxoutputdelay"></a><span data-ttu-id="c7be7-125">MaxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="c7be7-125">MaxOutputDelay</span></span>  
 <span data-ttu-id="c7be7-126">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="c7be7-126">Data type: datetime</span></span>  
  
 <span data-ttu-id="c7be7-127">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="c7be7-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c7be7-128">O intervalo máximo de tempo que uma parte de uma mensagem ou uma mensagem completa pode permanecer armazenada em buffer na memória antes de serem enviados.</span><span class="sxs-lookup"><span data-stu-id="c7be7-128">The maximum interval of time that a chunk of a message or a full message can remain buffered in memory before being sent out.</span></span>  
  
### <a name="maxpendingaccepts"></a><span data-ttu-id="c7be7-129">MaxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="c7be7-129">MaxPendingAccepts</span></span>  
 <span data-ttu-id="c7be7-130">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="c7be7-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="c7be7-131">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="c7be7-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c7be7-132">O número máximo de pendente assíncrono aceita threads que estão disponíveis para processar conexões de entrada no serviço.</span><span class="sxs-lookup"><span data-stu-id="c7be7-132">The maximum number of pending asynchronous accept threads that are available for processing incoming connections on the service.</span></span>  
  
### <a name="maxpendingconnections"></a><span data-ttu-id="c7be7-133">MaxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="c7be7-133">MaxPendingConnections</span></span>  
 <span data-ttu-id="c7be7-134">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="c7be7-134">Data type: sint32</span></span>  
  
 <span data-ttu-id="c7be7-135">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="c7be7-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c7be7-136">O número máximo de conexões pendentes.</span><span class="sxs-lookup"><span data-stu-id="c7be7-136">The maximum number of pending connections.</span></span>  
  
### <a name="transfermode"></a><span data-ttu-id="c7be7-137">TransferMode</span><span class="sxs-lookup"><span data-stu-id="c7be7-137">TransferMode</span></span>  
 <span data-ttu-id="c7be7-138">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="c7be7-138">Data type: string</span></span>  
  
 <span data-ttu-id="c7be7-139">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="c7be7-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c7be7-140">Um valor que especifica se as mensagens são armazenadas em buffer ou transmitidas com o transporte orientado a conexão.</span><span class="sxs-lookup"><span data-stu-id="c7be7-140">A value that specifies whether the messages are buffered or streamed with the connection-oriented transport.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7be7-141">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c7be7-141">Requirements</span></span>  
  
|<span data-ttu-id="c7be7-142">MOF</span><span class="sxs-lookup"><span data-stu-id="c7be7-142">MOF</span></span>|<span data-ttu-id="c7be7-143">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="c7be7-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="c7be7-144">Namespace</span><span class="sxs-lookup"><span data-stu-id="c7be7-144">Namespace</span></span>|<span data-ttu-id="c7be7-145">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="c7be7-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c7be7-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c7be7-146">See also</span></span>

- <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>
