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
ms.openlocfilehash: 522ed80f161f114af25e1fa7ad041c8238073d6f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796373"
---
# <a name="ireferenceappid-interface"></a><span data-ttu-id="afdc6-102">Interface IReferenceAppId</span><span class="sxs-lookup"><span data-stu-id="afdc6-102">IReferenceAppId Interface</span></span>
<span data-ttu-id="afdc6-103">Representa uma referência ao identificador exclusivo para o aplicativo no escopo atual.</span><span class="sxs-lookup"><span data-stu-id="afdc6-103">Represents a reference to the unique identifier for the application in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="afdc6-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="afdc6-104">Methods</span></span>  
  
|<span data-ttu-id="afdc6-105">Método</span><span class="sxs-lookup"><span data-stu-id="afdc6-105">Method</span></span>|<span data-ttu-id="afdc6-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="afdc6-106">Description</span></span>|  
|------------|-----------------|  
|`IReferenceAppId::get_CodeBase`|<span data-ttu-id="afdc6-107">Obtém um ponteiro para uma representação de cadeia de caracteres do identificador de código para o aplicativo `IReferenceAppId`referenciado por isso.</span><span class="sxs-lookup"><span data-stu-id="afdc6-107">Gets a pointer to a string representation of the code identifier for the application referenced by this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::put_CodeBase`|<span data-ttu-id="afdc6-108">Define o identificador de código para o aplicativo referenciado `IReferenceAppId`por isso.</span><span class="sxs-lookup"><span data-stu-id="afdc6-108">Sets the code identifier for the application referenced by this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::EnumAppPath`|<span data-ttu-id="afdc6-109">Obtém um ponteiro de interface para `IEnumReferenceIdentity` uma instância que `IReferenceIdentity` contém as instâncias `IReferenceAppId`que representam os membros desse.</span><span class="sxs-lookup"><span data-stu-id="afdc6-109">Gets an interface pointer to an `IEnumReferenceIdentity` instance containing the `IReferenceIdentity` instances that represent members of this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::get_SubscriptionId`|<span data-ttu-id="afdc6-110">Obtém um ponteiro para uma representação de cadeia de caracteres do identificador de token para uma `IReferenceAppId`assinatura para isso.</span><span class="sxs-lookup"><span data-stu-id="afdc6-110">Gets a pointer to a string representation of the token identifier for a subscription to this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::put_SubscriptionId`|<span data-ttu-id="afdc6-111">Define o identificador de token para uma assinatura para `IReferenceAppId` o valor da cadeia de caracteres especificada.</span><span class="sxs-lookup"><span data-stu-id="afdc6-111">Sets the token identifier for a subscription to this `IReferenceAppId` to the specified string value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="afdc6-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="afdc6-112">Requirements</span></span>  
 <span data-ttu-id="afdc6-113">**Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="afdc6-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="afdc6-114">**Cabeçalho:** Isolamento. h</span><span class="sxs-lookup"><span data-stu-id="afdc6-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="afdc6-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="afdc6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afdc6-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="afdc6-116">See also</span></span>

- [<span data-ttu-id="afdc6-117">Interfaces de fusão</span><span class="sxs-lookup"><span data-stu-id="afdc6-117">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="afdc6-118">Interface IEnumReferenceIdentity</span><span class="sxs-lookup"><span data-stu-id="afdc6-118">IEnumReferenceIdentity Interface</span></span>](ienumreferenceidentity-interface.md)
- [<span data-ttu-id="afdc6-119">Interface IReferenceIdentity</span><span class="sxs-lookup"><span data-stu-id="afdc6-119">IReferenceIdentity Interface</span></span>](ireferenceidentity-interface.md)
