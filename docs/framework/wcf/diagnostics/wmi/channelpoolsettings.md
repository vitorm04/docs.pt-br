---
title: ChannelPoolSettings
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d3f475bd-f780-4bbe-b291-339387322964
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e97e934673efbc6d0f72751c7cb1de6fba84a141
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="channelpoolsettings"></a><span data-ttu-id="a7fdc-102">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="a7fdc-102">ChannelPoolSettings</span></span>
<span data-ttu-id="a7fdc-103">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="a7fdc-103">ChannelPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7fdc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a7fdc-104">Syntax</span></span>  
  
```  
class ChannelPoolSettings  
{  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundChannelsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="a7fdc-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="a7fdc-105">Methods</span></span>  
 <span data-ttu-id="a7fdc-106">A classe ChannelPoolSettings não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="a7fdc-106">The ChannelPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="a7fdc-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="a7fdc-107">Properties</span></span>  
 <span data-ttu-id="a7fdc-108">A classe ChannelPoolSettings tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="a7fdc-108">The ChannelPoolSettings class has the following properties:</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="a7fdc-109">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="a7fdc-109">IdleTimeout</span></span>  
 <span data-ttu-id="a7fdc-110">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="a7fdc-110">Data type: datetime</span></span>  
  
 <span data-ttu-id="a7fdc-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="a7fdc-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a7fdc-112">O tempo máximo que a conexão pode ficar ociosa antes de ser desconectada.</span><span class="sxs-lookup"><span data-stu-id="a7fdc-112">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="leasetimeout"></a><span data-ttu-id="a7fdc-113">LeaseTimeout</span><span class="sxs-lookup"><span data-stu-id="a7fdc-113">LeaseTimeout</span></span>  
 <span data-ttu-id="a7fdc-114">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="a7fdc-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="a7fdc-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="a7fdc-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a7fdc-116">O tempo máximo para uma operação de concessão seja concluída antes de atingir o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="a7fdc-116">The maximum time for a lease operation to complete before timing out.</span></span>  
  
### <a name="maxoutboundchannelsperendpoint"></a><span data-ttu-id="a7fdc-117">MaxOutboundChannelsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="a7fdc-117">MaxOutboundChannelsPerEndpoint</span></span>  
 <span data-ttu-id="a7fdc-118">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="a7fdc-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="a7fdc-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="a7fdc-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a7fdc-120">O número máximo de canais de saída para cada ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="a7fdc-120">The maximum number of outbound channels for each endpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7fdc-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a7fdc-121">Requirements</span></span>  
  
|<span data-ttu-id="a7fdc-122">MOF</span><span class="sxs-lookup"><span data-stu-id="a7fdc-122">MOF</span></span>|<span data-ttu-id="a7fdc-123">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="a7fdc-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="a7fdc-124">Namespace</span><span class="sxs-lookup"><span data-stu-id="a7fdc-124">Namespace</span></span>|<span data-ttu-id="a7fdc-125">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="a7fdc-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a7fdc-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a7fdc-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.ChannelPoolSettings>
