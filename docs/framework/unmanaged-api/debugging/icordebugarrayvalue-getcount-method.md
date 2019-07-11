---
title: Método ICorDebugArrayValue::GetCount
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetCount
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetCount
helpviewer_keywords:
- ICorDebugArrayValue::GetCount method [.NET Framework debugging]
- GetCount method, ICorDebugArrayValue interface [.NET Framework debugging]
ms.assetid: 44cd98cf-2127-4d46-8c6a-da4e857bb6b0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e45f49d17a5b71abfb58ff8c0126abad49322c5b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67737591"
---
# <a name="icordebugarrayvaluegetcount-method"></a><span data-ttu-id="533c3-102">Método ICorDebugArrayValue::GetCount</span><span class="sxs-lookup"><span data-stu-id="533c3-102">ICorDebugArrayValue::GetCount Method</span></span>
<span data-ttu-id="533c3-103">Obtém o número total de elementos na matriz.</span><span class="sxs-lookup"><span data-stu-id="533c3-103">Gets the total number of elements in the array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="533c3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="533c3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCount (  
    [out] ULONG32 *pnCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="533c3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="533c3-105">Parameters</span></span>  
 `pnCount`  
 <span data-ttu-id="533c3-106">[out] Um ponteiro para o número total de elementos na matriz.</span><span class="sxs-lookup"><span data-stu-id="533c3-106">[out] A pointer to the total number of elements in the array.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="533c3-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="533c3-107">Requirements</span></span>  
 <span data-ttu-id="533c3-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="533c3-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="533c3-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="533c3-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="533c3-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="533c3-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="533c3-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="533c3-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
