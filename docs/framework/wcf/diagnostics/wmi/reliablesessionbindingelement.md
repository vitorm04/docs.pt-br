---
title: ReliableSessionBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: effda125-b8d3-4de6-8c0e-f59f5ea8f6eb
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3f4aff60c96db5071d41a3f011019b05746f0c96
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="reliablesessionbindingelement"></a><span data-ttu-id="79cd9-102">ReliableSessionBindingElement</span><span class="sxs-lookup"><span data-stu-id="79cd9-102">ReliableSessionBindingElement</span></span>
<span data-ttu-id="79cd9-103">ReliableSessionBindingElement</span><span class="sxs-lookup"><span data-stu-id="79cd9-103">ReliableSessionBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79cd9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="79cd9-104">Syntax</span></span>  
  
```  
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
  
## <a name="methods"></a><span data-ttu-id="79cd9-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="79cd9-105">Methods</span></span>  
 <span data-ttu-id="79cd9-106">A classe ReliableSessionBindingElement não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="79cd9-106">The ReliableSessionBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="79cd9-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="79cd9-107">Properties</span></span>  
 <span data-ttu-id="79cd9-108">A classe ReliableSessionBindingElement tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="79cd9-108">The ReliableSessionBindingElement class has the following properties:</span></span>  
  
### <a name="acknowledgementinterval"></a><span data-ttu-id="79cd9-109">AcknowledgementInterval</span><span class="sxs-lookup"><span data-stu-id="79cd9-109">AcknowledgementInterval</span></span>  
 <span data-ttu-id="79cd9-110">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="79cd9-110">Data type: datetime</span></span>  
  
 <span data-ttu-id="79cd9-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="79cd9-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="79cd9-112">O intervalo de tempo que um destino aguarda antes de enviar uma confirmação para a origem da mensagem em canais confiáveis que são criados pela fábrica.</span><span class="sxs-lookup"><span data-stu-id="79cd9-112">The interval of time that a destination waits before sending an acknowledgement to the message source on reliable channels that are created by the factory.</span></span>  
  
### <a name="flowcontrolenabled"></a><span data-ttu-id="79cd9-113">FlowControlEnabled</span><span class="sxs-lookup"><span data-stu-id="79cd9-113">FlowControlEnabled</span></span>  
 <span data-ttu-id="79cd9-114">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="79cd9-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="79cd9-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="79cd9-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="79cd9-116">Um valor booleano que especifica se o controle de fluxo está habilitado.</span><span class="sxs-lookup"><span data-stu-id="79cd9-116">A Boolean value that specifies whether flow control is enabled.</span></span>  
  
### <a name="inactivitytimeout"></a><span data-ttu-id="79cd9-117">InactivityTimeout</span><span class="sxs-lookup"><span data-stu-id="79cd9-117">InactivityTimeout</span></span>  
 <span data-ttu-id="79cd9-118">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="79cd9-118">Data type: datetime</span></span>  
  
 <span data-ttu-id="79cd9-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="79cd9-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="79cd9-120">Especifica a duração máxima que o canal vai permitir que a outra parte da comunicação para não enviar nenhuma mensagem antes de haver falha no canal.</span><span class="sxs-lookup"><span data-stu-id="79cd9-120">Specifies the maximum duration the channel is going to allow the other communicating party not to send any messages before faulting the channel.</span></span>  
  
### <a name="maxpendingchannels"></a><span data-ttu-id="79cd9-121">MaxPendingChannels</span><span class="sxs-lookup"><span data-stu-id="79cd9-121">MaxPendingChannels</span></span>  
 <span data-ttu-id="79cd9-122">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="79cd9-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="79cd9-123">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="79cd9-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="79cd9-124">O número máximo de canais que podem aguardar para serem aceitos no ouvinte.</span><span class="sxs-lookup"><span data-stu-id="79cd9-124">The maximum number of channels that can wait to be accepted on the listener.</span></span>  
  
### <a name="maxretrycount"></a><span data-ttu-id="79cd9-125">MaxRetryCount</span><span class="sxs-lookup"><span data-stu-id="79cd9-125">MaxRetryCount</span></span>  
 <span data-ttu-id="79cd9-126">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="79cd9-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="79cd9-127">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="79cd9-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="79cd9-128">O número máximo de vezes que um canal confiável tenta retransmitir uma mensagem não recebeu confirmação, chamando `Send` em seu canal subjacente.</span><span class="sxs-lookup"><span data-stu-id="79cd9-128">The maximum number of times a reliable channel attempts to retransmit a message it has not received an acknowledgement for, by calling `Send` on its underlying channel.</span></span>  
  
### <a name="maxtransferwindowsize"></a><span data-ttu-id="79cd9-129">MaxTransferWindowSize</span><span class="sxs-lookup"><span data-stu-id="79cd9-129">MaxTransferWindowSize</span></span>  
 <span data-ttu-id="79cd9-130">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="79cd9-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="79cd9-131">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="79cd9-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="79cd9-132">O tamanho da janela de transferência máxima para a sessão confiável.</span><span class="sxs-lookup"><span data-stu-id="79cd9-132">The maximum transfer window size for the reliable session.</span></span>  
  
### <a name="ordered"></a><span data-ttu-id="79cd9-133">Ordenada</span><span class="sxs-lookup"><span data-stu-id="79cd9-133">Ordered</span></span>  
 <span data-ttu-id="79cd9-134">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="79cd9-134">Data type: boolean</span></span>  
  
 <span data-ttu-id="79cd9-135">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="79cd9-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="79cd9-136">Um valor booleano que especifica se as mensagens são garantidas de chegar na ordem em que foram enviadas.</span><span class="sxs-lookup"><span data-stu-id="79cd9-136">A Boolean value that specifies whether messages are guaranteed to arrive in the order they were sent.</span></span>  
  
### <a name="reliablemessagingversion"></a><span data-ttu-id="79cd9-137">ReliableMessagingVersion</span><span class="sxs-lookup"><span data-stu-id="79cd9-137">ReliableMessagingVersion</span></span>  
 <span data-ttu-id="79cd9-138">Tipo de dados: número inteiro</span><span class="sxs-lookup"><span data-stu-id="79cd9-138">Data type: integer</span></span>  
  
 <span data-ttu-id="79cd9-139">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="79cd9-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="79cd9-140">Um inteiro que especifica a versão do protocolo WS-ReliableMessaging usada na sessão confiável.</span><span class="sxs-lookup"><span data-stu-id="79cd9-140">An integer that specifies the WS-ReliableMessaging protocol version used in the reliable session.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79cd9-141">Requisitos</span><span class="sxs-lookup"><span data-stu-id="79cd9-141">Requirements</span></span>  
  
|<span data-ttu-id="79cd9-142">MOF</span><span class="sxs-lookup"><span data-stu-id="79cd9-142">MOF</span></span>|<span data-ttu-id="79cd9-143">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="79cd9-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="79cd9-144">Namespace</span><span class="sxs-lookup"><span data-stu-id="79cd9-144">Namespace</span></span>|<span data-ttu-id="79cd9-145">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="79cd9-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="79cd9-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="79cd9-146">See Also</span></span>  
 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>
