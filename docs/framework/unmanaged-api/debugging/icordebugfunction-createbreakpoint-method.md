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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 695ce7f25813a191c74bec6563fc7f8ae8d1143d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57496108"
---
# <a name="icordebugfunctioncreatebreakpoint-method"></a><span data-ttu-id="c98a3-102">Método ICorDebugFunction::CreateBreakpoint</span><span class="sxs-lookup"><span data-stu-id="c98a3-102">ICorDebugFunction::CreateBreakpoint Method</span></span>
<span data-ttu-id="c98a3-103">Cria um ponto de interrupção no início desta função.</span><span class="sxs-lookup"><span data-stu-id="c98a3-103">Creates a breakpoint at the beginning of this function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c98a3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c98a3-104">Syntax</span></span>  
  
```  
HRESULT CreateBreakpoint (  
    [out] ICorDebugFunctionBreakpoint **ppBreakpoint  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c98a3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c98a3-105">Parameters</span></span>  
 `ppBreakpoint`  
 <span data-ttu-id="c98a3-106">[out] Um ponteiro para o endereço de um objeto ICorDebugFunctionBreakpoint que representa o novo ponto de interrupção para a função.</span><span class="sxs-lookup"><span data-stu-id="c98a3-106">[out] A pointer to the address of an ICorDebugFunctionBreakpoint object that represents the new breakpoint for the function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c98a3-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c98a3-107">Requirements</span></span>  
 <span data-ttu-id="c98a3-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c98a3-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c98a3-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c98a3-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c98a3-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c98a3-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c98a3-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c98a3-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
