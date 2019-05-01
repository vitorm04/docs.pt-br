---
title: Método ICorProfilerInfo::GetFunctionFromIP
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetFunctionFromIP
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetFunctionFromIP
helpviewer_keywords:
- GetFunctionFromIP method [.NET Framework profiling]
- ICorProfilerInfo::GetFunctionFromIP method [.NET Framework profiling]
ms.assetid: f069802a-198f-46dd-9f09-4f77adffc9ba
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 23fb9c58f2eac904b63294434654f3caf1ba9f41
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61991855"
---
# <a name="icorprofilerinfogetfunctionfromip-method"></a><span data-ttu-id="eb0c4-102">Método ICorProfilerInfo::GetFunctionFromIP</span><span class="sxs-lookup"><span data-stu-id="eb0c4-102">ICorProfilerInfo::GetFunctionFromIP Method</span></span>
<span data-ttu-id="eb0c4-103">Mapeia um ponteiro de instrução de código gerenciado para um `FunctionID`.</span><span class="sxs-lookup"><span data-stu-id="eb0c4-103">Maps a managed code instruction pointer to a `FunctionID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb0c4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="eb0c4-104">Syntax</span></span>  
  
```  
HRESULT GetFunctionFromIP(  
    [in]  LPCBYTE    ip,  
    [out] FunctionID *pFunctionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eb0c4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="eb0c4-105">Parameters</span></span>  
 `ip`  
 <span data-ttu-id="eb0c4-106">[in] O ponteiro de instrução em código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="eb0c4-106">[in] The instruction pointer in managed code.</span></span>  
  
 `pFunctionId`  
 <span data-ttu-id="eb0c4-107">[out] A ID da função retornada.</span><span class="sxs-lookup"><span data-stu-id="eb0c4-107">[out] The returned function ID.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb0c4-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="eb0c4-108">Requirements</span></span>  
 <span data-ttu-id="eb0c4-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb0c4-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb0c4-110">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="eb0c4-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="eb0c4-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eb0c4-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eb0c4-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb0c4-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb0c4-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="eb0c4-113">See also</span></span>

- [<span data-ttu-id="eb0c4-114">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="eb0c4-114">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
