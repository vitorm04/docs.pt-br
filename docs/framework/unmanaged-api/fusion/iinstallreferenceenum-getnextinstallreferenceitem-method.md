---
title: Método IInstallReferenceEnum::GetNextInstallReferenceItem
ms.date: 03/30/2017
api_name:
- IInstallReferenceEnum.GetNextInstallReferenceItem
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IInstallReferenceEnum::GetNextInstallReferenceItem
helpviewer_keywords:
- IInstallReferenceEnum::GetNextInstallReferenceItem method [.NET Framework fusion]
- GetNextInstallReferenceItem method [.NET Framework fusion]
ms.assetid: ce969c9d-6538-4c34-8784-148ffd99fe7a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 20e2bff4257df64f761fd8fff880643d4e786748
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796450"
---
# <a name="iinstallreferenceenumgetnextinstallreferenceitem-method"></a><span data-ttu-id="e80b3-102">Método IInstallReferenceEnum::GetNextInstallReferenceItem</span><span class="sxs-lookup"><span data-stu-id="e80b3-102">IInstallReferenceEnum::GetNextInstallReferenceItem Method</span></span>
<span data-ttu-id="e80b3-103">Obtém um ponteiro para o próximo objeto [IInstallReferenceItem](iinstallreferenceitem-interface.md) contido neste objeto [IInstallReferenceEnum](iinstallreferenceenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="e80b3-103">Gets a pointer to the next [IInstallReferenceItem](iinstallreferenceitem-interface.md) object contained in this [IInstallReferenceEnum](iinstallreferenceenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e80b3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e80b3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNextInstallReferenceItem (  
    [out] IInstallReferenceItem **ppRefItem,  
    [in]  DWORD dwFlags,  
    [in]  LPVOID pvReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e80b3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e80b3-105">Parameters</span></span>  
 `ppRefItem`  
 <span data-ttu-id="e80b3-106">fora O ponteiro `IInstallReferenceItem` retornado.</span><span class="sxs-lookup"><span data-stu-id="e80b3-106">[out] The returned `IInstallReferenceItem` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="e80b3-107">no Reservado para extensibilidade futura.</span><span class="sxs-lookup"><span data-stu-id="e80b3-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="e80b3-108">`dwFlags`deve ser 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="e80b3-108">`dwFlags` must be 0 (zero).</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="e80b3-109">no Reservado para extensibilidade futura.</span><span class="sxs-lookup"><span data-stu-id="e80b3-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="e80b3-110">`pvReserved`deve ser uma referência nula.</span><span class="sxs-lookup"><span data-stu-id="e80b3-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e80b3-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e80b3-111">Requirements</span></span>  
 <span data-ttu-id="e80b3-112">**Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e80b3-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e80b3-113">**Cabeçalho:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="e80b3-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="e80b3-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e80b3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e80b3-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e80b3-115">See also</span></span>

- [<span data-ttu-id="e80b3-116">Interface IInstallReferenceItem</span><span class="sxs-lookup"><span data-stu-id="e80b3-116">IInstallReferenceItem Interface</span></span>](iinstallreferenceitem-interface.md)
- [<span data-ttu-id="e80b3-117">Interface IInstallReferenceEnum</span><span class="sxs-lookup"><span data-stu-id="e80b3-117">IInstallReferenceEnum Interface</span></span>](iinstallreferenceenum-interface.md)
