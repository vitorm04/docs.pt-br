---
title: Depurando interfaces
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: b6297c26-7624-4431-8af4-14112d07bcd5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8b6d00d17615769a5d03d58e0eda5af62ca58368
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2019
ms.locfileid: "54415956"
---
# <a name="debugging-interfaces"></a><span data-ttu-id="1eb29-102">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="1eb29-102">Debugging Interfaces</span></span>
<span data-ttu-id="1eb29-103">Esta seção descreve as interfaces não gerenciadas que lidam com a depuração de um programa que está sendo executado no CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="1eb29-103">This section describes the unmanaged interfaces that handle the debugging of a program that is executing in the common language runtime (CLR).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1eb29-104">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="1eb29-104">In This Section</span></span>  
 [<span data-ttu-id="1eb29-105">Interface ICLRDataEnumMemoryRegions</span><span class="sxs-lookup"><span data-stu-id="1eb29-105">ICLRDataEnumMemoryRegions Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-interface.md)  
 <span data-ttu-id="1eb29-106">Fornece um método para enumerar as regiões da memória que são especificadas por chamadores.</span><span class="sxs-lookup"><span data-stu-id="1eb29-106">Provides a method to enumerate regions of memory that are specified by callers.</span></span>  
  
 [<span data-ttu-id="1eb29-107">Interface ICLRDataEnumMemoryRegionsCallback</span><span class="sxs-lookup"><span data-stu-id="1eb29-107">ICLRDataEnumMemoryRegionsCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md)  
 <span data-ttu-id="1eb29-108">Fornece um método de retorno de chamada para `EnumMemoryRegions` relatar ao depurador o resultado de uma tentativa de enumerar uma região especificada da memória.</span><span class="sxs-lookup"><span data-stu-id="1eb29-108">Provides a callback method for `EnumMemoryRegions` to report to the debugger, the result of an attempt to enumerate a specified region of memory.</span></span>  
  
 [<span data-ttu-id="1eb29-109">Interface ICLRDataTarget</span><span class="sxs-lookup"><span data-stu-id="1eb29-109">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)  
 <span data-ttu-id="1eb29-110">Fornece métodos para interação com um processo de CLR de destino.</span><span class="sxs-lookup"><span data-stu-id="1eb29-110">Provides methods for interaction with a target CLR process.</span></span>  
  
 [<span data-ttu-id="1eb29-111">Interface ICLRDataTarget2</span><span class="sxs-lookup"><span data-stu-id="1eb29-111">ICLRDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)  
 <span data-ttu-id="1eb29-112">Uma subclasse de `ICLRDataTarget` que é usada pela camada de serviços de acesso a dados para manipular as regiões de memória virtual no processo de destino.</span><span class="sxs-lookup"><span data-stu-id="1eb29-112">A subclass of `ICLRDataTarget` that is used by the data access services layer to manipulate virtual memory regions in the target process.</span></span>  
  
 [<span data-ttu-id="1eb29-113">Interface ICLRDataTarget3</span><span class="sxs-lookup"><span data-stu-id="1eb29-113">ICLRDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)  
 <span data-ttu-id="1eb29-114">Uma subclasse de [ICLRDataTarget2](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md) que fornece acesso a informações de exceção.</span><span class="sxs-lookup"><span data-stu-id="1eb29-114">A subclass of [ICLRDataTarget2](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md) that provides access to exception information.</span></span>  
  
 [<span data-ttu-id="1eb29-115">Interface ICLRDebugging</span><span class="sxs-lookup"><span data-stu-id="1eb29-115">ICLRDebugging Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-interface.md)  
 <span data-ttu-id="1eb29-116">Fornece métodos que manipulam os módulos de carregamento e descarregamento para depuração.</span><span class="sxs-lookup"><span data-stu-id="1eb29-116">Provides methods that handle loading and unloading modules for debugging.</span></span>  
  
 [<span data-ttu-id="1eb29-117">Interface ICLRDebuggingLibraryProvider</span><span class="sxs-lookup"><span data-stu-id="1eb29-117">ICLRDebuggingLibraryProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md)  
 <span data-ttu-id="1eb29-118">Inclui o [método ProvideLibrary](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md) método, que obtém um provedor de biblioteca de interface de retorno de chamada que permite que o common language runtime específica da versão bibliotecas de depuração ser localizada e carregada sob demanda.</span><span class="sxs-lookup"><span data-stu-id="1eb29-118">Includes the [ProvideLibrary Method](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md) method, which gets a library provider callback interface that allows common language runtime version-specific debugging libraries to be located and loaded on demand.</span></span>  
  
 [<span data-ttu-id="1eb29-119">Interface ICLRMetadataLocator</span><span class="sxs-lookup"><span data-stu-id="1eb29-119">ICLRMetadataLocator Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrmetadatalocator-interface.md)  
 <span data-ttu-id="1eb29-120">A interface usada pela camada de serviços de acesso a dados para localizar metadados de assemblies em um processo de destino.</span><span class="sxs-lookup"><span data-stu-id="1eb29-120">Interface used by the data access services layer to locate metadata of assemblies in a target process.</span></span>  
  
 [<span data-ttu-id="1eb29-121">Interface ICorDebug</span><span class="sxs-lookup"><span data-stu-id="1eb29-121">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 <span data-ttu-id="1eb29-122">Fornece métodos que permitem que os desenvolvedores depurem aplicativos no ambiente do CLR.</span><span class="sxs-lookup"><span data-stu-id="1eb29-122">Provides methods that allow developers to debug applications in the CLR environment.</span></span>  
  
 [<span data-ttu-id="1eb29-123">Interface1 ICorDebugAppDomain</span><span class="sxs-lookup"><span data-stu-id="1eb29-123">ICorDebugAppDomain Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-interface.md)  
 <span data-ttu-id="1eb29-124">Fornece métodos para depurar domínios de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1eb29-124">Provides methods for debugging application domains.</span></span>  
  
 [<span data-ttu-id="1eb29-125">Interface1 ICorDebugAppDomain2</span><span class="sxs-lookup"><span data-stu-id="1eb29-125">ICorDebugAppDomain2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain2-interface.md)  
 <span data-ttu-id="1eb29-126">Fornece métodos para trabalhar com matrizes, ponteiros, ponteiros de função e tipos ByRef.</span><span class="sxs-lookup"><span data-stu-id="1eb29-126">Provides methods to work with arrays, pointers, function pointers, and ByRef types.</span></span> <span data-ttu-id="1eb29-127">Essa interface é uma extensão da interface `ICorDebugAppDomain`.</span><span class="sxs-lookup"><span data-stu-id="1eb29-127">This interface is an extension of the `ICorDebugAppDomain` interface.</span></span>  
  
 [<span data-ttu-id="1eb29-128">Interface ICorDebugAppDomain3</span><span class="sxs-lookup"><span data-stu-id="1eb29-128">ICorDebugAppDomain3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)  
 <span data-ttu-id="1eb29-129">Fornece métodos para trabalhar com os tipos [!INCLUDE[wrt](../../../../includes/wrt-md.md)] em um domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1eb29-129">Provides methods to work with the [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types in an application domain.</span></span> <span data-ttu-id="1eb29-130">Essa interface é uma extensão das interfaces `ICorDebugAppDomain` e `ICorDebugAppDomain2`.</span><span class="sxs-lookup"><span data-stu-id="1eb29-130">This interface is an extension of the `ICorDebugAppDomain` and `ICorDebugAppDomain2` interfaces.</span></span>  
  
 [<span data-ttu-id="1eb29-131">Interface ICorDebugAppDomain4</span><span class="sxs-lookup"><span data-stu-id="1eb29-131">ICorDebugAppDomain4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain4-interface.md)  
 <span data-ttu-id="1eb29-132">Estende logicamente a [ICorDebugAppDomain](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-interface.md) interface para obter um objeto gerenciado de um COM callable wrapper.</span><span class="sxs-lookup"><span data-stu-id="1eb29-132">Logically extends the [ICorDebugAppDomain](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-interface.md) interface to get a managed object from a COM callable wrapper.</span></span>  
  
 [<span data-ttu-id="1eb29-133">Interface1 ICorDebugAppDomainEnum</span><span class="sxs-lookup"><span data-stu-id="1eb29-133">ICorDebugAppDomainEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomainenum-interface.md)  
 <span data-ttu-id="1eb29-134">Fornece um método que retorna um número especificado de valores `ICorDebugAppDomain` iniciando no próximo local na enumeração.</span><span class="sxs-lookup"><span data-stu-id="1eb29-134">Provides a method that returns a specified number of `ICorDebugAppDomain` values starting at the next location in the enumeration.</span></span>  
  
 [<span data-ttu-id="1eb29-135">Interface1 ICorDebugArrayValue</span><span class="sxs-lookup"><span data-stu-id="1eb29-135">ICorDebugArrayValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-interface.md)  
 <span data-ttu-id="1eb29-136">Uma subclasse de `ICorDebugHeapValue` que representa uma matriz unidimensional ou multidimensional.</span><span class="sxs-lookup"><span data-stu-id="1eb29-136">A subclass of `ICorDebugHeapValue` that represents a single-dimensional or multi-dimensional array.</span></span>  
  
 [<span data-ttu-id="1eb29-137">Interface1 ICorDebugAssembly</span><span class="sxs-lookup"><span data-stu-id="1eb29-137">ICorDebugAssembly Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-interface.md)  
 <span data-ttu-id="1eb29-138">Representa um assembly.</span><span class="sxs-lookup"><span data-stu-id="1eb29-138">Represents an assembly.</span></span>  
  
 [<span data-ttu-id="1eb29-139">Interface1 ICorDebugAssembly2</span><span class="sxs-lookup"><span data-stu-id="1eb29-139">ICorDebugAssembly2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly2-interface.md)  
 <span data-ttu-id="1eb29-140">Representa um assembly.</span><span class="sxs-lookup"><span data-stu-id="1eb29-140">Represents an assembly.</span></span> <span data-ttu-id="1eb29-141">Essa interface é uma extensão da interface `ICorDebugAssembly`.</span><span class="sxs-lookup"><span data-stu-id="1eb29-141">This interface is an extension of the `ICorDebugAssembly` interface.</span></span>  
  
 [<span data-ttu-id="1eb29-142">Interface ICorDebugAssembly3</span><span class="sxs-lookup"><span data-stu-id="1eb29-142">ICorDebugAssembly3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)  
 <span data-ttu-id="1eb29-143">Estende logicamente a [ICorDebugAssembly](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-interface.md) interface para fornecer suporte para assemblies de contêiner e seus assemblies contidos.</span><span class="sxs-lookup"><span data-stu-id="1eb29-143">Logically extends the [ICorDebugAssembly](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-interface.md) interface to provide support for container assemblies and their contained assemblies.</span></span> <span data-ttu-id="1eb29-144">**Disponível em apenas .NET nativo.**</span><span class="sxs-lookup"><span data-stu-id="1eb29-144">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="1eb29-145">Interface1 ICorDebugAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="1eb29-145">ICorDebugAssemblyEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassemblyenum-interface.md)  
 <span data-ttu-id="1eb29-146">Implementa métodos `ICorDebugEnum` e enumera matrizes de `ICorDebugAssembly`.</span><span class="sxs-lookup"><span data-stu-id="1eb29-146">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugAssembly` arrays.</span></span>  
  
 [<span data-ttu-id="1eb29-147">Interface ICorDebugBlockingObjectEnum</span><span class="sxs-lookup"><span data-stu-id="1eb29-147">ICorDebugBlockingObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-interface.md)  
 <span data-ttu-id="1eb29-148">Fornece um enumerador para uma lista dos [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) estruturas.</span><span class="sxs-lookup"><span data-stu-id="1eb29-148">Provides an enumerator for a list of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span>  
  
 [<span data-ttu-id="1eb29-149">Interface1 ICorDebugBoxValue</span><span class="sxs-lookup"><span data-stu-id="1eb29-149">ICorDebugBoxValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugboxvalue-interface.md)  
 <span data-ttu-id="1eb29-150">Uma subclasse de `ICorDebugHeapValue` que representa um objeto de classe com valor boxed.</span><span class="sxs-lookup"><span data-stu-id="1eb29-150">A subclass of `ICorDebugHeapValue` that represents a boxed value class object.</span></span>  
  
 [<span data-ttu-id="1eb29-151">Interface1 ICorDebugBreakpoint</span><span class="sxs-lookup"><span data-stu-id="1eb29-151">ICorDebugBreakpoint Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-interface.md)  
 <span data-ttu-id="1eb29-152">Representa um ponto de interrupção em uma função ou um ponto de inspeção em um valor.</span><span class="sxs-lookup"><span data-stu-id="1eb29-152">Represents a breakpoint in a function or a watch point on a value.</span></span>  
  
 [<span data-ttu-id="1eb29-153">Interface1 ICorDebugBreakpointEnum</span><span class="sxs-lookup"><span data-stu-id="1eb29-153">ICorDebugBreakpointEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpointenum-interface.md)  
 <span data-ttu-id="1eb29-154">Implementa métodos `ICorDebugEnum` e enumera matrizes de `ICorDebugBreakpoint`.</span><span class="sxs-lookup"><span data-stu-id="1eb29-154">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugBreakpoint` arrays.</span></span>  
  
 [<span data-ttu-id="1eb29-155">Interface1 ICorDebugChain</span><span class="sxs-lookup"><span data-stu-id="1eb29-155">ICorDebugChain Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-interface.md)  
 <span data-ttu-id="1eb29-156">Representa um segmento de uma pilha de chamadas física ou lógica.</span><span class="sxs-lookup"><span data-stu-id="1eb29-156">Represents a segment of a physical or logical call stack.</span></span>  
  
 [<span data-ttu-id="1eb29-157">Interface1 ICorDebugChainEnum</span><span class="sxs-lookup"><span data-stu-id="1eb29-157">ICorDebugChainEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchainenum-interface.md)  
 <span data-ttu-id="1eb29-158">Implementa métodos `ICorDebugEnum` e enumera matrizes de `ICorDebugChain`.</span><span class="sxs-lookup"><span data-stu-id="1eb29-158">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugChain` arrays.</span></span>  
  
 [<span data-ttu-id="1eb29-159">Interface1 ICorDebugClass</span><span class="sxs-lookup"><span data-stu-id="1eb29-159">ICorDebugClass Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md)  
 <span data-ttu-id="1eb29-160">Representa um tipo, que pode ser básico ou complexo (isto é, definido pelo usuário).</span><span class="sxs-lookup"><span data-stu-id="1eb29-160">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="1eb29-161">Se o tipo for genérico, `ICorDebugClass` representará o tipo genérico sem instância.</span><span class="sxs-lookup"><span data-stu-id="1eb29-161">If the type is generic, `ICorDebugClass` represents the uninstantiated generic type.</span></span>  
  
 [<span data-ttu-id="1eb29-162">Interface1 ICorDebugClass2</span><span class="sxs-lookup"><span data-stu-id="1eb29-162">ICorDebugClass2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass2-interface.md)  
 <span data-ttu-id="1eb29-163">Representa uma classe genérica ou uma classe com um parâmetro do método do tipo <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="1eb29-163">Represents a generic class or a class with a method parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="1eb29-164">Essa interface estende `ICorDebugClass`.</span><span class="sxs-lookup"><span data-stu-id="1eb29-164">This interface extends `ICorDebugClass`.</span></span>  
  
 [<span data-ttu-id="1eb29-165">Interface1 ICorDebugCode</span><span class="sxs-lookup"><span data-stu-id="1eb29-165">ICorDebugCode Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md)  
 <span data-ttu-id="1eb29-166">Representa um segmento de código MSIL (Microsoft Intermediate Language) ou código nativo.</span><span class="sxs-lookup"><span data-stu-id="1eb29-166">Represents a segment of either Microsoft intermediate language (MSIL) code or native code.</span></span>  
  
 [<span data-ttu-id="1eb29-167">Interface1 ICorDebugCode2</span><span class="sxs-lookup"><span data-stu-id="1eb29-167">ICorDebugCode2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-interface.md)  
 <span data-ttu-id="1eb29-168">Fornece métodos que estendem os recursos de `ICorDebugCode`.</span><span class="sxs-lookup"><span data-stu-id="1eb29-168">Provides methods that extend the capabilities of `ICorDebugCode`.</span></span>  
  
 [<span data-ttu-id="1eb29-169">Interface ICorDebugCode3</span><span class="sxs-lookup"><span data-stu-id="1eb29-169">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)  
 <span data-ttu-id="1eb29-170">Fornece um método que estende [ICorDebugCode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md) e [ICorDebugCode2](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-interface.md) para fornecer informações sobre um valor de retorno gerenciado.</span><span class="sxs-lookup"><span data-stu-id="1eb29-170">Provides a method that extends [ICorDebugCode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md) and [ICorDebugCode2](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-interface.md) to provide information about a managed return value.</span></span>  
  
 [<span data-ttu-id="1eb29-171">Interface ICorDebugCode4</span><span class="sxs-lookup"><span data-stu-id="1eb29-171">ICorDebugCode4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-interface.md)  
 <span data-ttu-id="1eb29-172">Fornece um método que permite que um depurador enumerar as variáveis locais e os argumentos em uma função.</span><span class="sxs-lookup"><span data-stu-id="1eb29-172">Provides a method that enables a debugger to enumerate the local variables and arguments in a function.</span></span>  
  
 [<span data-ttu-id="1eb29-173">Interface1 ICorDebugCodeEnum</span><span class="sxs-lookup"><span data-stu-id="1eb29-173">ICorDebugCodeEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcodeenum-interface.md)  
 <span data-ttu-id="1eb29-174">Implementa métodos `ICorDebugEnum` e enumera matrizes de `ICorDebugCode`.</span><span class="sxs-lookup"><span data-stu-id="1eb29-174">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugCode` arrays.</span></span>  
  
 [<span data-ttu-id="1eb29-175">Interface ICorDebugComObjectValue</span><span class="sxs-lookup"><span data-stu-id="1eb29-175">ICorDebugComObjectValue Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-interface.md)  
 <span data-ttu-id="1eb29-176">Fornece métodos para recuperar objetos da interface armazenados em cache.</span><span class="sxs-lookup"><span data-stu-id="1eb29-176">Provides methods to retrieve cached interface objects.</span></span>  
  
 [<span data-ttu-id="1eb29-177">Interface1 ICorDebugContext</span><span class="sxs-lookup"><span data-stu-id="1eb29-177">ICorDebugContext Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontext-interface.md)  
 <span data-ttu-id="1eb29-178">Representa um objeto de contexto.</span><span class="sxs-lookup"><span data-stu-id="1eb29-178">Represents a context object.</span></span> <span data-ttu-id="1eb29-179">Essa interface ainda não foi implementada.</span><span class="sxs-lookup"><span data-stu-id="1eb29-179">This interface has not been implemented yet.</span></span>  
  
 [<span data-ttu-id="1eb29-180">Interface1 ICorDebugController</span><span class="sxs-lookup"><span data-stu-id="1eb29-180">ICorDebugController Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-interface.md)  
 <span data-ttu-id="1eb29-181">Representa um escopo, um <xref:System.Diagnostics.Process> ou um <xref:System.AppDomain>, em que o contexto de execução de código pode ser controlado.</span><span class="sxs-lookup"><span data-stu-id="1eb29-181">Represents a scope, either a <xref:System.Diagnostics.Process> or an <xref:System.AppDomain>, in which code execution context can be controlled.</span></span>  
  
 [<span data-ttu-id="1eb29-182">Interface ICorDebugDataTarget</span><span class="sxs-lookup"><span data-stu-id="1eb29-182">ICorDebugDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)  
 <span data-ttu-id="1eb29-183">Fornece uma interface de retorno de chamada que oferece acesso a um determinado processo de destino.</span><span class="sxs-lookup"><span data-stu-id="1eb29-183">Provides a callback interface that provides access to a particular target process.</span></span>  
  
 [<span data-ttu-id="1eb29-184">Interface ICorDebugDataTarget2</span><span class="sxs-lookup"><span data-stu-id="1eb29-184">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)  
 <span data-ttu-id="1eb29-185">Estende logicamente a [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="1eb29-185">Logically extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface.</span></span> <span data-ttu-id="1eb29-186">**Disponível em apenas .NET nativo.**</span><span class="sxs-lookup"><span data-stu-id="1eb29-186">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="1eb29-187">Interface ICorDebugDataTarget3</span><span class="sxs-lookup"><span data-stu-id="1eb29-187">ICorDebugDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget3-interface.md)  
 <span data-ttu-id="1eb29-188">Estende logicamente a [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface para fornecer informações sobre os módulos carregados.</span><span class="sxs-lookup"><span data-stu-id="1eb29-188">Logically extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface to provide information about loaded modules.</span></span> <span data-ttu-id="1eb29-189">**Disponível em apenas .NET nativo.**</span><span class="sxs-lookup"><span data-stu-id="1eb29-189">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="1eb29-190">Interface ICorDebugDebugEvent</span><span class="sxs-lookup"><span data-stu-id="1eb29-190">ICorDebugDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)  
 <span data-ttu-id="1eb29-191">Define a interface base da qual derivam todos os eventos de depuração `ICorDebug`.</span><span class="sxs-lookup"><span data-stu-id="1eb29-191">Defines the base interface from which all `ICorDebug` debug events derive.</span></span> <span data-ttu-id="1eb29-192">**Disponível em apenas .NET nativo.**</span><span class="sxs-lookup"><span data-stu-id="1eb29-192">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="1eb29-193">Interface ICorDebugEditAndContinueErrorInfo</span><span class="sxs-lookup"><span data-stu-id="1eb29-193">ICorDebugEditAndContinueErrorInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeditandcontinueerrorinfo-interface.md)  
 <span data-ttu-id="1eb29-194">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="1eb29-194">Obsolete.</span></span> <span data-ttu-id="1eb29-195">Não use essa interface.</span><span class="sxs-lookup"><span data-stu-id="1eb29-195">Do not use this interface.</span></span>  
  
 [<span data-ttu-id="1eb29-196">Interface1 ICorDebugEditAndContinueSnapshot</span><span class="sxs-lookup"><span data-stu-id="1eb29-196">ICorDebugEditAndContinueSnapshot Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeditandcontinuesnapshot-interface.md)  
 <span data-ttu-id="1eb29-197">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="1eb29-197">Obsolete.</span></span> <span data-ttu-id="1eb29-198">Não use essa interface.</span><span class="sxs-lookup"><span data-stu-id="1eb29-198">Do not use this interface.</span></span>  
  
 [<span data-ttu-id="1eb29-199">Interface1 ICorDebugEnum</span><span class="sxs-lookup"><span data-stu-id="1eb29-199">ICorDebugEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-interface1.md)  
 <span data-ttu-id="1eb29-200">Serve como a interface da base abstrata para depurar enumeradores.</span><span class="sxs-lookup"><span data-stu-id="1eb29-200">Serves as the abstract base interface for debugging enumerators.</span></span>  
  
 [<span data-ttu-id="1eb29-201">Interface1 ICorDebugErrorInfoEnum</span><span class="sxs-lookup"><span data-stu-id="1eb29-201">ICorDebugErrorInfoEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugerrorinfoenum-interface.md)  
 <span data-ttu-id="1eb29-202">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="1eb29-202">Obsolete.</span></span> <span data-ttu-id="1eb29-203">Não use essa interface.</span><span class="sxs-lookup"><span data-stu-id="1eb29-203">Do not use this interface.</span></span>  
  
 [<span data-ttu-id="1eb29-204">Interface1 ICorDebugEval</span><span class="sxs-lookup"><span data-stu-id="1eb29-204">ICorDebugEval Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-interface.md)  
 <span data-ttu-id="1eb29-205">Fornece métodos para permitir que o depurador execute um código no contexto do código que está sendo depurado.</span><span class="sxs-lookup"><span data-stu-id="1eb29-205">Provides methods to enable the debugger to execute code within the context of the code being debugged.</span></span>  
  
 [<span data-ttu-id="1eb29-206">Interface1 ICorDebugEval2</span><span class="sxs-lookup"><span data-stu-id="1eb29-206">ICorDebugEval2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-interface.md)  
 <span data-ttu-id="1eb29-207">Estende `ICorDebugEval` para fornecer suporte a tipos genéricos.</span><span class="sxs-lookup"><span data-stu-id="1eb29-207">Extends `ICorDebugEval` to provide support for generic types.</span></span>  
  
 [<span data-ttu-id="1eb29-208">Interface ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="1eb29-208">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
 <span data-ttu-id="1eb29-209">Estende o [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface para oferecer suporte a eventos de exceção.</span><span class="sxs-lookup"><span data-stu-id="1eb29-209">Extends the [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface to support exception events.</span></span> <span data-ttu-id="1eb29-210">**Disponível em apenas .NET nativo.**</span><span class="sxs-lookup"><span data-stu-id="1eb29-210">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="1eb29-211">Interface ICorDebugExceptionObjectCallStackEnum</span><span class="sxs-lookup"><span data-stu-id="1eb29-211">ICorDebugExceptionObjectCallStackEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md)  
 <span data-ttu-id="1eb29-212">Fornece um enumerador para informações de pilha de chamadas que são inseridas em um objeto de exceção.</span><span class="sxs-lookup"><span data-stu-id="1eb29-212">Provides an enumerator for call stack information that is embedded in an exception object.</span></span>  
  
 [<span data-ttu-id="1eb29-213">Interface ICorDebugExceptionObjectValue</span><span class="sxs-lookup"><span data-stu-id="1eb29-213">ICorDebugExceptionObjectValue Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-interface.md)  
 <span data-ttu-id="1eb29-214">Estende o [ICorDebugObjectValue](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-interface.md) interface para fornecer informações de rastreamento de pilha de um objeto de exceção gerenciada.</span><span class="sxs-lookup"><span data-stu-id="1eb29-214">Extends the [ICorDebugObjectValue](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-interface.md) interface to provide stack trace information from a managed exception object.</span></span>  
  
 [<span data-ttu-id="1eb29-215">Interface1 ICorDebugFrame</span><span class="sxs-lookup"><span data-stu-id="1eb29-215">ICorDebugFrame Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-interface.md)  
 <span data-ttu-id="1eb29-216">Representa um quadro na pilha atual.</span><span class="sxs-lookup"><span data-stu-id="1eb29-216">Represents a frame on the current stack.</span></span>  
  
 [<span data-ttu-id="1eb29-217">Interface1 ICorDebugFrameEnum</span><span class="sxs-lookup"><span data-stu-id="1eb29-217">ICorDebugFrameEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframeenum-interface.md)  
 <span data-ttu-id="1eb29-218">Implementa métodos `ICorDebugEnum` e enumera matrizes de `ICorDebugFrame`.</span><span class="sxs-lookup"><span data-stu-id="1eb29-218">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugFrame` arrays.</span></span>  
  
 [<span data-ttu-id="1eb29-219">Interface1 ICorDebugFunction</span><span class="sxs-lookup"><span data-stu-id="1eb29-219">ICorDebugFunction Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-interface1.md)  
 <span data-ttu-id="1eb29-220">Representa uma função ou um método gerenciado.</span><span class="sxs-lookup"><span data-stu-id="1eb29-220">Represents a managed function or method.</span></span>  
  
 [<span data-ttu-id="1eb29-221">Interface1 ICorDebugFunction2</span><span class="sxs-lookup"><span data-stu-id="1eb29-221">ICorDebugFunction2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-interface.md)  
 <span data-ttu-id="1eb29-222">Estende `ICorDebugFunction` logicamente para fornecer suporte à depuração passo a passo Apenas Meu Código.</span><span class="sxs-lookup"><span data-stu-id="1eb29-222">Logically extends `ICorDebugFunction` to provide support for Just My Code step-through debugging.</span></span>  
  
 [<span data-ttu-id="1eb29-223">Interface ICorDebugFunction3</span><span class="sxs-lookup"><span data-stu-id="1eb29-223">ICorDebugFunction3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction3-interface.md)  
 <span data-ttu-id="1eb29-224">Estende logicamente a [ICorDebugFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-interface1.md) interface para fornecer acesso ao código de uma solicitação ReJIT.</span><span class="sxs-lookup"><span data-stu-id="1eb29-224">Logically extends the [ICorDebugFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-interface1.md) interface to provide access to code from a ReJIT request.</span></span>  
  
 [<span data-ttu-id="1eb29-225">Interface1 ICorDebugFunctionBreakpoint</span><span class="sxs-lookup"><span data-stu-id="1eb29-225">ICorDebugFunctionBreakpoint Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunctionbreakpoint-interface.md)  
 <span data-ttu-id="1eb29-226">Estende `ICorDebugBreakpoint` para fornecer suporte a pontos de interrupção dentro de funções.</span><span class="sxs-lookup"><span data-stu-id="1eb29-226">Extends `ICorDebugBreakpoint` to support breakpoints within functions.</span></span>  
  
 [<span data-ttu-id="1eb29-227">Interface ICorDebugGCReferenceEnum</span><span class="sxs-lookup"><span data-stu-id="1eb29-227">ICorDebugGCReferenceEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)  
 <span data-ttu-id="1eb29-228">Fornece um enumerador para objetos que serão coletados do lixo.</span><span class="sxs-lookup"><span data-stu-id="1eb29-228">Provides an enumerator for objects that will be garbage-collected.</span></span>  
  
 [<span data-ttu-id="1eb29-229">Interface1 ICorDebugGenericValue</span><span class="sxs-lookup"><span data-stu-id="1eb29-229">ICorDebugGenericValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-interface.md)  
 <span data-ttu-id="1eb29-230">Uma subclasse de `ICorDebugValue` que se aplica a todos os valores.</span><span class="sxs-lookup"><span data-stu-id="1eb29-230">A subclass of `ICorDebugValue` that applies to all values.</span></span> <span data-ttu-id="1eb29-231">Essa interface fornece métodos Get e Set para o valor.</span><span class="sxs-lookup"><span data-stu-id="1eb29-231">This interface provides Get and Set methods for the value.</span></span>  
  
 [<span data-ttu-id="1eb29-232">Interface ICorDebugGuidToTypeEnum</span><span class="sxs-lookup"><span data-stu-id="1eb29-232">ICorDebugGuidToTypeEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)  
 <span data-ttu-id="1eb29-233">Fornece um enumerador para um objeto que mapeia GUIDs e seus objetos `ICorDebugType` correspondentes.</span><span class="sxs-lookup"><span data-stu-id="1eb29-233">Provides an enumerator for an object that maps GUIDs and their corresponding `ICorDebugType` objects.</span></span>  
  
 [<span data-ttu-id="1eb29-234">Interface1 ICorDebugHandleValue</span><span class="sxs-lookup"><span data-stu-id="1eb29-234">ICorDebugHandleValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-interface.md)  
 <span data-ttu-id="1eb29-235">Uma subclasse de `ICorDebugReferenceValue` que representa um valor de referência para o qual o depurador criou um identificador para coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="1eb29-235">A subclass of `ICorDebugReferenceValue` that represents a reference value to which the debugger has created a handle for garbage collection.</span></span>  
  
 [<span data-ttu-id="1eb29-236">Interface ICorDebugHeapEnum</span><span class="sxs-lookup"><span data-stu-id="1eb29-236">ICorDebugHeapEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)  
 <span data-ttu-id="1eb29-237">Fornece um enumerador para objetos no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="1eb29-237">Provides an enumerator for objects on the managed heap.</span></span>  
  
 [<span data-ttu-id="1eb29-238">Interface ICorDebugHeapSegmentEnum</span><span class="sxs-lookup"><span data-stu-id="1eb29-238">ICorDebugHeapSegmentEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)  
 <span data-ttu-id="1eb29-239">Fornece um enumerador para regiões de memória do heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="1eb29-239">Provides an enumerator for the memory regions of the managed heap.</span></span>  
  
 [<span data-ttu-id="1eb29-240">Interface1 ICorDebugHeapValue</span><span class="sxs-lookup"><span data-stu-id="1eb29-240">ICorDebugHeapValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue-interface.md)  
 <span data-ttu-id="1eb29-241">Uma subclasse de `ICorDebugValue` que representa um objeto coletado pelo coletor de lixo do CLR.</span><span class="sxs-lookup"><span data-stu-id="1eb29-241">A subclass of `ICorDebugValue` that represents an object that has been collected by the CLR garbage collector.</span></span>  
  
 [<span data-ttu-id="1eb29-242">Interface1 ICorDebugHeapValue2</span><span class="sxs-lookup"><span data-stu-id="1eb29-242">ICorDebugHeapValue2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue2-interface1.md)  
 <span data-ttu-id="1eb29-243">Uma extensão de `ICorDebugHeapValue` que fornece suporte aos identificadores de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="1eb29-243">An extension of `ICorDebugHeapValue` that provides support for runtime handles.</span></span>  
  
 [<span data-ttu-id="1eb29-244">Interface ICorDebugHeapValue3</span><span class="sxs-lookup"><span data-stu-id="1eb29-244">ICorDebugHeapValue3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-interface.md)  
 <span data-ttu-id="1eb29-245">Expõe as propriedades de bloqueio de monitoramento de objetos.</span><span class="sxs-lookup"><span data-stu-id="1eb29-245">Exposes the monitor lock properties of objects.</span></span>  
  
 [<span data-ttu-id="1eb29-246">Interface ICorDebugILCode</span><span class="sxs-lookup"><span data-stu-id="1eb29-246">ICorDebugILCode Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md)  
 <span data-ttu-id="1eb29-247">Representa um segmento de código IL (Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="1eb29-247">Represents a segment of intermediate language (IL) code.</span></span>  
  
 [<span data-ttu-id="1eb29-248">Interface ICorDebugILCode2</span><span class="sxs-lookup"><span data-stu-id="1eb29-248">ICorDebugILCode2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-interface.md)  
 <span data-ttu-id="1eb29-249">Estende logicamente a [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) deslocamentos ao IL do método original de interface para fornecer métodos que retornam o token de assinatura de variável local de uma função e que mapeiam instrumentada IL (linguagem intermediária) do criador de perfil deslocamentos.</span><span class="sxs-lookup"><span data-stu-id="1eb29-249">Logically extends the [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) interface to provide methods that return the token for a function's local variable signature, and that map a profiler's instrumented intermediate language (IL) offsets to original method IL offsets.</span></span>  
  
 [<span data-ttu-id="1eb29-250">Interface1 ICorDebugILFrame</span><span class="sxs-lookup"><span data-stu-id="1eb29-250">ICorDebugILFrame Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-interface.md)  
 <span data-ttu-id="1eb29-251">Representa um registro de ativação do código MSIL.</span><span class="sxs-lookup"><span data-stu-id="1eb29-251">Represents a stack frame of MSIL code.</span></span>  
  
 [<span data-ttu-id="1eb29-252">Interface1 ICorDebugILFrame2</span><span class="sxs-lookup"><span data-stu-id="1eb29-252">ICorDebugILFrame2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-interface.md)  
 <span data-ttu-id="1eb29-253">Uma extensão lógica de `ICorDebugILFrame`.</span><span class="sxs-lookup"><span data-stu-id="1eb29-253">A logical extension of `ICorDebugILFrame`.</span></span>  
  
 [<span data-ttu-id="1eb29-254">Interface ICorDebugILFrame3</span><span class="sxs-lookup"><span data-stu-id="1eb29-254">ICorDebugILFrame3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-interface.md)  
 <span data-ttu-id="1eb29-255">Fornece um método que encapsula o valor de retorno de uma função.</span><span class="sxs-lookup"><span data-stu-id="1eb29-255">Provides a method that encapsulates the return value of a function.</span></span>  
  
 [<span data-ttu-id="1eb29-256">Interface ICorDebugILFrame4</span><span class="sxs-lookup"><span data-stu-id="1eb29-256">ICorDebugILFrame4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)  
 <span data-ttu-id="1eb29-257">Fornece métodos que permitem acessar as variáveis locais e inserir o código em um registro de ativação de código IL.</span><span class="sxs-lookup"><span data-stu-id="1eb29-257">Provides methods that allow you to access the local variables and code in a stack frame of intermediate language (IL) code.</span></span> <span data-ttu-id="1eb29-258">Um parâmetro especifica se o depurador possui acesso às variáveis e ao código adicionados na instrumentação do criador de perfil ReJIT.</span><span class="sxs-lookup"><span data-stu-id="1eb29-258">A parameter specifies whether the debugger has access to variables and code added in profiler ReJIT instrumentation.</span></span>  
  
 [<span data-ttu-id="1eb29-259">Interface ICorDebugInstanceFieldSymbol</span><span class="sxs-lookup"><span data-stu-id="1eb29-259">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)  
 <span data-ttu-id="1eb29-260">Representa as informações de símbolo de depuração de um campo de instância.</span><span class="sxs-lookup"><span data-stu-id="1eb29-260">Represents the debug symbol information for an instance field.</span></span> <span data-ttu-id="1eb29-261">**Disponível em apenas .NET nativo.**</span><span class="sxs-lookup"><span data-stu-id="1eb29-261">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="1eb29-262">Interface1 ICorDebugInternalFrame</span><span class="sxs-lookup"><span data-stu-id="1eb29-262">ICorDebugInternalFrame Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-interface.md)  
 <span data-ttu-id="1eb29-263">Identifica os tipos de quadro para o depurador.</span><span class="sxs-lookup"><span data-stu-id="1eb29-263">Identifies frame types for the debugger.</span></span>  
  
 [<span data-ttu-id="1eb29-264">Interface ICorDebugInternalFrame2</span><span class="sxs-lookup"><span data-stu-id="1eb29-264">ICorDebugInternalFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md)  
 <span data-ttu-id="1eb29-265">Fornece informações sobre os quadros internos, incluindo o endereço de pilha e a posição em relação ao [ICorDebugFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-interface.md) objetos.</span><span class="sxs-lookup"><span data-stu-id="1eb29-265">Provides information about internal frames, including stack address and position in relation to [ICorDebugFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-interface.md) objects.</span></span>  
  
 [<span data-ttu-id="1eb29-266">Interface ICorDebugLoadedModule</span><span class="sxs-lookup"><span data-stu-id="1eb29-266">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)  
 <span data-ttu-id="1eb29-267">Fornece informações sobre um módulo carregado.</span><span class="sxs-lookup"><span data-stu-id="1eb29-267">Provides information about a loaded module.</span></span> <span data-ttu-id="1eb29-268">**Disponível em apenas .NET nativo.**</span><span class="sxs-lookup"><span data-stu-id="1eb29-268">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="1eb29-269">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="1eb29-269">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)  
 <span data-ttu-id="1eb29-270">Fornece métodos para processar retornos de chamada do depurador.</span><span class="sxs-lookup"><span data-stu-id="1eb29-270">Provides methods to process debugger callbacks.</span></span>  
  
 [<span data-ttu-id="1eb29-271">Interface ICorDebugManagedCallback2</span><span class="sxs-lookup"><span data-stu-id="1eb29-271">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 <span data-ttu-id="1eb29-272">Fornece métodos para oferecer suporte à manipulação de exceção do depurador e aos assistentes de depuração gerenciados (MDAs).</span><span class="sxs-lookup"><span data-stu-id="1eb29-272">Provides methods to support debugger exception handling and managed debugging assistants (MDAs).</span></span> <span data-ttu-id="1eb29-273">`ICorDebugManagedCallback2` é uma extensão lógica de `ICorDebugManagedCallback`.</span><span class="sxs-lookup"><span data-stu-id="1eb29-273">`ICorDebugManagedCallback2` is a logical extension of `ICorDebugManagedCallback`.</span></span>  
  
 [<span data-ttu-id="1eb29-274">Interface ICorDebugManagedCallback3</span><span class="sxs-lookup"><span data-stu-id="1eb29-274">ICorDebugManagedCallback3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-interface.md)  
 <span data-ttu-id="1eb29-275">Fornece um método de retorno de chamada que indica que uma notificação personalizada ativada do depurador foi gerada.</span><span class="sxs-lookup"><span data-stu-id="1eb29-275">Provides a callback method that indicates that an enabled custom debugger notification has been raised.</span></span>  
  
 [<span data-ttu-id="1eb29-276">Interface ICorDebugMDA</span><span class="sxs-lookup"><span data-stu-id="1eb29-276">ICorDebugMDA Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)  
 <span data-ttu-id="1eb29-277">Representa uma mensagem do assistente de depuração gerenciado (MDA).</span><span class="sxs-lookup"><span data-stu-id="1eb29-277">Represents a managed debugging assistant (MDA) message.</span></span>  
  
 [<span data-ttu-id="1eb29-278">Interface ICorDebugMemoryBuffer</span><span class="sxs-lookup"><span data-stu-id="1eb29-278">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)  
 <span data-ttu-id="1eb29-279">Representa um buffer na memória.</span><span class="sxs-lookup"><span data-stu-id="1eb29-279">Represents an in-memory buffer.</span></span> <span data-ttu-id="1eb29-280">**Disponível em apenas .NET nativo.**</span><span class="sxs-lookup"><span data-stu-id="1eb29-280">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="1eb29-281">Interface ICorDebugMergedAssemblyRecord</span><span class="sxs-lookup"><span data-stu-id="1eb29-281">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)  
 <span data-ttu-id="1eb29-282">Fornece informações sobre um assembly mesclada.</span><span class="sxs-lookup"><span data-stu-id="1eb29-282">Provides information about a merged assembly.</span></span> <span data-ttu-id="1eb29-283">**Disponível em apenas .NET nativo.**</span><span class="sxs-lookup"><span data-stu-id="1eb29-283">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="1eb29-284">Interface ICorDebugMetaDataLocator</span><span class="sxs-lookup"><span data-stu-id="1eb29-284">ICorDebugMetaDataLocator Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmetadatalocator-interface.md)  
 <span data-ttu-id="1eb29-285">Fornece informações de metadados ao depurador.</span><span class="sxs-lookup"><span data-stu-id="1eb29-285">Provides metadata information to the debugger.</span></span>  
  
 [<span data-ttu-id="1eb29-286">Interface1 ICorDebugModule</span><span class="sxs-lookup"><span data-stu-id="1eb29-286">ICorDebugModule Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-interface.md)  
 <span data-ttu-id="1eb29-287">Representa um módulo de CLR, que é um executável ou uma biblioteca de vínculo dinâmico (DLL).</span><span class="sxs-lookup"><span data-stu-id="1eb29-287">Represents a CLR module, which is either an executable or a dynamic-link library (DLL).</span></span>  
  
 [<span data-ttu-id="1eb29-288">Interface1 ICorDebugModule2</span><span class="sxs-lookup"><span data-stu-id="1eb29-288">ICorDebugModule2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-interface.md)  
 <span data-ttu-id="1eb29-289">Serve como extensão lógica para `ICorDebugModule`.</span><span class="sxs-lookup"><span data-stu-id="1eb29-289">Serves as a logical extension to `ICorDebugModule`.</span></span>  
  
 [<span data-ttu-id="1eb29-290">Interface ICorDebugModule3</span><span class="sxs-lookup"><span data-stu-id="1eb29-290">ICorDebugModule3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule3-interface.md)  
 <span data-ttu-id="1eb29-291">Cria um leitor de símbolos para um módulo dinâmico.</span><span class="sxs-lookup"><span data-stu-id="1eb29-291">Creates a symbol reader for a dynamic module.</span></span>  
  
 [<span data-ttu-id="1eb29-292">Interface1 ICorDebugModuleBreakpoint</span><span class="sxs-lookup"><span data-stu-id="1eb29-292">ICorDebugModuleBreakpoint Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodulebreakpoint-interface.md)  
 <span data-ttu-id="1eb29-293">Estende `ICorDebugBreakpoint` para fornecer acesso aos módulos específicos.</span><span class="sxs-lookup"><span data-stu-id="1eb29-293">Extends `ICorDebugBreakpoint` to provide access to specific modules.</span></span>  
  
 [<span data-ttu-id="1eb29-294">Interface ICorDebugModuleDebugEvent</span><span class="sxs-lookup"><span data-stu-id="1eb29-294">ICorDebugModuleDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)  
 <span data-ttu-id="1eb29-295">Estende o [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface para oferecer suporte a eventos de nível de módulo.</span><span class="sxs-lookup"><span data-stu-id="1eb29-295">Extends the [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface to support module-level events.</span></span> <span data-ttu-id="1eb29-296">**Disponível em apenas .NET nativo.**</span><span class="sxs-lookup"><span data-stu-id="1eb29-296">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="1eb29-297">Interface1 ICorDebugModuleEnum</span><span class="sxs-lookup"><span data-stu-id="1eb29-297">ICorDebugModuleEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduleenum-interface.md)  
 <span data-ttu-id="1eb29-298">Implementa métodos `ICorDebugEnum` e enumera matrizes de `ICorDebugModule`.</span><span class="sxs-lookup"><span data-stu-id="1eb29-298">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugModule` arrays.</span></span>  
  
 [<span data-ttu-id="1eb29-299">Interface ICorDebugMutableDataTarget</span><span class="sxs-lookup"><span data-stu-id="1eb29-299">ICorDebugMutableDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)  
 <span data-ttu-id="1eb29-300">Estende o [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface para oferecer suporte a destinos de dados mutáveis.</span><span class="sxs-lookup"><span data-stu-id="1eb29-300">Extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface to support mutable data targets.</span></span>  
  
 [<span data-ttu-id="1eb29-301">Interface1 ICorDebugNativeFrame</span><span class="sxs-lookup"><span data-stu-id="1eb29-301">ICorDebugNativeFrame Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-interface.md)  
 <span data-ttu-id="1eb29-302">Uma implementação especializada de `ICorDebugFrame` usada para quadros nativos.</span><span class="sxs-lookup"><span data-stu-id="1eb29-302">A specialized implementation of `ICorDebugFrame` used for native frames.</span></span>  
  
 [<span data-ttu-id="1eb29-303">Interface ICorDebugNativeFrame2</span><span class="sxs-lookup"><span data-stu-id="1eb29-303">ICorDebugNativeFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)  
 <span data-ttu-id="1eb29-304">Fornece métodos que testam relações de quadros pai e filho.</span><span class="sxs-lookup"><span data-stu-id="1eb29-304">Provides methods that test for child and parent frame relationships.</span></span>  
  
 [<span data-ttu-id="1eb29-305">Interface1 ICorDebugObjectEnum</span><span class="sxs-lookup"><span data-stu-id="1eb29-305">ICorDebugObjectEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectenum-interface.md)  
 <span data-ttu-id="1eb29-306">Implementa métodos `ICorDebugEnum` e enumera matrizes de objetos pelos endereços virtuais relacionados (RVAs).</span><span class="sxs-lookup"><span data-stu-id="1eb29-306">Implements `ICorDebugEnum` methods, and enumerates arrays of objects by their relative virtual addresses (RVAs).</span></span>  
  
 [<span data-ttu-id="1eb29-307">Interface1 ICorDebugObjectValue</span><span class="sxs-lookup"><span data-stu-id="1eb29-307">ICorDebugObjectValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-interface.md)  
 <span data-ttu-id="1eb29-308">Uma subclasse de `ICorDebugValue` que representa um valor que contém um objeto.</span><span class="sxs-lookup"><span data-stu-id="1eb29-308">A subclass of `ICorDebugValue` that represents a value that contains an object.</span></span>  
  
 [<span data-ttu-id="1eb29-309">Interface1 ICorDebugObjectValue2</span><span class="sxs-lookup"><span data-stu-id="1eb29-309">ICorDebugObjectValue2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue2-interface.md)  
 <span data-ttu-id="1eb29-310">Estende `ICorDebugObjectValue` para oferecer suporte a herança e substituição.</span><span class="sxs-lookup"><span data-stu-id="1eb29-310">Extends `ICorDebugObjectValue` to support inheritance and overrides.</span></span>  
  
 [<span data-ttu-id="1eb29-311">Interface1 ICorDebugProcess</span><span class="sxs-lookup"><span data-stu-id="1eb29-311">ICorDebugProcess Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md)  
 <span data-ttu-id="1eb29-312">Representa um processo que está executando o código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="1eb29-312">Represents a process that is executing managed code.</span></span>  
  
 [<span data-ttu-id="1eb29-313">Interface1 ICorDebugProcess2</span><span class="sxs-lookup"><span data-stu-id="1eb29-313">ICorDebugProcess2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-interface1.md)  
 <span data-ttu-id="1eb29-314">Uma extensão lógica de `ICorDebugProcess`.</span><span class="sxs-lookup"><span data-stu-id="1eb29-314">A logical extension of `ICorDebugProcess`.</span></span>  
  
 [<span data-ttu-id="1eb29-315">Interface ICorDebugProcess3</span><span class="sxs-lookup"><span data-stu-id="1eb29-315">ICorDebugProcess3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md)  
 <span data-ttu-id="1eb29-316">Controla as notificações personalizadas do depurador.</span><span class="sxs-lookup"><span data-stu-id="1eb29-316">Controls custom debugger notifications.</span></span>  
  
 [<span data-ttu-id="1eb29-317">Interface ICorDebugProcess5</span><span class="sxs-lookup"><span data-stu-id="1eb29-317">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 <span data-ttu-id="1eb29-318">Estende o [ICorDebugProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md) local da interface para oferecer suporte ao acesso para o heap gerenciado, para fornecer informações sobre a coleta de lixo de objetos gerenciados e para determinar se um depurador carrega imagens do aplicativo cache de imagem nativa.</span><span class="sxs-lookup"><span data-stu-id="1eb29-318">Extends the [ICorDebugProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md) interface to support access to the managed heap, to provide information about garbage collection of managed objects, and to determine whether a debugger loads images from the application's local native image cache.</span></span>  
  
 [<span data-ttu-id="1eb29-319">Interface ICorDebugProcess6</span><span class="sxs-lookup"><span data-stu-id="1eb29-319">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)  
 <span data-ttu-id="1eb29-320">Estende logicamente a [ICorDebugProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md) interface para habilitar recursos como eventos de depuração gerenciados que são codificados em eventos de depuração de exceção nativa e divisão de módulo virtual.</span><span class="sxs-lookup"><span data-stu-id="1eb29-320">Logically extends the [ICorDebugProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md) interface to enable features such as decoding managed debug events that are encoded in native exception debug events and virtual module splitting.</span></span> <span data-ttu-id="1eb29-321">**Disponível em apenas .NET nativo.**</span><span class="sxs-lookup"><span data-stu-id="1eb29-321">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="1eb29-322">Interface ICorDebugProcess7</span><span class="sxs-lookup"><span data-stu-id="1eb29-322">ICorDebugProcess7 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-interface.md)  
 <span data-ttu-id="1eb29-323">Fornece um método que configura o depurador para manipular atualizações de metadados na memória no processo de destino.</span><span class="sxs-lookup"><span data-stu-id="1eb29-323">Provides a method that configures the debugger to handle in-memory metadata updates in the target process.</span></span>  
  
 [<span data-ttu-id="1eb29-324">Interface ICorDebugProcess8</span><span class="sxs-lookup"><span data-stu-id="1eb29-324">ICorDebugProcess8 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess8-interface.md)  
 <span data-ttu-id="1eb29-325">Estende logicamente a [ICorDebugProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md) interface para habilitar ou desabilitar determinados tipos de [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) retornos de chamada de exceção.</span><span class="sxs-lookup"><span data-stu-id="1eb29-325">Logically extends the [ICorDebugProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md) interface to enable or disable certain types of [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>  
  
 [<span data-ttu-id="1eb29-326">Interface1 ICorDebugProcessEnum</span><span class="sxs-lookup"><span data-stu-id="1eb29-326">ICorDebugProcessEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocessenum-interface.md)  
 <span data-ttu-id="1eb29-327">Implementa métodos `ICorDebugEnum` e enumera matrizes de `ICorDebugProcess`.</span><span class="sxs-lookup"><span data-stu-id="1eb29-327">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugProcess` arrays.</span></span>  
  
 [<span data-ttu-id="1eb29-328">Interface1 ICorDebugReferenceValue</span><span class="sxs-lookup"><span data-stu-id="1eb29-328">ICorDebugReferenceValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-interface.md)  
 <span data-ttu-id="1eb29-329">Uma subclasse de `ICorDebugValue` que oferece suporte a tipos de referência.</span><span class="sxs-lookup"><span data-stu-id="1eb29-329">A subclass of `ICorDebugValue` that supports reference types.</span></span>  
  
 [<span data-ttu-id="1eb29-330">Interface ICorDebugRegisterSet</span><span class="sxs-lookup"><span data-stu-id="1eb29-330">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)  
 <span data-ttu-id="1eb29-331">Representa o conjunto de registros disponíveis no computador que está executando o código no momento.</span><span class="sxs-lookup"><span data-stu-id="1eb29-331">Represents the set of registers available on the machine that is currently executing code.</span></span>  
  
 [<span data-ttu-id="1eb29-332">Interface ICorDebugRegisterSet2</span><span class="sxs-lookup"><span data-stu-id="1eb29-332">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)  
 <span data-ttu-id="1eb29-333">Estende os recursos de `ICorDebugRegisterSet` para as plataformas de hardware que possuem mais de 64 registros.</span><span class="sxs-lookup"><span data-stu-id="1eb29-333">Extends the capabilities of `ICorDebugRegisterSet` for hardware platforms that have more than 64 registers.</span></span>  
  
 [<span data-ttu-id="1eb29-334">Interface ICorDebugRemote</span><span class="sxs-lookup"><span data-stu-id="1eb29-334">ICorDebugRemote Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)  
 <span data-ttu-id="1eb29-335">Fornece a capacidade de iniciar ou anexar um depurador gerenciado a um processo remoto de destino.</span><span class="sxs-lookup"><span data-stu-id="1eb29-335">Provides the ability to launch or attach a managed debugger to a remote target process.</span></span>  
  
 [<span data-ttu-id="1eb29-336">Interface ICorDebugRemoteTarget</span><span class="sxs-lookup"><span data-stu-id="1eb29-336">ICorDebugRemoteTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)  
 <span data-ttu-id="1eb29-337">Fornece métodos que permitem a você depurar aplicativos baseados no Silverlight no ambiente do CLR.</span><span class="sxs-lookup"><span data-stu-id="1eb29-337">Provides methods that enable you to debug Silverlight-based applications in the CLR environment.</span></span>  
  
 [<span data-ttu-id="1eb29-338">Interface ICorDebugRuntimeUnwindableFrame</span><span class="sxs-lookup"><span data-stu-id="1eb29-338">ICorDebugRuntimeUnwindableFrame Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugruntimeunwindableframe-interface.md)  
 <span data-ttu-id="1eb29-339">Fornece suporte para os métodos não gerenciados que exigem que o CLR (Common Language Runtime) desenrole um quadro.</span><span class="sxs-lookup"><span data-stu-id="1eb29-339">Provides support for unmanaged methods that require the common language runtime (CLR) to unwind a frame.</span></span>  
  
 [<span data-ttu-id="1eb29-340">Interface ICorDebugStackWalk</span><span class="sxs-lookup"><span data-stu-id="1eb29-340">ICorDebugStackWalk Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)  
 <span data-ttu-id="1eb29-341">Fornece métodos para colocar os métodos gerenciados, ou quadros, em uma pilha de thread.</span><span class="sxs-lookup"><span data-stu-id="1eb29-341">Provides methods for getting the managed methods, or frames, on a thread’s stack.</span></span>  
  
 [<span data-ttu-id="1eb29-342">Interface ICorDebugStaticFieldSymbol</span><span class="sxs-lookup"><span data-stu-id="1eb29-342">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)  
 <span data-ttu-id="1eb29-343">Representa as informações de símbolo de depuração de um campo estático.</span><span class="sxs-lookup"><span data-stu-id="1eb29-343">Represents the debug symbol information for a static field.</span></span> <span data-ttu-id="1eb29-344">**Disponível em apenas .NET nativo.**</span><span class="sxs-lookup"><span data-stu-id="1eb29-344">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="1eb29-345">Interface1 ICorDebugStepper</span><span class="sxs-lookup"><span data-stu-id="1eb29-345">ICorDebugStepper Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-interface.md)  
 <span data-ttu-id="1eb29-346">Representa uma etapa na execução do código que é realizada por um depurador, serve como um identificador entre a emissão e a conclusão de um comando e fornece uma maneira de cancelar uma etapa.</span><span class="sxs-lookup"><span data-stu-id="1eb29-346">Represents a step in code execution that is performed by a debugger, serves as an identifier between the issuance and completion of a command, and provides a way to cancel a step.</span></span>  
  
 [<span data-ttu-id="1eb29-347">Interface1 ICorDebugStepper2</span><span class="sxs-lookup"><span data-stu-id="1eb29-347">ICorDebugStepper2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper2-interface1.md)  
 <span data-ttu-id="1eb29-348">Fornece suporte para a depuração JMC (Apenas Meu Código).</span><span class="sxs-lookup"><span data-stu-id="1eb29-348">Provides support for Just My Code (JMC) debugging.</span></span>  
  
 [<span data-ttu-id="1eb29-349">Interface1 ICorDebugStepperEnum</span><span class="sxs-lookup"><span data-stu-id="1eb29-349">ICorDebugStepperEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepperenum-interface.md)  
 <span data-ttu-id="1eb29-350">Implementa métodos `ICorDebugEnum` e enumera matrizes de `ICorDebugStepper`.</span><span class="sxs-lookup"><span data-stu-id="1eb29-350">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugStepper` arrays.</span></span>  
  
 [<span data-ttu-id="1eb29-351">Interface1 ICorDebugStringValue</span><span class="sxs-lookup"><span data-stu-id="1eb29-351">ICorDebugStringValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-interface.md)  
 <span data-ttu-id="1eb29-352">Uma subclasse de `ICorDebugHeapValue` que se aplica a valores de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="1eb29-352">A subclass of `ICorDebugHeapValue` that applies to string values.</span></span>  
  
 [<span data-ttu-id="1eb29-353">Interface ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="1eb29-353">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 <span data-ttu-id="1eb29-354">Fornece métodos que podem ser usados para recuperar informações de símbolo de depuração.</span><span class="sxs-lookup"><span data-stu-id="1eb29-354">Provides methods that can be used to retrieve debug symbol information.</span></span> <span data-ttu-id="1eb29-355">**Disponível em apenas .NET nativo.**</span><span class="sxs-lookup"><span data-stu-id="1eb29-355">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="1eb29-356">Interface ICorDebugSymbolProvider2</span><span class="sxs-lookup"><span data-stu-id="1eb29-356">ICorDebugSymbolProvider2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-interface.md)  
 <span data-ttu-id="1eb29-357">Estende logicamente a [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) interface para recuperar informações de símbolo de depuração adicionais.</span><span class="sxs-lookup"><span data-stu-id="1eb29-357">Logically extends the [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) interface to retrieve additional debug symbol information.</span></span> <span data-ttu-id="1eb29-358">**Disponível em apenas .NET nativo.**</span><span class="sxs-lookup"><span data-stu-id="1eb29-358">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="1eb29-359">Interface1 ICorDebugThread</span><span class="sxs-lookup"><span data-stu-id="1eb29-359">ICorDebugThread Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-interface.md)  
 <span data-ttu-id="1eb29-360">Representa um thread em um processo.</span><span class="sxs-lookup"><span data-stu-id="1eb29-360">Represents a thread in a process.</span></span> <span data-ttu-id="1eb29-361">O tempo de vida de uma instância `ICorDebugThread` é igual ao tempo de vida do thread que ela representa.</span><span class="sxs-lookup"><span data-stu-id="1eb29-361">The lifetime of an `ICorDebugThread` instance is the same as the lifetime of the thread it represents.</span></span>  
  
 [<span data-ttu-id="1eb29-362">Interface1 ICorDebugThread2</span><span class="sxs-lookup"><span data-stu-id="1eb29-362">ICorDebugThread2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interface.md)  
 <span data-ttu-id="1eb29-363">Serve como extensão lógica para `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="1eb29-363">Serves as a logical extension to `ICorDebugThread`.</span></span>  
  
 [<span data-ttu-id="1eb29-364">Interface ICorDebugThread3</span><span class="sxs-lookup"><span data-stu-id="1eb29-364">ICorDebugThread3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-interface.md)  
 <span data-ttu-id="1eb29-365">Fornece o ponto de entrada para o [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) e as interfaces correspondentes.</span><span class="sxs-lookup"><span data-stu-id="1eb29-365">Provides the entry point to the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) and corresponding interfaces.</span></span>  
  
 [<span data-ttu-id="1eb29-366">Interface ICorDebugThread4</span><span class="sxs-lookup"><span data-stu-id="1eb29-366">ICorDebugThread4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)  
 <span data-ttu-id="1eb29-367">Fornece informações de bloqueio de thread.</span><span class="sxs-lookup"><span data-stu-id="1eb29-367">Provides thread blocking information.</span></span>  
  
 [<span data-ttu-id="1eb29-368">Interface1 ICorDebugThreadEnum</span><span class="sxs-lookup"><span data-stu-id="1eb29-368">ICorDebugThreadEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthreadenum-interface1.md)  
 <span data-ttu-id="1eb29-369">Implementa métodos `ICorDebugEnum` e enumera matrizes de `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="1eb29-369">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugThread` arrays.</span></span>  
  
 [<span data-ttu-id="1eb29-370">Interface1 ICorDebugType</span><span class="sxs-lookup"><span data-stu-id="1eb29-370">ICorDebugType Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md)  
 <span data-ttu-id="1eb29-371">Representa um tipo, que pode ser básico ou complexo (isto é, definido pelo usuário).</span><span class="sxs-lookup"><span data-stu-id="1eb29-371">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="1eb29-372">Se o tipo for genérico, `ICorDebugType` representará o tipo genérico instanciado.</span><span class="sxs-lookup"><span data-stu-id="1eb29-372">If the type is generic, `ICorDebugType` represents the instantiated generic type.</span></span>  
  
 [<span data-ttu-id="1eb29-373">Interface ICorDebugType2</span><span class="sxs-lookup"><span data-stu-id="1eb29-373">ICorDebugType2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-interface.md)  
 <span data-ttu-id="1eb29-374">Estende o [ICorDebugType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md) interface para recuperar o identificador de tipo de um tipo base ou um tipo complexo (definido pelo usuário).</span><span class="sxs-lookup"><span data-stu-id="1eb29-374">Extends the [ICorDebugType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md) interface to retrieve the type identifier  of a base type or complex (user-defined) type.</span></span>  
  
 [<span data-ttu-id="1eb29-375">Interface1 ICorDebugTypeEnum</span><span class="sxs-lookup"><span data-stu-id="1eb29-375">ICorDebugTypeEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtypeenum-interface.md)  
 <span data-ttu-id="1eb29-376">Implementa métodos `ICorDebugEnum` e enumera matrizes de `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="1eb29-376">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugType` arrays.</span></span>  
  
 [<span data-ttu-id="1eb29-377">Interface ICorDebugUnmanagedCallback</span><span class="sxs-lookup"><span data-stu-id="1eb29-377">ICorDebugUnmanagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md)  
 <span data-ttu-id="1eb29-378">Fornece notificação de eventos nativos que não estão diretamente relacionados ao CLR.</span><span class="sxs-lookup"><span data-stu-id="1eb29-378">Provides notification of native events that are not directly related to the CLR.</span></span>  
  
 <span data-ttu-id="1eb29-379">"ICorDebugValue"</span><span class="sxs-lookup"><span data-stu-id="1eb29-379">"ICorDebugValue"</span></span>  
 <span data-ttu-id="1eb29-380">Representa um valor de leitura ou gravação no processo que está sendo depurado.</span><span class="sxs-lookup"><span data-stu-id="1eb29-380">Represents a read or write value in the process being debugged.</span></span>  
  
 <span data-ttu-id="1eb29-381">"ICorDebugValue2"</span><span class="sxs-lookup"><span data-stu-id="1eb29-381">"ICorDebugValue2"</span></span>  
 <span data-ttu-id="1eb29-382">Estende `ICorDebugValue` para oferecer suporte a `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="1eb29-382">Extends `ICorDebugValue` to provide support for `ICorDebugType`.</span></span>  
  
 [<span data-ttu-id="1eb29-383">Interface ICorDebugValue3</span><span class="sxs-lookup"><span data-stu-id="1eb29-383">ICorDebugValue3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)  
 <span data-ttu-id="1eb29-384">Estende as interfaces "ICorDebugValue" e "ICorDebugValue2" para fornecer suporte para matrizes que são maiores que 2 GB.</span><span class="sxs-lookup"><span data-stu-id="1eb29-384">Extends the "ICorDebugValue" and "ICorDebugValue2" interfaces to provide support for arrays that are larger than 2 GB.</span></span>  
  
 <span data-ttu-id="1eb29-385">"ICorDebugValueBreakpoint"</span><span class="sxs-lookup"><span data-stu-id="1eb29-385">"ICorDebugValueBreakpoint"</span></span>  
 <span data-ttu-id="1eb29-386">Estende `ICorDebugBreakpoint` para fornecer acesso a valores específicos.</span><span class="sxs-lookup"><span data-stu-id="1eb29-386">Extends `ICorDebugBreakpoint` to provide access to specific values.</span></span>  
  
 <span data-ttu-id="1eb29-387">"ICorDebugValueEnum"</span><span class="sxs-lookup"><span data-stu-id="1eb29-387">"ICorDebugValueEnum"</span></span>  
 <span data-ttu-id="1eb29-388">Implementa métodos `ICorDebugEnum` e enumera matrizes de `ICorDebugValue`.</span><span class="sxs-lookup"><span data-stu-id="1eb29-388">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugValue` arrays.</span></span>  
  
 [<span data-ttu-id="1eb29-389">Interface ICorDebugVariableHome</span><span class="sxs-lookup"><span data-stu-id="1eb29-389">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)  
 <span data-ttu-id="1eb29-390">Representa um argumento de uma função ou variável local.</span><span class="sxs-lookup"><span data-stu-id="1eb29-390">Represents a local variable or argument of a function.</span></span>  
  
 [<span data-ttu-id="1eb29-391">Interface ICorDebugVariableHomeEnum</span><span class="sxs-lookup"><span data-stu-id="1eb29-391">ICorDebugVariableHomeEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)  
 <span data-ttu-id="1eb29-392">Fornece um enumerador para as variáveis locais e os argumentos em uma função.</span><span class="sxs-lookup"><span data-stu-id="1eb29-392">Provides an enumerator to the local variables and arguments in a function.</span></span>  
  
 [<span data-ttu-id="1eb29-393">Interface ICorDebugVariableSymbol</span><span class="sxs-lookup"><span data-stu-id="1eb29-393">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 <span data-ttu-id="1eb29-394">Recupera as informações de símbolo de depuração de uma variável.</span><span class="sxs-lookup"><span data-stu-id="1eb29-394">Retrieves the debug symbol information for a variable.</span></span> <span data-ttu-id="1eb29-395">**Disponível em apenas .NET nativo.**</span><span class="sxs-lookup"><span data-stu-id="1eb29-395">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="1eb29-396">Interface ICorDebugVirtualUnwinder</span><span class="sxs-lookup"><span data-stu-id="1eb29-396">ICorDebugVirtualUnwinder Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvirtualunwinder-interface.md)  
 <span data-ttu-id="1eb29-397">Fornece métodos para ajudá-lo desenrolamento de pilha.</span><span class="sxs-lookup"><span data-stu-id="1eb29-397">Provides methods to help in stack unwinding.</span></span> <span data-ttu-id="1eb29-398">**Disponível em apenas .NET nativo.**</span><span class="sxs-lookup"><span data-stu-id="1eb29-398">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="1eb29-399">Interface ICorPublish</span><span class="sxs-lookup"><span data-stu-id="1eb29-399">ICorPublish Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)  
 <span data-ttu-id="1eb29-400">Serve como a interface geral para os processos de publicação.</span><span class="sxs-lookup"><span data-stu-id="1eb29-400">Serves as the general interface for the publishing processes.</span></span>  
  
 [<span data-ttu-id="1eb29-401">Interface ICorPublishAppDomain</span><span class="sxs-lookup"><span data-stu-id="1eb29-401">ICorPublishAppDomain Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)  
 <span data-ttu-id="1eb29-402">Representa e fornece informações sobre um domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1eb29-402">Represents and provides information about an application domain.</span></span>  
  
 [<span data-ttu-id="1eb29-403">Interface ICorPublishAppDomainEnum</span><span class="sxs-lookup"><span data-stu-id="1eb29-403">ICorPublishAppDomainEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)  
 <span data-ttu-id="1eb29-404">Fornece métodos que percorrem uma coleção de objetos `ICorPublishAppDomain` existentes em um processo.</span><span class="sxs-lookup"><span data-stu-id="1eb29-404">Provides methods that traverse a collection of `ICorPublishAppDomain` objects that currently exist within a process.</span></span>  
  
 [<span data-ttu-id="1eb29-405">Interface ICorPublishEnum</span><span class="sxs-lookup"><span data-stu-id="1eb29-405">ICorPublishEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)  
 <span data-ttu-id="1eb29-406">Serve como a base abstrata para a publicação de enumeradores.</span><span class="sxs-lookup"><span data-stu-id="1eb29-406">Serves as the abstract base for publishing enumerators.</span></span>  
  
 [<span data-ttu-id="1eb29-407">Interface ICorPublishProcess</span><span class="sxs-lookup"><span data-stu-id="1eb29-407">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)  
 <span data-ttu-id="1eb29-408">Fornece métodos que acessam informações sobre um processo.</span><span class="sxs-lookup"><span data-stu-id="1eb29-408">Provides methods that access information about a process.</span></span>  
  
 [<span data-ttu-id="1eb29-409">Interface ICorPublishProcessEnum</span><span class="sxs-lookup"><span data-stu-id="1eb29-409">ICorPublishProcessEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)  
 <span data-ttu-id="1eb29-410">Fornece métodos que percorrem uma coleção de objetos `ICorPublishProcess`.</span><span class="sxs-lookup"><span data-stu-id="1eb29-410">Provides methods that traverse a collection of `ICorPublishProcess` objects.</span></span>  

 <span data-ttu-id="1eb29-411">[ISOSDacInterface Interface](../../../../docs/framework/unmanaged-api/debugging/isosdacinterface-interface.md) fornece métodos auxiliares para acessar dados de `SOS`.</span><span class="sxs-lookup"><span data-stu-id="1eb29-411">[ISOSDacInterface Interface](../../../../docs/framework/unmanaged-api/debugging/isosdacinterface-interface.md) Provides helper methods to access data from `SOS`.</span></span>

 <span data-ttu-id="1eb29-412">[IXCLRDataMethodDefinition Interface](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethoddefinition-interface.md) fornece métodos para consultar informações sobre uma definição de método.</span><span class="sxs-lookup"><span data-stu-id="1eb29-412">[IXCLRDataMethodDefinition Interface](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethoddefinition-interface.md) Provides methods for querying information about a method definition.</span></span>
 
 <span data-ttu-id="1eb29-413">[IXCLRDataMethodInstance Interface](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethodinstance-interface.md) fornece métodos para consultar informações sobre uma instância de método.</span><span class="sxs-lookup"><span data-stu-id="1eb29-413">[IXCLRDataMethodInstance Interface](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethodinstance-interface.md) Provides methods for querying information about a method instance.</span></span>
 
 <span data-ttu-id="1eb29-414">[IXCLRDataModule Interface](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamodule-interface.md) fornece métodos para consultar informações sobre um módulo carregado.</span><span class="sxs-lookup"><span data-stu-id="1eb29-414">[IXCLRDataModule Interface](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamodule-interface.md) Provides methods for querying information about a loaded module.</span></span>
 
 <span data-ttu-id="1eb29-415">[IXCLRDataProcess Interface](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-interface.md) fornece métodos para consultar informações sobre um processo.</span><span class="sxs-lookup"><span data-stu-id="1eb29-415">[IXCLRDataProcess Interface](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-interface.md) Provides methods for querying information about a process.</span></span>
  
## <a name="related-sections"></a><span data-ttu-id="1eb29-416">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="1eb29-416">Related Sections</span></span>  
 [<span data-ttu-id="1eb29-417">Depurando coclasses</span><span class="sxs-lookup"><span data-stu-id="1eb29-417">Debugging Coclasses</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [<span data-ttu-id="1eb29-418">Depurando funções estáticas globais</span><span class="sxs-lookup"><span data-stu-id="1eb29-418">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)  
  
 [<span data-ttu-id="1eb29-419">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="1eb29-419">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
  
 [<span data-ttu-id="1eb29-420">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="1eb29-420">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
