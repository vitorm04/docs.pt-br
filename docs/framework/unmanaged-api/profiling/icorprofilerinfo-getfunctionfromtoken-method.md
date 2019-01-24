---
title: Método ICorProfilerInfo::GetFunctionFromToken
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 12f76059387f00316888cbe6d839bece33e3eef9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54520252"
---
# <a name="icorprofilerinfogetfunctionfromtoken-method"></a><span data-ttu-id="9197e-102">Método ICorProfilerInfo::GetFunctionFromToken</span><span class="sxs-lookup"><span data-stu-id="9197e-102">ICorProfilerInfo::GetFunctionFromToken Method</span></span>
<span data-ttu-id="9197e-103">Obtém a ID de uma função.</span><span class="sxs-lookup"><span data-stu-id="9197e-103">Gets the ID of a function.</span></span> <span data-ttu-id="9197e-104">Este método é obsoleto no .NET Framework versão 2.0.</span><span class="sxs-lookup"><span data-stu-id="9197e-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="9197e-105">Use o [ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md) método em vez disso.</span><span class="sxs-lookup"><span data-stu-id="9197e-105">Use the [ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9197e-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9197e-106">Syntax</span></span>  
  
```  
HRESULT GetFunctionFromToken(  
    [in]  ModuleID   moduleId,  
    [in]  mdToken    token,  
    [out] FunctionID *pFunctionId);  
```  
  
## <a name="remarks"></a><span data-ttu-id="9197e-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="9197e-107">Remarks</span></span>  
 <span data-ttu-id="9197e-108">O `GetFunctionFromToken` método não funcionará para funções em tipos genéricos ou funções genéricas; agora é obsoleta.</span><span class="sxs-lookup"><span data-stu-id="9197e-108">The `GetFunctionFromToken` method will not work for generic functions or functions in generic types; it is now obsolete.</span></span> <span data-ttu-id="9197e-109">Use `ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs` para todas as funções.</span><span class="sxs-lookup"><span data-stu-id="9197e-109">Use `ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs` for all functions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9197e-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9197e-110">Requirements</span></span>  
 <span data-ttu-id="9197e-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9197e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9197e-112">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9197e-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9197e-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9197e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9197e-114">**Versões do .NET framework:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="9197e-114">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9197e-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9197e-115">See also</span></span>
- [<span data-ttu-id="9197e-116">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="9197e-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
