---
title: OneWayBindingElement
ms.date: 03/30/2017
ms.assetid: 5c7e17c3-39b9-4214-ae08-9e6141734305
ms.openlocfilehash: 016ff823eb2c84a9f54c0763edadef1224e31517
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62040035"
---
# <a name="onewaybindingelement"></a><span data-ttu-id="ac6ca-102">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="ac6ca-102">OneWayBindingElement</span></span>
<span data-ttu-id="ac6ca-103">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="ac6ca-103">OneWayBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac6ca-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ac6ca-104">Syntax</span></span>  
  
```csharp
class OneWayBindingElement : BindingElement  
{  
  ChannelPoolSettings ChannelPoolSettings;  
  sint32 MaxAcceptedChannels;  
  boolean PacketRoutable;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="ac6ca-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="ac6ca-105">Methods</span></span>  
 <span data-ttu-id="ac6ca-106">A classe OneWayBindingElement não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="ac6ca-106">The OneWayBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="ac6ca-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="ac6ca-107">Properties</span></span>  
 <span data-ttu-id="ac6ca-108">A classe OneWayBindingElement tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="ac6ca-108">The OneWayBindingElement class has the following properties:</span></span>  
  
### <a name="channelpoolsettings"></a><span data-ttu-id="ac6ca-109">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="ac6ca-109">ChannelPoolSettings</span></span>  
 <span data-ttu-id="ac6ca-110">Tipo de dados: ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="ac6ca-110">Data type: ChannelPoolSettings</span></span>  
  
 <span data-ttu-id="ac6ca-111">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="ac6ca-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ac6ca-112">As configurações do pool de canal.</span><span class="sxs-lookup"><span data-stu-id="ac6ca-112">The channel pool settings.</span></span>  
  
### <a name="maxacceptedchannels"></a><span data-ttu-id="ac6ca-113">MaxAcceptedChannels</span><span class="sxs-lookup"><span data-stu-id="ac6ca-113">MaxAcceptedChannels</span></span>  
 <span data-ttu-id="ac6ca-114">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="ac6ca-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="ac6ca-115">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="ac6ca-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ac6ca-116">O número máximo de canais aceitos.</span><span class="sxs-lookup"><span data-stu-id="ac6ca-116">The maximum number of accepted channels.</span></span>  
  
### <a name="packetroutable"></a><span data-ttu-id="ac6ca-117">PacketRoutable</span><span class="sxs-lookup"><span data-stu-id="ac6ca-117">PacketRoutable</span></span>  
 <span data-ttu-id="ac6ca-118">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="ac6ca-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="ac6ca-119">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="ac6ca-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ac6ca-120">Um valor que indica se o pacote é roteável.</span><span class="sxs-lookup"><span data-stu-id="ac6ca-120">A value that indicates whether the packet is routable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac6ca-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ac6ca-121">Requirements</span></span>  
  
|<span data-ttu-id="ac6ca-122">MOF</span><span class="sxs-lookup"><span data-stu-id="ac6ca-122">MOF</span></span>|<span data-ttu-id="ac6ca-123">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="ac6ca-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="ac6ca-124">Namespace</span><span class="sxs-lookup"><span data-stu-id="ac6ca-124">Namespace</span></span>|<span data-ttu-id="ac6ca-125">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="ac6ca-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ac6ca-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ac6ca-126">See also</span></span>

- <xref:System.ServiceModel.Channels.OneWayBindingElement>
