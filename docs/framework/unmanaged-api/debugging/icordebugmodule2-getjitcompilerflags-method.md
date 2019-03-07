---
title: Método ICorDebugModule2::GetJITCompilerFlags
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.GetJITCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::GetJITCompilerFlags
helpviewer_keywords:
- GetJITCompilerFlags method [.NET Framework debugging]
- ICorDebugModule2::GetJITCompilerFlags method [.NET Framework debugging]
ms.assetid: 7212d9f4-989b-44e3-b8d4-ffc35922f6a0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 77f4e745e4bd45be51b497fdd5bab95cd24c9685
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57475366"
---
# <a name="icordebugmodule2getjitcompilerflags-method"></a><span data-ttu-id="36273-102">Método ICorDebugModule2::GetJITCompilerFlags</span><span class="sxs-lookup"><span data-stu-id="36273-102">ICorDebugModule2::GetJITCompilerFlags Method</span></span>
<span data-ttu-id="36273-103">Obtém os sinalizadores que controlam a compilação just-in-time (JIT) deste ICorDebugModule2.</span><span class="sxs-lookup"><span data-stu-id="36273-103">Gets the flags that control the just-in-time (JIT) compilation of this ICorDebugModule2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36273-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="36273-104">Syntax</span></span>  
  
```  
HRESULT GetJITCompilerFlags (  
    [out] DWORD   *pdwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="36273-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="36273-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="36273-106">[out] Um ponteiro para um valor igual a [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) enumeração que controla a compilação JIT.</span><span class="sxs-lookup"><span data-stu-id="36273-106">[out] A pointer to a value of the [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) enumeration that controls the JIT compilation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36273-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="36273-107">Requirements</span></span>  
 <span data-ttu-id="36273-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="36273-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36273-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="36273-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="36273-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="36273-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="36273-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36273-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
