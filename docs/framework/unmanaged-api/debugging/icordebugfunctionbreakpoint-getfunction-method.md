---
title: Método ICorDebugFunctionBreakpoint::GetFunction
ms.date: 03/30/2017
api_name:
- ICorDebugFunctionBreakpoint.GetFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunctionBreakpoint::GetFunction
helpviewer_keywords:
- ICorDebugFunctionBreakpoint::GetFunction method [.NET Framework debugging]
- GetFunction method, ICorDebugFunctionBreakpoint interface [.NET Framework debugging]
ms.assetid: 2a62dae5-dd8a-4696-b817-0e1e586c24a0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a1da93ea073d6ae9f2e79f251014b2db5282a22c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763783"
---
# <a name="icordebugfunctionbreakpointgetfunction-method"></a><span data-ttu-id="0638e-102">Método ICorDebugFunctionBreakpoint::GetFunction</span><span class="sxs-lookup"><span data-stu-id="0638e-102">ICorDebugFunctionBreakpoint::GetFunction Method</span></span>
<span data-ttu-id="0638e-103">Obtém um ponteiro de interface para um ICorDebugFunction que faz referência à função na qual o ponto de interrupção é definido.</span><span class="sxs-lookup"><span data-stu-id="0638e-103">Gets an interface pointer to an ICorDebugFunction that references the function in which the breakpoint is set.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0638e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0638e-104">Syntax</span></span>  
  
```  
HRESULT GetFunction (  
    [out] ICorDebugFunction  **ppFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0638e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0638e-105">Parameters</span></span>  
 `ppFunction`  
 <span data-ttu-id="0638e-106">[out] Um ponteiro para o endereço da função na qual o ponto de interrupção é definido.</span><span class="sxs-lookup"><span data-stu-id="0638e-106">[out] A pointer to the address of the function in which the breakpoint is set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0638e-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0638e-107">Requirements</span></span>  
 <span data-ttu-id="0638e-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0638e-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0638e-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0638e-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0638e-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0638e-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0638e-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0638e-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
