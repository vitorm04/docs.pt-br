---
title: ConnectionOrientedTransportBindingElement
ms.date: 03/30/2017
ms.assetid: c1308313-f0e2-49e6-977d-6b4ce9ad35d1
ms.openlocfilehash: 04e6abc5941ec99769ff2c15d47881b60e81d2e0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59973519"
---
# <a name="connectionorientedtransportbindingelement"></a><span data-ttu-id="de7fb-102">ConnectionOrientedTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="de7fb-102">ConnectionOrientedTransportBindingElement</span></span>
<span data-ttu-id="de7fb-103">ConnectionOrientedTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="de7fb-103">ConnectionOrientedTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de7fb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="de7fb-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="de7fb-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="de7fb-105">Methods</span></span>  
 <span data-ttu-id="de7fb-106">A classe ConnectionOrientedTransportBindingElement não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="de7fb-106">The ConnectionOrientedTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="de7fb-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="de7fb-107">Properties</span></span>  
 <span data-ttu-id="de7fb-108">A classe ConnectionOrientedTransportBindingElement tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="de7fb-108">The ConnectionOrientedTransportBindingElement class has the following properties:</span></span>  
  
### <a name="channelinitializationtimeout"></a><span data-ttu-id="de7fb-109">ChannelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="de7fb-109">ChannelInitializationTimeout</span></span>  
 <span data-ttu-id="de7fb-110">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="de7fb-110">Data type: datetime</span></span>  
  
 <span data-ttu-id="de7fb-111">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="de7fb-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="de7fb-112">O timespan que especifica quanto tempo a inicialização do canal tem para ser concluída antes do tempo limite.</span><span class="sxs-lookup"><span data-stu-id="de7fb-112">The timespan that specifies how long the channel initialization has to complete before timing out.</span></span>  
  
### <a name="connectionbuffersize"></a><span data-ttu-id="de7fb-113">ConnectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="de7fb-113">ConnectionBufferSize</span></span>  
 <span data-ttu-id="de7fb-114">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="de7fb-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="de7fb-115">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="de7fb-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="de7fb-116">O tamanho do buffer usado para transmitir uma parte da mensagem serializada na conexão do cliente ou do serviço.</span><span class="sxs-lookup"><span data-stu-id="de7fb-116">The size of the buffer used to transmit a chunk of the serialized message on the wire from the client or service.</span></span>  
  
### <a name="hostnamecomparisonmode"></a><span data-ttu-id="de7fb-117">HostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="de7fb-117">HostNameComparisonMode</span></span>  
 <span data-ttu-id="de7fb-118">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="de7fb-118">Data type: string</span></span>  
  
 <span data-ttu-id="de7fb-119">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="de7fb-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="de7fb-120">Um valor que indica se o nome do host é usado para alcançar o serviço ao fazer a correspondência no URI.</span><span class="sxs-lookup"><span data-stu-id="de7fb-120">A value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>  
  
### <a name="maxbuffersize"></a><span data-ttu-id="de7fb-121">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="de7fb-121">MaxBufferSize</span></span>  
 <span data-ttu-id="de7fb-122">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="de7fb-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="de7fb-123">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="de7fb-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="de7fb-124">O tamanho máximo do buffer a usar.</span><span class="sxs-lookup"><span data-stu-id="de7fb-124">The maximum size of the buffer to use.</span></span>  
  
### <a name="maxoutputdelay"></a><span data-ttu-id="de7fb-125">MaxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="de7fb-125">MaxOutputDelay</span></span>  
 <span data-ttu-id="de7fb-126">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="de7fb-126">Data type: datetime</span></span>  
  
 <span data-ttu-id="de7fb-127">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="de7fb-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="de7fb-128">O intervalo máximo de tempo que uma parte de uma mensagem ou uma mensagem completa pode permanecer armazenada em buffer na memória antes de serem enviados.</span><span class="sxs-lookup"><span data-stu-id="de7fb-128">The maximum interval of time that a chunk of a message or a full message can remain buffered in memory before being sent out.</span></span>  
  
### <a name="maxpendingaccepts"></a><span data-ttu-id="de7fb-129">MaxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="de7fb-129">MaxPendingAccepts</span></span>  
 <span data-ttu-id="de7fb-130">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="de7fb-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="de7fb-131">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="de7fb-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="de7fb-132">O número máximo de pendente assíncrono aceita threads que estão disponíveis para processar conexões de entrada no serviço.</span><span class="sxs-lookup"><span data-stu-id="de7fb-132">The maximum number of pending asynchronous accept threads that are available for processing incoming connections on the service.</span></span>  
  
### <a name="maxpendingconnections"></a><span data-ttu-id="de7fb-133">MaxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="de7fb-133">MaxPendingConnections</span></span>  
 <span data-ttu-id="de7fb-134">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="de7fb-134">Data type: sint32</span></span>  
  
 <span data-ttu-id="de7fb-135">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="de7fb-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="de7fb-136">O número máximo de conexões pendentes.</span><span class="sxs-lookup"><span data-stu-id="de7fb-136">The maximum number of pending connections.</span></span>  
  
### <a name="transfermode"></a><span data-ttu-id="de7fb-137">TransferMode</span><span class="sxs-lookup"><span data-stu-id="de7fb-137">TransferMode</span></span>  
 <span data-ttu-id="de7fb-138">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="de7fb-138">Data type: string</span></span>  
  
 <span data-ttu-id="de7fb-139">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="de7fb-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="de7fb-140">Um valor que especifica se as mensagens são armazenadas em buffer ou transmitidas com o transporte orientado a conexão.</span><span class="sxs-lookup"><span data-stu-id="de7fb-140">A value that specifies whether the messages are buffered or streamed with the connection-oriented transport.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de7fb-141">Requisitos</span><span class="sxs-lookup"><span data-stu-id="de7fb-141">Requirements</span></span>  
  
|<span data-ttu-id="de7fb-142">MOF</span><span class="sxs-lookup"><span data-stu-id="de7fb-142">MOF</span></span>|<span data-ttu-id="de7fb-143">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="de7fb-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="de7fb-144">Namespace</span><span class="sxs-lookup"><span data-stu-id="de7fb-144">Namespace</span></span>|<span data-ttu-id="de7fb-145">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="de7fb-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="de7fb-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="de7fb-146">See also</span></span>

- <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>
