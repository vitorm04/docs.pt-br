---
title: "Criando perfil de enumerações"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- profiling enumerations [.NET Framework]
- enumerations [.NET Framework profiling]
- unmanaged enumerations [.NET Framework], profiling
ms.assetid: 8d5f9570-9853-4ce8-8101-df235d5b258e
caps.latest.revision: "21"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 84ac67b35bdbf686edb2fa35cc651aad4c19516b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="profiling-enumerations"></a><span data-ttu-id="8fcb7-102">Criando perfil de enumerações</span><span class="sxs-lookup"><span data-stu-id="8fcb7-102">Profiling Enumerations</span></span>
<span data-ttu-id="8fcb7-103">Esta seção descreve as enumerações não gerenciadas que a API de criação de perfis utiliza.</span><span class="sxs-lookup"><span data-stu-id="8fcb7-103">This section describes the unmanaged enumerations that the profiling API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8fcb7-104">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="8fcb7-104">In This Section</span></span>  
 [<span data-ttu-id="8fcb7-105">Enumeração COR_PRF_CLAUSE_TYPE</span><span class="sxs-lookup"><span data-stu-id="8fcb7-105">COR_PRF_CLAUSE_TYPE Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-clause-type-enumeration.md)  
 <span data-ttu-id="8fcb7-106">Indica o tipo de cláusula de exceção que o código acabou de inserir ou deixar.</span><span class="sxs-lookup"><span data-stu-id="8fcb7-106">Indicates the type of exception clause that the code has just entered or left.</span></span>  
  
 [<span data-ttu-id="8fcb7-107">Enumeração COR_PRF_CODEGEN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="8fcb7-107">COR_PRF_CODEGEN_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md)  
 <span data-ttu-id="8fcb7-108">Define os sinalizadores de geração de código que podem ser definidos com o [: Setcodegenflags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="8fcb7-108">Defines the code generation flags that can be set with the [ICorProfilerFunctionControl::SetCodegenFlags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) method.</span></span>  
  
 [<span data-ttu-id="8fcb7-109">Enumeração COR_PRF_FINALIZER_FLAGS</span><span class="sxs-lookup"><span data-stu-id="8fcb7-109">COR_PRF_FINALIZER_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-finalizer-flags-enumeration.md)  
 <span data-ttu-id="8fcb7-110">Descreve o finalizador de um objeto.</span><span class="sxs-lookup"><span data-stu-id="8fcb7-110">Describes the finalizer for an object.</span></span>  
  
 [<span data-ttu-id="8fcb7-111">Enumeração COR_PRF_GC_GENERATION</span><span class="sxs-lookup"><span data-stu-id="8fcb7-111">COR_PRF_GC_GENERATION Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md)  
 <span data-ttu-id="8fcb7-112">Identifica uma geração de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="8fcb7-112">Identifies a garbage collection generation.</span></span>  
  
 [<span data-ttu-id="8fcb7-113">Enumeração COR_PRF_GC_REASON</span><span class="sxs-lookup"><span data-stu-id="8fcb7-113">COR_PRF_GC_REASON Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-reason-enumeration.md)  
 <span data-ttu-id="8fcb7-114">Indica o motivo pelo qual essa coleta de lixo está ocorrendo.</span><span class="sxs-lookup"><span data-stu-id="8fcb7-114">Indicates the reason that garbage collection is occurring.</span></span>  
  
 [<span data-ttu-id="8fcb7-115">Enumeração COR_PRF_GC_ROOT_FLAGS</span><span class="sxs-lookup"><span data-stu-id="8fcb7-115">COR_PRF_GC_ROOT_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-flags-enumeration.md)  
 <span data-ttu-id="8fcb7-116">Indica propriedades de uma raiz do coletor de lixo.</span><span class="sxs-lookup"><span data-stu-id="8fcb7-116">Indicates properties of a garbage collector root.</span></span>  
  
 [<span data-ttu-id="8fcb7-117">Enumeração COR_PRF_GC_ROOT_KIND</span><span class="sxs-lookup"><span data-stu-id="8fcb7-117">COR_PRF_GC_ROOT_KIND Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-kind-enumeration.md)  
 <span data-ttu-id="8fcb7-118">Indica o tipo de coletor de lixo raiz que é exposto pelo [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="8fcb7-118">Indicates the kind of garbage collector root that is exposed by the [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) callback.</span></span>  
  
 [<span data-ttu-id="8fcb7-119">Enumeração COR_PRF_HIGH_MONITOR</span><span class="sxs-lookup"><span data-stu-id="8fcb7-119">COR_PRF_HIGH_MONITOR Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md)  
 <span data-ttu-id="8fcb7-120">Fornece sinalizadores além daqueles encontrados no [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeração que o criador de perfil pode especificar para o [ICorProfilerInfo5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) método quando ele está sendo carregado.</span><span class="sxs-lookup"><span data-stu-id="8fcb7-120">Provides flags in addition to those found in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration that the profiler can specify to the [ICorProfilerInfo5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method when it is loading.</span></span>  
  
 [<span data-ttu-id="8fcb7-121">Enumeração COR_PRF_JIT_CACHE</span><span class="sxs-lookup"><span data-stu-id="8fcb7-121">COR_PRF_JIT_CACHE Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-jit-cache-enumeration.md)  
 <span data-ttu-id="8fcb7-122">Indica o resultado de uma busca de função armazenada em cache.</span><span class="sxs-lookup"><span data-stu-id="8fcb7-122">Indicates the result of a cached function search.</span></span>  
  
 [<span data-ttu-id="8fcb7-123">Enumeração COR_PRF_MISC</span><span class="sxs-lookup"><span data-stu-id="8fcb7-123">COR_PRF_MISC Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-misc-enumeration.md)  
 <span data-ttu-id="8fcb7-124">Contém valores constantes que especificam identificadores especiais.</span><span class="sxs-lookup"><span data-stu-id="8fcb7-124">Contains constant values that specify special identifiers.</span></span>  
  
 [<span data-ttu-id="8fcb7-125">Enumeração COR_PRF_MODULE_FLAGS</span><span class="sxs-lookup"><span data-stu-id="8fcb7-125">COR_PRF_MODULE_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md)  
 <span data-ttu-id="8fcb7-126">Especifica as propriedades de um módulo.</span><span class="sxs-lookup"><span data-stu-id="8fcb7-126">Specifies the properties of a module.</span></span>  
  
 [<span data-ttu-id="8fcb7-127">Enumeração COR_PRF_MONITOR</span><span class="sxs-lookup"><span data-stu-id="8fcb7-127">COR_PRF_MONITOR Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)  
 <span data-ttu-id="8fcb7-128">Contém valores usados para especificar comportamentos, recursos ou eventos que o criador de perfis deseja assinar.</span><span class="sxs-lookup"><span data-stu-id="8fcb7-128">Contains values that are used to specify behavior, capabilities, or events to which the profiler wishes to subscribe.</span></span>  
  
 [<span data-ttu-id="8fcb7-129">Enumeração COR_PRF_RUNTIME_TYPE</span><span class="sxs-lookup"><span data-stu-id="8fcb7-129">COR_PRF_RUNTIME_TYPE Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-runtime-type-enumeration.md)  
 <span data-ttu-id="8fcb7-130">Contém valores que indicam a versão do tempo de execução da linguagem comum.</span><span class="sxs-lookup"><span data-stu-id="8fcb7-130">Contains values that indicate the version of the common language runtime.</span></span>  
  
 [<span data-ttu-id="8fcb7-131">Enumeração COR_PRF_SNAPSHOT_INFO</span><span class="sxs-lookup"><span data-stu-id="8fcb7-131">COR_PRF_SNAPSHOT_INFO Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-snapshot-info-enumeration.md)  
 <span data-ttu-id="8fcb7-132">Especifica a quantidade de dados repassada com um instantâneo da pilha em cada chamada para a função `StackSnapshotCallback` do criador de perfis.</span><span class="sxs-lookup"><span data-stu-id="8fcb7-132">Specifies how much data to pass back with a stack snapshot in each call to the profiler's `StackSnapshotCallback` function.</span></span>  
  
 [<span data-ttu-id="8fcb7-133">Enumeração COR_PRF_STATIC_TYPE</span><span class="sxs-lookup"><span data-stu-id="8fcb7-133">COR_PRF_STATIC_TYPE Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-static-type-enumeration.md)  
 <span data-ttu-id="8fcb7-134">Indica se um campo é estático e, em caso positivo, a qualidade estática aplicada ao campo.</span><span class="sxs-lookup"><span data-stu-id="8fcb7-134">Indicates whether a field is static and, if so, the static quality that applies to the field.</span></span>  
  
 [<span data-ttu-id="8fcb7-135">Enumeração COR_PRF_SUSPEND_REASON</span><span class="sxs-lookup"><span data-stu-id="8fcb7-135">COR_PRF_SUSPEND_REASON Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-suspend-reason-enumeration.md)  
 <span data-ttu-id="8fcb7-136">Indica o motivo pelo qual o tempo de execução foi suspenso.</span><span class="sxs-lookup"><span data-stu-id="8fcb7-136">Indicates the reason that the runtime was suspended.</span></span>  
  
 [<span data-ttu-id="8fcb7-137">Enumeração COR_PRF_TRANSITION_REASON</span><span class="sxs-lookup"><span data-stu-id="8fcb7-137">COR_PRF_TRANSITION_REASON Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md)  
 <span data-ttu-id="8fcb7-138">Indica o motivo para uma transição de código gerenciado para não gerenciado ou vice-versa.</span><span class="sxs-lookup"><span data-stu-id="8fcb7-138">Indicates the reason for a transition from managed to unmanaged code, or vice versa.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="8fcb7-139">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="8fcb7-139">Related Sections</span></span>  
 [<span data-ttu-id="8fcb7-140">Visão geral da criação de perfil</span><span class="sxs-lookup"><span data-stu-id="8fcb7-140">Profiling Overview</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [<span data-ttu-id="8fcb7-141">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="8fcb7-141">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
  
 [<span data-ttu-id="8fcb7-142">Criando perfil de funções estáticas globais</span><span class="sxs-lookup"><span data-stu-id="8fcb7-142">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
  
 [<span data-ttu-id="8fcb7-143">Estruturas de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="8fcb7-143">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
