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
ms.openlocfilehash: acf0ba3938568524479e12b93ae8cebbcf52f909
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33411723"
---
# <a name="icordebugfunction2getjmcstatus-method"></a><span data-ttu-id="f4890-102">Método ICorDebugFunction2::GetJMCStatus</span><span class="sxs-lookup"><span data-stu-id="f4890-102">ICorDebugFunction2::GetJMCStatus Method</span></span>
<span data-ttu-id="f4890-103">Obtém um valor que indica se a função que é representada pelo objeto ICorDebugFunction2 está marcada como código de usuário.</span><span class="sxs-lookup"><span data-stu-id="f4890-103">Gets a value that indicates whether the function that is represented by this ICorDebugFunction2 object is marked as user code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4890-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f4890-104">Syntax</span></span>  
  
```  
HRESULT GetJMCStatus (  
    [out] BOOL   *pbIsJustMyCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f4890-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f4890-105">Parameters</span></span>  
 `pbIsJustMyCode`  
 <span data-ttu-id="f4890-106">[out] Um ponteiro para um valor booliano que é `true`, se essa função é marcada como código de usuário; caso contrário, o valor é `false`.</span><span class="sxs-lookup"><span data-stu-id="f4890-106">[out] A pointer to a Boolean value that is `true`, if this function is marked as user code; otherwise, the value is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f4890-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="f4890-107">Remarks</span></span>  
 <span data-ttu-id="f4890-108">Se a função é representado por esse `ICorDebugFunction2` não pode ser depurado, `pbIsJustMyCode` sempre será `false`.</span><span class="sxs-lookup"><span data-stu-id="f4890-108">If the function represented by this `ICorDebugFunction2` cannot be debugged, `pbIsJustMyCode` will always be `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4890-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f4890-109">Requirements</span></span>  
 <span data-ttu-id="f4890-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f4890-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4890-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f4890-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f4890-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f4890-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f4890-113">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4890-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
