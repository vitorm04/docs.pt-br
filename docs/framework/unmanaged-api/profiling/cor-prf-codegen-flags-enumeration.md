---
title: Enumeração COR_PRF_CODEGEN_FLAGS
ms.date: 03/30/2017
api_name:
- COR_PRF_CODEGEN_FLAGS
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_CODEGEN_FLAGS
helpviewer_keywords:
- COR_PRF_CODEGEN_FLAGS enumeration [.NET Framework profiling]
ms.assetid: 3e184022-0247-4824-a23d-6b29593d8d01
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 321318b63368ed6e57d235cf97d94485352f8686
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59211355"
---
# <a name="corprfcodegenflags-enumeration"></a><span data-ttu-id="5d76b-102">Enumeração COR_PRF_CODEGEN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="5d76b-102">COR_PRF_CODEGEN_FLAGS Enumeration</span></span>
<span data-ttu-id="5d76b-103">Define os sinalizadores de geração de código que podem ser definidos com o [icorprofilerfunctioncontrol:: Setcodegenflags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="5d76b-103">Defines the code generation flags that can be set with the [ICorProfilerFunctionControl::SetCodegenFlags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d76b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5d76b-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_CODEGEN_DISABLE_INLINING =          0x0001,  
    COR_PRF_CODEGEN_DISABLE_ALL_OPTIMIZATIONS = 0x0002,  
} COR_PRF_CODEGEN_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="5d76b-105">Membros</span><span class="sxs-lookup"><span data-stu-id="5d76b-105">Members</span></span>  
  
|<span data-ttu-id="5d76b-106">Membro</span><span class="sxs-lookup"><span data-stu-id="5d76b-106">Member</span></span>|<span data-ttu-id="5d76b-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="5d76b-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_CODEGEN_DISABLE_INLINING`|<span data-ttu-id="5d76b-108">Não há funções serão embutidas no corpo dessa função.</span><span class="sxs-lookup"><span data-stu-id="5d76b-108">No functions will be inlined into this function’s body.</span></span> <span data-ttu-id="5d76b-109">No entanto, a função em si pode ser embutida em chamadores.</span><span class="sxs-lookup"><span data-stu-id="5d76b-109">However, the function itself may be inlined into its callers.</span></span>|  
|`COR_PRF_CODEGEN_DISABLE_ALL_OPTIMIZATIONS`|<span data-ttu-id="5d76b-110">Todas as otimizações serão desabilitadas para o corpo dessa função.</span><span class="sxs-lookup"><span data-stu-id="5d76b-110">All optimizations will be disabled for this function’s body.</span></span> <span data-ttu-id="5d76b-111">No entanto, a função em si ainda pode ser embutida em chamadores.</span><span class="sxs-lookup"><span data-stu-id="5d76b-111">However, the function itself may still be inlined into its callers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5d76b-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="5d76b-112">Remarks</span></span>  
 <span data-ttu-id="5d76b-113">O `COR_PRF_CODEGEN_FLAGS` enumeração é usada pelo [icorprofilerfunctioncontrol:: Setcodegenflags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) método para habilitar o criador de perfil controlar a geração de código para a função recompilado por JIT.</span><span class="sxs-lookup"><span data-stu-id="5d76b-113">The `COR_PRF_CODEGEN_FLAGS` enumeration is used by the [ICorProfilerFunctionControl::SetCodegenFlags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) method to enable the profiler to control the code generation for the JIT-recompiled function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d76b-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5d76b-114">Requirements</span></span>  
 <span data-ttu-id="5d76b-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d76b-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d76b-116">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5d76b-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5d76b-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5d76b-117">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="5d76b-118">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="5d76b-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5d76b-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5d76b-119">See also</span></span>

- [<span data-ttu-id="5d76b-120">Criando perfil de enumerações</span><span class="sxs-lookup"><span data-stu-id="5d76b-120">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
