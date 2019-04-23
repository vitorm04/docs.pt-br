---
title: Método ICorDebugCode2::GetCompilerFlags
ms.date: 03/30/2017
api_name:
- ICorDebugCode2.GetCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode2::GetCompilerFlags
helpviewer_keywords:
- GetCompilerFlags method [.NET Framework debugging]
- ICorDebugCode2::GetCompilerFlags method [.NET Framework debugging]
ms.assetid: 532e9dfd-d114-4c75-b952-1accce102643
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4733d59eb14f736f1369de82a7e9c677a65c3f86
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59093638"
---
# <a name="icordebugcode2getcompilerflags-method"></a><span data-ttu-id="0e583-102">Método ICorDebugCode2::GetCompilerFlags</span><span class="sxs-lookup"><span data-stu-id="0e583-102">ICorDebugCode2::GetCompilerFlags Method</span></span>
<span data-ttu-id="0e583-103">Obtém os sinalizadores que especificam as condições sob as quais esse objeto de código foi o just-in-time (JIT) compilados ou gerados usando o gerador de imagem nativa (Ngen.exe).</span><span class="sxs-lookup"><span data-stu-id="0e583-103">Gets the flags that specify the conditions under which this code object was either just-in-time (JIT) compiled or generated using the native image generator (Ngen.exe).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e583-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0e583-104">Syntax</span></span>  
  
```  
HRESULT GetCompilerFlags (  
    [out] DWORD *pdwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0e583-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0e583-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="0e583-106">[out] Um ponteiro para um valor igual a [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) enumeração que especifica o comportamento do compilador JIT ou o gerador de imagem nativa.</span><span class="sxs-lookup"><span data-stu-id="0e583-106">[out] A pointer to a value of the [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) enumeration that specifies the behavior of the JIT compiler or the native image generator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e583-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0e583-107">Requirements</span></span>  
 <span data-ttu-id="0e583-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e583-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e583-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0e583-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0e583-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0e583-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0e583-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e583-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e583-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0e583-112">See also</span></span>
