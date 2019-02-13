---
title: Depurando interfaces
ms.date: 02/07/2019
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: b6297c26-7624-4431-8af4-14112d07bcd5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: afa4e6cd4e99540030d3a9e151da4bbe711d973a
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/13/2019
ms.locfileid: "56219822"
---
# <a name="debugging-interfaces"></a><span data-ttu-id="88ebc-102">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="88ebc-102">Debugging Interfaces</span></span>
<span data-ttu-id="88ebc-103">Esta seção descreve as interfaces não gerenciadas que lidam com a depuração de um programa que está sendo executado no CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="88ebc-103">This section describes the unmanaged interfaces that handle the debugging of a program that is executing in the common language runtime (CLR).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="88ebc-104">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="88ebc-104">In This Section</span></span>  
 <span data-ttu-id="88ebc-105">[Interface ICLRDataEnumMemoryRegions](iclrdataenummemoryregions-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-105">[ICLRDataEnumMemoryRegions Interface](iclrdataenummemoryregions-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-106">Fornece um método para enumerar as regiões da memória que são especificadas por chamadores.</span><span class="sxs-lookup"><span data-stu-id="88ebc-106">Provides a method to enumerate regions of memory that are specified by callers.</span></span>  
  
 <span data-ttu-id="88ebc-107">[Interface ICLRDataEnumMemoryRegionsCallback](iclrdataenummemoryregionscallback-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-107">[ICLRDataEnumMemoryRegionsCallback Interface](iclrdataenummemoryregionscallback-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-108">Fornece um método de retorno de chamada para `EnumMemoryRegions` relatar ao depurador o resultado de uma tentativa de enumerar uma região especificada da memória.</span><span class="sxs-lookup"><span data-stu-id="88ebc-108">Provides a callback method for `EnumMemoryRegions` to report to the debugger, the result of an attempt to enumerate a specified region of memory.</span></span>  
  
 <span data-ttu-id="88ebc-109">[Interface ICLRDataTarget](iclrdatatarget-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-109">[ICLRDataTarget Interface](iclrdatatarget-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-110">Fornece métodos para interação com um processo de CLR de destino.</span><span class="sxs-lookup"><span data-stu-id="88ebc-110">Provides methods for interaction with a target CLR process.</span></span>  
  
 <span data-ttu-id="88ebc-111">[Interface ICLRDataTarget2](iclrdatatarget2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-111">[ICLRDataTarget2 Interface](iclrdatatarget2-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-112">Uma subclasse de `ICLRDataTarget` que é usada pela camada de serviços de acesso a dados para manipular as regiões de memória virtual no processo de destino.</span><span class="sxs-lookup"><span data-stu-id="88ebc-112">A subclass of `ICLRDataTarget` that is used by the data access services layer to manipulate virtual memory regions in the target process.</span></span>  
  
 <span data-ttu-id="88ebc-113">[Interface ICLRDataTarget3](iclrdatatarget3-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-113">[ICLRDataTarget3 Interface](iclrdatatarget3-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-114">Uma subclasse de [ICLRDataTarget2](iclrdatatarget2-interface.md) que fornece acesso a informações de exceção.</span><span class="sxs-lookup"><span data-stu-id="88ebc-114">A subclass of [ICLRDataTarget2](iclrdatatarget2-interface.md) that provides access to exception information.</span></span>  
  
 <span data-ttu-id="88ebc-115">[Interface ICLRDebugging](iclrdebugging-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-115">[ICLRDebugging Interface](iclrdebugging-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-116">Fornece métodos que manipulam os módulos de carregamento e descarregamento para depuração.</span><span class="sxs-lookup"><span data-stu-id="88ebc-116">Provides methods that handle loading and unloading modules for debugging.</span></span>  
  
 <span data-ttu-id="88ebc-117">[Interface ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-117">[ICLRDebuggingLibraryProvider Interface](iclrdebugginglibraryprovider-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-118">Inclui o [método ProvideLibrary](iclrdebugginglibraryprovider-providelibrary-method.md) método, que obtém um provedor de biblioteca de interface de retorno de chamada que permite que o common language runtime específica da versão bibliotecas de depuração ser localizada e carregada sob demanda.</span><span class="sxs-lookup"><span data-stu-id="88ebc-118">Includes the [ProvideLibrary Method](iclrdebugginglibraryprovider-providelibrary-method.md) method, which gets a library provider callback interface that allows common language runtime version-specific debugging libraries to be located and loaded on demand.</span></span>  
  
 <span data-ttu-id="88ebc-119">[Interface ICLRMetadataLocator](iclrmetadatalocator-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-119">[ICLRMetadataLocator Interface](iclrmetadatalocator-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-120">A interface usada pela camada de serviços de acesso a dados para localizar metadados de assemblies em um processo de destino.</span><span class="sxs-lookup"><span data-stu-id="88ebc-120">Interface used by the data access services layer to locate metadata of assemblies in a target process.</span></span>  
  
 <span data-ttu-id="88ebc-121">[Interface ICorDebug](icordebug-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-121">[ICorDebug Interface](icordebug-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-122">Fornece métodos que permitem que os desenvolvedores depurem aplicativos no ambiente do CLR.</span><span class="sxs-lookup"><span data-stu-id="88ebc-122">Provides methods that allow developers to debug applications in the CLR environment.</span></span>  
  
 <span data-ttu-id="88ebc-123">[ICorDebugAppDomain Interface1](icordebugappdomain-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-123">[ICorDebugAppDomain Interface1](icordebugappdomain-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-124">Fornece métodos para depurar domínios de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="88ebc-124">Provides methods for debugging application domains.</span></span>  
  
 <span data-ttu-id="88ebc-125">[ICorDebugAppDomain2 Interface1](icordebugappdomain2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-125">[ICorDebugAppDomain2 Interface1](icordebugappdomain2-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-126">Fornece métodos para trabalhar com matrizes, ponteiros, ponteiros de função e tipos ByRef.</span><span class="sxs-lookup"><span data-stu-id="88ebc-126">Provides methods to work with arrays, pointers, function pointers, and ByRef types.</span></span> <span data-ttu-id="88ebc-127">Essa interface é uma extensão da interface `ICorDebugAppDomain`.</span><span class="sxs-lookup"><span data-stu-id="88ebc-127">This interface is an extension of the `ICorDebugAppDomain` interface.</span></span>  
  
 <span data-ttu-id="88ebc-128">[Interface ICorDebugAppDomain3](icordebugappdomain3-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-128">[ICorDebugAppDomain3 Interface](icordebugappdomain3-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-129">Fornece métodos para trabalhar com os tipos [!INCLUDE[wrt](../../../../includes/wrt-md.md)] em um domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="88ebc-129">Provides methods to work with the [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types in an application domain.</span></span> <span data-ttu-id="88ebc-130">Essa interface é uma extensão das interfaces `ICorDebugAppDomain` e `ICorDebugAppDomain2`.</span><span class="sxs-lookup"><span data-stu-id="88ebc-130">This interface is an extension of the `ICorDebugAppDomain` and `ICorDebugAppDomain2` interfaces.</span></span>  
  
 <span data-ttu-id="88ebc-131">[Interface ICorDebugAppDomain4](icordebugappdomain4-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-131">[ICorDebugAppDomain4 Interface](icordebugappdomain4-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-132">Estende logicamente a [ICorDebugAppDomain](icordebugappdomain-interface.md) interface para obter um objeto gerenciado de um COM callable wrapper.</span><span class="sxs-lookup"><span data-stu-id="88ebc-132">Logically extends the [ICorDebugAppDomain](icordebugappdomain-interface.md) interface to get a managed object from a COM callable wrapper.</span></span>  
  
 <span data-ttu-id="88ebc-133">[ICorDebugAppDomainEnum Interface1](icordebugappdomainenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-133">[ICorDebugAppDomainEnum Interface1](icordebugappdomainenum-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-134">Fornece um método que retorna um número especificado de valores `ICorDebugAppDomain` iniciando no próximo local na enumeração.</span><span class="sxs-lookup"><span data-stu-id="88ebc-134">Provides a method that returns a specified number of `ICorDebugAppDomain` values starting at the next location in the enumeration.</span></span>  
  
 <span data-ttu-id="88ebc-135">[ICorDebugArrayValue Interface1](icordebugarrayvalue-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-135">[ICorDebugArrayValue Interface1](icordebugarrayvalue-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-136">Uma subclasse de `ICorDebugHeapValue` que representa uma matriz unidimensional ou multidimensional.</span><span class="sxs-lookup"><span data-stu-id="88ebc-136">A subclass of `ICorDebugHeapValue` that represents a single-dimensional or multi-dimensional array.</span></span>  
  
 <span data-ttu-id="88ebc-137">[ICorDebugAssembly Interface1](icordebugassembly-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-137">[ICorDebugAssembly Interface1](icordebugassembly-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-138">Representa um assembly.</span><span class="sxs-lookup"><span data-stu-id="88ebc-138">Represents an assembly.</span></span>  
  
 <span data-ttu-id="88ebc-139">[Interface1 ICorDebugAssembly2](icordebugassembly2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-139">[ICorDebugAssembly2 Interface1](icordebugassembly2-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-140">Representa um assembly.</span><span class="sxs-lookup"><span data-stu-id="88ebc-140">Represents an assembly.</span></span> <span data-ttu-id="88ebc-141">Essa interface é uma extensão da interface `ICorDebugAssembly`.</span><span class="sxs-lookup"><span data-stu-id="88ebc-141">This interface is an extension of the `ICorDebugAssembly` interface.</span></span>  
  
 <span data-ttu-id="88ebc-142">[Interface ICorDebugAssembly3](icordebugassembly3-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-142">[ICorDebugAssembly3 Interface](icordebugassembly3-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-143">Estende logicamente a [ICorDebugAssembly](icordebugassembly-interface.md) interface para fornecer suporte para assemblies de contêiner e seus assemblies contidos.</span><span class="sxs-lookup"><span data-stu-id="88ebc-143">Logically extends the [ICorDebugAssembly](icordebugassembly-interface.md) interface to provide support for container assemblies and their contained assemblies.</span></span> <span data-ttu-id="88ebc-144">**Disponível em apenas .NET nativo.**</span><span class="sxs-lookup"><span data-stu-id="88ebc-144">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="88ebc-145">[ICorDebugAssemblyEnum Interface1](icordebugassemblyenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-145">[ICorDebugAssemblyEnum Interface1](icordebugassemblyenum-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-146">Implementa métodos `ICorDebugEnum` e enumera matrizes de `ICorDebugAssembly`.</span><span class="sxs-lookup"><span data-stu-id="88ebc-146">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugAssembly` arrays.</span></span>  
  
 <span data-ttu-id="88ebc-147">[Interface ICorDebugBlockingObjectEnum](icordebugblockingobjectenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-147">[ICorDebugBlockingObjectEnum Interface](icordebugblockingobjectenum-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-148">Fornece um enumerador para uma lista dos [CorDebugBlockingObject](cordebugblockingobject-structure.md) estruturas.</span><span class="sxs-lookup"><span data-stu-id="88ebc-148">Provides an enumerator for a list of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures.</span></span>  
  
 <span data-ttu-id="88ebc-149">[ICorDebugBoxValue Interface1](icordebugboxvalue-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-149">[ICorDebugBoxValue Interface1](icordebugboxvalue-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-150">Uma subclasse de `ICorDebugHeapValue` que representa um objeto de classe com valor boxed.</span><span class="sxs-lookup"><span data-stu-id="88ebc-150">A subclass of `ICorDebugHeapValue` that represents a boxed value class object.</span></span>  
  
 <span data-ttu-id="88ebc-151">[ICorDebugBreakpoint Interface1](icordebugbreakpoint-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-151">[ICorDebugBreakpoint Interface1](icordebugbreakpoint-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-152">Representa um ponto de interrupção em uma função ou um ponto de inspeção em um valor.</span><span class="sxs-lookup"><span data-stu-id="88ebc-152">Represents a breakpoint in a function or a watch point on a value.</span></span>  
  
 <span data-ttu-id="88ebc-153">[ICorDebugBreakpointEnum Interface1](icordebugbreakpointenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-153">[ICorDebugBreakpointEnum Interface1](icordebugbreakpointenum-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-154">Implementa métodos `ICorDebugEnum` e enumera matrizes de `ICorDebugBreakpoint`.</span><span class="sxs-lookup"><span data-stu-id="88ebc-154">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugBreakpoint` arrays.</span></span>  
  
 <span data-ttu-id="88ebc-155">[ICorDebugChain Interface1](icordebugchain-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-155">[ICorDebugChain Interface1](icordebugchain-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-156">Representa um segmento de uma pilha de chamadas física ou lógica.</span><span class="sxs-lookup"><span data-stu-id="88ebc-156">Represents a segment of a physical or logical call stack.</span></span>  
  
 <span data-ttu-id="88ebc-157">[ICorDebugChainEnum Interface1](icordebugchainenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-157">[ICorDebugChainEnum Interface1](icordebugchainenum-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-158">Implementa métodos `ICorDebugEnum` e enumera matrizes de `ICorDebugChain`.</span><span class="sxs-lookup"><span data-stu-id="88ebc-158">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugChain` arrays.</span></span>  
  
 <span data-ttu-id="88ebc-159">[ICorDebugClass Interface1](icordebugclass-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-159">[ICorDebugClass Interface1](icordebugclass-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-160">Representa um tipo, que pode ser básico ou complexo (isto é, definido pelo usuário).</span><span class="sxs-lookup"><span data-stu-id="88ebc-160">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="88ebc-161">Se o tipo for genérico, `ICorDebugClass` representará o tipo genérico sem instância.</span><span class="sxs-lookup"><span data-stu-id="88ebc-161">If the type is generic, `ICorDebugClass` represents the uninstantiated generic type.</span></span>  
  
 <span data-ttu-id="88ebc-162">[ICorDebugClass2 Interface1](icordebugclass2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-162">[ICorDebugClass2 Interface1](icordebugclass2-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-163">Representa uma classe genérica ou uma classe com um parâmetro do método do tipo <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="88ebc-163">Represents a generic class or a class with a method parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="88ebc-164">Essa interface estende `ICorDebugClass`.</span><span class="sxs-lookup"><span data-stu-id="88ebc-164">This interface extends `ICorDebugClass`.</span></span>  
  
 <span data-ttu-id="88ebc-165">[ICorDebugCode Interface1](icordebugcode-interface1.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-165">[ICorDebugCode Interface1](icordebugcode-interface1.md)\\</span></span>
 <span data-ttu-id="88ebc-166">Representa um segmento de código MSIL (Microsoft Intermediate Language) ou código nativo.</span><span class="sxs-lookup"><span data-stu-id="88ebc-166">Represents a segment of either Microsoft intermediate language (MSIL) code or native code.</span></span>  
  
 <span data-ttu-id="88ebc-167">[Interface1 ICorDebugCode2](icordebugcode2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-167">[ICorDebugCode2 Interface1](icordebugcode2-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-168">Fornece métodos que estendem os recursos de `ICorDebugCode`.</span><span class="sxs-lookup"><span data-stu-id="88ebc-168">Provides methods that extend the capabilities of `ICorDebugCode`.</span></span>  
  
 <span data-ttu-id="88ebc-169">[Interface ICorDebugCode3](icordebugcode3-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-169">[ICorDebugCode3 Interface](icordebugcode3-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-170">Fornece um método que estende [ICorDebugCode](icordebugcode-interface1.md) e [ICorDebugCode2](icordebugcode2-interface.md) para fornecer informações sobre um valor de retorno gerenciado.</span><span class="sxs-lookup"><span data-stu-id="88ebc-170">Provides a method that extends [ICorDebugCode](icordebugcode-interface1.md) and [ICorDebugCode2](icordebugcode2-interface.md) to provide information about a managed return value.</span></span>  
  
 <span data-ttu-id="88ebc-171">[Interface ICorDebugCode4](icordebugcode4-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-171">[ICorDebugCode4 Interface](icordebugcode4-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-172">Fornece um método que permite que um depurador enumerar as variáveis locais e os argumentos em uma função.</span><span class="sxs-lookup"><span data-stu-id="88ebc-172">Provides a method that enables a debugger to enumerate the local variables and arguments in a function.</span></span>  
  
 <span data-ttu-id="88ebc-173">[ICorDebugCodeEnum Interface1](icordebugcodeenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-173">[ICorDebugCodeEnum Interface1](icordebugcodeenum-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-174">Implementa métodos `ICorDebugEnum` e enumera matrizes de `ICorDebugCode`.</span><span class="sxs-lookup"><span data-stu-id="88ebc-174">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugCode` arrays.</span></span>  
  
 <span data-ttu-id="88ebc-175">[Interface ICorDebugComObjectValue](icordebugcomobjectvalue-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-175">[ICorDebugComObjectValue Interface](icordebugcomobjectvalue-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-176">Fornece métodos para recuperar objetos da interface armazenados em cache.</span><span class="sxs-lookup"><span data-stu-id="88ebc-176">Provides methods to retrieve cached interface objects.</span></span>  
  
 <span data-ttu-id="88ebc-177">[ICorDebugContext Interface1](icordebugcontext-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-177">[ICorDebugContext Interface1](icordebugcontext-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-178">Representa um objeto de contexto.</span><span class="sxs-lookup"><span data-stu-id="88ebc-178">Represents a context object.</span></span> <span data-ttu-id="88ebc-179">Essa interface ainda não foi implementada.</span><span class="sxs-lookup"><span data-stu-id="88ebc-179">This interface has not been implemented yet.</span></span>  
  
 <span data-ttu-id="88ebc-180">[ICorDebugController Interface1](icordebugcontroller-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-180">[ICorDebugController Interface1](icordebugcontroller-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-181">Representa um escopo, um <xref:System.Diagnostics.Process> ou um <xref:System.AppDomain>, em que o contexto de execução de código pode ser controlado.</span><span class="sxs-lookup"><span data-stu-id="88ebc-181">Represents a scope, either a <xref:System.Diagnostics.Process> or an <xref:System.AppDomain>, in which code execution context can be controlled.</span></span>  
  
 <span data-ttu-id="88ebc-182">[Interface ICorDebugDataTarget](icordebugdatatarget-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-182">[ICorDebugDataTarget Interface](icordebugdatatarget-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-183">Fornece uma interface de retorno de chamada que oferece acesso a um determinado processo de destino.</span><span class="sxs-lookup"><span data-stu-id="88ebc-183">Provides a callback interface that provides access to a particular target process.</span></span>  
  
 <span data-ttu-id="88ebc-184">[Interface ICorDebugDataTarget2](icordebugdatatarget2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-184">[ICorDebugDataTarget2 Interface](icordebugdatatarget2-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-185">Estende logicamente a [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="88ebc-185">Logically extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface.</span></span> <span data-ttu-id="88ebc-186">**Disponível em apenas .NET nativo.**</span><span class="sxs-lookup"><span data-stu-id="88ebc-186">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="88ebc-187">[Interface ICorDebugDataTarget3](icordebugdatatarget3-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-187">[ICorDebugDataTarget3 Interface](icordebugdatatarget3-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-188">Estende logicamente a [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface para fornecer informações sobre os módulos carregados.</span><span class="sxs-lookup"><span data-stu-id="88ebc-188">Logically extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface to provide information about loaded modules.</span></span> <span data-ttu-id="88ebc-189">**Disponível em apenas .NET nativo.**</span><span class="sxs-lookup"><span data-stu-id="88ebc-189">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="88ebc-190">[Interface ICorDebugDebugEvent](icordebugdebugevent-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-190">[ICorDebugDebugEvent Interface](icordebugdebugevent-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-191">Define a interface base da qual derivam todos os eventos de depuração `ICorDebug`.</span><span class="sxs-lookup"><span data-stu-id="88ebc-191">Defines the base interface from which all `ICorDebug` debug events derive.</span></span> <span data-ttu-id="88ebc-192">**Disponível em apenas .NET nativo.**</span><span class="sxs-lookup"><span data-stu-id="88ebc-192">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="88ebc-193">[Interface ICorDebugEditAndContinueErrorInfo](icordebugeditandcontinueerrorinfo-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-193">[ICorDebugEditAndContinueErrorInfo Interface](icordebugeditandcontinueerrorinfo-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-194">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="88ebc-194">Obsolete.</span></span> <span data-ttu-id="88ebc-195">Não use essa interface.</span><span class="sxs-lookup"><span data-stu-id="88ebc-195">Do not use this interface.</span></span>  
  
 <span data-ttu-id="88ebc-196">[ICorDebugEditAndContinueSnapshot Interface1](icordebugeditandcontinuesnapshot-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-196">[ICorDebugEditAndContinueSnapshot Interface1](icordebugeditandcontinuesnapshot-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-197">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="88ebc-197">Obsolete.</span></span> <span data-ttu-id="88ebc-198">Não use essa interface.</span><span class="sxs-lookup"><span data-stu-id="88ebc-198">Do not use this interface.</span></span>  
  
 <span data-ttu-id="88ebc-199">[ICorDebugEnum Interface1](icordebugenum-interface1.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-199">[ICorDebugEnum Interface1](icordebugenum-interface1.md)\\</span></span>
 <span data-ttu-id="88ebc-200">Serve como a interface da base abstrata para depurar enumeradores.</span><span class="sxs-lookup"><span data-stu-id="88ebc-200">Serves as the abstract base interface for debugging enumerators.</span></span>  
  
 <span data-ttu-id="88ebc-201">[ICorDebugErrorInfoEnum Interface1](icordebugerrorinfoenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-201">[ICorDebugErrorInfoEnum Interface1](icordebugerrorinfoenum-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-202">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="88ebc-202">Obsolete.</span></span> <span data-ttu-id="88ebc-203">Não use essa interface.</span><span class="sxs-lookup"><span data-stu-id="88ebc-203">Do not use this interface.</span></span>  
  
 <span data-ttu-id="88ebc-204">[ICorDebugEval Interface1](icordebugeval-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-204">[ICorDebugEval Interface1](icordebugeval-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-205">Fornece métodos para permitir que o depurador execute um código no contexto do código que está sendo depurado.</span><span class="sxs-lookup"><span data-stu-id="88ebc-205">Provides methods to enable the debugger to execute code within the context of the code being debugged.</span></span>  
  
 <span data-ttu-id="88ebc-206">[Interface1 ICorDebugEval2](icordebugeval2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-206">[ICorDebugEval2 Interface1](icordebugeval2-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-207">Estende `ICorDebugEval` para fornecer suporte a tipos genéricos.</span><span class="sxs-lookup"><span data-stu-id="88ebc-207">Extends `ICorDebugEval` to provide support for generic types.</span></span>  
  
 <span data-ttu-id="88ebc-208">[Interface ICorDebugExceptionDebugEvent](icordebugexceptiondebugevent-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-208">[ICorDebugExceptionDebugEvent Interface](icordebugexceptiondebugevent-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-209">Estende o [ICorDebugDebugEvent](icordebugdebugevent-interface.md) interface para oferecer suporte a eventos de exceção.</span><span class="sxs-lookup"><span data-stu-id="88ebc-209">Extends the [ICorDebugDebugEvent](icordebugdebugevent-interface.md) interface to support exception events.</span></span> <span data-ttu-id="88ebc-210">**Disponível em apenas .NET nativo.**</span><span class="sxs-lookup"><span data-stu-id="88ebc-210">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="88ebc-211">[Interface ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-211">[ICorDebugExceptionObjectCallStackEnum Interface](icordebugexceptionobjectcallstackenum-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-212">Fornece um enumerador para informações de pilha de chamadas que são inseridas em um objeto de exceção.</span><span class="sxs-lookup"><span data-stu-id="88ebc-212">Provides an enumerator for call stack information that is embedded in an exception object.</span></span>  
  
 <span data-ttu-id="88ebc-213">[Interface ICorDebugExceptionObjectValue](icordebugexceptionobjectvalue-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-213">[ICorDebugExceptionObjectValue Interface](icordebugexceptionobjectvalue-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-214">Estende o [ICorDebugObjectValue](icordebugobjectvalue-interface.md) interface para fornecer informações de rastreamento de pilha de um objeto de exceção gerenciada.</span><span class="sxs-lookup"><span data-stu-id="88ebc-214">Extends the [ICorDebugObjectValue](icordebugobjectvalue-interface.md) interface to provide stack trace information from a managed exception object.</span></span>  
  
 <span data-ttu-id="88ebc-215">[ICorDebugFrame Interface1](icordebugframe-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-215">[ICorDebugFrame Interface1](icordebugframe-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-216">Representa um quadro na pilha atual.</span><span class="sxs-lookup"><span data-stu-id="88ebc-216">Represents a frame on the current stack.</span></span>  
  
 <span data-ttu-id="88ebc-217">[ICorDebugFrameEnum Interface1](icordebugframeenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-217">[ICorDebugFrameEnum Interface1](icordebugframeenum-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-218">Implementa métodos `ICorDebugEnum` e enumera matrizes de `ICorDebugFrame`.</span><span class="sxs-lookup"><span data-stu-id="88ebc-218">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugFrame` arrays.</span></span>  
  
 <span data-ttu-id="88ebc-219">[ICorDebugFunction Interface1](icordebugfunction-interface1.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-219">[ICorDebugFunction Interface1](icordebugfunction-interface1.md)\\</span></span>
 <span data-ttu-id="88ebc-220">Representa uma função ou um método gerenciado.</span><span class="sxs-lookup"><span data-stu-id="88ebc-220">Represents a managed function or method.</span></span>  
  
 <span data-ttu-id="88ebc-221">[ICorDebugFunction2 Interface1](icordebugfunction2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-221">[ICorDebugFunction2 Interface1](icordebugfunction2-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-222">Estende `ICorDebugFunction` logicamente para fornecer suporte à depuração passo a passo Apenas Meu Código.</span><span class="sxs-lookup"><span data-stu-id="88ebc-222">Logically extends `ICorDebugFunction` to provide support for Just My Code step-through debugging.</span></span>  
  
 <span data-ttu-id="88ebc-223">[Interface ICorDebugFunction3](icordebugfunction3-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-223">[ICorDebugFunction3 Interface](icordebugfunction3-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-224">Estende logicamente a [ICorDebugFunction](icordebugfunction-interface1.md) interface para fornecer acesso ao código de uma solicitação ReJIT.</span><span class="sxs-lookup"><span data-stu-id="88ebc-224">Logically extends the [ICorDebugFunction](icordebugfunction-interface1.md) interface to provide access to code from a ReJIT request.</span></span>  
  
 <span data-ttu-id="88ebc-225">[ICorDebugFunctionBreakpoint Interface1](icordebugfunctionbreakpoint-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-225">[ICorDebugFunctionBreakpoint Interface1](icordebugfunctionbreakpoint-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-226">Estende `ICorDebugBreakpoint` para fornecer suporte a pontos de interrupção dentro de funções.</span><span class="sxs-lookup"><span data-stu-id="88ebc-226">Extends `ICorDebugBreakpoint` to support breakpoints within functions.</span></span>  
  
 <span data-ttu-id="88ebc-227">[Interface ICorDebugGCReferenceEnum](icordebuggcreferenceenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-227">[ICorDebugGCReferenceEnum Interface](icordebuggcreferenceenum-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-228">Fornece um enumerador para objetos que serão coletados do lixo.</span><span class="sxs-lookup"><span data-stu-id="88ebc-228">Provides an enumerator for objects that will be garbage-collected.</span></span>  
  
 <span data-ttu-id="88ebc-229">[ICorDebugGenericValue Interface1](icordebuggenericvalue-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-229">[ICorDebugGenericValue Interface1](icordebuggenericvalue-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-230">Uma subclasse de `ICorDebugValue` que se aplica a todos os valores.</span><span class="sxs-lookup"><span data-stu-id="88ebc-230">A subclass of `ICorDebugValue` that applies to all values.</span></span> <span data-ttu-id="88ebc-231">Essa interface fornece métodos Get e Set para o valor.</span><span class="sxs-lookup"><span data-stu-id="88ebc-231">This interface provides Get and Set methods for the value.</span></span>  
  
 <span data-ttu-id="88ebc-232">[Interface ICorDebugGuidToTypeEnum](icordebugguidtotypeenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-232">[ICorDebugGuidToTypeEnum Interface](icordebugguidtotypeenum-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-233">Fornece um enumerador para um objeto que mapeia GUIDs e seus objetos `ICorDebugType` correspondentes.</span><span class="sxs-lookup"><span data-stu-id="88ebc-233">Provides an enumerator for an object that maps GUIDs and their corresponding `ICorDebugType` objects.</span></span>  
  
 <span data-ttu-id="88ebc-234">[ICorDebugHandleValue Interface1](icordebughandlevalue-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-234">[ICorDebugHandleValue Interface1](icordebughandlevalue-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-235">Uma subclasse de `ICorDebugReferenceValue` que representa um valor de referência para o qual o depurador criou um identificador para coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="88ebc-235">A subclass of `ICorDebugReferenceValue` that represents a reference value to which the debugger has created a handle for garbage collection.</span></span>  
  
 <span data-ttu-id="88ebc-236">[Interface ICorDebugHeapEnum](icordebugheapenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-236">[ICorDebugHeapEnum Interface](icordebugheapenum-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-237">Fornece um enumerador para objetos no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="88ebc-237">Provides an enumerator for objects on the managed heap.</span></span>  
  
 <span data-ttu-id="88ebc-238">[Interface ICorDebugHeapSegmentEnum](icordebugheapsegmentenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-238">[ICorDebugHeapSegmentEnum Interface](icordebugheapsegmentenum-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-239">Fornece um enumerador para regiões de memória do heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="88ebc-239">Provides an enumerator for the memory regions of the managed heap.</span></span>  
  
 <span data-ttu-id="88ebc-240">[ICorDebugHeapValue Interface1](icordebugheapvalue-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-240">[ICorDebugHeapValue Interface1](icordebugheapvalue-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-241">Uma subclasse de `ICorDebugValue` que representa um objeto coletado pelo coletor de lixo do CLR.</span><span class="sxs-lookup"><span data-stu-id="88ebc-241">A subclass of `ICorDebugValue` that represents an object that has been collected by the CLR garbage collector.</span></span>  
  
 <span data-ttu-id="88ebc-242">[Interface1 ICorDebugHeapValue2](icordebugheapvalue2-interface1.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-242">[ICorDebugHeapValue2 Interface1](icordebugheapvalue2-interface1.md)\\</span></span>
 <span data-ttu-id="88ebc-243">Uma extensão de `ICorDebugHeapValue` que fornece suporte aos identificadores de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="88ebc-243">An extension of `ICorDebugHeapValue` that provides support for runtime handles.</span></span>  
  
 <span data-ttu-id="88ebc-244">[Interface ICorDebugHeapValue3](icordebugheapvalue3-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-244">[ICorDebugHeapValue3 Interface](icordebugheapvalue3-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-245">Expõe as propriedades de bloqueio de monitoramento de objetos.</span><span class="sxs-lookup"><span data-stu-id="88ebc-245">Exposes the monitor lock properties of objects.</span></span>  
  
 <span data-ttu-id="88ebc-246">[Interface ICorDebugILCode](icordebugilcode-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-246">[ICorDebugILCode Interface](icordebugilcode-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-247">Representa um segmento de código IL (Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="88ebc-247">Represents a segment of intermediate language (IL) code.</span></span>  
  
 <span data-ttu-id="88ebc-248">[Interface ICorDebugILCode2](icordebugilcode2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-248">[ICorDebugILCode2 Interface](icordebugilcode2-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-249">Estende logicamente a [ICorDebugILCode](icordebugilcode-interface.md) deslocamentos ao IL do método original de interface para fornecer métodos que retornam o token de assinatura de variável local de uma função e que mapeiam instrumentada IL (linguagem intermediária) do criador de perfil deslocamentos.</span><span class="sxs-lookup"><span data-stu-id="88ebc-249">Logically extends the [ICorDebugILCode](icordebugilcode-interface.md) interface to provide methods that return the token for a function's local variable signature, and that map a profiler's instrumented intermediate language (IL) offsets to original method IL offsets.</span></span>  
  
 <span data-ttu-id="88ebc-250">[ICorDebugILFrame Interface1](icordebugilframe-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-250">[ICorDebugILFrame Interface1](icordebugilframe-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-251">Representa um registro de ativação do código MSIL.</span><span class="sxs-lookup"><span data-stu-id="88ebc-251">Represents a stack frame of MSIL code.</span></span>  
  
 <span data-ttu-id="88ebc-252">[Interface1 ICorDebugILFrame2](icordebugilframe2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-252">[ICorDebugILFrame2 Interface1](icordebugilframe2-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-253">Uma extensão lógica de `ICorDebugILFrame`.</span><span class="sxs-lookup"><span data-stu-id="88ebc-253">A logical extension of `ICorDebugILFrame`.</span></span>  
  
 <span data-ttu-id="88ebc-254">[Interface ICorDebugILFrame3](icordebugilframe3-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-254">[ICorDebugILFrame3 Interface](icordebugilframe3-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-255">Fornece um método que encapsula o valor de retorno de uma função.</span><span class="sxs-lookup"><span data-stu-id="88ebc-255">Provides a method that encapsulates the return value of a function.</span></span>  
  
 <span data-ttu-id="88ebc-256">[Interface ICorDebugILFrame4](icordebugilframe4-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-256">[ICorDebugILFrame4 Interface](icordebugilframe4-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-257">Fornece métodos que permitem acessar as variáveis locais e inserir o código em um registro de ativação de código IL.</span><span class="sxs-lookup"><span data-stu-id="88ebc-257">Provides methods that allow you to access the local variables and code in a stack frame of intermediate language (IL) code.</span></span> <span data-ttu-id="88ebc-258">Um parâmetro especifica se o depurador possui acesso às variáveis e ao código adicionados na instrumentação do criador de perfil ReJIT.</span><span class="sxs-lookup"><span data-stu-id="88ebc-258">A parameter specifies whether the debugger has access to variables and code added in profiler ReJIT instrumentation.</span></span>  
  
 <span data-ttu-id="88ebc-259">[Interface ICorDebugInstanceFieldSymbol](icordebuginstancefieldsymbol-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-259">[ICorDebugInstanceFieldSymbol Interface](icordebuginstancefieldsymbol-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-260">Representa as informações de símbolo de depuração de um campo de instância.</span><span class="sxs-lookup"><span data-stu-id="88ebc-260">Represents the debug symbol information for an instance field.</span></span> <span data-ttu-id="88ebc-261">**Disponível em apenas .NET nativo.**</span><span class="sxs-lookup"><span data-stu-id="88ebc-261">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="88ebc-262">[ICorDebugInternalFrame Interface1](icordebuginternalframe-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-262">[ICorDebugInternalFrame Interface1](icordebuginternalframe-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-263">Identifica os tipos de quadro para o depurador.</span><span class="sxs-lookup"><span data-stu-id="88ebc-263">Identifies frame types for the debugger.</span></span>  
  
 <span data-ttu-id="88ebc-264">[Interface ICorDebugInternalFrame2](icordebuginternalframe2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-264">[ICorDebugInternalFrame2 Interface](icordebuginternalframe2-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-265">Fornece informações sobre os quadros internos, incluindo o endereço de pilha e a posição em relação ao [ICorDebugFrame](icordebugframe-interface.md) objetos.</span><span class="sxs-lookup"><span data-stu-id="88ebc-265">Provides information about internal frames, including stack address and position in relation to [ICorDebugFrame](icordebugframe-interface.md) objects.</span></span>  
  
 <span data-ttu-id="88ebc-266">[Interface ICorDebugLoadedModule](icordebugloadedmodule-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-266">[ICorDebugLoadedModule Interface](icordebugloadedmodule-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-267">Fornece informações sobre um módulo carregado.</span><span class="sxs-lookup"><span data-stu-id="88ebc-267">Provides information about a loaded module.</span></span> <span data-ttu-id="88ebc-268">**Disponível em apenas .NET nativo.**</span><span class="sxs-lookup"><span data-stu-id="88ebc-268">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="88ebc-269">[Interface ICorDebugManagedCallback](icordebugmanagedcallback-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-269">[ICorDebugManagedCallback Interface](icordebugmanagedcallback-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-270">Fornece métodos para processar retornos de chamada do depurador.</span><span class="sxs-lookup"><span data-stu-id="88ebc-270">Provides methods to process debugger callbacks.</span></span>  
  
 <span data-ttu-id="88ebc-271">[Interface ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-271">[ICorDebugManagedCallback2 Interface](icordebugmanagedcallback2-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-272">Fornece métodos para oferecer suporte à manipulação de exceção do depurador e aos assistentes de depuração gerenciados (MDAs).</span><span class="sxs-lookup"><span data-stu-id="88ebc-272">Provides methods to support debugger exception handling and managed debugging assistants (MDAs).</span></span> <span data-ttu-id="88ebc-273">`ICorDebugManagedCallback2` é uma extensão lógica de `ICorDebugManagedCallback`.</span><span class="sxs-lookup"><span data-stu-id="88ebc-273">`ICorDebugManagedCallback2` is a logical extension of `ICorDebugManagedCallback`.</span></span>  
  
 <span data-ttu-id="88ebc-274">[Interface ICorDebugManagedCallback3](icordebugmanagedcallback3-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-274">[ICorDebugManagedCallback3 Interface](icordebugmanagedcallback3-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-275">Fornece um método de retorno de chamada que indica que uma notificação personalizada ativada do depurador foi gerada.</span><span class="sxs-lookup"><span data-stu-id="88ebc-275">Provides a callback method that indicates that an enabled custom debugger notification has been raised.</span></span>  
  
 <span data-ttu-id="88ebc-276">[Interface ICorDebugMDA](icordebugmda-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-276">[ICorDebugMDA Interface](icordebugmda-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-277">Representa uma mensagem do assistente de depuração gerenciado (MDA).</span><span class="sxs-lookup"><span data-stu-id="88ebc-277">Represents a managed debugging assistant (MDA) message.</span></span>  
  
 <span data-ttu-id="88ebc-278">[Interface ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-278">[ICorDebugMemoryBuffer Interface](icordebugmemorybuffer-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-279">Representa um buffer na memória.</span><span class="sxs-lookup"><span data-stu-id="88ebc-279">Represents an in-memory buffer.</span></span> <span data-ttu-id="88ebc-280">**Disponível em apenas .NET nativo.**</span><span class="sxs-lookup"><span data-stu-id="88ebc-280">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="88ebc-281">[Interface ICorDebugMergedAssemblyRecord](icordebugmergedassemblyrecord-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-281">[ICorDebugMergedAssemblyRecord Interface](icordebugmergedassemblyrecord-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-282">Fornece informações sobre um assembly mesclada.</span><span class="sxs-lookup"><span data-stu-id="88ebc-282">Provides information about a merged assembly.</span></span> <span data-ttu-id="88ebc-283">**Disponível em apenas .NET nativo.**</span><span class="sxs-lookup"><span data-stu-id="88ebc-283">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="88ebc-284">[Interface ICorDebugMetaDataLocator](icordebugmetadatalocator-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-284">[ICorDebugMetaDataLocator Interface](icordebugmetadatalocator-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-285">Fornece informações de metadados ao depurador.</span><span class="sxs-lookup"><span data-stu-id="88ebc-285">Provides metadata information to the debugger.</span></span>  
  
 <span data-ttu-id="88ebc-286">[ICorDebugModule Interface1](icordebugmodule-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-286">[ICorDebugModule Interface1](icordebugmodule-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-287">Representa um módulo de CLR, que é um executável ou uma biblioteca de vínculo dinâmico (DLL).</span><span class="sxs-lookup"><span data-stu-id="88ebc-287">Represents a CLR module, which is either an executable or a dynamic-link library (DLL).</span></span>  
  
 <span data-ttu-id="88ebc-288">[Interface1 ICorDebugModule2](icordebugmodule2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-288">[ICorDebugModule2 Interface1](icordebugmodule2-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-289">Serve como extensão lógica para `ICorDebugModule`.</span><span class="sxs-lookup"><span data-stu-id="88ebc-289">Serves as a logical extension to `ICorDebugModule`.</span></span>  
  
 <span data-ttu-id="88ebc-290">[Interface ICorDebugModule3](icordebugmodule3-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-290">[ICorDebugModule3 Interface](icordebugmodule3-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-291">Cria um leitor de símbolos para um módulo dinâmico.</span><span class="sxs-lookup"><span data-stu-id="88ebc-291">Creates a symbol reader for a dynamic module.</span></span>  
  
 <span data-ttu-id="88ebc-292">[ICorDebugModuleBreakpoint Interface1](icordebugmodulebreakpoint-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-292">[ICorDebugModuleBreakpoint Interface1](icordebugmodulebreakpoint-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-293">Estende `ICorDebugBreakpoint` para fornecer acesso aos módulos específicos.</span><span class="sxs-lookup"><span data-stu-id="88ebc-293">Extends `ICorDebugBreakpoint` to provide access to specific modules.</span></span>  
  
 <span data-ttu-id="88ebc-294">[Interface ICorDebugModuleDebugEvent](icordebugmoduledebugevent-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-294">[ICorDebugModuleDebugEvent Interface](icordebugmoduledebugevent-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-295">Estende o [ICorDebugDebugEvent](icordebugdebugevent-interface.md) interface para oferecer suporte a eventos de nível de módulo.</span><span class="sxs-lookup"><span data-stu-id="88ebc-295">Extends the [ICorDebugDebugEvent](icordebugdebugevent-interface.md) interface to support module-level events.</span></span> <span data-ttu-id="88ebc-296">**Disponível em apenas .NET nativo.**</span><span class="sxs-lookup"><span data-stu-id="88ebc-296">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="88ebc-297">[ICorDebugModuleEnum Interface1](icordebugmoduleenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-297">[ICorDebugModuleEnum Interface1](icordebugmoduleenum-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-298">Implementa métodos `ICorDebugEnum` e enumera matrizes de `ICorDebugModule`.</span><span class="sxs-lookup"><span data-stu-id="88ebc-298">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugModule` arrays.</span></span>  
  
 <span data-ttu-id="88ebc-299">[Interface ICorDebugMutableDataTarget](icordebugmutabledatatarget-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-299">[ICorDebugMutableDataTarget Interface](icordebugmutabledatatarget-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-300">Estende o [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface para oferecer suporte a destinos de dados mutáveis.</span><span class="sxs-lookup"><span data-stu-id="88ebc-300">Extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface to support mutable data targets.</span></span>  
  
 <span data-ttu-id="88ebc-301">[ICorDebugNativeFrame Interface1](icordebugnativeframe-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-301">[ICorDebugNativeFrame Interface1](icordebugnativeframe-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-302">Uma implementação especializada de `ICorDebugFrame` usada para quadros nativos.</span><span class="sxs-lookup"><span data-stu-id="88ebc-302">A specialized implementation of `ICorDebugFrame` used for native frames.</span></span>  
  
 <span data-ttu-id="88ebc-303">[Interface ICorDebugNativeFrame2](icordebugnativeframe2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-303">[ICorDebugNativeFrame2 Interface](icordebugnativeframe2-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-304">Fornece métodos que testam relações de quadros pai e filho.</span><span class="sxs-lookup"><span data-stu-id="88ebc-304">Provides methods that test for child and parent frame relationships.</span></span>  
  
 <span data-ttu-id="88ebc-305">[ICorDebugObjectEnum Interface1](icordebugobjectenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-305">[ICorDebugObjectEnum Interface1](icordebugobjectenum-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-306">Implementa métodos `ICorDebugEnum` e enumera matrizes de objetos pelos endereços virtuais relacionados (RVAs).</span><span class="sxs-lookup"><span data-stu-id="88ebc-306">Implements `ICorDebugEnum` methods, and enumerates arrays of objects by their relative virtual addresses (RVAs).</span></span>  
  
 <span data-ttu-id="88ebc-307">[ICorDebugObjectValue Interface1](icordebugobjectvalue-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-307">[ICorDebugObjectValue Interface1](icordebugobjectvalue-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-308">Uma subclasse de `ICorDebugValue` que representa um valor que contém um objeto.</span><span class="sxs-lookup"><span data-stu-id="88ebc-308">A subclass of `ICorDebugValue` that represents a value that contains an object.</span></span>  
  
 <span data-ttu-id="88ebc-309">[Interface1 ICorDebugObjectValue2](icordebugobjectvalue2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-309">[ICorDebugObjectValue2 Interface1](icordebugobjectvalue2-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-310">Estende `ICorDebugObjectValue` para oferecer suporte a herança e substituição.</span><span class="sxs-lookup"><span data-stu-id="88ebc-310">Extends `ICorDebugObjectValue` to support inheritance and overrides.</span></span>  
  
 <span data-ttu-id="88ebc-311">[ICorDebugProcess Interface1](icordebugprocess-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-311">[ICorDebugProcess Interface1](icordebugprocess-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-312">Representa um processo que está executando o código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="88ebc-312">Represents a process that is executing managed code.</span></span>  
  
 <span data-ttu-id="88ebc-313">[Interface1 ICorDebugProcess2](icordebugprocess2-interface1.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-313">[ICorDebugProcess2 Interface1](icordebugprocess2-interface1.md)\\</span></span>
 <span data-ttu-id="88ebc-314">Uma extensão lógica de `ICorDebugProcess`.</span><span class="sxs-lookup"><span data-stu-id="88ebc-314">A logical extension of `ICorDebugProcess`.</span></span>  
  
 <span data-ttu-id="88ebc-315">[Interface ICorDebugProcess3](icordebugprocess3-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-315">[ICorDebugProcess3 Interface](icordebugprocess3-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-316">Controla as notificações personalizadas do depurador.</span><span class="sxs-lookup"><span data-stu-id="88ebc-316">Controls custom debugger notifications.</span></span>

 <span data-ttu-id="88ebc-317">[Interface ICorDebugProcess4](icordebugprocess4-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-317">[ICorDebugProcess4 Interface](icordebugprocess4-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-318">Fornece suporte para fora do controle de execução do processo.</span><span class="sxs-lookup"><span data-stu-id="88ebc-318">Provides support for out of process execution control.</span></span>
  
 <span data-ttu-id="88ebc-319">[Interface ICorDebugProcess5](icordebugprocess5-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-319">[ICorDebugProcess5 Interface](icordebugprocess5-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-320">Estende o [ICorDebugProcess](icordebugprocess-interface.md) local da interface para oferecer suporte ao acesso para o heap gerenciado, para fornecer informações sobre a coleta de lixo de objetos gerenciados e para determinar se um depurador carrega imagens do aplicativo cache de imagem nativa.</span><span class="sxs-lookup"><span data-stu-id="88ebc-320">Extends the [ICorDebugProcess](icordebugprocess-interface.md) interface to support access to the managed heap, to provide information about garbage collection of managed objects, and to determine whether a debugger loads images from the application's local native image cache.</span></span>  
  
 <span data-ttu-id="88ebc-321">[Interface ICorDebugProcess6](icordebugprocess6-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-321">[ICorDebugProcess6 Interface](icordebugprocess6-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-322">Estende logicamente a [ICorDebugProcess](icordebugprocess-interface.md) interface para habilitar recursos como eventos de depuração gerenciados que são codificados em eventos de depuração de exceção nativa e divisão de módulo virtual.</span><span class="sxs-lookup"><span data-stu-id="88ebc-322">Logically extends the [ICorDebugProcess](icordebugprocess-interface.md) interface to enable features such as decoding managed debug events that are encoded in native exception debug events and virtual module splitting.</span></span> <span data-ttu-id="88ebc-323">**Disponível em apenas .NET nativo.**</span><span class="sxs-lookup"><span data-stu-id="88ebc-323">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="88ebc-324">[Interface ICorDebugProcess7](icordebugprocess7-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-324">[ICorDebugProcess7 Interface](icordebugprocess7-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-325">Fornece um método que configura o depurador para manipular atualizações de metadados na memória no processo de destino.</span><span class="sxs-lookup"><span data-stu-id="88ebc-325">Provides a method that configures the debugger to handle in-memory metadata updates in the target process.</span></span>  
  
 <span data-ttu-id="88ebc-326">[Interface ICorDebugProcess8](icordebugprocess8-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-326">[ICorDebugProcess8 Interface](icordebugprocess8-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-327">Estende logicamente a [ICorDebugProcess](icordebugprocess-interface.md) interface para habilitar ou desabilitar determinados tipos de [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) retornos de chamada de exceção.</span><span class="sxs-lookup"><span data-stu-id="88ebc-327">Logically extends the [ICorDebugProcess](icordebugprocess-interface.md) interface to enable or disable certain types of [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>  
  
 <span data-ttu-id="88ebc-328">[ICorDebugProcessEnum Interface1](icordebugprocessenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-328">[ICorDebugProcessEnum Interface1](icordebugprocessenum-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-329">Implementa métodos `ICorDebugEnum` e enumera matrizes de `ICorDebugProcess`.</span><span class="sxs-lookup"><span data-stu-id="88ebc-329">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugProcess` arrays.</span></span>  
  
 <span data-ttu-id="88ebc-330">[ICorDebugReferenceValue Interface1](icordebugreferencevalue-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-330">[ICorDebugReferenceValue Interface1](icordebugreferencevalue-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-331">Uma subclasse de `ICorDebugValue` que oferece suporte a tipos de referência.</span><span class="sxs-lookup"><span data-stu-id="88ebc-331">A subclass of `ICorDebugValue` that supports reference types.</span></span>  
  
 <span data-ttu-id="88ebc-332">[ICorDebugRegisterSet Interface](icordebugregisterset-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-332">[ICorDebugRegisterSet Interface](icordebugregisterset-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-333">Representa o conjunto de registros disponíveis no computador que está executando o código no momento.</span><span class="sxs-lookup"><span data-stu-id="88ebc-333">Represents the set of registers available on the machine that is currently executing code.</span></span>  
  
 <span data-ttu-id="88ebc-334">[ICorDebugRegisterSet2 Interface](icordebugregisterset2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-334">[ICorDebugRegisterSet2 Interface](icordebugregisterset2-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-335">Estende os recursos de `ICorDebugRegisterSet` para as plataformas de hardware que possuem mais de 64 registros.</span><span class="sxs-lookup"><span data-stu-id="88ebc-335">Extends the capabilities of `ICorDebugRegisterSet` for hardware platforms that have more than 64 registers.</span></span>  
  
 <span data-ttu-id="88ebc-336">[Interface ICorDebugRemote](icordebugremote-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-336">[ICorDebugRemote Interface](icordebugremote-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-337">Fornece a capacidade de iniciar ou anexar um depurador gerenciado a um processo remoto de destino.</span><span class="sxs-lookup"><span data-stu-id="88ebc-337">Provides the ability to launch or attach a managed debugger to a remote target process.</span></span>  
  
 <span data-ttu-id="88ebc-338">[Interface ICorDebugRemoteTarget](icordebugremotetarget-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-338">[ICorDebugRemoteTarget Interface](icordebugremotetarget-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-339">Fornece métodos que permitem a você depurar aplicativos baseados no Silverlight no ambiente do CLR.</span><span class="sxs-lookup"><span data-stu-id="88ebc-339">Provides methods that enable you to debug Silverlight-based applications in the CLR environment.</span></span>  
  
 <span data-ttu-id="88ebc-340">[Interface ICorDebugRuntimeUnwindableFrame](icordebugruntimeunwindableframe-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-340">[ICorDebugRuntimeUnwindableFrame Interface](icordebugruntimeunwindableframe-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-341">Fornece suporte para os métodos não gerenciados que exigem que o CLR (Common Language Runtime) desenrole um quadro.</span><span class="sxs-lookup"><span data-stu-id="88ebc-341">Provides support for unmanaged methods that require the common language runtime (CLR) to unwind a frame.</span></span>  
  
 <span data-ttu-id="88ebc-342">[Interface ICorDebugStackWalk](icordebugstackwalk-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-342">[ICorDebugStackWalk Interface](icordebugstackwalk-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-343">Fornece métodos para colocar os métodos gerenciados, ou quadros, em uma pilha de thread.</span><span class="sxs-lookup"><span data-stu-id="88ebc-343">Provides methods for getting the managed methods, or frames, on a thread’s stack.</span></span>  
  
 <span data-ttu-id="88ebc-344">[Interface ICorDebugStaticFieldSymbol](icordebugstaticfieldsymbol-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-344">[ICorDebugStaticFieldSymbol Interface](icordebugstaticfieldsymbol-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-345">Representa as informações de símbolo de depuração de um campo estático.</span><span class="sxs-lookup"><span data-stu-id="88ebc-345">Represents the debug symbol information for a static field.</span></span> <span data-ttu-id="88ebc-346">**Disponível em apenas .NET nativo.**</span><span class="sxs-lookup"><span data-stu-id="88ebc-346">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="88ebc-347">[ICorDebugStepper Interface1](icordebugstepper-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-347">[ICorDebugStepper Interface1](icordebugstepper-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-348">Representa uma etapa na execução do código que é realizada por um depurador, serve como um identificador entre a emissão e a conclusão de um comando e fornece uma maneira de cancelar uma etapa.</span><span class="sxs-lookup"><span data-stu-id="88ebc-348">Represents a step in code execution that is performed by a debugger, serves as an identifier between the issuance and completion of a command, and provides a way to cancel a step.</span></span>  
  
 <span data-ttu-id="88ebc-349">[Interface1 ICorDebugStepper2](icordebugstepper2-interface1.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-349">[ICorDebugStepper2 Interface1](icordebugstepper2-interface1.md)\\</span></span>
 <span data-ttu-id="88ebc-350">Fornece suporte para a depuração JMC (Apenas Meu Código).</span><span class="sxs-lookup"><span data-stu-id="88ebc-350">Provides support for Just My Code (JMC) debugging.</span></span>  
  
 <span data-ttu-id="88ebc-351">[ICorDebugStepperEnum Interface1](icordebugstepperenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-351">[ICorDebugStepperEnum Interface1](icordebugstepperenum-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-352">Implementa métodos `ICorDebugEnum` e enumera matrizes de `ICorDebugStepper`.</span><span class="sxs-lookup"><span data-stu-id="88ebc-352">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugStepper` arrays.</span></span>  
  
 <span data-ttu-id="88ebc-353">[ICorDebugStringValue Interface1](icordebugstringvalue-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-353">[ICorDebugStringValue Interface1](icordebugstringvalue-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-354">Uma subclasse de `ICorDebugHeapValue` que se aplica a valores de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="88ebc-354">A subclass of `ICorDebugHeapValue` that applies to string values.</span></span>  
  
 <span data-ttu-id="88ebc-355">[Interface ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-355">[ICorDebugSymbolProvider Interface](icordebugsymbolprovider-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-356">Fornece métodos que podem ser usados para recuperar informações de símbolo de depuração.</span><span class="sxs-lookup"><span data-stu-id="88ebc-356">Provides methods that can be used to retrieve debug symbol information.</span></span> <span data-ttu-id="88ebc-357">**Disponível em apenas .NET nativo.**</span><span class="sxs-lookup"><span data-stu-id="88ebc-357">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="88ebc-358">[Interface ICorDebugSymbolProvider2](icordebugsymbolprovider2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-358">[ICorDebugSymbolProvider2 Interface](icordebugsymbolprovider2-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-359">Estende logicamente a [ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md) interface para recuperar informações de símbolo de depuração adicionais.</span><span class="sxs-lookup"><span data-stu-id="88ebc-359">Logically extends the [ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md) interface to retrieve additional debug symbol information.</span></span> <span data-ttu-id="88ebc-360">**Disponível em apenas .NET nativo.**</span><span class="sxs-lookup"><span data-stu-id="88ebc-360">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="88ebc-361">[ICorDebugThread Interface1](icordebugthread-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-361">[ICorDebugThread Interface1](icordebugthread-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-362">Representa um thread em um processo.</span><span class="sxs-lookup"><span data-stu-id="88ebc-362">Represents a thread in a process.</span></span> <span data-ttu-id="88ebc-363">O tempo de vida de uma instância `ICorDebugThread` é igual ao tempo de vida do thread que ela representa.</span><span class="sxs-lookup"><span data-stu-id="88ebc-363">The lifetime of an `ICorDebugThread` instance is the same as the lifetime of the thread it represents.</span></span>  
  
 <span data-ttu-id="88ebc-364">[Interface1 ICorDebugThread2](icordebugthread2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-364">[ICorDebugThread2 Interface1](icordebugthread2-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-365">Serve como extensão lógica para `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="88ebc-365">Serves as a logical extension to `ICorDebugThread`.</span></span>  
  
 <span data-ttu-id="88ebc-366">[Interface ICorDebugThread3](icordebugthread3-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-366">[ICorDebugThread3 Interface](icordebugthread3-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-367">Fornece o ponto de entrada para o [ICorDebugStackWalk](icordebugstackwalk-interface.md) e as interfaces correspondentes.</span><span class="sxs-lookup"><span data-stu-id="88ebc-367">Provides the entry point to the [ICorDebugStackWalk](icordebugstackwalk-interface.md) and corresponding interfaces.</span></span>  
  
 <span data-ttu-id="88ebc-368">[Interface ICorDebugThread4](icordebugthread4-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-368">[ICorDebugThread4 Interface](icordebugthread4-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-369">Fornece informações de bloqueio de thread.</span><span class="sxs-lookup"><span data-stu-id="88ebc-369">Provides thread blocking information.</span></span>  
  
 <span data-ttu-id="88ebc-370">[ICorDebugThreadEnum Interface1](icordebugthreadenum-interface1.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-370">[ICorDebugThreadEnum Interface1](icordebugthreadenum-interface1.md)\\</span></span>
 <span data-ttu-id="88ebc-371">Implementa métodos `ICorDebugEnum` e enumera matrizes de `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="88ebc-371">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugThread` arrays.</span></span>  
  
 <span data-ttu-id="88ebc-372">[ICorDebugType Interface1](icordebugtype-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-372">[ICorDebugType Interface1](icordebugtype-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-373">Representa um tipo, que pode ser básico ou complexo (isto é, definido pelo usuário).</span><span class="sxs-lookup"><span data-stu-id="88ebc-373">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="88ebc-374">Se o tipo for genérico, `ICorDebugType` representará o tipo genérico instanciado.</span><span class="sxs-lookup"><span data-stu-id="88ebc-374">If the type is generic, `ICorDebugType` represents the instantiated generic type.</span></span>  
  
 <span data-ttu-id="88ebc-375">[Interface ICorDebugType2](icordebugtype2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-375">[ICorDebugType2 Interface](icordebugtype2-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-376">Estende o [ICorDebugType](icordebugtype-interface.md) interface para recuperar o identificador de tipo de um tipo base ou um tipo complexo (definido pelo usuário).</span><span class="sxs-lookup"><span data-stu-id="88ebc-376">Extends the [ICorDebugType](icordebugtype-interface.md) interface to retrieve the type identifier  of a base type or complex (user-defined) type.</span></span>  
  
 <span data-ttu-id="88ebc-377">[ICorDebugTypeEnum Interface1](icordebugtypeenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-377">[ICorDebugTypeEnum Interface1](icordebugtypeenum-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-378">Implementa métodos `ICorDebugEnum` e enumera matrizes de `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="88ebc-378">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugType` arrays.</span></span>  
  
 <span data-ttu-id="88ebc-379">[Interface ICorDebugUnmanagedCallback](icordebugunmanagedcallback-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-379">[ICorDebugUnmanagedCallback Interface](icordebugunmanagedcallback-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-380">Fornece notificação de eventos nativos que não estão diretamente relacionados ao CLR.</span><span class="sxs-lookup"><span data-stu-id="88ebc-380">Provides notification of native events that are not directly related to the CLR.</span></span>  
  
 <span data-ttu-id="88ebc-381">[ICorDebugValue](icordebugvalue-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-381">[ICorDebugValue](icordebugvalue-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-382">Representa um valor de leitura ou gravação no processo que está sendo depurado.</span><span class="sxs-lookup"><span data-stu-id="88ebc-382">Represents a read or write value in the process being debugged.</span></span>  
  
 <span data-ttu-id="88ebc-383">[ICorDebugValue2](icordebugvalue2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-383">[ICorDebugValue2](icordebugvalue2-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-384">Estende `ICorDebugValue` para oferecer suporte a `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="88ebc-384">Extends `ICorDebugValue` to provide support for `ICorDebugType`.</span></span>  
  
 <span data-ttu-id="88ebc-385">[Interface ICorDebugValue3](icordebugvalue3-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-385">[ICorDebugValue3 Interface](icordebugvalue3-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-386">Estende as interfaces "ICorDebugValue" e "ICorDebugValue2" para fornecer suporte para matrizes que são maiores que 2 GB.</span><span class="sxs-lookup"><span data-stu-id="88ebc-386">Extends the "ICorDebugValue" and "ICorDebugValue2" interfaces to provide support for arrays that are larger than 2 GB.</span></span>  
  
 <span data-ttu-id="88ebc-387">[ICorDebugValueBreakpoint](icordebugvaluebreakpoint-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-387">[ICorDebugValueBreakpoint](icordebugvaluebreakpoint-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-388">Estende `ICorDebugBreakpoint` para fornecer acesso a valores específicos.</span><span class="sxs-lookup"><span data-stu-id="88ebc-388">Extends `ICorDebugBreakpoint` to provide access to specific values.</span></span>  
  
 <span data-ttu-id="88ebc-389">[ICorDebugValueEnum](icordebugvalueenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-389">[ICorDebugValueEnum](icordebugvalueenum-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-390">Implementa métodos `ICorDebugEnum` e enumera matrizes de `ICorDebugValue`.</span><span class="sxs-lookup"><span data-stu-id="88ebc-390">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugValue` arrays.</span></span>  
  
 <span data-ttu-id="88ebc-391">[Interface ICorDebugVariableHome](icordebugvariablehome-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-391">[ICorDebugVariableHome Interface](icordebugvariablehome-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-392">Representa um argumento de uma função ou variável local.</span><span class="sxs-lookup"><span data-stu-id="88ebc-392">Represents a local variable or argument of a function.</span></span>  
  
 <span data-ttu-id="88ebc-393">[Interface ICorDebugVariableHomeEnum](icordebugvariablehomeenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-393">[ICorDebugVariableHomeEnum Interface](icordebugvariablehomeenum-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-394">Fornece um enumerador para as variáveis locais e os argumentos em uma função.</span><span class="sxs-lookup"><span data-stu-id="88ebc-394">Provides an enumerator to the local variables and arguments in a function.</span></span>  
  
 <span data-ttu-id="88ebc-395">[Interface ICorDebugVariableSymbol](icordebugvariablesymbol-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-395">[ICorDebugVariableSymbol Interface](icordebugvariablesymbol-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-396">Recupera as informações de símbolo de depuração de uma variável.</span><span class="sxs-lookup"><span data-stu-id="88ebc-396">Retrieves the debug symbol information for a variable.</span></span> <span data-ttu-id="88ebc-397">**Disponível em apenas .NET nativo.**</span><span class="sxs-lookup"><span data-stu-id="88ebc-397">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="88ebc-398">[Interface ICorDebugVirtualUnwinder](icordebugvirtualunwinder-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-398">[ICorDebugVirtualUnwinder Interface](icordebugvirtualunwinder-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-399">Fornece métodos para ajudá-lo desenrolamento de pilha.</span><span class="sxs-lookup"><span data-stu-id="88ebc-399">Provides methods to help in stack unwinding.</span></span> <span data-ttu-id="88ebc-400">**Disponível em apenas .NET nativo.**</span><span class="sxs-lookup"><span data-stu-id="88ebc-400">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="88ebc-401">[Interface ICorPublish](icorpublish-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-401">[ICorPublish Interface](icorpublish-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-402">Serve como a interface geral para os processos de publicação.</span><span class="sxs-lookup"><span data-stu-id="88ebc-402">Serves as the general interface for the publishing processes.</span></span>  
  
 <span data-ttu-id="88ebc-403">[ICorPublishAppDomain Interface](icorpublishappdomain-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-403">[ICorPublishAppDomain Interface](icorpublishappdomain-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-404">Representa e fornece informações sobre um domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="88ebc-404">Represents and provides information about an application domain.</span></span>  
  
 <span data-ttu-id="88ebc-405">[Interface ICorPublishAppDomainEnum](icorpublishappdomainenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-405">[ICorPublishAppDomainEnum Interface](icorpublishappdomainenum-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-406">Fornece métodos que percorrem uma coleção de objetos `ICorPublishAppDomain` existentes em um processo.</span><span class="sxs-lookup"><span data-stu-id="88ebc-406">Provides methods that traverse a collection of `ICorPublishAppDomain` objects that currently exist within a process.</span></span>  
  
 <span data-ttu-id="88ebc-407">[Interface ICorPublishEnum](icorpublishenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-407">[ICorPublishEnum Interface](icorpublishenum-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-408">Serve como a base abstrata para a publicação de enumeradores.</span><span class="sxs-lookup"><span data-stu-id="88ebc-408">Serves as the abstract base for publishing enumerators.</span></span>  
  
 <span data-ttu-id="88ebc-409">[Interface ICorPublishProcess](icorpublishprocess-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-409">[ICorPublishProcess Interface](icorpublishprocess-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-410">Fornece métodos que acessam informações sobre um processo.</span><span class="sxs-lookup"><span data-stu-id="88ebc-410">Provides methods that access information about a process.</span></span>  
  
 <span data-ttu-id="88ebc-411">[Interface ICorPublishProcessEnum](icorpublishprocessenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-411">[ICorPublishProcessEnum Interface](icorpublishprocessenum-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-412">Fornece métodos que percorrem uma coleção de objetos `ICorPublishProcess`.</span><span class="sxs-lookup"><span data-stu-id="88ebc-412">Provides methods that traverse a collection of `ICorPublishProcess` objects.</span></span>  

 <span data-ttu-id="88ebc-413">[ISOSDacInterface Interface](isosdacinterface-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-413">[ISOSDacInterface Interface](isosdacinterface-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-414">Fornece métodos auxiliares para acessar dados de `SOS`.</span><span class="sxs-lookup"><span data-stu-id="88ebc-414">Provides helper methods to access data from `SOS`.</span></span>

 <span data-ttu-id="88ebc-415">[Interface IXCLRDataMethodDefinition](ixclrdatamethoddefinition-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-415">[IXCLRDataMethodDefinition Interface](ixclrdatamethoddefinition-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-416">Fornece métodos para consultar informações sobre uma definição de método.</span><span class="sxs-lookup"><span data-stu-id="88ebc-416">Provides methods for querying information about a method definition.</span></span>
 
 <span data-ttu-id="88ebc-417">[Interface IXCLRDataMethodInstance](ixclrdatamethodinstance-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-417">[IXCLRDataMethodInstance Interface](ixclrdatamethodinstance-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-418">Fornece métodos para consultar informações sobre uma instância de método.</span><span class="sxs-lookup"><span data-stu-id="88ebc-418">Provides methods for querying information about a method instance.</span></span>
 
 <span data-ttu-id="88ebc-419">[Interface IXCLRDataModule](ixclrdatamodule-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-419">[IXCLRDataModule Interface](ixclrdatamodule-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-420">Fornece métodos para consultar informações sobre um módulo carregado.</span><span class="sxs-lookup"><span data-stu-id="88ebc-420">Provides methods for querying information about a loaded module.</span></span>
 
 <span data-ttu-id="88ebc-421">[Interface IXCLRDataProcess](ixclrdataprocess-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-421">[IXCLRDataProcess Interface](ixclrdataprocess-interface.md)\\</span></span>
 <span data-ttu-id="88ebc-422">Fornece métodos para consultar informações sobre um processo.</span><span class="sxs-lookup"><span data-stu-id="88ebc-422">Provides methods for querying information about a process.</span></span>
  
## <a name="related-sections"></a><span data-ttu-id="88ebc-423">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="88ebc-423">Related Sections</span></span>  
 <span data-ttu-id="88ebc-424">[Depurando Coclasses](debugging-coclasses.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-424">[Debugging Coclasses](debugging-coclasses.md)\\</span></span>
 <span data-ttu-id="88ebc-425">[Depurando funções estáticas globais](debugging-global-static-functions.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-425">[Debugging Global Static Functions](debugging-global-static-functions.md)\\</span></span>
 <span data-ttu-id="88ebc-426">[Declarando enumerações](debugging-enumerations.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-426">[Debugging Enumerations](debugging-enumerations.md)\\</span></span>
 <span data-ttu-id="88ebc-427">[Estruturas de depuração](debugging-structures.md)\\</span><span class="sxs-lookup"><span data-stu-id="88ebc-427">[Debugging Structures](debugging-structures.md)\\</span></span>
