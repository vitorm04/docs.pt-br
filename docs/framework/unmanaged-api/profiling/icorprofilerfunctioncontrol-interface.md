---
title: Interface ICorProfilerFunctionControl
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionControl
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionControl
helpviewer_keywords:
- ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: 4e3d3141-4662-4166-8f05-bc857c1b4216
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 37e0c9dcbd8975338e7c64dbd9c44dd54508b4d6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54649707"
---
# <a name="icorprofilerfunctioncontrol-interface"></a><span data-ttu-id="0ce1a-102">Interface ICorProfilerFunctionControl</span><span class="sxs-lookup"><span data-stu-id="0ce1a-102">ICorProfilerFunctionControl Interface</span></span>
<span data-ttu-id="0ce1a-103">Fornece métodos que permitem a um criador de perfis de código se comunicar com o tempo de execução de linguagem comum (CLR) para controlar como o compilador JIT deve gerar código ao recompilar um método específico.</span><span class="sxs-lookup"><span data-stu-id="0ce1a-103">Provides methods that allow a code profiler to communicate with the common language runtime (CLR) to control how the JIT compiler should generate code when recompiling a specific method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0ce1a-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="0ce1a-104">Methods</span></span>  
  
|<span data-ttu-id="0ce1a-105">Método</span><span class="sxs-lookup"><span data-stu-id="0ce1a-105">Method</span></span>|<span data-ttu-id="0ce1a-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ce1a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0ce1a-107">Método SetCodegenFlags</span><span class="sxs-lookup"><span data-stu-id="0ce1a-107">SetCodegenFlags Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md)|<span data-ttu-id="0ce1a-108">Define um ou mais sinalizadores do [COR_PRF_CODEGEN_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md) enumeração para controlar a geração de código para um just-in-time (JIT) recompilada função.</span><span class="sxs-lookup"><span data-stu-id="0ce1a-108">Sets one or more flags from the [COR_PRF_CODEGEN_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md) enumeration to control code generation for a just-in-time (JIT) recompiled function.</span></span>|  
|[<span data-ttu-id="0ce1a-109">Método SetILFunctionBody</span><span class="sxs-lookup"><span data-stu-id="0ce1a-109">SetILFunctionBody Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setilfunctionbody-method.md)|<span data-ttu-id="0ce1a-110">Substitui o corpo CIL (Common Intermediate Language) do método.</span><span class="sxs-lookup"><span data-stu-id="0ce1a-110">Replaces the Common Intermediate Language (CIL) body of the method.</span></span>|  
|[<span data-ttu-id="0ce1a-111">Método SetILInstrumentedCodeMap</span><span class="sxs-lookup"><span data-stu-id="0ce1a-111">SetILInstrumentedCodeMap Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md)|<span data-ttu-id="0ce1a-112">Define um mapa de códigos para a função especificada usando as entradas de mapa Common Intermediate Language (CIL) especificadas.</span><span class="sxs-lookup"><span data-stu-id="0ce1a-112">Sets a code map for the specified function by using the specified Common Intermediate Language (CIL) map entries.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0ce1a-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="0ce1a-113">Remarks</span></span>  
 <span data-ttu-id="0ce1a-114">A interface de `ICorProfilerFunctionControl` fornece métodos para controlar a geração de código para uma única função recompilada.</span><span class="sxs-lookup"><span data-stu-id="0ce1a-114">The `ICorProfilerFunctionControl` interface provides methods for controlling code generation for a single recompiled function.</span></span> <span data-ttu-id="0ce1a-115">O criador de perfil obtém uma instância dessa interface por meio de [ICorProfilerCallback4::GetReJITParameters](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="0ce1a-115">The profiler obtains an instance of this interface through the [ICorProfilerCallback4::GetReJITParameters](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) callback.</span></span> <span data-ttu-id="0ce1a-116">Cada instância do `ICorProfilerFunctionControl` controla todas as instâncias de uma função.</span><span class="sxs-lookup"><span data-stu-id="0ce1a-116">Each instance of `ICorProfilerFunctionControl` controls all instances of one function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ce1a-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0ce1a-117">Requirements</span></span>  
 <span data-ttu-id="0ce1a-118">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0ce1a-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ce1a-119">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0ce1a-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0ce1a-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0ce1a-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0ce1a-121">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ce1a-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ce1a-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ce1a-122">See also</span></span>
- [<span data-ttu-id="0ce1a-123">Interface ICorProfilerInfo4</span><span class="sxs-lookup"><span data-stu-id="0ce1a-123">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [<span data-ttu-id="0ce1a-124">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="0ce1a-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="0ce1a-125">Método EnumJITedFunctions2</span><span class="sxs-lookup"><span data-stu-id="0ce1a-125">EnumJITedFunctions2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md)
