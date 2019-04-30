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
ms.openlocfilehash: d23a0a489cfe13201b7798920feb3528db3b0709
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988657"
---
# <a name="icordebugfunction2getjmcstatus-method"></a><span data-ttu-id="70ad0-102">Método ICorDebugFunction2::GetJMCStatus</span><span class="sxs-lookup"><span data-stu-id="70ad0-102">ICorDebugFunction2::GetJMCStatus Method</span></span>
<span data-ttu-id="70ad0-103">Obtém um valor que indica se a função que é representada por esse objeto ICorDebugFunction2 está marcada como código do usuário.</span><span class="sxs-lookup"><span data-stu-id="70ad0-103">Gets a value that indicates whether the function that is represented by this ICorDebugFunction2 object is marked as user code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70ad0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="70ad0-104">Syntax</span></span>  
  
```  
HRESULT GetJMCStatus (  
    [out] BOOL   *pbIsJustMyCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="70ad0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="70ad0-105">Parameters</span></span>  
 `pbIsJustMyCode`  
 <span data-ttu-id="70ad0-106">[out] Um ponteiro para um valor booliano que será `true`, se essa função é marcada como código de usuário; caso contrário, o valor será `false`.</span><span class="sxs-lookup"><span data-stu-id="70ad0-106">[out] A pointer to a Boolean value that is `true`, if this function is marked as user code; otherwise, the value is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="70ad0-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="70ad0-107">Remarks</span></span>  
 <span data-ttu-id="70ad0-108">Se a função representado por este `ICorDebugFunction2` não pode ser depurado `pbIsJustMyCode` sempre será `false`.</span><span class="sxs-lookup"><span data-stu-id="70ad0-108">If the function represented by this `ICorDebugFunction2` cannot be debugged, `pbIsJustMyCode` will always be `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70ad0-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="70ad0-109">Requirements</span></span>  
 <span data-ttu-id="70ad0-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70ad0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70ad0-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="70ad0-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="70ad0-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="70ad0-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="70ad0-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70ad0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
