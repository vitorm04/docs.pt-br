---
title: Enumeração COR_PRF_FINALIZER_FLAGS
ms.date: 03/30/2017
api_name:
- COR_PRF_FINALIZER_FLAGS
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_FINALIZER_FLAGS
helpviewer_keywords:
- COR_PRF_FINALIZER_FLAGS enumeration [.NET Framework profiling]
ms.assetid: 297d7721-3911-4f36-9e34-d9da0c33e22a
topic_type:
- apiref
ms.openlocfilehash: daca2849908a7798b588ff06f6e117d412db1b33
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867263"
---
# <a name="cor_prf_finalizer_flags-enumeration"></a><span data-ttu-id="d9605-102">Enumeração COR_PRF_FINALIZER_FLAGS</span><span class="sxs-lookup"><span data-stu-id="d9605-102">COR_PRF_FINALIZER_FLAGS Enumeration</span></span>
<span data-ttu-id="d9605-103">Descreve o finalizador de um objeto.</span><span class="sxs-lookup"><span data-stu-id="d9605-103">Describes the finalizer for an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9605-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d9605-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_FINALIZER_CRITICAL = 0x1  
} COR_PRF_FINALIZER_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="d9605-105">Membros</span><span class="sxs-lookup"><span data-stu-id="d9605-105">Members</span></span>  
  
|<span data-ttu-id="d9605-106">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9605-106">Member</span></span>|<span data-ttu-id="d9605-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="d9605-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FINALIZER_CRITICAL`|<span data-ttu-id="d9605-108">O finalizador é crítico.</span><span class="sxs-lookup"><span data-stu-id="d9605-108">The finalizer is critical.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d9605-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="d9605-109">Remarks</span></span>  
 <span data-ttu-id="d9605-110">A enumeração `COR_PRF_FINALIZER_FLAGS` é usada pelo método [ICorProfilerCallback2:: FinalizeableObjectQueued](icorprofilercallback2-finalizeableobjectqueued-method.md) para descrever o finalizador de um objeto.</span><span class="sxs-lookup"><span data-stu-id="d9605-110">The `COR_PRF_FINALIZER_FLAGS` enumeration is used by the [ICorProfilerCallback2::FinalizeableObjectQueued](icorprofilercallback2-finalizeableobjectqueued-method.md) method to describe the finalizer for an object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9605-111">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="d9605-111">Requirements</span></span>  
 <span data-ttu-id="d9605-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9605-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9605-113">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="d9605-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d9605-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d9605-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d9605-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9605-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9605-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="d9605-116">See also</span></span>

- [<span data-ttu-id="d9605-117">Criando perfil de enumerações</span><span class="sxs-lookup"><span data-stu-id="d9605-117">Profiling Enumerations</span></span>](profiling-enumerations.md)
