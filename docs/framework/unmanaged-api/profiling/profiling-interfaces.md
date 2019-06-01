---
title: Criação de perfil de interfaces
ms.date: 04/10/2018
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], profiling
- profiling interfaces [.NET Framework]
- interfaces [.NET Framework profiling]
ms.assetid: d9303db8-e881-4217-91b7-8c7573c8ef9e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d97960a43e1d7ce625d96755a7c597a0425d0911
ms.sourcegitcommit: 518e7634b86d3980ec7da5f8c308cc1054daedb7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/01/2019
ms.locfileid: "66457469"
---
# <a name="profiling-interfaces"></a><span data-ttu-id="b4117-102">Criação de perfil de interfaces</span><span class="sxs-lookup"><span data-stu-id="b4117-102">Profiling Interfaces</span></span>
<span data-ttu-id="b4117-103">Esta seção descreve as interfaces não gerenciadas que permitem criar o perfil de um programa que está sendo executado no CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="b4117-103">This section describes the unmanaged interfaces that enable you to profile a program that is being executed by the common language runtime (CLR).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b4117-104">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="b4117-104">In This Section</span></span>  
 [<span data-ttu-id="b4117-105">Interface ICLRProfiling</span><span class="sxs-lookup"><span data-stu-id="b4117-105">ICLRProfiling Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-interface.md)  
 <span data-ttu-id="b4117-106">Fornece o [AttachProfiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) método, que permite que um criador de perfil anexar a um processo em execução.</span><span class="sxs-lookup"><span data-stu-id="b4117-106">Provides the [AttachProfiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) method, which enables a profiler to attach to a running process.</span></span>  
  
 [<span data-ttu-id="b4117-107">Interface ICorProfilerAssemblyReferenceProvider</span><span class="sxs-lookup"><span data-stu-id="b4117-107">ICorProfilerAssemblyReferenceProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md)  
 <span data-ttu-id="b4117-108">Permite que o criador de perfil informe ao CLR de referências de assembly que o criador de perfil será adicionado a [ICorProfilerCallback:: Moduleloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="b4117-108">Enables the profiler to inform the CLR of assembly references that the profiler will add in the [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>  
  
 [<span data-ttu-id="b4117-109">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="b4117-109">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 <span data-ttu-id="b4117-110">Fornece métodos usados pelo CLR para notificar um criador de perfis de código quando ocorrerem os eventos assinados pelo criador de perfis.</span><span class="sxs-lookup"><span data-stu-id="b4117-110">Provides methods that are used by the CLR to notify a code profiler when the events to which the profiler has subscribed occur.</span></span>  
  
 [<span data-ttu-id="b4117-111">Interface ICorProfilerCallback2</span><span class="sxs-lookup"><span data-stu-id="b4117-111">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)  
 <span data-ttu-id="b4117-112">Estende a interface `ICorProfilerCallback` com retornos de chamadas com suporte no .NET Framework 2.0 e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="b4117-112">Extends the `ICorProfilerCallback` interface with callbacks supported in the .NET Framework 2.0 and later versions.</span></span>  
  
 [<span data-ttu-id="b4117-113">Interface ICorProfilerCallback3</span><span class="sxs-lookup"><span data-stu-id="b4117-113">ICorProfilerCallback3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)  
 <span data-ttu-id="b4117-114">Fornece métodos de retorno de chamada que o CLR usa para comunicar anexação e desanexação de informações de estado ao criador de perfis.</span><span class="sxs-lookup"><span data-stu-id="b4117-114">Provides callback methods that the CLR uses to communicate attach and detach state information to the profiler.</span></span>  
  
 [<span data-ttu-id="b4117-115">Interface ICorProfilerCallback4</span><span class="sxs-lookup"><span data-stu-id="b4117-115">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)  
 <span data-ttu-id="b4117-116">Fornece métodos de retorno de chamada que o CLR usa para comunicar informações ao criador de perfis.</span><span class="sxs-lookup"><span data-stu-id="b4117-116">Provides callback methods that the CLR uses to communicate information to the profiler.</span></span>  
  
 [<span data-ttu-id="b4117-117">Interface ICorProfilerCallback5</span><span class="sxs-lookup"><span data-stu-id="b4117-117">ICorProfilerCallback5 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md)  
 <span data-ttu-id="b4117-118">Fornece um método que identifica o fechamento transitivo de objetos referenciados por raízes de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="b4117-118">Provides a method that identifies the transitive closure of objects referenced by garbage collection roots.</span></span>  
  
 [<span data-ttu-id="b4117-119">Interface ICorProfilerCallback6</span><span class="sxs-lookup"><span data-stu-id="b4117-119">ICorProfilerCallback6 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md)  
 <span data-ttu-id="b4117-120">Fornece um método de retorno de chamada que o CLR usa para notificar um criador de perfis de que um assembly está carregando.</span><span class="sxs-lookup"><span data-stu-id="b4117-120">Provides a callback method that the CLR uses to notify a profiler that an assembly is loading.</span></span>  
  
 [<span data-ttu-id="b4117-121">Interface ICorProfilerCallback7</span><span class="sxs-lookup"><span data-stu-id="b4117-121">ICorProfilerCallback7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-interface.md)  
 <span data-ttu-id="b4117-122">Fornece um método de retorno de chamada que o common language runtime usa para notificar o criador de perfil que o fluxo de símbolo associado a um módulo na memória é atualizado.</span><span class="sxs-lookup"><span data-stu-id="b4117-122">Provides a callback method that the common language runtime uses to notify the profiler that the symbol stream associated with an in-memory module is updated.</span></span>  

[<span data-ttu-id="b4117-123">Interface ICorProfilerCallback8</span><span class="sxs-lookup"><span data-stu-id="b4117-123">ICorProfilerCallback8 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback8-interface.md)  
<span data-ttu-id="b4117-124">Fornece métodos de retorno de chamada que o common language runtime usa para notificar o criador de perfil que a compilação JIT de um método dinâmico foi iniciado e concluído.</span><span class="sxs-lookup"><span data-stu-id="b4117-124">Provides callback methods that the common language runtime uses to notify the profiler that JIT compilation of a dynamic method has started and finished.</span></span>

[<span data-ttu-id="b4117-125">Interface ICorProfilerCallback9</span><span class="sxs-lookup"><span data-stu-id="b4117-125">ICorProfilerCallback9 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback9-interface.md)  
<span data-ttu-id="b4117-126">Fornece um método de retorno de chamada que o common language runtime usa para notificar o criador de perfil um método dinâmico é lixo coletado e, subsequentemente, foi descarregado.</span><span class="sxs-lookup"><span data-stu-id="b4117-126">Provides a callback method that the common language runtime uses to notify the profiler that a dynamic method is garbage collected and subsequently unloaded.</span></span>

 [<span data-ttu-id="b4117-127">Interface ICorProfilerFunctionControl</span><span class="sxs-lookup"><span data-stu-id="b4117-127">ICorProfilerFunctionControl Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md)  
 <span data-ttu-id="b4117-128">Fornece métodos que permitem um criador de perfis de código se comunicar com o CLR para controlar como o compilador JIT deve gerar código ao recompilar um método específico.</span><span class="sxs-lookup"><span data-stu-id="b4117-128">Provides methods that allow a code profiler to communicate with the CLR to control how the JIT compiler should generate code when recompiling a specific method.</span></span>  
  
 [<span data-ttu-id="b4117-129">Interface ICorProfilerFunctionEnum</span><span class="sxs-lookup"><span data-stu-id="b4117-129">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)  
 <span data-ttu-id="b4117-130">Fornece métodos para iterar de forma sequencial por meio de uma coleção de funções no CLR.</span><span class="sxs-lookup"><span data-stu-id="b4117-130">Provides methods to sequentially iterate through a collection of functions in the CLR.</span></span>  
  
 [<span data-ttu-id="b4117-131">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="b4117-131">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 <span data-ttu-id="b4117-132">Fornece métodos para uso por criadores de perfis de código para se comunicar com o CLR para controlar o monitoramento de eventos e solicitar informações.</span><span class="sxs-lookup"><span data-stu-id="b4117-132">Provides methods for use by code profilers to communicate with the CLR to control event monitoring and request information.</span></span>  
  
 [<span data-ttu-id="b4117-133">Interface ICorProfilerInfo2</span><span class="sxs-lookup"><span data-stu-id="b4117-133">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 <span data-ttu-id="b4117-134">Estende a interface de `ICorProfilerInfo` com métodos que têm suporte no .NET Framework 2.0 e em versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="b4117-134">Extends the `ICorProfilerInfo` interface with methods supported in the .NET Framework 2.0 and later versions.</span></span>  
  
 [<span data-ttu-id="b4117-135">Interface ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="b4117-135">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 <span data-ttu-id="b4117-136">Estende o `ICorProfilerInfo2` interface com métodos com suporte no .NET Framework 4 e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="b4117-136">Extends the `ICorProfilerInfo2` interface with methods supported in the .NET Framework 4 and later versions.</span></span>  
  
 [<span data-ttu-id="b4117-137">Interface ICorProfilerInfo4</span><span class="sxs-lookup"><span data-stu-id="b4117-137">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 <span data-ttu-id="b4117-138">Fornece métodos que os criadores de perfis de código usam para se comunicar com o CLR para controlar o monitoramento de eventos e solicitar informações.</span><span class="sxs-lookup"><span data-stu-id="b4117-138">Provides methods that code profilers use to communicate with the CLR to control event monitoring and to request information.</span></span>  
  
 [<span data-ttu-id="b4117-139">Interface ICorProfilerInfo5</span><span class="sxs-lookup"><span data-stu-id="b4117-139">ICorProfilerInfo5 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)  
 <span data-ttu-id="b4117-140">Fornece métodos para uso por criadores de perfis de código para se comunicar com o CLR para controlar o monitoramento de eventos.</span><span class="sxs-lookup"><span data-stu-id="b4117-140">Provides methods for use by code profilers to communicate with the CLR to control event monitoring.</span></span>  
  
 [<span data-ttu-id="b4117-141">Interface ICorProfilerInfo6</span><span class="sxs-lookup"><span data-stu-id="b4117-141">ICorProfilerInfo6 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md)  
 <span data-ttu-id="b4117-142">Fornece um enumerador para todos os métodos que pertencem a um determinado módulo do NGen e que são embutidos no corpo de um determinado método.</span><span class="sxs-lookup"><span data-stu-id="b4117-142">Provides an enumerator to all the methods that belong to a given NGen module and that are inlined in the body of a given method.</span></span>  
  
 [<span data-ttu-id="b4117-143">Interface ICorProfilerInfo7</span><span class="sxs-lookup"><span data-stu-id="b4117-143">ICorProfilerInfo7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)  
 <span data-ttu-id="b4117-144">Fornece um método para aplicar recentemente definido metadados para um módulo e que fornece acesso a um fluxo de símbolo na memória.</span><span class="sxs-lookup"><span data-stu-id="b4117-144">Provides a method to apply newly defined metadata to a module and that provides access to an in-memory symbol stream.</span></span>  
  
 [<span data-ttu-id="b4117-145">Interface ICorProfilerModuleEnum</span><span class="sxs-lookup"><span data-stu-id="b4117-145">ICorProfilerModuleEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)  
 <span data-ttu-id="b4117-146">Fornece métodos para iterar de forma sequencial por meio de uma coleção de módulos carregados pelo aplicativo ou pelo criador de perfis.</span><span class="sxs-lookup"><span data-stu-id="b4117-146">Provides methods to sequentially iterate through a collection of modules loaded by the application or the profiler.</span></span>  
  
 [<span data-ttu-id="b4117-147">Interface ICorProfilerObjectEnum</span><span class="sxs-lookup"><span data-stu-id="b4117-147">ICorProfilerObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)  
 <span data-ttu-id="b4117-148">Fornece métodos para iterar de forma sequencial por meio de uma coleção de objetos congelados que são gerados pelo [Ngen.exe (Native Image Generator)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md).</span><span class="sxs-lookup"><span data-stu-id="b4117-148">Provides methods to sequentially iterate through a collection of frozen objects that are generated by [Ngen.exe (Native Image Generator)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md).</span></span>  
  
 [<span data-ttu-id="b4117-149">Interface ICorProfilerThreadEnum</span><span class="sxs-lookup"><span data-stu-id="b4117-149">ICorProfilerThreadEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)  
 <span data-ttu-id="b4117-150">Fornece métodos para iterar de forma sequencial por meio de uma coleção de threads no CLR.</span><span class="sxs-lookup"><span data-stu-id="b4117-150">Provides methods to sequentially iterate through a collection of threads in the CLR.</span></span>  
  
 [<span data-ttu-id="b4117-151">Interface IMethodMalloc</span><span class="sxs-lookup"><span data-stu-id="b4117-151">IMethodMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md)  
 <span data-ttu-id="b4117-152">Fornece o [Alloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md) método alocar memória para um novo corpo de função do Microsoft intermediate language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="b4117-152">Provides the [Alloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md) method to allocate memory for a new Microsoft intermediate language (MSIL) function body.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b4117-153">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="b4117-153">Related Sections</span></span>  
 [<span data-ttu-id="b4117-154">Visão geral da criação de perfil</span><span class="sxs-lookup"><span data-stu-id="b4117-154">Profiling Overview</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [<span data-ttu-id="b4117-155">Criando perfil de funções estáticas globais</span><span class="sxs-lookup"><span data-stu-id="b4117-155">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
  
 [<span data-ttu-id="b4117-156">Criando perfil de enumerações</span><span class="sxs-lookup"><span data-stu-id="b4117-156">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)  
  
 [<span data-ttu-id="b4117-157">Estruturas de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="b4117-157">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
