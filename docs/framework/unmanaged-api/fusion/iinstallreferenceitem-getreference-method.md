---
title: "Método IInstallReferenceItem::GetReference"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IInstallReferenceItem.GetReference
api_location: fusion.dll
api_type: COM
f1_keywords: IInstallReferenceItem::GetReference
helpviewer_keywords:
- IInstallReferenceItem::GetReference method [.NET Framework fusion]
- GetReference method [.NET Framework fusion]
ms.assetid: 8960332f-c98a-405a-ba92-7003de0c1187
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8686e27e63d7363e61bf4c8f1898b71d21fda52b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="iinstallreferenceitemgetreference-method"></a><span data-ttu-id="cacd0-102">Método IInstallReferenceItem::GetReference</span><span class="sxs-lookup"><span data-stu-id="cacd0-102">IInstallReferenceItem::GetReference Method</span></span>
<span data-ttu-id="cacd0-103">Obtém um ponteiro para o [FUSION_INSTALL_REFERENCE](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md) estrutura representada por esse [IInstallReferenceItem](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md) objeto.</span><span class="sxs-lookup"><span data-stu-id="cacd0-103">Gets a pointer to the [FUSION_INSTALL_REFERENCE](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md) structure represented by this [IInstallReferenceItem](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cacd0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cacd0-104">Syntax</span></span>  
  
```  
HRESULT GetReference (  
    [out] LPFUSION_INSTALL_REFERENCE *ppRefData,  
    [in]  DWORD dwFlags,  
    [in]  LPVOID pvReserved  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cacd0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cacd0-105">Parameters</span></span>  
 `ppRefData`  
 <span data-ttu-id="cacd0-106">[out] Retornado `FUSION_INSTALL_REFERENCE` ponteiro.</span><span class="sxs-lookup"><span data-stu-id="cacd0-106">[out] The returned `FUSION_INSTALL_REFERENCE` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="cacd0-107">[in] Reservado para extensibilidade futura.</span><span class="sxs-lookup"><span data-stu-id="cacd0-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="cacd0-108">`dwFlags`deve ser 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="cacd0-108">`dwFlags` must be 0 (zero).</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="cacd0-109">[in] Reservado para extensibilidade futura.</span><span class="sxs-lookup"><span data-stu-id="cacd0-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="cacd0-110">`pvReserved`deve ser uma referência nula.</span><span class="sxs-lookup"><span data-stu-id="cacd0-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cacd0-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cacd0-111">Requirements</span></span>  
 <span data-ttu-id="cacd0-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cacd0-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cacd0-113">**Cabeçalho:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="cacd0-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="cacd0-114">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cacd0-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cacd0-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cacd0-115">See Also</span></span>  
 [<span data-ttu-id="cacd0-116">Interface IInstallReferenceItem</span><span class="sxs-lookup"><span data-stu-id="cacd0-116">IInstallReferenceItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md)  
 [<span data-ttu-id="cacd0-117">Estrutura FUSION_INSTALL_REFERENCE</span><span class="sxs-lookup"><span data-stu-id="cacd0-117">FUSION_INSTALL_REFERENCE Structure</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md)
