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
ms.openlocfilehash: f33225eae4b62f2d5f0793212ae7dcc70e97f508
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73088526"
---
# <a name="icordebugarrayvaluegetcount-method"></a><span data-ttu-id="ac16b-102">Método ICorDebugArrayValue::GetCount</span><span class="sxs-lookup"><span data-stu-id="ac16b-102">ICorDebugArrayValue::GetCount Method</span></span>
<span data-ttu-id="ac16b-103">Obtém o número total de elementos na matriz.</span><span class="sxs-lookup"><span data-stu-id="ac16b-103">Gets the total number of elements in the array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac16b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ac16b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCount (  
    [out] ULONG32 *pnCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ac16b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ac16b-105">Parameters</span></span>  
 `pnCount`  
 <span data-ttu-id="ac16b-106">fora Um ponteiro para o número total de elementos na matriz.</span><span class="sxs-lookup"><span data-stu-id="ac16b-106">[out] A pointer to the total number of elements in the array.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac16b-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ac16b-107">Requirements</span></span>  
 <span data-ttu-id="ac16b-108">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac16b-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac16b-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ac16b-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ac16b-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ac16b-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ac16b-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac16b-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
