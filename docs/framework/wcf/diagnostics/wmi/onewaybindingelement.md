---
title: OneWayBindingElement
ms.date: 03/30/2017
ms.assetid: 5c7e17c3-39b9-4214-ae08-9e6141734305
ms.openlocfilehash: 34220a3651819978f5f597fdc67d54630ec5e059
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50195808"
---
# <a name="onewaybindingelement"></a><span data-ttu-id="828eb-102">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="828eb-102">OneWayBindingElement</span></span>
<span data-ttu-id="828eb-103">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="828eb-103">OneWayBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="828eb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="828eb-104">Syntax</span></span>  
  
```csharp
class OneWayBindingElement : BindingElement  
{  
  ChannelPoolSettings ChannelPoolSettings;  
  sint32 MaxAcceptedChannels;  
  boolean PacketRoutable;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="828eb-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="828eb-105">Methods</span></span>  
 <span data-ttu-id="828eb-106">A classe OneWayBindingElement não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="828eb-106">The OneWayBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="828eb-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="828eb-107">Properties</span></span>  
 <span data-ttu-id="828eb-108">A classe OneWayBindingElement tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="828eb-108">The OneWayBindingElement class has the following properties:</span></span>  
  
### <a name="channelpoolsettings"></a><span data-ttu-id="828eb-109">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="828eb-109">ChannelPoolSettings</span></span>  
 <span data-ttu-id="828eb-110">Tipo de dados: ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="828eb-110">Data type: ChannelPoolSettings</span></span>  
  
 <span data-ttu-id="828eb-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="828eb-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="828eb-112">As configurações do pool de canal.</span><span class="sxs-lookup"><span data-stu-id="828eb-112">The channel pool settings.</span></span>  
  
### <a name="maxacceptedchannels"></a><span data-ttu-id="828eb-113">MaxAcceptedChannels</span><span class="sxs-lookup"><span data-stu-id="828eb-113">MaxAcceptedChannels</span></span>  
 <span data-ttu-id="828eb-114">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="828eb-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="828eb-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="828eb-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="828eb-116">O número máximo de canais aceitos.</span><span class="sxs-lookup"><span data-stu-id="828eb-116">The maximum number of accepted channels.</span></span>  
  
### <a name="packetroutable"></a><span data-ttu-id="828eb-117">PacketRoutable</span><span class="sxs-lookup"><span data-stu-id="828eb-117">PacketRoutable</span></span>  
 <span data-ttu-id="828eb-118">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="828eb-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="828eb-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="828eb-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="828eb-120">Um valor que indica se o pacote é roteável.</span><span class="sxs-lookup"><span data-stu-id="828eb-120">A value that indicates whether the packet is routable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="828eb-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="828eb-121">Requirements</span></span>  
  
|<span data-ttu-id="828eb-122">MOF</span><span class="sxs-lookup"><span data-stu-id="828eb-122">MOF</span></span>|<span data-ttu-id="828eb-123">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="828eb-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="828eb-124">Namespace</span><span class="sxs-lookup"><span data-stu-id="828eb-124">Namespace</span></span>|<span data-ttu-id="828eb-125">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="828eb-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="828eb-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="828eb-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.OneWayBindingElement>
