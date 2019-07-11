---
title: Método ICorDebugFunction2::GetJMCStatus
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2.GetJMCStatus
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2::GetJMCStatus
helpviewer_keywords:
- ICorDebugFunction2::GetJMCStatus method [.NET Framework debugging]
- GetJMCStatus method [.NET Framework debugging]
ms.assetid: 840a71ed-bf5a-4f5e-8ed6-762222b34493
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ed2364c7c47aed1430a86aeee3daabf6b94cbf3b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754482"
---
# <a name="icordebugfunction2getjmcstatus-method"></a><span data-ttu-id="860ec-102">Método ICorDebugFunction2::GetJMCStatus</span><span class="sxs-lookup"><span data-stu-id="860ec-102">ICorDebugFunction2::GetJMCStatus Method</span></span>
<span data-ttu-id="860ec-103">Obtém um valor que indica se a função que é representada por esse objeto ICorDebugFunction2 está marcada como código do usuário.</span><span class="sxs-lookup"><span data-stu-id="860ec-103">Gets a value that indicates whether the function that is represented by this ICorDebugFunction2 object is marked as user code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="860ec-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="860ec-104">Syntax</span></span>  
  
```cpp  
HRESULT GetJMCStatus (  
    [out] BOOL   *pbIsJustMyCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="860ec-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="860ec-105">Parameters</span></span>  
 `pbIsJustMyCode`  
 <span data-ttu-id="860ec-106">[out] Um ponteiro para um valor booliano que será `true`, se essa função é marcada como código de usuário; caso contrário, o valor será `false`.</span><span class="sxs-lookup"><span data-stu-id="860ec-106">[out] A pointer to a Boolean value that is `true`, if this function is marked as user code; otherwise, the value is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="860ec-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="860ec-107">Remarks</span></span>  
 <span data-ttu-id="860ec-108">Se a função representado por este `ICorDebugFunction2` não pode ser depurado `pbIsJustMyCode` sempre será `false`.</span><span class="sxs-lookup"><span data-stu-id="860ec-108">If the function represented by this `ICorDebugFunction2` cannot be debugged, `pbIsJustMyCode` will always be `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="860ec-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="860ec-109">Requirements</span></span>  
 <span data-ttu-id="860ec-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="860ec-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="860ec-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="860ec-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="860ec-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="860ec-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="860ec-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="860ec-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
