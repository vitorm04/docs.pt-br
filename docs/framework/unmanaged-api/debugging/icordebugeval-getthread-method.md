---
title: Método ICorDebugEval::GetThread
ms.date: 03/30/2017
api_name:
- ICorDebugEval.GetThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::GetThread
helpviewer_keywords:
- GetThread method, ICorDebugEval interface [.NET Framework debugging]
- ICorDebugEval::GetThread method [.NET Framework debugging]
ms.assetid: 57163b0d-c8a7-44af-9078-e7a895d29f9a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 24bc096a0ba01c58aa963d69fa46a1d1bbe8be75
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67752904"
---
# <a name="icordebugevalgetthread-method"></a><span data-ttu-id="ef442-102">Método ICorDebugEval::GetThread</span><span class="sxs-lookup"><span data-stu-id="ef442-102">ICorDebugEval::GetThread Method</span></span>
<span data-ttu-id="ef442-103">Obtém o thread em que essa avaliação está em execução ou será executado.</span><span class="sxs-lookup"><span data-stu-id="ef442-103">Gets the thread in which this evaluation is executing or will execute.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef442-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ef442-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThread (  
    [out] ICorDebugThread   **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ef442-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ef442-105">Parameters</span></span>  
 `ppThread`  
 <span data-ttu-id="ef442-106">[out] Um ponteiro para o endereço de um objeto de ICorDebugThread que representa o thread.</span><span class="sxs-lookup"><span data-stu-id="ef442-106">[out] A pointer to the address of an ICorDebugThread object that represents the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef442-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ef442-107">Requirements</span></span>  
 <span data-ttu-id="ef442-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ef442-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef442-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ef442-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ef442-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ef442-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ef442-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef442-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
