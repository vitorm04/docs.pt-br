---
title: ReliableSessionBindingElement
ms.date: 03/30/2017
ms.assetid: effda125-b8d3-4de6-8c0e-f59f5ea8f6eb
ms.openlocfilehash: b0a621da43402777cc620f1876bd968a72bb8c12
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61962910"
---
# <a name="reliablesessionbindingelement"></a><span data-ttu-id="af9b7-102">ReliableSessionBindingElement</span><span class="sxs-lookup"><span data-stu-id="af9b7-102">ReliableSessionBindingElement</span></span>
<span data-ttu-id="af9b7-103">ReliableSessionBindingElement</span><span class="sxs-lookup"><span data-stu-id="af9b7-103">ReliableSessionBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af9b7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="af9b7-104">Syntax</span></span>  
  
```csharp
class ReliableSessionBindingElement : BindingElement  
{  
  datetime AcknowledgementInterval;  
  boolean FlowControlEnabled;  
  datetime InactivityTimeout;  
  sint32 MaxPendingChannels;  
  sint32 MaxRetryCount;  
  sint32 MaxTransferWindowSize;  
  boolean Ordered;  
  integer ReliableMessagingVersion;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="af9b7-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="af9b7-105">Methods</span></span>  
 <span data-ttu-id="af9b7-106">A classe ReliableSessionBindingElement não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="af9b7-106">The ReliableSessionBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="af9b7-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="af9b7-107">Properties</span></span>  
 <span data-ttu-id="af9b7-108">A classe ReliableSessionBindingElement tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="af9b7-108">The ReliableSessionBindingElement class has the following properties:</span></span>  
  
### <a name="acknowledgementinterval"></a><span data-ttu-id="af9b7-109">AcknowledgementInterval</span><span class="sxs-lookup"><span data-stu-id="af9b7-109">AcknowledgementInterval</span></span>  
 <span data-ttu-id="af9b7-110">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="af9b7-110">Data type: datetime</span></span>  
  
 <span data-ttu-id="af9b7-111">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="af9b7-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="af9b7-112">O intervalo de tempo que um destino aguarda antes de enviar uma confirmação para a origem da mensagem em canais confiáveis criados pela fábrica.</span><span class="sxs-lookup"><span data-stu-id="af9b7-112">The interval of time that a destination waits before sending an acknowledgement to the message source on reliable channels that are created by the factory.</span></span>  
  
### <a name="flowcontrolenabled"></a><span data-ttu-id="af9b7-113">FlowControlEnabled</span><span class="sxs-lookup"><span data-stu-id="af9b7-113">FlowControlEnabled</span></span>  
 <span data-ttu-id="af9b7-114">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="af9b7-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="af9b7-115">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="af9b7-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="af9b7-116">Um valor booliano que especifica se o controle de fluxo está habilitado.</span><span class="sxs-lookup"><span data-stu-id="af9b7-116">A Boolean value that specifies whether flow control is enabled.</span></span>  
  
### <a name="inactivitytimeout"></a><span data-ttu-id="af9b7-117">InactivityTimeout</span><span class="sxs-lookup"><span data-stu-id="af9b7-117">InactivityTimeout</span></span>  
 <span data-ttu-id="af9b7-118">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="af9b7-118">Data type: datetime</span></span>  
  
 <span data-ttu-id="af9b7-119">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="af9b7-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="af9b7-120">Especifica a duração máxima que o canal vai permitir que a outra parte da comunicação para não enviar todas as mensagens antes de gerar falha no canal.</span><span class="sxs-lookup"><span data-stu-id="af9b7-120">Specifies the maximum duration the channel is going to allow the other communicating party not to send any messages before faulting the channel.</span></span>  
  
### <a name="maxpendingchannels"></a><span data-ttu-id="af9b7-121">MaxPendingChannels</span><span class="sxs-lookup"><span data-stu-id="af9b7-121">MaxPendingChannels</span></span>  
 <span data-ttu-id="af9b7-122">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="af9b7-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="af9b7-123">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="af9b7-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="af9b7-124">O número máximo de canais que podem aguardar para serem aceitos no ouvinte.</span><span class="sxs-lookup"><span data-stu-id="af9b7-124">The maximum number of channels that can wait to be accepted on the listener.</span></span>  
  
### <a name="maxretrycount"></a><span data-ttu-id="af9b7-125">MaxRetryCount</span><span class="sxs-lookup"><span data-stu-id="af9b7-125">MaxRetryCount</span></span>  
 <span data-ttu-id="af9b7-126">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="af9b7-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="af9b7-127">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="af9b7-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="af9b7-128">O número máximo de vezes que um canal confiável tenta retransmitir uma mensagem que não recebeu confirmação, chamando `Send` em seu canal subjacente.</span><span class="sxs-lookup"><span data-stu-id="af9b7-128">The maximum number of times a reliable channel attempts to retransmit a message it has not received an acknowledgement for, by calling `Send` on its underlying channel.</span></span>  
  
### <a name="maxtransferwindowsize"></a><span data-ttu-id="af9b7-129">MaxTransferWindowSize</span><span class="sxs-lookup"><span data-stu-id="af9b7-129">MaxTransferWindowSize</span></span>  
 <span data-ttu-id="af9b7-130">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="af9b7-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="af9b7-131">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="af9b7-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="af9b7-132">O tamanho da janela de transferência máxima para a sessão confiável.</span><span class="sxs-lookup"><span data-stu-id="af9b7-132">The maximum transfer window size for the reliable session.</span></span>  
  
### <a name="ordered"></a><span data-ttu-id="af9b7-133">Ordenada</span><span class="sxs-lookup"><span data-stu-id="af9b7-133">Ordered</span></span>  
 <span data-ttu-id="af9b7-134">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="af9b7-134">Data type: boolean</span></span>  
  
 <span data-ttu-id="af9b7-135">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="af9b7-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="af9b7-136">Um valor booliano que especifica se as mensagens são garantidas de chegar na ordem em que foram enviadas.</span><span class="sxs-lookup"><span data-stu-id="af9b7-136">A Boolean value that specifies whether messages are guaranteed to arrive in the order they were sent.</span></span>  
  
### <a name="reliablemessagingversion"></a><span data-ttu-id="af9b7-137">ReliableMessagingVersion</span><span class="sxs-lookup"><span data-stu-id="af9b7-137">ReliableMessagingVersion</span></span>  
 <span data-ttu-id="af9b7-138">Tipo de dados: número inteiro</span><span class="sxs-lookup"><span data-stu-id="af9b7-138">Data type: integer</span></span>  
  
 <span data-ttu-id="af9b7-139">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="af9b7-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="af9b7-140">Um inteiro que especifica a versão do protocolo WS-ReliableMessaging usada na sessão confiável.</span><span class="sxs-lookup"><span data-stu-id="af9b7-140">An integer that specifies the WS-ReliableMessaging protocol version used in the reliable session.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af9b7-141">Requisitos</span><span class="sxs-lookup"><span data-stu-id="af9b7-141">Requirements</span></span>  
  
|<span data-ttu-id="af9b7-142">MOF</span><span class="sxs-lookup"><span data-stu-id="af9b7-142">MOF</span></span>|<span data-ttu-id="af9b7-143">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="af9b7-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="af9b7-144">Namespace</span><span class="sxs-lookup"><span data-stu-id="af9b7-144">Namespace</span></span>|<span data-ttu-id="af9b7-145">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="af9b7-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="af9b7-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="af9b7-146">See also</span></span>

- <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>
