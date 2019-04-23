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
ms.openlocfilehash: cd0a554535122b81f5812102c7951f56b294796a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59213357"
---
# <a name="iinstallreferenceitemgetreference-method"></a><span data-ttu-id="b923f-102">Método IInstallReferenceItem::GetReference</span><span class="sxs-lookup"><span data-stu-id="b923f-102">IInstallReferenceItem::GetReference Method</span></span>
<span data-ttu-id="b923f-103">Obtém um ponteiro para o [FUSION_INSTALL_REFERENCE](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md) estrutura representada por este [IInstallReferenceItem](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md) objeto.</span><span class="sxs-lookup"><span data-stu-id="b923f-103">Gets a pointer to the [FUSION_INSTALL_REFERENCE](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md) structure represented by this [IInstallReferenceItem](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b923f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b923f-104">Syntax</span></span>  
  
```  
HRESULT GetReference (  
    [out] LPFUSION_INSTALL_REFERENCE *ppRefData,  
    [in]  DWORD dwFlags,  
    [in]  LPVOID pvReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b923f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b923f-105">Parameters</span></span>  
 `ppRefData`  
 <span data-ttu-id="b923f-106">[out] Retornado `FUSION_INSTALL_REFERENCE` ponteiro.</span><span class="sxs-lookup"><span data-stu-id="b923f-106">[out] The returned `FUSION_INSTALL_REFERENCE` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="b923f-107">[in] Reservado para extensibilidade futura.</span><span class="sxs-lookup"><span data-stu-id="b923f-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="b923f-108">`dwFlags` deve ser 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="b923f-108">`dwFlags` must be 0 (zero).</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="b923f-109">[in] Reservado para extensibilidade futura.</span><span class="sxs-lookup"><span data-stu-id="b923f-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="b923f-110">`pvReserved` deve ser uma referência nula.</span><span class="sxs-lookup"><span data-stu-id="b923f-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b923f-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b923f-111">Requirements</span></span>  
 <span data-ttu-id="b923f-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b923f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b923f-113">**Cabeçalho:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="b923f-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="b923f-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b923f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b923f-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b923f-115">See also</span></span>

- [<span data-ttu-id="b923f-116">Interface IInstallReferenceItem</span><span class="sxs-lookup"><span data-stu-id="b923f-116">IInstallReferenceItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md)
- [<span data-ttu-id="b923f-117">Estrutura FUSION_INSTALL_REFERENCE</span><span class="sxs-lookup"><span data-stu-id="b923f-117">FUSION_INSTALL_REFERENCE Structure</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md)
