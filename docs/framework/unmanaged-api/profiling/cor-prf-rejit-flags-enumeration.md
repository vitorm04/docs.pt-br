---
title: Enumeração COR_PRF_REJIT_FLAGS
ms.date: 08/06/2019
api_name:
- COR_PRF_REJIT_FLAGS Enumeration
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_REJIT_FLAGS
helpviewer_keywords:
- COR_PRF_REJIT_FLAGS enumeration [.NET Framework profiling]
topic_type:
- apiref
author: davmason
ms.author: davmason
ms.openlocfilehash: 1b1d6ad5d465d746f4c1a9400c43613591373322
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90546940"
---
# <a name="cor_prf_rejit_flags-enumeration"></a><span data-ttu-id="272c7-102">Enumeração COR_PRF_REJIT_FLAGS</span><span class="sxs-lookup"><span data-stu-id="272c7-102">COR_PRF_REJIT_FLAGS Enumeration</span></span>
<span data-ttu-id="272c7-103">Contém valores que indicam como a API [ICorProfilerInfo10:: RequestReJITWithInliners](icorprofilerinfo10-requestrejitwithinliners-method.md) deve se comportar.</span><span class="sxs-lookup"><span data-stu-id="272c7-103">Contains values that indicate how the [ICorProfilerInfo10::RequestReJITWithInliners](icorprofilerinfo10-requestrejitwithinliners-method.md) API should behave.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="272c7-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="272c7-104">Syntax</span></span>  
  
```cpp  
typedef enum  
{
    COR_PRF_REJIT_BLOCK_INLINING = 0x1,
    COR_PRF_REJIT_INLINING_CALLBACKS    = 0x2
} COR_PRF_REJIT_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="272c7-105">Membros</span><span class="sxs-lookup"><span data-stu-id="272c7-105">Members</span></span>  
  
|<span data-ttu-id="272c7-106">Membro</span><span class="sxs-lookup"><span data-stu-id="272c7-106">Member</span></span>|<span data-ttu-id="272c7-107">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="272c7-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_REJIT_BLOCK_INLINING`| <span data-ttu-id="272c7-108">Os métodos ReJITted serão impedidos de serem embutidos em outros métodos.</span><span class="sxs-lookup"><span data-stu-id="272c7-108">ReJITted methods will be blocked from being inlined in other methods.</span></span> |  
|`COR_PRF_REJIT_INLINING_CALLBACKS`| <span data-ttu-id="272c7-109">Receber `GetFunctionParameters` retornos de chamada para todos os métodos que embutiram os métodos solicitados a serem ReJITteddos.</span><span class="sxs-lookup"><span data-stu-id="272c7-109">Receive `GetFunctionParameters` callbacks for any methods that inline the methods requested to be ReJITted.</span></span> |  

## <a name="requirements"></a><span data-ttu-id="272c7-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="272c7-110">Requirements</span></span>  
 <span data-ttu-id="272c7-111">**Plataformas:** Consulte [sistemas operacionais com suporte do .NET Core](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="272c7-111">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>  
  
 <span data-ttu-id="272c7-112">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="272c7-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="272c7-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="272c7-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="272c7-114">**.NET Framework versões:**[!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="272c7-114">**.NET Framework Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span></span>
  
## <a name="see-also"></a><span data-ttu-id="272c7-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="272c7-115">See also</span></span>

- [<span data-ttu-id="272c7-116">Criando perfil de enumerações</span><span class="sxs-lookup"><span data-stu-id="272c7-116">Profiling Enumerations</span></span>](profiling-enumerations.md)
