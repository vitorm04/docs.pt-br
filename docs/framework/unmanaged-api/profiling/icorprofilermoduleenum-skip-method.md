---
title: Método ICorProfilerModuleEnum::Skip
ms.date: 03/30/2017
api_name:
- ICorProfilerModuleEnum.Skip Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerModuleEnum::Skip
helpviewer_keywords:
- Skip method, ICorProfilerModuleEnum interface [.NET Framework profiling]
- ICorProfilerModuleEnum::Skip method [.NET Framework profiling]
ms.assetid: 8dc29c6a-e2ba-41d8-a1e0-0fdd21421e0b
topic_type:
- apiref
ms.openlocfilehash: fb7a2a6d8bac7e9a67a5275694fc07e0f1d469e1
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76861327"
---
# <a name="icorprofilermoduleenumskip-method"></a><span data-ttu-id="873ea-102">Método ICorProfilerModuleEnum::Skip</span><span class="sxs-lookup"><span data-stu-id="873ea-102">ICorProfilerModuleEnum::Skip Method</span></span>
<span data-ttu-id="873ea-103">Avança o cursor do enumerador de sua posição atual para que o número especificado de elementos seja ignorado.</span><span class="sxs-lookup"><span data-stu-id="873ea-103">Advances the enumerator's cursor from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="873ea-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="873ea-104">Syntax</span></span>  
  
```cpp  
HRESULT Skip([in] ULONG celt);  
```  
  
## <a name="parameters"></a><span data-ttu-id="873ea-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="873ea-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="873ea-106">no O número de elementos a serem ignorados.</span><span class="sxs-lookup"><span data-stu-id="873ea-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="873ea-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="873ea-107">Return Value</span></span>  
 <span data-ttu-id="873ea-108">Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.</span><span class="sxs-lookup"><span data-stu-id="873ea-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="873ea-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="873ea-109">HRESULT</span></span>|<span data-ttu-id="873ea-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="873ea-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="873ea-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="873ea-111">S_OK</span></span>|<span data-ttu-id="873ea-112">`celt` elementos foram ignorados.</span><span class="sxs-lookup"><span data-stu-id="873ea-112">`celt` elements were skipped.</span></span>|  
|<span data-ttu-id="873ea-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="873ea-113">S_FALSE</span></span>|<span data-ttu-id="873ea-114">Menos de `celt` elementos foram ignorados, o que indica que não há mais elementos.</span><span class="sxs-lookup"><span data-stu-id="873ea-114">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="873ea-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="873ea-115">Remarks</span></span>  
 <span data-ttu-id="873ea-116">A nova posição do cursor deste enumerador é (posição atual) + `celt`.</span><span class="sxs-lookup"><span data-stu-id="873ea-116">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="873ea-117">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="873ea-117">Requirements</span></span>  
 <span data-ttu-id="873ea-118">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="873ea-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="873ea-119">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="873ea-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="873ea-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="873ea-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="873ea-121">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="873ea-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="873ea-122">Veja também</span><span class="sxs-lookup"><span data-stu-id="873ea-122">See also</span></span>

- [<span data-ttu-id="873ea-123">Interface ICorProfilerModuleEnum</span><span class="sxs-lookup"><span data-stu-id="873ea-123">ICorProfilerModuleEnum Interface</span></span>](icorprofilermoduleenum-interface.md)
- [<span data-ttu-id="873ea-124">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="873ea-124">Profiling Interfaces</span></span>](profiling-interfaces.md)
