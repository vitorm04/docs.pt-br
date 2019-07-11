---
title: Método ICorDebugBreakpoint::IsActive
ms.date: 03/30/2017
api_name:
- ICorDebugBreakpoint.IsActive
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBreakpoint::IsActive
helpviewer_keywords:
- ICorDebugBreakpoint::IsActive method [.NET Framework debugging]
- IsActive method, ICorDebugBreakpoint interface [.NET Framework debugging]
ms.assetid: 06e583d6-d88a-4ff5-bb95-5c48618a461c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6d78208c180638e9048ae39664b8ce8f57be90da
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745161"
---
# <a name="icordebugbreakpointisactive-method"></a><span data-ttu-id="f6900-102">Método ICorDebugBreakpoint::IsActive</span><span class="sxs-lookup"><span data-stu-id="f6900-102">ICorDebugBreakpoint::IsActive Method</span></span>
<span data-ttu-id="f6900-103">Obtém um valor que indica se este `ICorDebugBreakpoint` está ativa.</span><span class="sxs-lookup"><span data-stu-id="f6900-103">Gets a value that indicates whether this `ICorDebugBreakpoint` is active.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6900-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f6900-104">Syntax</span></span>  
  
```cpp  
HRESULT IsActive (  
    [out] BOOL *pbActive  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f6900-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f6900-105">Parameters</span></span>  
 `pbActive`  
 <span data-ttu-id="f6900-106">[out] `true` se esse ponto de interrupção estiver ativa; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="f6900-106">[out] `true` if this breakpoint is active; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6900-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f6900-107">Requirements</span></span>  
 <span data-ttu-id="f6900-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6900-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6900-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f6900-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f6900-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f6900-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f6900-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6900-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
