---
title: Método ICorProfilerThreadEnum::Skip
ms.date: 03/30/2017
api_name:
- ICorProfilerThreadEnum.Skip
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerThreadEnum::Skip
helpviewer_keywords:
- Skip method, ICorProfilerThreadEnum interface [.NET Framework profiling]
- ICorProfilerThreadEnum::Skip method [.NET Framework profiling]
ms.assetid: acb8b029-4a96-4ed7-ae3c-310204e5ceea
topic_type:
- apiref
ms.openlocfilehash: b08a501f7d55fbb193afd8c297ca7725348dac76
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76860899"
---
# <a name="icorprofilerthreadenumskip-method"></a><span data-ttu-id="d5cd6-102">Método ICorProfilerThreadEnum::Skip</span><span class="sxs-lookup"><span data-stu-id="d5cd6-102">ICorProfilerThreadEnum::Skip Method</span></span>
<span data-ttu-id="d5cd6-103">Avança o cursor do enumerador de sua posição atual para ignorar o número especificado de elementos.</span><span class="sxs-lookup"><span data-stu-id="d5cd6-103">Advances the enumerator's cursor from its current position to skip the specified number of elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5cd6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d5cd6-104">Syntax</span></span>  
  
```cpp  
HRESULT Skip (    [in] ULONG celt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d5cd6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d5cd6-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="d5cd6-106">no O número de elementos a serem ignorados.</span><span class="sxs-lookup"><span data-stu-id="d5cd6-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d5cd6-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="d5cd6-107">Return Value</span></span>  
 <span data-ttu-id="d5cd6-108">Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.</span><span class="sxs-lookup"><span data-stu-id="d5cd6-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="d5cd6-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d5cd6-109">HRESULT</span></span>|<span data-ttu-id="d5cd6-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="d5cd6-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d5cd6-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="d5cd6-111">S_OK</span></span>|<span data-ttu-id="d5cd6-112">`celt` elementos foram ignorados.</span><span class="sxs-lookup"><span data-stu-id="d5cd6-112">`celt` elements were skipped.</span></span>|  
|<span data-ttu-id="d5cd6-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="d5cd6-113">S_FALSE</span></span>|<span data-ttu-id="d5cd6-114">Menos de `celt` elementos foram ignorados, o que indica que não há mais elementos.</span><span class="sxs-lookup"><span data-stu-id="d5cd6-114">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d5cd6-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="d5cd6-115">Remarks</span></span>  
 <span data-ttu-id="d5cd6-116">A nova posição do cursor deste enumerador é (posição atual) + `celt`.</span><span class="sxs-lookup"><span data-stu-id="d5cd6-116">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5cd6-117">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="d5cd6-117">Requirements</span></span>  
 <span data-ttu-id="d5cd6-118">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5cd6-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5cd6-119">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="d5cd6-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d5cd6-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d5cd6-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d5cd6-121">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5cd6-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5cd6-122">Veja também</span><span class="sxs-lookup"><span data-stu-id="d5cd6-122">See also</span></span>

- [<span data-ttu-id="d5cd6-123">Interface ICorProfilerThreadEnum</span><span class="sxs-lookup"><span data-stu-id="d5cd6-123">ICorProfilerThreadEnum Interface</span></span>](icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="d5cd6-124">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="d5cd6-124">Profiling Interfaces</span></span>](profiling-interfaces.md)
