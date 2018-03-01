---
title: Interface IReferenceAppId
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IReferenceAppId
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IReferenceAppId
helpviewer_keywords:
- IReferenceAppId interface [.NET Framework fusion]
ms.assetid: 8eb9e565-f358-43ce-900e-a8f8a5aa6cfb
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 22ac2d75632b3c670d7c185cbbf5081732dcaffc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ireferenceappid-interface"></a><span data-ttu-id="deaa2-102">Interface IReferenceAppId</span><span class="sxs-lookup"><span data-stu-id="deaa2-102">IReferenceAppId Interface</span></span>
<span data-ttu-id="deaa2-103">Representa uma referência para o identificador exclusivo para o aplicativo no escopo atual.</span><span class="sxs-lookup"><span data-stu-id="deaa2-103">Represents a reference to the unique identifier for the application in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="deaa2-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="deaa2-104">Methods</span></span>  
  
|<span data-ttu-id="deaa2-105">Método</span><span class="sxs-lookup"><span data-stu-id="deaa2-105">Method</span></span>|<span data-ttu-id="deaa2-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="deaa2-106">Description</span></span>|  
|------------|-----------------|  
|`IReferenceAppId::get_CodeBase`|<span data-ttu-id="deaa2-107">Obtém um ponteiro para uma representação de cadeia de caracteres do identificador de código para o aplicativo referenciado por este `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="deaa2-107">Gets a pointer to a string representation of the code identifier for the application referenced by this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::put_CodeBase`|<span data-ttu-id="deaa2-108">Define o identificador de código para o aplicativo referenciado por este `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="deaa2-108">Sets the code identifier for the application referenced by this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::EnumAppPath`|<span data-ttu-id="deaa2-109">Obtém um ponteiro de interface para um `IEnumReferenceIdentity` instância que contém o `IReferenceIdentity` instâncias que representam os membros deste `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="deaa2-109">Gets an interface pointer to an `IEnumReferenceIdentity` instance containing the `IReferenceIdentity` instances that represent members of this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::get_SubscriptionId`|<span data-ttu-id="deaa2-110">Obtém um ponteiro para uma representação de cadeia de caracteres do identificador de token para uma assinatura para este `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="deaa2-110">Gets a pointer to a string representation of the token identifier for a subscription to this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::put_SubscriptionId`|<span data-ttu-id="deaa2-111">Define o identificador para uma assinatura de token para este `IReferenceAppId` para o valor de cadeia de caracteres especificada.</span><span class="sxs-lookup"><span data-stu-id="deaa2-111">Sets the token identifier for a subscription to this `IReferenceAppId` to the specified string value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="deaa2-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="deaa2-112">Requirements</span></span>  
 <span data-ttu-id="deaa2-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="deaa2-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="deaa2-114">**Cabeçalho:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="deaa2-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="deaa2-115">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="deaa2-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="deaa2-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="deaa2-116">See Also</span></span>  
 [<span data-ttu-id="deaa2-117">Interfaces de fusão</span><span class="sxs-lookup"><span data-stu-id="deaa2-117">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [<span data-ttu-id="deaa2-118">Interface IEnumReferenceIdentity</span><span class="sxs-lookup"><span data-stu-id="deaa2-118">IEnumReferenceIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ienumreferenceidentity-interface.md)  
 [<span data-ttu-id="deaa2-119">Interface IReferenceIdentity</span><span class="sxs-lookup"><span data-stu-id="deaa2-119">IReferenceIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)
