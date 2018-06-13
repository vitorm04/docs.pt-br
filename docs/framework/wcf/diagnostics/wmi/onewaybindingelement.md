---
title: OneWayBindingElement
ms.date: 03/30/2017
ms.assetid: 5c7e17c3-39b9-4214-ae08-9e6141734305
ms.openlocfilehash: ee7cfed20234175ba54dd25dbbbab4615c1ed7af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485731"
---
# <a name="onewaybindingelement"></a><span data-ttu-id="03ce8-102">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="03ce8-102">OneWayBindingElement</span></span>
<span data-ttu-id="03ce8-103">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="03ce8-103">OneWayBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03ce8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="03ce8-104">Syntax</span></span>  
  
```  
class OneWayBindingElement : BindingElement  
{  
  ChannelPoolSettings ChannelPoolSettings;  
  sint32 MaxAcceptedChannels;  
  boolean PacketRoutable;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="03ce8-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="03ce8-105">Methods</span></span>  
 <span data-ttu-id="03ce8-106">A classe OneWayBindingElement não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="03ce8-106">The OneWayBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="03ce8-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="03ce8-107">Properties</span></span>  
 <span data-ttu-id="03ce8-108">A classe OneWayBindingElement tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="03ce8-108">The OneWayBindingElement class has the following properties:</span></span>  
  
### <a name="channelpoolsettings"></a><span data-ttu-id="03ce8-109">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="03ce8-109">ChannelPoolSettings</span></span>  
 <span data-ttu-id="03ce8-110">Tipo de dados: ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="03ce8-110">Data type: ChannelPoolSettings</span></span>  
  
 <span data-ttu-id="03ce8-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="03ce8-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="03ce8-112">As configurações de pool do canal.</span><span class="sxs-lookup"><span data-stu-id="03ce8-112">The channel pool settings.</span></span>  
  
### <a name="maxacceptedchannels"></a><span data-ttu-id="03ce8-113">MaxAcceptedChannels</span><span class="sxs-lookup"><span data-stu-id="03ce8-113">MaxAcceptedChannels</span></span>  
 <span data-ttu-id="03ce8-114">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="03ce8-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="03ce8-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="03ce8-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="03ce8-116">O número máximo de canais aceitos.</span><span class="sxs-lookup"><span data-stu-id="03ce8-116">The maximum number of accepted channels.</span></span>  
  
### <a name="packetroutable"></a><span data-ttu-id="03ce8-117">PacketRoutable</span><span class="sxs-lookup"><span data-stu-id="03ce8-117">PacketRoutable</span></span>  
 <span data-ttu-id="03ce8-118">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="03ce8-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="03ce8-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="03ce8-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="03ce8-120">Um valor que indica se o pacote é roteável.</span><span class="sxs-lookup"><span data-stu-id="03ce8-120">A value that indicates whether the packet is routable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03ce8-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="03ce8-121">Requirements</span></span>  
  
|<span data-ttu-id="03ce8-122">MOF</span><span class="sxs-lookup"><span data-stu-id="03ce8-122">MOF</span></span>|<span data-ttu-id="03ce8-123">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="03ce8-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="03ce8-124">Namespace</span><span class="sxs-lookup"><span data-stu-id="03ce8-124">Namespace</span></span>|<span data-ttu-id="03ce8-125">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="03ce8-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="03ce8-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="03ce8-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.OneWayBindingElement>
