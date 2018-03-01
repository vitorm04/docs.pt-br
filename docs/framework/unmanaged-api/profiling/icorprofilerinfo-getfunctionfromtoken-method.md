---
title: "Método ICorProfilerInfo::GetFunctionFromToken"
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
- ICorProfilerInfo.GetFunctionFromToken
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetFunctionFromToken
helpviewer_keywords:
- ICorProfilerInfo::GetFunctionFromToken method [.NET Framework profiling]
- GetFunctionFromToken method, ICorProfilerInfo interface [.NET Framework profiling]
ms.assetid: 0eed759f-cce8-405d-88dc-9ee293a38928
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0c90a63f075c392ca3ff02a47190f9c4dfe6aad5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfogetfunctionfromtoken-method"></a><span data-ttu-id="602b2-102">Método ICorProfilerInfo::GetFunctionFromToken</span><span class="sxs-lookup"><span data-stu-id="602b2-102">ICorProfilerInfo::GetFunctionFromToken Method</span></span>
<span data-ttu-id="602b2-103">Obtém a ID de uma função.</span><span class="sxs-lookup"><span data-stu-id="602b2-103">Gets the ID of a function.</span></span> <span data-ttu-id="602b2-104">Este método está obsoleto no .NET Framework versão 2.0.</span><span class="sxs-lookup"><span data-stu-id="602b2-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="602b2-105">Use o [ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md) método em vez disso.</span><span class="sxs-lookup"><span data-stu-id="602b2-105">Use the [ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="602b2-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="602b2-106">Syntax</span></span>  
  
```  
HRESULT GetFunctionFromToken(  
    [in]  ModuleID   moduleId,  
    [in]  mdToken    token,  
    [out] FunctionID *pFunctionId);  
```  
  
## <a name="remarks"></a><span data-ttu-id="602b2-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="602b2-107">Remarks</span></span>  
 <span data-ttu-id="602b2-108">O `GetFunctionFromToken` método não funcionará para funções genéricas ou funções em tipos genéricos; agora é obsoleta.</span><span class="sxs-lookup"><span data-stu-id="602b2-108">The `GetFunctionFromToken` method will not work for generic functions or functions in generic types; it is now obsolete.</span></span> <span data-ttu-id="602b2-109">Use `ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs` para todas as funções.</span><span class="sxs-lookup"><span data-stu-id="602b2-109">Use `ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs` for all functions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="602b2-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="602b2-110">Requirements</span></span>  
 <span data-ttu-id="602b2-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="602b2-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="602b2-112">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="602b2-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="602b2-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="602b2-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="602b2-114">**Versões do .NET framework:** 1.1 e 1.0</span><span class="sxs-lookup"><span data-stu-id="602b2-114">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="602b2-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="602b2-115">See Also</span></span>  
 [<span data-ttu-id="602b2-116">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="602b2-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
