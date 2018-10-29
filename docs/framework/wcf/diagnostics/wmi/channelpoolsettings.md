---
title: ChannelPoolSettings
ms.date: 03/30/2017
ms.assetid: d3f475bd-f780-4bbe-b291-339387322964
ms.openlocfilehash: d763be92243768bce9fdaefcd3e3575effac464b
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50200477"
---
# <a name="channelpoolsettings"></a><span data-ttu-id="0718b-102">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="0718b-102">ChannelPoolSettings</span></span>
<span data-ttu-id="0718b-103">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="0718b-103">ChannelPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0718b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0718b-104">Syntax</span></span>  
  
```csharp
class ChannelPoolSettings  
{  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundChannelsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="0718b-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="0718b-105">Methods</span></span>  
 <span data-ttu-id="0718b-106">A classe ChannelPoolSettings não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="0718b-106">The ChannelPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="0718b-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="0718b-107">Properties</span></span>  
 <span data-ttu-id="0718b-108">A classe ChannelPoolSettings tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="0718b-108">The ChannelPoolSettings class has the following properties:</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="0718b-109">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="0718b-109">IdleTimeout</span></span>  
 <span data-ttu-id="0718b-110">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="0718b-110">Data type: datetime</span></span>  
  
 <span data-ttu-id="0718b-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="0718b-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0718b-112">O tempo máximo que a conexão pode ficar ociosa antes de ser desconectada.</span><span class="sxs-lookup"><span data-stu-id="0718b-112">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="leasetimeout"></a><span data-ttu-id="0718b-113">LeaseTimeout</span><span class="sxs-lookup"><span data-stu-id="0718b-113">LeaseTimeout</span></span>  
 <span data-ttu-id="0718b-114">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="0718b-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="0718b-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="0718b-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0718b-116">O tempo máximo para uma operação seja concluída antes de atingir o tempo limite de concessão.</span><span class="sxs-lookup"><span data-stu-id="0718b-116">The maximum time for a lease operation to complete before timing out.</span></span>  
  
### <a name="maxoutboundchannelsperendpoint"></a><span data-ttu-id="0718b-117">MaxOutboundChannelsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="0718b-117">MaxOutboundChannelsPerEndpoint</span></span>  
 <span data-ttu-id="0718b-118">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="0718b-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="0718b-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="0718b-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0718b-120">O número máximo de canais de saída para cada ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="0718b-120">The maximum number of outbound channels for each endpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0718b-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0718b-121">Requirements</span></span>  
  
|<span data-ttu-id="0718b-122">MOF</span><span class="sxs-lookup"><span data-stu-id="0718b-122">MOF</span></span>|<span data-ttu-id="0718b-123">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="0718b-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="0718b-124">Namespace</span><span class="sxs-lookup"><span data-stu-id="0718b-124">Namespace</span></span>|<span data-ttu-id="0718b-125">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="0718b-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0718b-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0718b-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.ChannelPoolSettings>
