---
title: Método ICorProfilerFunctionEnum::Skip
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionEnum.Skip Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum::Skip
helpviewer_keywords:
- Skip method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
- ICorProfilerFunctionEnum::Skip method [.NET Framework profiling]
ms.assetid: 051465b9-e479-494a-804b-c880323b4cbe
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f0e334c75afee60591db2b4e1f45cf0ec753ee2e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59141642"
---
# <a name="icorprofilerfunctionenumskip-method"></a><span data-ttu-id="55b4b-102">Método ICorProfilerFunctionEnum::Skip</span><span class="sxs-lookup"><span data-stu-id="55b4b-102">ICorProfilerFunctionEnum::Skip Method</span></span>
<span data-ttu-id="55b4b-103">Avança o cursor do enumerador de sua posição atual para que o número especificado de elementos é ignorado.</span><span class="sxs-lookup"><span data-stu-id="55b4b-103">Advances the enumerator's cursor from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55b4b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="55b4b-104">Syntax</span></span>  
  
```  
HRESULT Skip([in] ULONG celt);  
```  
  
## <a name="parameters"></a><span data-ttu-id="55b4b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="55b4b-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="55b4b-106">[in] O número de elementos a serem ignoradas.</span><span class="sxs-lookup"><span data-stu-id="55b4b-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="55b4b-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="55b4b-107">Return Value</span></span>  
 <span data-ttu-id="55b4b-108">Esse método retorna os HRESULTs específicos a seguir, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="55b4b-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="55b4b-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="55b4b-109">HRESULT</span></span>|<span data-ttu-id="55b4b-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="55b4b-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="55b4b-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="55b4b-111">S_OK</span></span>|<span data-ttu-id="55b4b-112">`celt` elementos foram ignorados.</span><span class="sxs-lookup"><span data-stu-id="55b4b-112">`celt` elements were skipped.</span></span>|  
|<span data-ttu-id="55b4b-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="55b4b-113">S_FALSE</span></span>|<span data-ttu-id="55b4b-114">Menos de `celt` elementos foram ignorados, que indica que não há mais nenhum elemento.</span><span class="sxs-lookup"><span data-stu-id="55b4b-114">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="55b4b-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="55b4b-115">Remarks</span></span>  
 <span data-ttu-id="55b4b-116">A nova posição do cursor deste enumerador é (posição atual) + `celt`.</span><span class="sxs-lookup"><span data-stu-id="55b4b-116">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55b4b-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="55b4b-117">Requirements</span></span>  
 <span data-ttu-id="55b4b-118">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="55b4b-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55b4b-119">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="55b4b-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="55b4b-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="55b4b-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="55b4b-121">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55b4b-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55b4b-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="55b4b-122">See also</span></span>

- [<span data-ttu-id="55b4b-123">Interface ICorProfilerFunctionEnum</span><span class="sxs-lookup"><span data-stu-id="55b4b-123">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="55b4b-124">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="55b4b-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
