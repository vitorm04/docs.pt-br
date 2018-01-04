---
title: "Método ICorProfilerInfo::GetFunctionFromIP"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetFunctionFromIP
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetFunctionFromIP
helpviewer_keywords:
- GetFunctionFromIP method [.NET Framework profiling]
- ICorProfilerInfo::GetFunctionFromIP method [.NET Framework profiling]
ms.assetid: f069802a-198f-46dd-9f09-4f77adffc9ba
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 144d80bb0e4111e319427d6a265d199b04b7f863
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfogetfunctionfromip-method"></a><span data-ttu-id="8750f-102">Método ICorProfilerInfo::GetFunctionFromIP</span><span class="sxs-lookup"><span data-stu-id="8750f-102">ICorProfilerInfo::GetFunctionFromIP Method</span></span>
<span data-ttu-id="8750f-103">Mapeia um ponteiro de instrução do código gerenciado para um `FunctionID`.</span><span class="sxs-lookup"><span data-stu-id="8750f-103">Maps a managed code instruction pointer to a `FunctionID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8750f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8750f-104">Syntax</span></span>  
  
```  
HRESULT GetFunctionFromIP(  
    [in]  LPCBYTE    ip,  
    [out] FunctionID *pFunctionId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8750f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8750f-105">Parameters</span></span>  
 `ip`  
 <span data-ttu-id="8750f-106">[in] O ponteiro de instrução em código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="8750f-106">[in] The instruction pointer in managed code.</span></span>  
  
 `pFunctionId`  
 <span data-ttu-id="8750f-107">[out] A ID de função retornado.</span><span class="sxs-lookup"><span data-stu-id="8750f-107">[out] The returned function ID.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8750f-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8750f-108">Requirements</span></span>  
 <span data-ttu-id="8750f-109">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8750f-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8750f-110">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8750f-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8750f-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8750f-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8750f-112">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8750f-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8750f-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8750f-113">See Also</span></span>  
 [<span data-ttu-id="8750f-114">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="8750f-114">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
