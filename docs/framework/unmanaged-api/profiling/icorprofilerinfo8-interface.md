---
title: Interface ICorProfilerInfo8
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 210029ed1b1c7d780f3895f975f7a72227bbea80
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973816"
---
# <a name="icorprofilerinfo8-interface"></a><span data-ttu-id="2992b-102">Interface ICorProfilerInfo8</span><span class="sxs-lookup"><span data-stu-id="2992b-102">ICorProfilerInfo8 Interface</span></span>

<span data-ttu-id="2992b-103">Uma subclasse de [ICorProfilerInfo7](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md) que fornece métodos para consultar informações sobre métodos dinâmicos.</span><span class="sxs-lookup"><span data-stu-id="2992b-103">A subclass of [ICorProfilerInfo7](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md) that provides methods to query information about dynamic methods.</span></span>

## <a name="methods"></a><span data-ttu-id="2992b-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="2992b-104">Methods</span></span>  

| <span data-ttu-id="2992b-105">Método</span><span class="sxs-lookup"><span data-stu-id="2992b-105">Method</span></span>|<span data-ttu-id="2992b-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="2992b-106">Description</span></span>|  
| ------------|-----------------|  
|[<span data-ttu-id="2992b-107">Método IsFunctionDynamic</span><span class="sxs-lookup"><span data-stu-id="2992b-107">IsFunctionDynamic Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-isfunctiondynamic-method.md)| <span data-ttu-id="2992b-108">Determina se uma função não tem metadados associados.</span><span class="sxs-lookup"><span data-stu-id="2992b-108">Determines if a function does not have associated metadata.</span></span>|
|[<span data-ttu-id="2992b-109">Método GetFunctionFromIP3</span><span class="sxs-lookup"><span data-stu-id="2992b-109">GetFunctionFromIP3 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-getfunctionfromip3-method.md)| <span data-ttu-id="2992b-110">Mapeia um ponteiro de instrução de código gerenciado para uma FunctionID.</span><span class="sxs-lookup"><span data-stu-id="2992b-110">Maps a managed code instruction pointer to a FunctionID.</span></span> <span data-ttu-id="2992b-111">Esse método funciona para métodos dinâmicos e não dinâmicos.</span><span class="sxs-lookup"><span data-stu-id="2992b-111">This method works for both dynamic and non-dynamic methods.</span></span> |
|[<span data-ttu-id="2992b-112">Método GetDynamicFunctionInfo</span><span class="sxs-lookup"><span data-stu-id="2992b-112">GetDynamicFunctionInfo Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-getdynamicfunctioninfo-method.md)| <span data-ttu-id="2992b-113">Recupera informações sobre métodos dinâmicos.</span><span class="sxs-lookup"><span data-stu-id="2992b-113">Retrieves information about dynamic methods.</span></span> |

## <a name="requirements"></a><span data-ttu-id="2992b-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2992b-114">Requirements</span></span>  
<span data-ttu-id="2992b-115">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2992b-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="2992b-116">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2992b-116">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="2992b-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="2992b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
## <a name="see-also"></a><span data-ttu-id="2992b-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2992b-118">See also</span></span>
- [<span data-ttu-id="2992b-119">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="2992b-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
