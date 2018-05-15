---
title: Método ICorProfilerObjectEnum::Next
ms.date: 03/30/2017
api_name:
- ICorProfilerObjectEnum.Next
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerObjectEnum::Next
helpviewer_keywords:
- Next method, ICorProfilerObjectEnum interface [.NET Framework profiling]
- ICorProfilerObjectEnum::Next method [.NET Framework profiling]
ms.assetid: b420433c-5ebe-4986-bba1-97902e6db819
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: af896b67cda885613ffb268172c7773f2be17133
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerobjectenumnext-method"></a><span data-ttu-id="07f38-102">Método ICorProfilerObjectEnum::Next</span><span class="sxs-lookup"><span data-stu-id="07f38-102">ICorProfilerObjectEnum::Next Method</span></span>
<span data-ttu-id="07f38-103">Obtém o número especificado de contíguos objetos de uma coleção sequencial de objetos, a posição atual do enumerador na sequência.</span><span class="sxs-lookup"><span data-stu-id="07f38-103">Gets the specified number of contiguous objects from a sequential collection of objects, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07f38-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="07f38-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG                    celt,  
    [out, size_is(celt), length_is(*pceltFetched)]    
        ObjectID                  objects[],  
    [out] ULONG                   *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="07f38-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="07f38-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="07f38-106">[in] O número de objetos a serem recuperados.</span><span class="sxs-lookup"><span data-stu-id="07f38-106">[in] The number of objects to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="07f38-107">[out] Uma matriz de `ObjectID` valores, cada um deles representa um objeto recuperado.</span><span class="sxs-lookup"><span data-stu-id="07f38-107">[out] An array of `ObjectID` values, each of which represents a retrieved object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="07f38-108">[out] Um ponteiro para o número de elementos realmente retornados no `objects` matriz.</span><span class="sxs-lookup"><span data-stu-id="07f38-108">[out] A pointer to the number of elements actually returned in the `objects` array.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07f38-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="07f38-109">Requirements</span></span>  
 <span data-ttu-id="07f38-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="07f38-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07f38-111">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="07f38-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="07f38-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="07f38-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="07f38-113">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07f38-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07f38-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="07f38-114">See Also</span></span>  
 [<span data-ttu-id="07f38-115">Interface ICorProfilerObjectEnum</span><span class="sxs-lookup"><span data-stu-id="07f38-115">ICorProfilerObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)
