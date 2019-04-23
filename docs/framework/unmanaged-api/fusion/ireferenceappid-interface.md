---
title: Interface IReferenceAppId
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 25733e459423500352595d6be0eee26ef75ca7e2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59157190"
---
# <a name="ireferenceappid-interface"></a><span data-ttu-id="12a98-102">Interface IReferenceAppId</span><span class="sxs-lookup"><span data-stu-id="12a98-102">IReferenceAppId Interface</span></span>
<span data-ttu-id="12a98-103">Representa uma referência para o identificador exclusivo para o aplicativo no escopo atual.</span><span class="sxs-lookup"><span data-stu-id="12a98-103">Represents a reference to the unique identifier for the application in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="12a98-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="12a98-104">Methods</span></span>  
  
|<span data-ttu-id="12a98-105">Método</span><span class="sxs-lookup"><span data-stu-id="12a98-105">Method</span></span>|<span data-ttu-id="12a98-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="12a98-106">Description</span></span>|  
|------------|-----------------|  
|`IReferenceAppId::get_CodeBase`|<span data-ttu-id="12a98-107">Obtém um ponteiro para uma representação de cadeia de caracteres do identificador de código para o aplicativo referenciado por este `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="12a98-107">Gets a pointer to a string representation of the code identifier for the application referenced by this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::put_CodeBase`|<span data-ttu-id="12a98-108">Define o identificador de código para o aplicativo referenciado por este `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="12a98-108">Sets the code identifier for the application referenced by this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::EnumAppPath`|<span data-ttu-id="12a98-109">Obtém um ponteiro de interface para um `IEnumReferenceIdentity` instância que contém o `IReferenceIdentity` instâncias que representam os membros deste `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="12a98-109">Gets an interface pointer to an `IEnumReferenceIdentity` instance containing the `IReferenceIdentity` instances that represent members of this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::get_SubscriptionId`|<span data-ttu-id="12a98-110">Obtém um ponteiro para uma representação de cadeia de caracteres do identificador de token para uma assinatura a este `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="12a98-110">Gets a pointer to a string representation of the token identifier for a subscription to this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::put_SubscriptionId`|<span data-ttu-id="12a98-111">Define o identificador de token para uma assinatura para essa `IReferenceAppId` para o valor de cadeia de caracteres especificada.</span><span class="sxs-lookup"><span data-stu-id="12a98-111">Sets the token identifier for a subscription to this `IReferenceAppId` to the specified string value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="12a98-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="12a98-112">Requirements</span></span>  
 <span data-ttu-id="12a98-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12a98-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12a98-114">**Cabeçalho:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="12a98-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="12a98-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12a98-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12a98-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="12a98-116">See also</span></span>

- [<span data-ttu-id="12a98-117">Interfaces de fusão</span><span class="sxs-lookup"><span data-stu-id="12a98-117">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
- [<span data-ttu-id="12a98-118">Interface IEnumReferenceIdentity</span><span class="sxs-lookup"><span data-stu-id="12a98-118">IEnumReferenceIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ienumreferenceidentity-interface.md)
- [<span data-ttu-id="12a98-119">Interface IReferenceIdentity</span><span class="sxs-lookup"><span data-stu-id="12a98-119">IReferenceIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)
