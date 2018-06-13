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
ms.openlocfilehash: da22570441324a01fea307116bc23601e62919a4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33411358"
---
# <a name="icordebugfunctionbreakpointgetfunction-method"></a><span data-ttu-id="e0736-102">Método ICorDebugFunctionBreakpoint::GetFunction</span><span class="sxs-lookup"><span data-stu-id="e0736-102">ICorDebugFunctionBreakpoint::GetFunction Method</span></span>
<span data-ttu-id="e0736-103">Obtém um ponteiro de interface para um ICorDebugFunction que faz referência à função na qual o ponto de interrupção está definido.</span><span class="sxs-lookup"><span data-stu-id="e0736-103">Gets an interface pointer to an ICorDebugFunction that references the function in which the breakpoint is set.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0736-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e0736-104">Syntax</span></span>  
  
```  
HRESULT GetFunction (  
    [out] ICorDebugFunction  **ppFunction  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e0736-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e0736-105">Parameters</span></span>  
 `ppFunction`  
 <span data-ttu-id="e0736-106">[out] Um ponteiro para o endereço da função na qual o ponto de interrupção está definido.</span><span class="sxs-lookup"><span data-stu-id="e0736-106">[out] A pointer to the address of the function in which the breakpoint is set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0736-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e0736-107">Requirements</span></span>  
 <span data-ttu-id="e0736-108">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0736-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0736-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e0736-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e0736-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e0736-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e0736-111">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0736-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
