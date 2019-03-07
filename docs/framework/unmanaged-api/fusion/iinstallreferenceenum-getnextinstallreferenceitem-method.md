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
ms.openlocfilehash: c23494f8c0a977624b899f01e843ba3545a22fbb
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57501637"
---
# <a name="iinstallreferenceenumgetnextinstallreferenceitem-method"></a><span data-ttu-id="46c7c-102">Método IInstallReferenceEnum::GetNextInstallReferenceItem</span><span class="sxs-lookup"><span data-stu-id="46c7c-102">IInstallReferenceEnum::GetNextInstallReferenceItem Method</span></span>
<span data-ttu-id="46c7c-103">Obtém um ponteiro para a próxima [IInstallReferenceItem](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md) objeto contido nesse [IInstallReferenceEnum](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md) objeto.</span><span class="sxs-lookup"><span data-stu-id="46c7c-103">Gets a pointer to the next [IInstallReferenceItem](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md) object contained in this [IInstallReferenceEnum](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46c7c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="46c7c-104">Syntax</span></span>  
  
```  
HRESULT GetNextInstallReferenceItem (  
    [out] IInstallReferenceItem **ppRefItem,  
    [in]  DWORD dwFlags,  
    [in]  LPVOID pvReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="46c7c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="46c7c-105">Parameters</span></span>  
 `ppRefItem`  
 <span data-ttu-id="46c7c-106">[out] Retornado `IInstallReferenceItem` ponteiro.</span><span class="sxs-lookup"><span data-stu-id="46c7c-106">[out] The returned `IInstallReferenceItem` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="46c7c-107">[in] Reservado para extensibilidade futura.</span><span class="sxs-lookup"><span data-stu-id="46c7c-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="46c7c-108">`dwFlags` deve ser 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="46c7c-108">`dwFlags` must be 0 (zero).</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="46c7c-109">[in] Reservado para extensibilidade futura.</span><span class="sxs-lookup"><span data-stu-id="46c7c-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="46c7c-110">`pvReserved` deve ser uma referência nula.</span><span class="sxs-lookup"><span data-stu-id="46c7c-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46c7c-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="46c7c-111">Requirements</span></span>  
 <span data-ttu-id="46c7c-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="46c7c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46c7c-113">**Cabeçalho:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="46c7c-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="46c7c-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46c7c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46c7c-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="46c7c-115">See also</span></span>
- [<span data-ttu-id="46c7c-116">Interface IInstallReferenceItem</span><span class="sxs-lookup"><span data-stu-id="46c7c-116">IInstallReferenceItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md)
- [<span data-ttu-id="46c7c-117">Interface IInstallReferenceEnum</span><span class="sxs-lookup"><span data-stu-id="46c7c-117">IInstallReferenceEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md)
