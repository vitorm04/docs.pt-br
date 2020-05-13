---
title: Método ICorDebugFunction::CreateBreakpoint
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.CreateBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::CreateBreakpoint
helpviewer_keywords:
- ICorDebugFunction::CreateBreakpoint method [.NET Framework debugging]
- CreateBreakpoint method, ICorDebugFunction interface [.NET Framework debugging]
ms.assetid: ffd0f708-0d21-4fae-a395-63b6c45828fa
topic_type:
- apiref
ms.openlocfilehash: 5d7e83c6aa494f2363698d0220bbfe724b54e612
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209429"
---
# <a name="icordebugfunctioncreatebreakpoint-method"></a><span data-ttu-id="126f3-102">Método ICorDebugFunction::CreateBreakpoint</span><span class="sxs-lookup"><span data-stu-id="126f3-102">ICorDebugFunction::CreateBreakpoint Method</span></span>
<span data-ttu-id="126f3-103">Cria um ponto de interrupção no início desta função.</span><span class="sxs-lookup"><span data-stu-id="126f3-103">Creates a breakpoint at the beginning of this function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="126f3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="126f3-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateBreakpoint (  
    [out] ICorDebugFunctionBreakpoint **ppBreakpoint  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="126f3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="126f3-105">Parameters</span></span>  
 `ppBreakpoint`  
 <span data-ttu-id="126f3-106">fora Um ponteiro para o endereço de um objeto ICorDebugFunctionBreakpoint que representa o novo ponto de interrupção para a função.</span><span class="sxs-lookup"><span data-stu-id="126f3-106">[out] A pointer to the address of an ICorDebugFunctionBreakpoint object that represents the new breakpoint for the function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="126f3-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="126f3-107">Requirements</span></span>  
 <span data-ttu-id="126f3-108">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="126f3-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="126f3-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="126f3-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="126f3-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="126f3-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="126f3-111">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="126f3-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
