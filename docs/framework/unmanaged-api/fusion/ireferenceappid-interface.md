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
ms.openlocfilehash: 6f20fb2e9e026253fb02b47dfcd63cf655acc4ee
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131655"
---
# <a name="ireferenceappid-interface"></a><span data-ttu-id="f05b5-102">Interface IReferenceAppId</span><span class="sxs-lookup"><span data-stu-id="f05b5-102">IReferenceAppId Interface</span></span>
<span data-ttu-id="f05b5-103">Representa uma referência ao identificador exclusivo para o aplicativo no escopo atual.</span><span class="sxs-lookup"><span data-stu-id="f05b5-103">Represents a reference to the unique identifier for the application in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f05b5-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="f05b5-104">Methods</span></span>  
  
|<span data-ttu-id="f05b5-105">Método</span><span class="sxs-lookup"><span data-stu-id="f05b5-105">Method</span></span>|<span data-ttu-id="f05b5-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="f05b5-106">Description</span></span>|  
|------------|-----------------|  
|`IReferenceAppId::get_CodeBase`|<span data-ttu-id="f05b5-107">Obtém um ponteiro para uma representação de cadeia de caracteres do identificador de código para o aplicativo referenciado por este `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="f05b5-107">Gets a pointer to a string representation of the code identifier for the application referenced by this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::put_CodeBase`|<span data-ttu-id="f05b5-108">Define o identificador de código para o aplicativo referenciado por este `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="f05b5-108">Sets the code identifier for the application referenced by this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::EnumAppPath`|<span data-ttu-id="f05b5-109">Obtém um ponteiro de interface para uma instância de `IEnumReferenceIdentity` que contém as instâncias de `IReferenceIdentity` que representam os membros dessa `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="f05b5-109">Gets an interface pointer to an `IEnumReferenceIdentity` instance containing the `IReferenceIdentity` instances that represent members of this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::get_SubscriptionId`|<span data-ttu-id="f05b5-110">Obtém um ponteiro para uma representação de cadeia de caracteres do identificador de token para uma assinatura para essa `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="f05b5-110">Gets a pointer to a string representation of the token identifier for a subscription to this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::put_SubscriptionId`|<span data-ttu-id="f05b5-111">Define o identificador de token para uma assinatura para essa `IReferenceAppId` para o valor da cadeia de caracteres especificada.</span><span class="sxs-lookup"><span data-stu-id="f05b5-111">Sets the token identifier for a subscription to this `IReferenceAppId` to the specified string value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f05b5-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f05b5-112">Requirements</span></span>  
 <span data-ttu-id="f05b5-113">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f05b5-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f05b5-114">**Cabeçalho:** Isolamento. h</span><span class="sxs-lookup"><span data-stu-id="f05b5-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="f05b5-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f05b5-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f05b5-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f05b5-116">See also</span></span>

- [<span data-ttu-id="f05b5-117">Interfaces de fusão</span><span class="sxs-lookup"><span data-stu-id="f05b5-117">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="f05b5-118">Interface IEnumReferenceIdentity</span><span class="sxs-lookup"><span data-stu-id="f05b5-118">IEnumReferenceIdentity Interface</span></span>](ienumreferenceidentity-interface.md)
- [<span data-ttu-id="f05b5-119">Interface IReferenceIdentity</span><span class="sxs-lookup"><span data-stu-id="f05b5-119">IReferenceIdentity Interface</span></span>](ireferenceidentity-interface.md)
