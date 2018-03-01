---
title: "Método ICorDebugBreakpointEnum::Next"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugBreakpointEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBreakpointEnum::Next
helpviewer_keywords:
- Next method, ICorDebugBreakpointEnum interface [.NET Framework debugging]
- ICorDebugBreakpointEnum::Next method [.NET Framework debugging]
ms.assetid: 2e6bbaea-79ba-448c-a0e3-7c90fc7c2939
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b81da25a630b034d4ec2f277f738a5337bdbec3e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugbreakpointenumnext-method"></a><span data-ttu-id="9b545-102">Método ICorDebugBreakpointEnum::Next</span><span class="sxs-lookup"><span data-stu-id="9b545-102">ICorDebugBreakpointEnum::Next Method</span></span>
<span data-ttu-id="9b545-103">Obtém o número especificado de instâncias de ICorDebugBreakpoint de enumeração, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="9b545-103">Gets the specified number of ICorDebugBreakpoint instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b545-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9b545-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugBreakpoint *breakpoints[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9b545-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9b545-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="9b545-106">[in] O número de `ICorDebugBreakpoint` instâncias a serem recuperados.</span><span class="sxs-lookup"><span data-stu-id="9b545-106">[in] The number of `ICorDebugBreakpoint` instances to be retrieved.</span></span>  
  
 `breakpoints`  
 <span data-ttu-id="9b545-107">[out] Uma matriz de ponteiros, cada qual apontando para um `ICorDebugBreakpoint` objeto que representa um ponto de interrupção.</span><span class="sxs-lookup"><span data-stu-id="9b545-107">[out] An array of pointers, each of which points to an `ICorDebugBreakpoint` object that represents a breakpoint.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="9b545-108">[out] Um ponteiro para o número de `ICorDebugBreakpoint` , na verdade, retornadas de instâncias.</span><span class="sxs-lookup"><span data-stu-id="9b545-108">[out] A pointer to the number of `ICorDebugBreakpoint` instances actually returned.</span></span> <span data-ttu-id="9b545-109">Esse valor pode ser null se `celt` é um.</span><span class="sxs-lookup"><span data-stu-id="9b545-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b545-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9b545-110">Requirements</span></span>  
 <span data-ttu-id="9b545-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b545-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b545-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9b545-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9b545-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9b545-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9b545-114">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b545-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
