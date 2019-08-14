---
title: ICorProfilerInfo10::GetLOHObjectSizeThreshold
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.GetLOHObjectSizeThreshold
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: d6b6575cf04635b40b504b11bc415f61f05b4205
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68974016"
---
# <a name="icorprofilerinfo10getlohobjectsizethreshold-method"></a><span data-ttu-id="11ba0-102">Método ICorProfilerInfo10:: GetLOHObjectSizeThreshold</span><span class="sxs-lookup"><span data-stu-id="11ba0-102">ICorProfilerInfo10::GetLOHObjectSizeThreshold Method</span></span>
  
 <span data-ttu-id="11ba0-103">Obtém o valor do limite de LOH (heap de objeto grande) configurado.</span><span class="sxs-lookup"><span data-stu-id="11ba0-103">Gets the value of the configured large object heap (LOH) threshold.</span></span>   
  
## <a name="syntax"></a><span data-ttu-id="11ba0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="11ba0-104">Syntax</span></span>  
  
```cpp
HRESULT GetLOHObjectSizeThreshold( [out] DWORD *pThreshold );
```  
  
#### <a name="parameters"></a><span data-ttu-id="11ba0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="11ba0-105">Parameters</span></span>  
 `pThreshold` \
 <span data-ttu-id="11ba0-106">fora O limite de heap de objeto grande em bytes.</span><span class="sxs-lookup"><span data-stu-id="11ba0-106">[out] The large object heap threshold in bytes.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="11ba0-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="11ba0-107">Remarks</span></span>  
 <span data-ttu-id="11ba0-108">Os objetos maiores que o limite de heap de objeto grande serão alocados no heap de objeto grande.</span><span class="sxs-lookup"><span data-stu-id="11ba0-108">Objects larger than the large object heap threshold will be allocated on the large object heap.</span></span> <span data-ttu-id="11ba0-109">A partir do .NET Core 3,0, o limite de heap de objeto `pThreshold` grande é configurável, conterá o tamanho limite de heap de objeto grande ativo em bytes.</span><span class="sxs-lookup"><span data-stu-id="11ba0-109">Starting with .NET Core 3.0 the large object heap threshold is configurable, `pThreshold` will contain the active large object heap threshold size in bytes.</span></span>

## <a name="requirements"></a><span data-ttu-id="11ba0-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="11ba0-110">Requirements</span></span>  
 <span data-ttu-id="11ba0-111">**Compatíveis** Consulte [sistemas operacionais com suporte do .NET Core](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span><span class="sxs-lookup"><span data-stu-id="11ba0-111">**Platforms:** See [.NET Core supported operating systems](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span></span>  
  
 <span data-ttu-id="11ba0-112">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="11ba0-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="11ba0-113">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="11ba0-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="11ba0-114">**Versões do .net:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11ba0-114">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>
  
## <a name="see-also"></a><span data-ttu-id="11ba0-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="11ba0-115">See also</span></span>
- [<span data-ttu-id="11ba0-116">Interface ICorProfilerInfo10</span><span class="sxs-lookup"><span data-stu-id="11ba0-116">ICorProfilerInfo10 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-interface.md)

