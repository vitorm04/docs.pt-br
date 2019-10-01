---
title: Método ICorDebugCode::GetFunction
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetFunction
helpviewer_keywords:
- GetFunction method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetFunction method [.NET Framework debugging]
ms.assetid: c568b737-fdb2-4816-accd-051f5ab760f1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 825840536968562a53d9e05b8a4628a1df79407d
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700829"
---
# <a name="icordebugcodegetfunction-method"></a><span data-ttu-id="23909-102">Método ICorDebugCode::GetFunction</span><span class="sxs-lookup"><span data-stu-id="23909-102">ICorDebugCode::GetFunction Method</span></span>
<span data-ttu-id="23909-103">Obtém o "ICorDebugFunction" associado a este "ICorDebugCode".</span><span class="sxs-lookup"><span data-stu-id="23909-103">Gets the "ICorDebugFunction" associated with this "ICorDebugCode".</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23909-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="23909-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunction (  
    [out] ICorDebugFunction **ppFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="23909-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="23909-105">Parameters</span></span>  
 `ppFunction`  
 <span data-ttu-id="23909-106">fora Um ponteiro para o endereço da função.</span><span class="sxs-lookup"><span data-stu-id="23909-106">[out] A pointer to the address of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="23909-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="23909-107">Remarks</span></span>  
 <span data-ttu-id="23909-108">`ICorDebugCode` e `ICorDebugFunction` mantêm uma relação um-para-um.</span><span class="sxs-lookup"><span data-stu-id="23909-108">`ICorDebugCode` and `ICorDebugFunction` maintain a one-to-one relationship.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23909-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="23909-109">Requirements</span></span>  
 <span data-ttu-id="23909-110">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="23909-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23909-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="23909-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="23909-112">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="23909-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="23909-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23909-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
