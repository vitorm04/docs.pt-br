---
title: Método IInstallReferenceItem::GetReference
ms.date: 03/30/2017
api_name:
- IInstallReferenceItem.GetReference
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IInstallReferenceItem::GetReference
helpviewer_keywords:
- IInstallReferenceItem::GetReference method [.NET Framework fusion]
- GetReference method [.NET Framework fusion]
ms.assetid: 8960332f-c98a-405a-ba92-7003de0c1187
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5b01c7cea477182c7590664ae9e850e99a89c4bc
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67773950"
---
# <a name="iinstallreferenceitemgetreference-method"></a><span data-ttu-id="c28ff-102">Método IInstallReferenceItem::GetReference</span><span class="sxs-lookup"><span data-stu-id="c28ff-102">IInstallReferenceItem::GetReference Method</span></span>
<span data-ttu-id="c28ff-103">Obtém um ponteiro para o [FUSION_INSTALL_REFERENCE](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md) estrutura representada por este [IInstallReferenceItem](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md) objeto.</span><span class="sxs-lookup"><span data-stu-id="c28ff-103">Gets a pointer to the [FUSION_INSTALL_REFERENCE](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md) structure represented by this [IInstallReferenceItem](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c28ff-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c28ff-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReference (  
    [out] LPFUSION_INSTALL_REFERENCE *ppRefData,  
    [in]  DWORD dwFlags,  
    [in]  LPVOID pvReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c28ff-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c28ff-105">Parameters</span></span>  
 `ppRefData`  
 <span data-ttu-id="c28ff-106">[out] Retornado `FUSION_INSTALL_REFERENCE` ponteiro.</span><span class="sxs-lookup"><span data-stu-id="c28ff-106">[out] The returned `FUSION_INSTALL_REFERENCE` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="c28ff-107">[in] Reservado para extensibilidade futura.</span><span class="sxs-lookup"><span data-stu-id="c28ff-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="c28ff-108">`dwFlags` deve ser 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="c28ff-108">`dwFlags` must be 0 (zero).</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="c28ff-109">[in] Reservado para extensibilidade futura.</span><span class="sxs-lookup"><span data-stu-id="c28ff-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="c28ff-110">`pvReserved` deve ser uma referência nula.</span><span class="sxs-lookup"><span data-stu-id="c28ff-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c28ff-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c28ff-111">Requirements</span></span>  
 <span data-ttu-id="c28ff-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c28ff-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c28ff-113">**Cabeçalho:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="c28ff-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="c28ff-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c28ff-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c28ff-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c28ff-115">See also</span></span>

- [<span data-ttu-id="c28ff-116">Interface IInstallReferenceItem</span><span class="sxs-lookup"><span data-stu-id="c28ff-116">IInstallReferenceItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md)
- [<span data-ttu-id="c28ff-117">Estrutura FUSION_INSTALL_REFERENCE</span><span class="sxs-lookup"><span data-stu-id="c28ff-117">FUSION_INSTALL_REFERENCE Structure</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md)
