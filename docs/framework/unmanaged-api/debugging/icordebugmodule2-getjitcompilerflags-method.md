---
title: "Método ICorDebugModule2::GetJITCompilerFlags"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule2.GetJITCompilerFlags
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule2::GetJITCompilerFlags
helpviewer_keywords:
- GetJITCompilerFlags method [.NET Framework debugging]
- ICorDebugModule2::GetJITCompilerFlags method [.NET Framework debugging]
ms.assetid: 7212d9f4-989b-44e3-b8d4-ffc35922f6a0
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0a158b779ad85b8161d6f6ea8bf2dc4c1db1a283
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmodule2getjitcompilerflags-method"></a><span data-ttu-id="11a75-102">Método ICorDebugModule2::GetJITCompilerFlags</span><span class="sxs-lookup"><span data-stu-id="11a75-102">ICorDebugModule2::GetJITCompilerFlags Method</span></span>
<span data-ttu-id="11a75-103">Obtém os sinalizadores que controlam a compilação just-in-time (JIT) deste ICorDebugModule2.</span><span class="sxs-lookup"><span data-stu-id="11a75-103">Gets the flags that control the just-in-time (JIT) compilation of this ICorDebugModule2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11a75-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="11a75-104">Syntax</span></span>  
  
```  
HRESULT GetJITCompilerFlags (  
    [out] DWORD   *pdwFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="11a75-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="11a75-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="11a75-106">[out] Um ponteiro para um valor de [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) enumeração que controla a compilação JIT.</span><span class="sxs-lookup"><span data-stu-id="11a75-106">[out] A pointer to a value of the [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) enumeration that controls the JIT compilation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11a75-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="11a75-107">Requirements</span></span>  
 <span data-ttu-id="11a75-108">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11a75-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11a75-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="11a75-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="11a75-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="11a75-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="11a75-111">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11a75-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
