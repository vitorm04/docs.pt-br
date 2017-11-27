---
title: "Enumeração COR_PRF_CODEGEN_FLAGS"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_PRF_CODEGEN_FLAGS
api_location: mscorwks.dll
api_type: COM
f1_keywords: COR_PRF_CODEGEN_FLAGS
helpviewer_keywords: COR_PRF_CODEGEN_FLAGS enumeration [.NET Framework profiling]
ms.assetid: 3e184022-0247-4824-a23d-6b29593d8d01
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c2c97510077fefd730827ac00326d267fd1c62ef
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="corprfcodegenflags-enumeration"></a><span data-ttu-id="1e2d5-102">Enumeração COR_PRF_CODEGEN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="1e2d5-102">COR_PRF_CODEGEN_FLAGS Enumeration</span></span>
<span data-ttu-id="1e2d5-103">Define os sinalizadores de geração de código que podem ser definidos com o [: Setcodegenflags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="1e2d5-103">Defines the code generation flags that can be set with the [ICorProfilerFunctionControl::SetCodegenFlags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e2d5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1e2d5-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_CODEGEN_DISABLE_INLINING =          0x0001,  
    COR_PRF_CODEGEN_DISABLE_ALL_OPTIMIZATIONS = 0x0002,  
} COR_PRF_CODEGEN_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="1e2d5-105">Membros</span><span class="sxs-lookup"><span data-stu-id="1e2d5-105">Members</span></span>  
  
|<span data-ttu-id="1e2d5-106">Membro</span><span class="sxs-lookup"><span data-stu-id="1e2d5-106">Member</span></span>|<span data-ttu-id="1e2d5-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="1e2d5-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_CODEGEN_DISABLE_INLINING`|<span data-ttu-id="1e2d5-108">Nenhuma função será embutida no corpo dessa função.</span><span class="sxs-lookup"><span data-stu-id="1e2d5-108">No functions will be inlined into this function’s body.</span></span> <span data-ttu-id="1e2d5-109">No entanto, a função em si pode ser embutida em seus chamadores.</span><span class="sxs-lookup"><span data-stu-id="1e2d5-109">However, the function itself may be inlined into its callers.</span></span>|  
|`COR_PRF_CODEGEN_DISABLE_ALL_OPTIMIZATIONS`|<span data-ttu-id="1e2d5-110">Todas as otimizações serão desabilitadas para o corpo desta função.</span><span class="sxs-lookup"><span data-stu-id="1e2d5-110">All optimizations will be disabled for this function’s body.</span></span> <span data-ttu-id="1e2d5-111">No entanto, a função em si ainda pode ser embutida em seus chamadores.</span><span class="sxs-lookup"><span data-stu-id="1e2d5-111">However, the function itself may still be inlined into its callers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1e2d5-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="1e2d5-112">Remarks</span></span>  
 <span data-ttu-id="1e2d5-113">O `COR_PRF_CODEGEN_FLAGS` enumeração é usada pelo [: Setcodegenflags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) método para permitir que o criador de perfil controlar a geração de código para a função recompilado JIT.</span><span class="sxs-lookup"><span data-stu-id="1e2d5-113">The `COR_PRF_CODEGEN_FLAGS` enumeration is used by the [ICorProfilerFunctionControl::SetCodegenFlags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) method to enable the profiler to control the code generation for the JIT-recompiled function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e2d5-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1e2d5-114">Requirements</span></span>  
 <span data-ttu-id="1e2d5-115">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1e2d5-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e2d5-116">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1e2d5-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1e2d5-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1e2d5-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1e2d5-118">**Versões do .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e2d5-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e2d5-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1e2d5-119">See Also</span></span>  
 [<span data-ttu-id="1e2d5-120">Enumerações de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="1e2d5-120">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
