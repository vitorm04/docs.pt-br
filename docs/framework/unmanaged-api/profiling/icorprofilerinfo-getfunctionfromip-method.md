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
ms.openlocfilehash: 2b0859d2f6d4ea2abf72867f2a803132cbd04225
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54568641"
---
# <a name="icorprofilerinfogetfunctionfromip-method"></a><span data-ttu-id="a3907-102">Método ICorProfilerInfo::GetFunctionFromIP</span><span class="sxs-lookup"><span data-stu-id="a3907-102">ICorProfilerInfo::GetFunctionFromIP Method</span></span>
<span data-ttu-id="a3907-103">Mapeia um ponteiro de instrução de código gerenciado para um `FunctionID`.</span><span class="sxs-lookup"><span data-stu-id="a3907-103">Maps a managed code instruction pointer to a `FunctionID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3907-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a3907-104">Syntax</span></span>  
  
```  
HRESULT GetFunctionFromIP(  
    [in]  LPCBYTE    ip,  
    [out] FunctionID *pFunctionId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a3907-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a3907-105">Parameters</span></span>  
 `ip`  
 <span data-ttu-id="a3907-106">[in] O ponteiro de instrução em código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="a3907-106">[in] The instruction pointer in managed code.</span></span>  
  
 `pFunctionId`  
 <span data-ttu-id="a3907-107">[out] A ID da função retornada.</span><span class="sxs-lookup"><span data-stu-id="a3907-107">[out] The returned function ID.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3907-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a3907-108">Requirements</span></span>  
 <span data-ttu-id="a3907-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a3907-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3907-110">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a3907-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a3907-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a3907-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a3907-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3907-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3907-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a3907-113">See also</span></span>
- [<span data-ttu-id="a3907-114">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="a3907-114">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
