---
title: "Método ICorDebugCode2::GetCompilerFlags"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugCode2.GetCompilerFlags
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugCode2::GetCompilerFlags
helpviewer_keywords:
- GetCompilerFlags method [.NET Framework debugging]
- ICorDebugCode2::GetCompilerFlags method [.NET Framework debugging]
ms.assetid: 532e9dfd-d114-4c75-b952-1accce102643
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b0e8d36b3551b3520213e1c2ffa7e2d215e8535b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcode2getcompilerflags-method"></a><span data-ttu-id="e853d-102">Método ICorDebugCode2::GetCompilerFlags</span><span class="sxs-lookup"><span data-stu-id="e853d-102">ICorDebugCode2::GetCompilerFlags Method</span></span>
<span data-ttu-id="e853d-103">Obtém os sinalizadores que especificam as condições sob as quais este objeto de código foi qualquer just-in-time (JIT) compilado ou gerado usando o gerador de imagem nativa (Ngen.exe).</span><span class="sxs-lookup"><span data-stu-id="e853d-103">Gets the flags that specify the conditions under which this code object was either just-in-time (JIT) compiled or generated using the native image generator (Ngen.exe).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e853d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e853d-104">Syntax</span></span>  
  
```  
HRESULT GetCompilerFlags (  
    [out] DWORD *pdwFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e853d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e853d-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="e853d-106">[out] Um ponteiro para um valor de [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) enumeração que especifica o comportamento do compilador JIT ou o gerador de imagem nativa.</span><span class="sxs-lookup"><span data-stu-id="e853d-106">[out] A pointer to a value of the [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) enumeration that specifies the behavior of the JIT compiler or the native image generator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e853d-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e853d-107">Requirements</span></span>  
 <span data-ttu-id="e853d-108">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e853d-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e853d-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e853d-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e853d-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e853d-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e853d-111">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e853d-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e853d-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e853d-112">See Also</span></span>  
 
