---
title: ChannelPoolSettings
ms.date: 03/30/2017
ms.assetid: d3f475bd-f780-4bbe-b291-339387322964
ms.openlocfilehash: 8900af77d0d385bb68b4b85e1d15be57bb7a8d14
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59972856"
---
# <a name="channelpoolsettings"></a><span data-ttu-id="e0299-102">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="e0299-102">ChannelPoolSettings</span></span>
<span data-ttu-id="e0299-103">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="e0299-103">ChannelPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0299-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e0299-104">Syntax</span></span>  
  
```csharp
class ChannelPoolSettings  
{  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundChannelsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="e0299-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="e0299-105">Methods</span></span>  
 <span data-ttu-id="e0299-106">A classe ChannelPoolSettings não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="e0299-106">The ChannelPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="e0299-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="e0299-107">Properties</span></span>  
 <span data-ttu-id="e0299-108">A classe ChannelPoolSettings tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="e0299-108">The ChannelPoolSettings class has the following properties:</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="e0299-109">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="e0299-109">IdleTimeout</span></span>  
 <span data-ttu-id="e0299-110">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="e0299-110">Data type: datetime</span></span>  
  
 <span data-ttu-id="e0299-111">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="e0299-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e0299-112">O tempo máximo que a conexão pode ficar ociosa antes de ser desconectada.</span><span class="sxs-lookup"><span data-stu-id="e0299-112">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="leasetimeout"></a><span data-ttu-id="e0299-113">LeaseTimeout</span><span class="sxs-lookup"><span data-stu-id="e0299-113">LeaseTimeout</span></span>  
 <span data-ttu-id="e0299-114">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="e0299-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="e0299-115">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="e0299-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e0299-116">O tempo máximo para uma operação seja concluída antes de atingir o tempo limite de concessão.</span><span class="sxs-lookup"><span data-stu-id="e0299-116">The maximum time for a lease operation to complete before timing out.</span></span>  
  
### <a name="maxoutboundchannelsperendpoint"></a><span data-ttu-id="e0299-117">MaxOutboundChannelsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="e0299-117">MaxOutboundChannelsPerEndpoint</span></span>  
 <span data-ttu-id="e0299-118">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="e0299-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="e0299-119">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="e0299-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e0299-120">O número máximo de canais de saída para cada ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="e0299-120">The maximum number of outbound channels for each endpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0299-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e0299-121">Requirements</span></span>  
  
|<span data-ttu-id="e0299-122">MOF</span><span class="sxs-lookup"><span data-stu-id="e0299-122">MOF</span></span>|<span data-ttu-id="e0299-123">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="e0299-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="e0299-124">Namespace</span><span class="sxs-lookup"><span data-stu-id="e0299-124">Namespace</span></span>|<span data-ttu-id="e0299-125">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="e0299-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e0299-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e0299-126">See also</span></span>

- <xref:System.ServiceModel.Channels.ChannelPoolSettings>
