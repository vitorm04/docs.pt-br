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
ms.openlocfilehash: c49bdcb9345960bce018cefd4443948f997c7267
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428365"
---
# <a name="cor_prf_codegen_flags-enumeration"></a><span data-ttu-id="bc93a-102">Enumeração COR_PRF_CODEGEN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="bc93a-102">COR_PRF_CODEGEN_FLAGS Enumeration</span></span>
<span data-ttu-id="bc93a-103">Define os sinalizadores de geração de código que podem ser definidos com o método [ICorProfilerFunctionControl:: SetCodegenFlags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) .</span><span class="sxs-lookup"><span data-stu-id="bc93a-103">Defines the code generation flags that can be set with the [ICorProfilerFunctionControl::SetCodegenFlags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc93a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bc93a-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_CODEGEN_DISABLE_INLINING =          0x0001,  
    COR_PRF_CODEGEN_DISABLE_ALL_OPTIMIZATIONS = 0x0002,  
} COR_PRF_CODEGEN_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="bc93a-105">Membros</span><span class="sxs-lookup"><span data-stu-id="bc93a-105">Members</span></span>  
  
|<span data-ttu-id="bc93a-106">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="bc93a-106">Member</span></span>|<span data-ttu-id="bc93a-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="bc93a-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_CODEGEN_DISABLE_INLINING`|<span data-ttu-id="bc93a-108">Nenhuma função será embutida no corpo de uma dessas funções.</span><span class="sxs-lookup"><span data-stu-id="bc93a-108">No functions will be inlined into this function’s body.</span></span> <span data-ttu-id="bc93a-109">No entanto, a própria função pode ser embutida em seus chamadores.</span><span class="sxs-lookup"><span data-stu-id="bc93a-109">However, the function itself may be inlined into its callers.</span></span>|  
|`COR_PRF_CODEGEN_DISABLE_ALL_OPTIMIZATIONS`|<span data-ttu-id="bc93a-110">Todas as otimizações serão desabilitadas para o corpo da função.</span><span class="sxs-lookup"><span data-stu-id="bc93a-110">All optimizations will be disabled for this function’s body.</span></span> <span data-ttu-id="bc93a-111">No entanto, a função em si ainda pode ser embutida em seus chamadores.</span><span class="sxs-lookup"><span data-stu-id="bc93a-111">However, the function itself may still be inlined into its callers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bc93a-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="bc93a-112">Remarks</span></span>  
 <span data-ttu-id="bc93a-113">A enumeração `COR_PRF_CODEGEN_FLAGS` é usada pelo método [ICorProfilerFunctionControl:: SetCodegenFlags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) para permitir que o criador de perfil controle a geração de código para a função JIT-recompilada.</span><span class="sxs-lookup"><span data-stu-id="bc93a-113">The `COR_PRF_CODEGEN_FLAGS` enumeration is used by the [ICorProfilerFunctionControl::SetCodegenFlags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) method to enable the profiler to control the code generation for the JIT-recompiled function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc93a-114">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="bc93a-114">Requirements</span></span>  
 <span data-ttu-id="bc93a-115">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bc93a-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc93a-116">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="bc93a-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bc93a-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bc93a-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bc93a-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc93a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc93a-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bc93a-119">See also</span></span>

- [<span data-ttu-id="bc93a-120">Criando perfil de enumerações</span><span class="sxs-lookup"><span data-stu-id="bc93a-120">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
