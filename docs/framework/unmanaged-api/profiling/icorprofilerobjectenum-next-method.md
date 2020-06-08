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
ms.openlocfilehash: 850f05520e4146b5016bb574f02aa800dfcaaf32
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84494573"
---
# <a name="icorprofilerobjectenumnext-method"></a><span data-ttu-id="ec6f0-102">Método ICorProfilerObjectEnum::Next</span><span class="sxs-lookup"><span data-stu-id="ec6f0-102">ICorProfilerObjectEnum::Next Method</span></span>
<span data-ttu-id="ec6f0-103">Obtém o número especificado de objetos contíguos de uma coleção sequencial de objetos, começando na posição atual do enumerador na sequência.</span><span class="sxs-lookup"><span data-stu-id="ec6f0-103">Gets the specified number of contiguous objects from a sequential collection of objects, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec6f0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ec6f0-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG                    celt,  
    [out, size_is(celt), length_is(*pceltFetched)]
        ObjectID                  objects[],  
    [out] ULONG                   *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ec6f0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ec6f0-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="ec6f0-106">no O número de objetos a serem recuperados.</span><span class="sxs-lookup"><span data-stu-id="ec6f0-106">[in] The number of objects to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="ec6f0-107">fora Uma matriz de `ObjectID` valores, cada um representando um objeto recuperado.</span><span class="sxs-lookup"><span data-stu-id="ec6f0-107">[out] An array of `ObjectID` values, each of which represents a retrieved object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="ec6f0-108">fora Um ponteiro para o número de elementos realmente retornados na `objects` matriz.</span><span class="sxs-lookup"><span data-stu-id="ec6f0-108">[out] A pointer to the number of elements actually returned in the `objects` array.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec6f0-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ec6f0-109">Requirements</span></span>  
 <span data-ttu-id="ec6f0-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec6f0-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec6f0-111">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="ec6f0-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ec6f0-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ec6f0-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ec6f0-113">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec6f0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec6f0-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="ec6f0-114">See also</span></span>

- [<span data-ttu-id="ec6f0-115">Interface ICorProfilerObjectEnum</span><span class="sxs-lookup"><span data-stu-id="ec6f0-115">ICorProfilerObjectEnum Interface</span></span>](icorprofilerobjectenum-interface.md)
