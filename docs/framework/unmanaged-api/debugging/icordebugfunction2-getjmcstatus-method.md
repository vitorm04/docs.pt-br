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
ms.openlocfilehash: 56dc5f87b32b3aaa0bfbb69541d5a01ae26606ab
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213225"
---
# <a name="icordebugfunction2getjmcstatus-method"></a><span data-ttu-id="8c1b5-102">Método ICorDebugFunction2::GetJMCStatus</span><span class="sxs-lookup"><span data-stu-id="8c1b5-102">ICorDebugFunction2::GetJMCStatus Method</span></span>
<span data-ttu-id="8c1b5-103">Obtém um valor que indica se a função representada por esse objeto ICorDebugFunction2 está marcada como código de usuário.</span><span class="sxs-lookup"><span data-stu-id="8c1b5-103">Gets a value that indicates whether the function that is represented by this ICorDebugFunction2 object is marked as user code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c1b5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8c1b5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetJMCStatus (  
    [out] BOOL   *pbIsJustMyCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8c1b5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8c1b5-105">Parameters</span></span>  
 `pbIsJustMyCode`  
 <span data-ttu-id="8c1b5-106">fora Um ponteiro para um valor booliano `true` , se essa função estiver marcada como código de usuário; caso contrário, o valor será `false` .</span><span class="sxs-lookup"><span data-stu-id="8c1b5-106">[out] A pointer to a Boolean value that is `true`, if this function is marked as user code; otherwise, the value is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8c1b5-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="8c1b5-107">Remarks</span></span>  
 <span data-ttu-id="8c1b5-108">Se a função representada por isso `ICorDebugFunction2` não puder ser depurada, `pbIsJustMyCode` sempre será `false` .</span><span class="sxs-lookup"><span data-stu-id="8c1b5-108">If the function represented by this `ICorDebugFunction2` cannot be debugged, `pbIsJustMyCode` will always be `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c1b5-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8c1b5-109">Requirements</span></span>  
 <span data-ttu-id="8c1b5-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c1b5-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c1b5-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8c1b5-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8c1b5-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8c1b5-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8c1b5-113">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c1b5-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
