---
title: "Método IInstallReferenceEnum::GetNextInstallReferenceItem"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IInstallReferenceEnum.GetNextInstallReferenceItem
api_location: fusion.dll
api_type: COM
f1_keywords: IInstallReferenceEnum::GetNextInstallReferenceItem
helpviewer_keywords:
- IInstallReferenceEnum::GetNextInstallReferenceItem method [.NET Framework fusion]
- GetNextInstallReferenceItem method [.NET Framework fusion]
ms.assetid: ce969c9d-6538-4c34-8784-148ffd99fe7a
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: db7e8bfaf396293f89f4b2e2bb20b5f6f532db19
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="iinstallreferenceenumgetnextinstallreferenceitem-method"></a><span data-ttu-id="cf23c-102">Método IInstallReferenceEnum::GetNextInstallReferenceItem</span><span class="sxs-lookup"><span data-stu-id="cf23c-102">IInstallReferenceEnum::GetNextInstallReferenceItem Method</span></span>
<span data-ttu-id="cf23c-103">Obtém um ponteiro para o próximo [IInstallReferenceItem](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md) objeto contido neste [IInstallReferenceEnum](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md) objeto.</span><span class="sxs-lookup"><span data-stu-id="cf23c-103">Gets a pointer to the next [IInstallReferenceItem](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md) object contained in this [IInstallReferenceEnum](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf23c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cf23c-104">Syntax</span></span>  
  
```  
HRESULT GetNextInstallReferenceItem (  
    [out] IInstallReferenceItem **ppRefItem,  
    [in]  DWORD dwFlags,  
    [in]  LPVOID pvReserved  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cf23c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cf23c-105">Parameters</span></span>  
 `ppRefItem`  
 <span data-ttu-id="cf23c-106">[out] Retornado `IInstallReferenceItem` ponteiro.</span><span class="sxs-lookup"><span data-stu-id="cf23c-106">[out] The returned `IInstallReferenceItem` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="cf23c-107">[in] Reservado para extensibilidade futura.</span><span class="sxs-lookup"><span data-stu-id="cf23c-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="cf23c-108">`dwFlags`deve ser 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="cf23c-108">`dwFlags` must be 0 (zero).</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="cf23c-109">[in] Reservado para extensibilidade futura.</span><span class="sxs-lookup"><span data-stu-id="cf23c-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="cf23c-110">`pvReserved`deve ser uma referência nula.</span><span class="sxs-lookup"><span data-stu-id="cf23c-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf23c-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cf23c-111">Requirements</span></span>  
 <span data-ttu-id="cf23c-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf23c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf23c-113">**Cabeçalho:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="cf23c-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="cf23c-114">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf23c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf23c-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cf23c-115">See Also</span></span>  
 [<span data-ttu-id="cf23c-116">Interface IInstallReferenceItem</span><span class="sxs-lookup"><span data-stu-id="cf23c-116">IInstallReferenceItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md)  
 [<span data-ttu-id="cf23c-117">Interface IInstallReferenceEnum</span><span class="sxs-lookup"><span data-stu-id="cf23c-117">IInstallReferenceEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md)
