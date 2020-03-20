---
title: Depurando interfaces
ms.date: 02/07/2019
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: b6297c26-7624-4431-8af4-14112d07bcd5
ms.openlocfilehash: c4b9cdc2bc90096ab7c3b041bd8aa2742b48c35c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179163"
---
# <a name="debugging-interfaces"></a><span data-ttu-id="a4068-102">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="a4068-102">Debugging Interfaces</span></span>
<span data-ttu-id="a4068-103">Esta seção descreve as interfaces não gerenciadas que lidam com a depuração de um programa que está sendo executado no CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="a4068-103">This section describes the unmanaged interfaces that handle the debugging of a program that is executing in the common language runtime (CLR).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a4068-104">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="a4068-104">In This Section</span></span>  
 <span data-ttu-id="a4068-105">[ICLRDataEnumMemoryRegions Interface](iclrdataenummemoryregions-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-105">[ICLRDataEnumMemoryRegions Interface](iclrdataenummemoryregions-interface.md)</span></span>\
 <span data-ttu-id="a4068-106">Fornece um método para enumerar as regiões da memória que são especificadas por chamadores.</span><span class="sxs-lookup"><span data-stu-id="a4068-106">Provides a method to enumerate regions of memory that are specified by callers.</span></span>  
  
 <span data-ttu-id="a4068-107">[Interface de retorno de callback do ICLRDataEnumMemoryRegions](iclrdataenummemoryregionscallback-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-107">[ICLRDataEnumMemoryRegionsCallback Interface](iclrdataenummemoryregionscallback-interface.md)</span></span>\
 <span data-ttu-id="a4068-108">Fornece um método de retorno de chamada para `EnumMemoryRegions` relatar ao depurador o resultado de uma tentativa de enumerar uma região especificada da memória.</span><span class="sxs-lookup"><span data-stu-id="a4068-108">Provides a callback method for `EnumMemoryRegions` to report to the debugger, the result of an attempt to enumerate a specified region of memory.</span></span>  
  
 <span data-ttu-id="a4068-109">[ICLRDataTarget Interface](iclrdatatarget-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-109">[ICLRDataTarget Interface](iclrdatatarget-interface.md)</span></span>\
 <span data-ttu-id="a4068-110">Fornece métodos para interação com um processo de CLR de destino.</span><span class="sxs-lookup"><span data-stu-id="a4068-110">Provides methods for interaction with a target CLR process.</span></span>  
  
 <span data-ttu-id="a4068-111">[ICLRDataTarget2 Interface](iclrdatatarget2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-111">[ICLRDataTarget2 Interface](iclrdatatarget2-interface.md)</span></span>\
 <span data-ttu-id="a4068-112">Uma subclasse de `ICLRDataTarget` que é usada pela camada de serviços de acesso a dados para manipular as regiões de memória virtual no processo de destino.</span><span class="sxs-lookup"><span data-stu-id="a4068-112">A subclass of `ICLRDataTarget` that is used by the data access services layer to manipulate virtual memory regions in the target process.</span></span>  
  
 <span data-ttu-id="a4068-113">[ICLRDataTarget3 Interface](iclrdatatarget3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-113">[ICLRDataTarget3 Interface](iclrdatatarget3-interface.md)</span></span>\
 <span data-ttu-id="a4068-114">Uma subclasse de [ICLRDataTarget2](iclrdatatarget2-interface.md) que fornece acesso a informações de exceção.</span><span class="sxs-lookup"><span data-stu-id="a4068-114">A subclass of [ICLRDataTarget2](iclrdatatarget2-interface.md) that provides access to exception information.</span></span>  
  
 <span data-ttu-id="a4068-115">[Interface de depuração do ICLR](iclrdebugging-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-115">[ICLRDebugging Interface](iclrdebugging-interface.md)</span></span>\
 <span data-ttu-id="a4068-116">Fornece métodos que manipulam os módulos de carregamento e descarregamento para depuração.</span><span class="sxs-lookup"><span data-stu-id="a4068-116">Provides methods that handle loading and unloading modules for debugging.</span></span>  
  
 <span data-ttu-id="a4068-117">[Interface de provedor de biblioteca do ICLRDebugging](iclrdebugginglibraryprovider-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-117">[ICLRDebuggingLibraryProvider Interface](iclrdebugginglibraryprovider-interface.md)</span></span>\
 <span data-ttu-id="a4068-118">Inclui o método [ProvideLibrary Method,](iclrdebugginglibraryprovider-providelibrary-method.md) que obtém uma interface de retorno de chamada do provedor de biblioteca que permite que bibliotecas de depuração específicas de versão em tempo de execução de idiomas comuns sejam localizadas e carregadas demanda.</span><span class="sxs-lookup"><span data-stu-id="a4068-118">Includes the [ProvideLibrary Method](iclrdebugginglibraryprovider-providelibrary-method.md) method, which gets a library provider callback interface that allows common language runtime version-specific debugging libraries to be located and loaded on demand.</span></span>  
  
 <span data-ttu-id="a4068-119">[ICLRMetadataLocator Interface](iclrmetadatalocator-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-119">[ICLRMetadataLocator Interface](iclrmetadatalocator-interface.md)</span></span>\
 <span data-ttu-id="a4068-120">A interface usada pela camada de serviços de acesso a dados para localizar metadados de assemblies em um processo de destino.</span><span class="sxs-lookup"><span data-stu-id="a4068-120">Interface used by the data access services layer to locate metadata of assemblies in a target process.</span></span>  
  
 <span data-ttu-id="a4068-121">[ICorDebug Interface](icordebug-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-121">[ICorDebug Interface](icordebug-interface.md)</span></span>\
 <span data-ttu-id="a4068-122">Fornece métodos que permitem que os desenvolvedores depurem aplicativos no ambiente do CLR.</span><span class="sxs-lookup"><span data-stu-id="a4068-122">Provides methods that allow developers to debug applications in the CLR environment.</span></span>  
  
 <span data-ttu-id="a4068-123">[Interface de domínio do ICorDebugApp](icordebugappdomain-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-123">[ICorDebugAppDomain Interface](icordebugappdomain-interface.md)</span></span>\
 <span data-ttu-id="a4068-124">Fornece métodos para depurar domínios de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a4068-124">Provides methods for debugging application domains.</span></span>  
  
 <span data-ttu-id="a4068-125">[ICorDebugAppDomain2 Interface](icordebugappdomain2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-125">[ICorDebugAppDomain2 Interface](icordebugappdomain2-interface.md)</span></span>\
 <span data-ttu-id="a4068-126">Fornece métodos para trabalhar com matrizes, ponteiros, ponteiros de função e tipos ByRef.</span><span class="sxs-lookup"><span data-stu-id="a4068-126">Provides methods to work with arrays, pointers, function pointers, and ByRef types.</span></span> <span data-ttu-id="a4068-127">Essa interface é uma extensão da interface `ICorDebugAppDomain`.</span><span class="sxs-lookup"><span data-stu-id="a4068-127">This interface is an extension of the `ICorDebugAppDomain` interface.</span></span>  
  
 <span data-ttu-id="a4068-128">[ICorDebugAppDomain3 Interface](icordebugappdomain3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-128">[ICorDebugAppDomain3 Interface](icordebugappdomain3-interface.md)</span></span>\
 <span data-ttu-id="a4068-129">Fornece métodos para trabalhar com os tipos de tempo de execução do Windows em um domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a4068-129">Provides methods to work with the Windows Runtime types in an application domain.</span></span> <span data-ttu-id="a4068-130">Essa interface é uma extensão das interfaces `ICorDebugAppDomain` e `ICorDebugAppDomain2`.</span><span class="sxs-lookup"><span data-stu-id="a4068-130">This interface is an extension of the `ICorDebugAppDomain` and `ICorDebugAppDomain2` interfaces.</span></span>  
  
 <span data-ttu-id="a4068-131">[ICorDebugAppDomain4 Interface](icordebugappdomain4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-131">[ICorDebugAppDomain4 Interface](icordebugappdomain4-interface.md)</span></span>\
 <span data-ttu-id="a4068-132">Logicamente, estende a interface [ICorDebugAppDomain](icordebugappdomain-interface.md) para obter um objeto gerenciado a partir de um invólucro callable COM.</span><span class="sxs-lookup"><span data-stu-id="a4068-132">Logically extends the [ICorDebugAppDomain](icordebugappdomain-interface.md) interface to get a managed object from a COM callable wrapper.</span></span>  
  
 <span data-ttu-id="a4068-133">[ICorDebugAppDomainEnum Interface](icordebugappdomainenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-133">[ICorDebugAppDomainEnum Interface](icordebugappdomainenum-interface.md)</span></span>\
 <span data-ttu-id="a4068-134">Fornece um método que retorna um número especificado de valores `ICorDebugAppDomain` iniciando no próximo local na enumeração.</span><span class="sxs-lookup"><span data-stu-id="a4068-134">Provides a method that returns a specified number of `ICorDebugAppDomain` values starting at the next location in the enumeration.</span></span>  
  
 <span data-ttu-id="a4068-135">[Interface de valor do ICorDebugArray](icordebugarrayvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-135">[ICorDebugArrayValue Interface](icordebugarrayvalue-interface.md)</span></span>\
 <span data-ttu-id="a4068-136">Uma subclasse de `ICorDebugHeapValue` que representa uma matriz unidimensional ou multidimensional.</span><span class="sxs-lookup"><span data-stu-id="a4068-136">A subclass of `ICorDebugHeapValue` that represents a single-dimensional or multi-dimensional array.</span></span>  
  
 <span data-ttu-id="a4068-137">[ICorDebugAssembly Interface](icordebugassembly-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-137">[ICorDebugAssembly Interface](icordebugassembly-interface.md)</span></span>\
 <span data-ttu-id="a4068-138">Representa um assembly.</span><span class="sxs-lookup"><span data-stu-id="a4068-138">Represents an assembly.</span></span>  
  
 <span data-ttu-id="a4068-139">[ICorDebugAssembly2 Interface](icordebugassembly2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-139">[ICorDebugAssembly2 Interface](icordebugassembly2-interface.md)</span></span>\
 <span data-ttu-id="a4068-140">Representa um assembly.</span><span class="sxs-lookup"><span data-stu-id="a4068-140">Represents an assembly.</span></span> <span data-ttu-id="a4068-141">Essa interface é uma extensão da interface `ICorDebugAssembly`.</span><span class="sxs-lookup"><span data-stu-id="a4068-141">This interface is an extension of the `ICorDebugAssembly` interface.</span></span>  
  
 <span data-ttu-id="a4068-142">[ICorDebugAssembly3 Interface](icordebugassembly3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-142">[ICorDebugAssembly3 Interface](icordebugassembly3-interface.md)</span></span>\
 <span data-ttu-id="a4068-143">Logicamente, estende a interface [ICorDebugAssembly](icordebugassembly-interface.md) para fornecer suporte para conjuntos de contêineres e seus conjuntos contidos.</span><span class="sxs-lookup"><span data-stu-id="a4068-143">Logically extends the [ICorDebugAssembly](icordebugassembly-interface.md) interface to provide support for container assemblies and their contained assemblies.</span></span> <span data-ttu-id="a4068-144">**Disponível apenas no .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="a4068-144">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="a4068-145">[ICorDebugAssemblyEnum Interface](icordebugassemblyenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-145">[ICorDebugAssemblyEnum Interface](icordebugassemblyenum-interface.md)</span></span>\
 <span data-ttu-id="a4068-146">Implementa métodos `ICorDebugEnum` e enumera matrizes de `ICorDebugAssembly`.</span><span class="sxs-lookup"><span data-stu-id="a4068-146">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugAssembly` arrays.</span></span>  
  
 <span data-ttu-id="a4068-147">[ICorDebugBlockingObjectEnum Interface](icordebugblockingobjectenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-147">[ICorDebugBlockingObjectEnum Interface](icordebugblockingobjectenum-interface.md)</span></span>\
 <span data-ttu-id="a4068-148">Fornece um enumerador para uma lista de estruturas [CorDebugBlockingObject.](cordebugblockingobject-structure.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-148">Provides an enumerator for a list of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures.</span></span>  
  
 <span data-ttu-id="a4068-149">[ICorDebugBoxValue Interface](icordebugboxvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-149">[ICorDebugBoxValue Interface](icordebugboxvalue-interface.md)</span></span>\
 <span data-ttu-id="a4068-150">Uma subclasse de `ICorDebugHeapValue` que representa um objeto de classe com valor boxed.</span><span class="sxs-lookup"><span data-stu-id="a4068-150">A subclass of `ICorDebugHeapValue` that represents a boxed value class object.</span></span>  
  
 <span data-ttu-id="a4068-151">[ICorDebugBreakpoint Interface](icordebugbreakpoint-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-151">[ICorDebugBreakpoint Interface](icordebugbreakpoint-interface.md)</span></span>\
 <span data-ttu-id="a4068-152">Representa um ponto de interrupção em uma função ou um ponto de inspeção em um valor.</span><span class="sxs-lookup"><span data-stu-id="a4068-152">Represents a breakpoint in a function or a watch point on a value.</span></span>  
  
 <span data-ttu-id="a4068-153">[ICorDebugBreakpointEnum Interface](icordebugbreakpointenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-153">[ICorDebugBreakpointEnum Interface](icordebugbreakpointenum-interface.md)</span></span>\
 <span data-ttu-id="a4068-154">Implementa métodos `ICorDebugEnum` e enumera matrizes de `ICorDebugBreakpoint`.</span><span class="sxs-lookup"><span data-stu-id="a4068-154">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugBreakpoint` arrays.</span></span>  
  
 <span data-ttu-id="a4068-155">[ICorDebugChain Interface](icordebugchain-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-155">[ICorDebugChain Interface](icordebugchain-interface.md)</span></span>\
 <span data-ttu-id="a4068-156">Representa um segmento de uma pilha de chamadas física ou lógica.</span><span class="sxs-lookup"><span data-stu-id="a4068-156">Represents a segment of a physical or logical call stack.</span></span>  
  
 <span data-ttu-id="a4068-157">[ICorDebugChainEnum Interface](icordebugchainenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-157">[ICorDebugChainEnum Interface](icordebugchainenum-interface.md)</span></span>\
 <span data-ttu-id="a4068-158">Implementa métodos `ICorDebugEnum` e enumera matrizes de `ICorDebugChain`.</span><span class="sxs-lookup"><span data-stu-id="a4068-158">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugChain` arrays.</span></span>  
  
 <span data-ttu-id="a4068-159">[ICorDebugClass Interface](icordebugclass-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-159">[ICorDebugClass Interface](icordebugclass-interface.md)</span></span>\
 <span data-ttu-id="a4068-160">Representa um tipo, que pode ser básico ou complexo (isto é, definido pelo usuário).</span><span class="sxs-lookup"><span data-stu-id="a4068-160">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="a4068-161">Se o tipo for genérico, `ICorDebugClass` representará o tipo genérico sem instância.</span><span class="sxs-lookup"><span data-stu-id="a4068-161">If the type is generic, `ICorDebugClass` represents the uninstantiated generic type.</span></span>  
  
 <span data-ttu-id="a4068-162">[ICorDebugClass2 Interface](icordebugclass2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-162">[ICorDebugClass2 Interface](icordebugclass2-interface.md)</span></span>\
 <span data-ttu-id="a4068-163">Representa uma classe genérica ou uma classe com um parâmetro do método do tipo <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="a4068-163">Represents a generic class or a class with a method parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="a4068-164">Essa interface estende `ICorDebugClass`.</span><span class="sxs-lookup"><span data-stu-id="a4068-164">This interface extends `ICorDebugClass`.</span></span>  
  
 <span data-ttu-id="a4068-165">[ICorDebugCode Interface](icordebugcode-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-165">[ICorDebugCode Interface](icordebugcode-interface1.md)</span></span>\
 <span data-ttu-id="a4068-166">Representa um segmento de código MSIL (Microsoft Intermediate Language) ou código nativo.</span><span class="sxs-lookup"><span data-stu-id="a4068-166">Represents a segment of either Microsoft intermediate language (MSIL) code or native code.</span></span>  
  
 <span data-ttu-id="a4068-167">[ICorDebugCode2 Interface](icordebugcode2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-167">[ICorDebugCode2 Interface](icordebugcode2-interface.md)</span></span>\
 <span data-ttu-id="a4068-168">Fornece métodos que estendem os recursos de `ICorDebugCode`.</span><span class="sxs-lookup"><span data-stu-id="a4068-168">Provides methods that extend the capabilities of `ICorDebugCode`.</span></span>  
  
 <span data-ttu-id="a4068-169">[ICorDebugCode3 Interface](icordebugcode3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-169">[ICorDebugCode3 Interface](icordebugcode3-interface.md)</span></span>\
 <span data-ttu-id="a4068-170">Fornece um método que estende [o ICorDebugCode](icordebugcode-interface1.md) e [o ICorDebugCode2](icordebugcode2-interface.md) para fornecer informações sobre um valor de retorno gerenciado.</span><span class="sxs-lookup"><span data-stu-id="a4068-170">Provides a method that extends [ICorDebugCode](icordebugcode-interface1.md) and [ICorDebugCode2](icordebugcode2-interface.md) to provide information about a managed return value.</span></span>  
  
 <span data-ttu-id="a4068-171">[ICorDebugCode4 Interface](icordebugcode4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-171">[ICorDebugCode4 Interface](icordebugcode4-interface.md)</span></span>\
 <span data-ttu-id="a4068-172">Fornece um método que permite que um depurador enumerar as variáveis e argumentos locais em uma função.</span><span class="sxs-lookup"><span data-stu-id="a4068-172">Provides a method that enables a debugger to enumerate the local variables and arguments in a function.</span></span>  
  
 <span data-ttu-id="a4068-173">[ICorDebugCodeEnum Interface](icordebugcodeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-173">[ICorDebugCodeEnum Interface](icordebugcodeenum-interface.md)</span></span>\
 <span data-ttu-id="a4068-174">Implementa métodos `ICorDebugEnum` e enumera matrizes de `ICorDebugCode`.</span><span class="sxs-lookup"><span data-stu-id="a4068-174">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugCode` arrays.</span></span>  
  
 <span data-ttu-id="a4068-175">[ICorDebugComObjectValue Interface](icordebugcomobjectvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-175">[ICorDebugComObjectValue Interface](icordebugcomobjectvalue-interface.md)</span></span>\
 <span data-ttu-id="a4068-176">Fornece métodos para recuperar objetos da interface armazenados em cache.</span><span class="sxs-lookup"><span data-stu-id="a4068-176">Provides methods to retrieve cached interface objects.</span></span>  
  
 <span data-ttu-id="a4068-177">[Interface de contexto de iCorDebug](icordebugcontext-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-177">[ICorDebugContext Interface](icordebugcontext-interface.md)</span></span>\
 <span data-ttu-id="a4068-178">Representa um objeto de contexto.</span><span class="sxs-lookup"><span data-stu-id="a4068-178">Represents a context object.</span></span> <span data-ttu-id="a4068-179">Essa interface ainda não foi implementada.</span><span class="sxs-lookup"><span data-stu-id="a4068-179">This interface has not been implemented yet.</span></span>  
  
 <span data-ttu-id="a4068-180">[Interface ICorDecontrollerController](icordebugcontroller-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-180">[ICorDebugController Interface](icordebugcontroller-interface.md)</span></span>\
 <span data-ttu-id="a4068-181">Representa um escopo, um <xref:System.Diagnostics.Process> ou um <xref:System.AppDomain>, em que o contexto de execução de código pode ser controlado.</span><span class="sxs-lookup"><span data-stu-id="a4068-181">Represents a scope, either a <xref:System.Diagnostics.Process> or an <xref:System.AppDomain>, in which code execution context can be controlled.</span></span>  
  
 <span data-ttu-id="a4068-182">[Interface de destino iCorDebugData](icordebugdatatarget-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-182">[ICorDebugDataTarget Interface](icordebugdatatarget-interface.md)</span></span>\
 <span data-ttu-id="a4068-183">Fornece uma interface de retorno de chamada que oferece acesso a um determinado processo de destino.</span><span class="sxs-lookup"><span data-stu-id="a4068-183">Provides a callback interface that provides access to a particular target process.</span></span>  
  
 <span data-ttu-id="a4068-184">[ICorDebugDataTarget2 Interface](icordebugdatatarget2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-184">[ICorDebugDataTarget2 Interface](icordebugdatatarget2-interface.md)</span></span>\
 <span data-ttu-id="a4068-185">Logicamente, estende a interface [ICorDebugDataTarget.](icordebugdatatarget-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-185">Logically extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface.</span></span> <span data-ttu-id="a4068-186">**Disponível apenas no .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="a4068-186">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="a4068-187">[ICorDebugDataTarget3 Interface](icordebugdatatarget3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-187">[ICorDebugDataTarget3 Interface](icordebugdatatarget3-interface.md)</span></span>\
 <span data-ttu-id="a4068-188">Logicamente, estende a interface [ICorDebugDataTarget](icordebugdatatarget-interface.md) para fornecer informações sobre módulos carregados.</span><span class="sxs-lookup"><span data-stu-id="a4068-188">Logically extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface to provide information about loaded modules.</span></span> <span data-ttu-id="a4068-189">**Disponível apenas no .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="a4068-189">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="a4068-190">[ICorDebugDebugEvent Interface](icordebugdebugevent-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-190">[ICorDebugDebugEvent Interface](icordebugdebugevent-interface.md)</span></span>\
 <span data-ttu-id="a4068-191">Define a interface base da qual derivam todos os eventos de depuração `ICorDebug`.</span><span class="sxs-lookup"><span data-stu-id="a4068-191">Defines the base interface from which all `ICorDebug` debug events derive.</span></span> <span data-ttu-id="a4068-192">**Disponível apenas no .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="a4068-192">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="a4068-193">[ICorDebugEditAndContinuErrorInfo Interface](icordebugeditandcontinueerrorinfo-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-193">[ICorDebugEditAndContinueErrorInfo Interface](icordebugeditandcontinueerrorinfo-interface.md)</span></span>\
 <span data-ttu-id="a4068-194">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="a4068-194">Obsolete.</span></span> <span data-ttu-id="a4068-195">Não use essa interface.</span><span class="sxs-lookup"><span data-stu-id="a4068-195">Do not use this interface.</span></span>  
  
 <span data-ttu-id="a4068-196">[Interface iCorDebugEditAndContinusnapshot](icordebugeditandcontinuesnapshot-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-196">[ICorDebugEditAndContinueSnapshot Interface](icordebugeditandcontinuesnapshot-interface.md)</span></span>\
 <span data-ttu-id="a4068-197">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="a4068-197">Obsolete.</span></span> <span data-ttu-id="a4068-198">Não use essa interface.</span><span class="sxs-lookup"><span data-stu-id="a4068-198">Do not use this interface.</span></span>  
  
 <span data-ttu-id="a4068-199">[ICorDebugEnum Interface](icordebugenum-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-199">[ICorDebugEnum Interface](icordebugenum-interface1.md)</span></span>\
 <span data-ttu-id="a4068-200">Serve como a interface da base abstrata para depurar enumeradores.</span><span class="sxs-lookup"><span data-stu-id="a4068-200">Serves as the abstract base interface for debugging enumerators.</span></span>  
  
 <span data-ttu-id="a4068-201">[ICorDebugErrorInfoEnum Interface](icordebugerrorinfoenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-201">[ICorDebugErrorInfoEnum Interface](icordebugerrorinfoenum-interface.md)</span></span>\
 <span data-ttu-id="a4068-202">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="a4068-202">Obsolete.</span></span> <span data-ttu-id="a4068-203">Não use essa interface.</span><span class="sxs-lookup"><span data-stu-id="a4068-203">Do not use this interface.</span></span>  
  
 <span data-ttu-id="a4068-204">[ICorDebugEval Interface](icordebugeval-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-204">[ICorDebugEval Interface](icordebugeval-interface.md)</span></span>\
 <span data-ttu-id="a4068-205">Fornece métodos para permitir que o depurador execute um código no contexto do código que está sendo depurado.</span><span class="sxs-lookup"><span data-stu-id="a4068-205">Provides methods to enable the debugger to execute code within the context of the code being debugged.</span></span>  
  
 <span data-ttu-id="a4068-206">[ICorDebugEval2 Interface](icordebugeval2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-206">[ICorDebugEval2 Interface](icordebugeval2-interface.md)</span></span>\
 <span data-ttu-id="a4068-207">Estende `ICorDebugEval` para fornecer suporte a tipos genéricos.</span><span class="sxs-lookup"><span data-stu-id="a4068-207">Extends `ICorDebugEval` to provide support for generic types.</span></span>  
  
 <span data-ttu-id="a4068-208">[Interface de evento iCorDebugDebug](icordebugexceptiondebugevent-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-208">[ICorDebugExceptionDebugEvent Interface](icordebugexceptiondebugevent-interface.md)</span></span>\
 <span data-ttu-id="a4068-209">Estende a interface [ICorDebugDebugEvent](icordebugdebugevent-interface.md) para suportar eventos de exceção.</span><span class="sxs-lookup"><span data-stu-id="a4068-209">Extends the [ICorDebugDebugEvent](icordebugdebugevent-interface.md) interface to support exception events.</span></span> <span data-ttu-id="a4068-210">**Disponível apenas no .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="a4068-210">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="a4068-211">[ICorDebugExceptionObjectCallStackEnum Interface](icordebugexceptionobjectcallstackenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-211">[ICorDebugExceptionObjectCallStackEnum Interface](icordebugexceptionobjectcallstackenum-interface.md)</span></span>\
 <span data-ttu-id="a4068-212">Fornece um enumerador para informações de pilha de chamadas que são inseridas em um objeto de exceção.</span><span class="sxs-lookup"><span data-stu-id="a4068-212">Provides an enumerator for call stack information that is embedded in an exception object.</span></span>  
  
 <span data-ttu-id="a4068-213">[ICorDebugExceptionObjectInterface de valor](icordebugexceptionobjectvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-213">[ICorDebugExceptionObjectValue Interface](icordebugexceptionobjectvalue-interface.md)</span></span>\
 <span data-ttu-id="a4068-214">Estende a interface [ICorDebugObjectValue](icordebugobjectvalue-interface.md) para fornecer informações de rastreamento de pilha a partir de um objeto de exceção gerenciado.</span><span class="sxs-lookup"><span data-stu-id="a4068-214">Extends the [ICorDebugObjectValue](icordebugobjectvalue-interface.md) interface to provide stack trace information from a managed exception object.</span></span>  
  
 <span data-ttu-id="a4068-215">[ICorDebugFrame Interface](icordebugframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-215">[ICorDebugFrame Interface](icordebugframe-interface.md)</span></span>\
 <span data-ttu-id="a4068-216">Representa um quadro na pilha atual.</span><span class="sxs-lookup"><span data-stu-id="a4068-216">Represents a frame on the current stack.</span></span>  
  
 <span data-ttu-id="a4068-217">[ICorDebugFrameEnum Interface](icordebugframeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-217">[ICorDebugFrameEnum Interface](icordebugframeenum-interface.md)</span></span>\
 <span data-ttu-id="a4068-218">Implementa métodos `ICorDebugEnum` e enumera matrizes de `ICorDebugFrame`.</span><span class="sxs-lookup"><span data-stu-id="a4068-218">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugFrame` arrays.</span></span>  
  
 <span data-ttu-id="a4068-219">[Interface de função iCorDebug](icordebugfunction-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-219">[ICorDebugFunction Interface](icordebugfunction-interface1.md)</span></span>\
 <span data-ttu-id="a4068-220">Representa uma função ou um método gerenciado.</span><span class="sxs-lookup"><span data-stu-id="a4068-220">Represents a managed function or method.</span></span>  
  
 <span data-ttu-id="a4068-221">[ICorDebugFunction2 Interface](icordebugfunction2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-221">[ICorDebugFunction2 Interface](icordebugfunction2-interface.md)</span></span>\
 <span data-ttu-id="a4068-222">Estende `ICorDebugFunction` logicamente para fornecer suporte à depuração passo a passo Apenas Meu Código.</span><span class="sxs-lookup"><span data-stu-id="a4068-222">Logically extends `ICorDebugFunction` to provide support for Just My Code step-through debugging.</span></span>  
  
 <span data-ttu-id="a4068-223">[ICorDebugFunction3 Interface](icordebugfunction3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-223">[ICorDebugFunction3 Interface](icordebugfunction3-interface.md)</span></span>\
 <span data-ttu-id="a4068-224">Logicamente, estende a interface [ICorDebugFunction](icordebugfunction-interface1.md) para fornecer acesso ao código a partir de uma solicitação ReJIT.</span><span class="sxs-lookup"><span data-stu-id="a4068-224">Logically extends the [ICorDebugFunction](icordebugfunction-interface1.md) interface to provide access to code from a ReJIT request.</span></span>  
  
 <span data-ttu-id="a4068-225">[ICorDebugFunctionBreakpoint Interface](icordebugfunctionbreakpoint-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-225">[ICorDebugFunctionBreakpoint Interface](icordebugfunctionbreakpoint-interface.md)</span></span>\
 <span data-ttu-id="a4068-226">Estende `ICorDebugBreakpoint` para fornecer suporte a pontos de interrupção dentro de funções.</span><span class="sxs-lookup"><span data-stu-id="a4068-226">Extends `ICorDebugBreakpoint` to support breakpoints within functions.</span></span>  
  
 <span data-ttu-id="a4068-227">[ICorDebugGCReferenceEnum Interface](icordebuggcreferenceenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-227">[ICorDebugGCReferenceEnum Interface](icordebuggcreferenceenum-interface.md)</span></span>\
 <span data-ttu-id="a4068-228">Fornece um enumerador para objetos que serão coletados do lixo.</span><span class="sxs-lookup"><span data-stu-id="a4068-228">Provides an enumerator for objects that will be garbage-collected.</span></span>  
  
 <span data-ttu-id="a4068-229">[ICorDebugGenericValue Interface](icordebuggenericvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-229">[ICorDebugGenericValue Interface](icordebuggenericvalue-interface.md)</span></span>\
 <span data-ttu-id="a4068-230">Uma subclasse de `ICorDebugValue` que se aplica a todos os valores.</span><span class="sxs-lookup"><span data-stu-id="a4068-230">A subclass of `ICorDebugValue` that applies to all values.</span></span> <span data-ttu-id="a4068-231">Essa interface fornece métodos Get e Set para o valor.</span><span class="sxs-lookup"><span data-stu-id="a4068-231">This interface provides Get and Set methods for the value.</span></span>  
  
 <span data-ttu-id="a4068-232">[ICorDebugGuidToTypeEnum Interface](icordebugguidtotypeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-232">[ICorDebugGuidToTypeEnum Interface](icordebugguidtotypeenum-interface.md)</span></span>\
 <span data-ttu-id="a4068-233">Fornece um enumerador para um objeto que mapeia GUIDs e seus objetos `ICorDebugType` correspondentes.</span><span class="sxs-lookup"><span data-stu-id="a4068-233">Provides an enumerator for an object that maps GUIDs and their corresponding `ICorDebugType` objects.</span></span>  
  
 <span data-ttu-id="a4068-234">[ICorDebugHandleValue Interface](icordebughandlevalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-234">[ICorDebugHandleValue Interface](icordebughandlevalue-interface.md)</span></span>\
 <span data-ttu-id="a4068-235">Uma subclasse de `ICorDebugReferenceValue` que representa um valor de referência para o qual o depurador criou um identificador para coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="a4068-235">A subclass of `ICorDebugReferenceValue` that represents a reference value to which the debugger has created a handle for garbage collection.</span></span>  
  
 <span data-ttu-id="a4068-236">[ICorDebugHeapEnum Interface](icordebugheapenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-236">[ICorDebugHeapEnum Interface](icordebugheapenum-interface.md)</span></span>\
 <span data-ttu-id="a4068-237">Fornece um enumerador para objetos no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="a4068-237">Provides an enumerator for objects on the managed heap.</span></span>  
  
 <span data-ttu-id="a4068-238">[ICorDebugHeapSegmentEnum Interface](icordebugheapsegmentenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-238">[ICorDebugHeapSegmentEnum Interface](icordebugheapsegmentenum-interface.md)</span></span>\
 <span data-ttu-id="a4068-239">Fornece um enumerador para regiões de memória do heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="a4068-239">Provides an enumerator for the memory regions of the managed heap.</span></span>  
  
 <span data-ttu-id="a4068-240">[ICorDebugHeapValue Interface](icordebugheapvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-240">[ICorDebugHeapValue Interface](icordebugheapvalue-interface.md)</span></span>\
 <span data-ttu-id="a4068-241">Uma subclasse de `ICorDebugValue` que representa um objeto coletado pelo coletor de lixo do CLR.</span><span class="sxs-lookup"><span data-stu-id="a4068-241">A subclass of `ICorDebugValue` that represents an object that has been collected by the CLR garbage collector.</span></span>  
  
 <span data-ttu-id="a4068-242">[ICorDebugHeapValue2 Interface](icordebugheapvalue2-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-242">[ICorDebugHeapValue2 Interface](icordebugheapvalue2-interface1.md)</span></span>\
 <span data-ttu-id="a4068-243">Uma extensão de `ICorDebugHeapValue` que fornece suporte aos identificadores de runtime.</span><span class="sxs-lookup"><span data-stu-id="a4068-243">An extension of `ICorDebugHeapValue` that provides support for runtime handles.</span></span>  
  
 <span data-ttu-id="a4068-244">[ICorDebugHeapValue3 Interface](icordebugheapvalue3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-244">[ICorDebugHeapValue3 Interface](icordebugheapvalue3-interface.md)</span></span>\
 <span data-ttu-id="a4068-245">Expõe as propriedades de bloqueio de monitoramento de objetos.</span><span class="sxs-lookup"><span data-stu-id="a4068-245">Exposes the monitor lock properties of objects.</span></span>  
  
 <span data-ttu-id="a4068-246">[ICorDebugILCode Interface](icordebugilcode-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-246">[ICorDebugILCode Interface](icordebugilcode-interface.md)</span></span>\
 <span data-ttu-id="a4068-247">Representa um segmento de código IL (Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="a4068-247">Represents a segment of intermediate language (IL) code.</span></span>  
  
 <span data-ttu-id="a4068-248">[ICorDebugILCode2 Interface](icordebugilcode2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-248">[ICorDebugILCode2 Interface](icordebugilcode2-interface.md)</span></span>\
 <span data-ttu-id="a4068-249">Logicamente, estende a interface [ICorDebugILCode](icordebugilcode-interface.md) para fornecer métodos que retornam o token para a assinatura variável local de uma função, e que mapeiam as compensações de linguagem intermediária (IL) instrumentadas de um profiler para deslocamentos il do método original.</span><span class="sxs-lookup"><span data-stu-id="a4068-249">Logically extends the [ICorDebugILCode](icordebugilcode-interface.md) interface to provide methods that return the token for a function's local variable signature, and that map a profiler's instrumented intermediate language (IL) offsets to original method IL offsets.</span></span>  
  
 <span data-ttu-id="a4068-250">[ICorDebugILFrame Interface](icordebugilframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-250">[ICorDebugILFrame Interface](icordebugilframe-interface.md)</span></span>\
 <span data-ttu-id="a4068-251">Representa um registro de ativação do código MSIL.</span><span class="sxs-lookup"><span data-stu-id="a4068-251">Represents a stack frame of MSIL code.</span></span>  
  
 <span data-ttu-id="a4068-252">[ICorDebugILFrame2 Interface](icordebugilframe2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-252">[ICorDebugILFrame2 Interface](icordebugilframe2-interface.md)</span></span>\
 <span data-ttu-id="a4068-253">Uma extensão lógica de `ICorDebugILFrame`.</span><span class="sxs-lookup"><span data-stu-id="a4068-253">A logical extension of `ICorDebugILFrame`.</span></span>  
  
 <span data-ttu-id="a4068-254">[ICorDebugILFrame3 Interface](icordebugilframe3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-254">[ICorDebugILFrame3 Interface](icordebugilframe3-interface.md)</span></span>\
 <span data-ttu-id="a4068-255">Fornece um método que encapsula o valor de retorno de uma função.</span><span class="sxs-lookup"><span data-stu-id="a4068-255">Provides a method that encapsulates the return value of a function.</span></span>  
  
 <span data-ttu-id="a4068-256">[ICorDebugILFrame4 Interface](icordebugilframe4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-256">[ICorDebugILFrame4 Interface](icordebugilframe4-interface.md)</span></span>\
 <span data-ttu-id="a4068-257">Fornece métodos que permitem acessar as variáveis locais e inserir o código em um registro de ativação de código IL.</span><span class="sxs-lookup"><span data-stu-id="a4068-257">Provides methods that allow you to access the local variables and code in a stack frame of intermediate language (IL) code.</span></span> <span data-ttu-id="a4068-258">Um parâmetro especifica se o depurador possui acesso às variáveis e ao código adicionados na instrumentação do criador de perfil ReJIT.</span><span class="sxs-lookup"><span data-stu-id="a4068-258">A parameter specifies whether the debugger has access to variables and code added in profiler ReJIT instrumentation.</span></span>  
  
 <span data-ttu-id="a4068-259">[ICorDebugInstanceFieldSymbol Interface](icordebuginstancefieldsymbol-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-259">[ICorDebugInstanceFieldSymbol Interface](icordebuginstancefieldsymbol-interface.md)</span></span>\
 <span data-ttu-id="a4068-260">Representa a informação do símbolo de depuração para um campo de instância.</span><span class="sxs-lookup"><span data-stu-id="a4068-260">Represents the debug symbol information for an instance field.</span></span> <span data-ttu-id="a4068-261">**Disponível apenas no .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="a4068-261">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="a4068-262">[Interface de imagem interna do ICorDebug](icordebuginternalframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-262">[ICorDebugInternalFrame Interface](icordebuginternalframe-interface.md)</span></span>\
 <span data-ttu-id="a4068-263">Identifica os tipos de quadro para o depurador.</span><span class="sxs-lookup"><span data-stu-id="a4068-263">Identifies frame types for the debugger.</span></span>  
  
 <span data-ttu-id="a4068-264">[ICorDebugInternalFrame2 Interface](icordebuginternalframe2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-264">[ICorDebugInternalFrame2 Interface](icordebuginternalframe2-interface.md)</span></span>\
 <span data-ttu-id="a4068-265">Fornece informações sobre quadros internos, incluindo endereço de pilha e posição em relação a objetos [ICorDebugFrame.](icordebugframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-265">Provides information about internal frames, including stack address and position in relation to [ICorDebugFrame](icordebugframe-interface.md) objects.</span></span>  
  
 <span data-ttu-id="a4068-266">[ICorDebugLoadedModule Interface](icordebugloadedmodule-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-266">[ICorDebugLoadedModule Interface](icordebugloadedmodule-interface.md)</span></span>\
 <span data-ttu-id="a4068-267">Fornece informações sobre um módulo carregado.</span><span class="sxs-lookup"><span data-stu-id="a4068-267">Provides information about a loaded module.</span></span> <span data-ttu-id="a4068-268">**Disponível apenas no .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="a4068-268">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="a4068-269">[Interface de retorno de chamada gerenciada do ICorDebug](icordebugmanagedcallback-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-269">[ICorDebugManagedCallback Interface](icordebugmanagedcallback-interface.md)</span></span>\
 <span data-ttu-id="a4068-270">Fornece métodos para processar retornos de chamada do depurador.</span><span class="sxs-lookup"><span data-stu-id="a4068-270">Provides methods to process debugger callbacks.</span></span>  
  
 <span data-ttu-id="a4068-271">[ICorDebugManagedCallback2 Interface](icordebugmanagedcallback2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-271">[ICorDebugManagedCallback2 Interface](icordebugmanagedcallback2-interface.md)</span></span>\
 <span data-ttu-id="a4068-272">Fornece métodos para oferecer suporte à manipulação de exceção do depurador e aos assistentes de depuração gerenciados (MDAs).</span><span class="sxs-lookup"><span data-stu-id="a4068-272">Provides methods to support debugger exception handling and managed debugging assistants (MDAs).</span></span> <span data-ttu-id="a4068-273">`ICorDebugManagedCallback2` é uma extensão lógica de `ICorDebugManagedCallback`.</span><span class="sxs-lookup"><span data-stu-id="a4068-273">`ICorDebugManagedCallback2` is a logical extension of `ICorDebugManagedCallback`.</span></span>  
  
 <span data-ttu-id="a4068-274">[ICorDebugManagedCallback3 Interface](icordebugmanagedcallback3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-274">[ICorDebugManagedCallback3 Interface](icordebugmanagedcallback3-interface.md)</span></span>\
 <span data-ttu-id="a4068-275">Fornece um método de retorno de chamada que indica que uma notificação personalizada ativada do depurador foi gerada.</span><span class="sxs-lookup"><span data-stu-id="a4068-275">Provides a callback method that indicates that an enabled custom debugger notification has been raised.</span></span>  
  
 <span data-ttu-id="a4068-276">[ICorDebugMDA Interface](icordebugmda-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-276">[ICorDebugMDA Interface](icordebugmda-interface.md)</span></span>\
 <span data-ttu-id="a4068-277">Representa uma mensagem do assistente de depuração gerenciado (MDA).</span><span class="sxs-lookup"><span data-stu-id="a4068-277">Represents a managed debugging assistant (MDA) message.</span></span>  
  
 <span data-ttu-id="a4068-278">[ICorDebugMemoryBuffer Interface](icordebugmemorybuffer-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-278">[ICorDebugMemoryBuffer Interface](icordebugmemorybuffer-interface.md)</span></span>\
 <span data-ttu-id="a4068-279">Representa um buffer na memória.</span><span class="sxs-lookup"><span data-stu-id="a4068-279">Represents an in-memory buffer.</span></span> <span data-ttu-id="a4068-280">**Disponível apenas no .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="a4068-280">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="a4068-281">[Interface de registro de gravação de ICorDebugMergedAssembly](icordebugmergedassemblyrecord-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-281">[ICorDebugMergedAssemblyRecord Interface](icordebugmergedassemblyrecord-interface.md)</span></span>\
 <span data-ttu-id="a4068-282">Fornece informações sobre uma montagem mesclada.</span><span class="sxs-lookup"><span data-stu-id="a4068-282">Provides information about a merged assembly.</span></span> <span data-ttu-id="a4068-283">**Disponível apenas no .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="a4068-283">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="a4068-284">[ICorDebugMetaDataLocator Interface](icordebugmetadatalocator-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-284">[ICorDebugMetaDataLocator Interface](icordebugmetadatalocator-interface.md)</span></span>\
 <span data-ttu-id="a4068-285">Fornece informações de metadados ao depurador.</span><span class="sxs-lookup"><span data-stu-id="a4068-285">Provides metadata information to the debugger.</span></span>  
  
 <span data-ttu-id="a4068-286">[ICorDebugModule Interface](icordebugmodule-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-286">[ICorDebugModule Interface](icordebugmodule-interface.md)</span></span>\
 <span data-ttu-id="a4068-287">Representa um módulo de CLR, que é um executável ou uma biblioteca de vínculo dinâmico (DLL).</span><span class="sxs-lookup"><span data-stu-id="a4068-287">Represents a CLR module, which is either an executable or a dynamic-link library (DLL).</span></span>  
  
 <span data-ttu-id="a4068-288">[ICorDebugModule2 Interface](icordebugmodule2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-288">[ICorDebugModule2 Interface](icordebugmodule2-interface.md)</span></span>\
 <span data-ttu-id="a4068-289">Serve como extensão lógica para `ICorDebugModule`.</span><span class="sxs-lookup"><span data-stu-id="a4068-289">Serves as a logical extension to `ICorDebugModule`.</span></span>  
  
 <span data-ttu-id="a4068-290">[ICorDebugModule3 Interface](icordebugmodule3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-290">[ICorDebugModule3 Interface](icordebugmodule3-interface.md)</span></span>\
 <span data-ttu-id="a4068-291">Cria um leitor de símbolos para um módulo dinâmico.</span><span class="sxs-lookup"><span data-stu-id="a4068-291">Creates a symbol reader for a dynamic module.</span></span>  
  
 <span data-ttu-id="a4068-292">[ICorDebugModuleBreakpoint Interface](icordebugmodulebreakpoint-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-292">[ICorDebugModuleBreakpoint Interface](icordebugmodulebreakpoint-interface.md)</span></span>\
 <span data-ttu-id="a4068-293">Estende `ICorDebugBreakpoint` para fornecer acesso aos módulos específicos.</span><span class="sxs-lookup"><span data-stu-id="a4068-293">Extends `ICorDebugBreakpoint` to provide access to specific modules.</span></span>  
  
 <span data-ttu-id="a4068-294">[Interface de evento iCorDebugDebug](icordebugmoduledebugevent-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-294">[ICorDebugModuleDebugEvent Interface](icordebugmoduledebugevent-interface.md)</span></span>\
 <span data-ttu-id="a4068-295">Estende a interface [ICorDebugDebugEvent](icordebugdebugevent-interface.md) para suportar eventos em nível de módulo.</span><span class="sxs-lookup"><span data-stu-id="a4068-295">Extends the [ICorDebugDebugEvent](icordebugdebugevent-interface.md) interface to support module-level events.</span></span> <span data-ttu-id="a4068-296">**Disponível apenas no .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="a4068-296">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="a4068-297">[ICorDebugModuleEnum Interface](icordebugmoduleenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-297">[ICorDebugModuleEnum Interface](icordebugmoduleenum-interface.md)</span></span>\
 <span data-ttu-id="a4068-298">Implementa métodos `ICorDebugEnum` e enumera matrizes de `ICorDebugModule`.</span><span class="sxs-lookup"><span data-stu-id="a4068-298">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugModule` arrays.</span></span>  
  
 <span data-ttu-id="a4068-299">[ICorDebugMutableDataTarget Interface](icordebugmutabledatatarget-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-299">[ICorDebugMutableDataTarget Interface](icordebugmutabledatatarget-interface.md)</span></span>\
 <span data-ttu-id="a4068-300">Estende a interface [ICorDebugDataTarget](icordebugdatatarget-interface.md) para suportar metas de dados mutáveis.</span><span class="sxs-lookup"><span data-stu-id="a4068-300">Extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface to support mutable data targets.</span></span>  
  
 <span data-ttu-id="a4068-301">[Interface de frame nativo do ICorDebug](icordebugnativeframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-301">[ICorDebugNativeFrame Interface](icordebugnativeframe-interface.md)</span></span>\
 <span data-ttu-id="a4068-302">Uma implementação especializada de `ICorDebugFrame` usada para quadros nativos.</span><span class="sxs-lookup"><span data-stu-id="a4068-302">A specialized implementation of `ICorDebugFrame` used for native frames.</span></span>  
  
 <span data-ttu-id="a4068-303">[ICorDebugNativeFrame2 Interface](icordebugnativeframe2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-303">[ICorDebugNativeFrame2 Interface](icordebugnativeframe2-interface.md)</span></span>\
 <span data-ttu-id="a4068-304">Fornece métodos que testam relações de quadros pai e filho.</span><span class="sxs-lookup"><span data-stu-id="a4068-304">Provides methods that test for child and parent frame relationships.</span></span>  
  
 <span data-ttu-id="a4068-305">[ICorDebugObjectEnum Interface](icordebugobjectenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-305">[ICorDebugObjectEnum Interface](icordebugobjectenum-interface.md)</span></span>\
 <span data-ttu-id="a4068-306">Implementa métodos `ICorDebugEnum` e enumera matrizes de objetos pelos endereços virtuais relacionados (RVAs).</span><span class="sxs-lookup"><span data-stu-id="a4068-306">Implements `ICorDebugEnum` methods, and enumerates arrays of objects by their relative virtual addresses (RVAs).</span></span>  
  
 <span data-ttu-id="a4068-307">[Interface de valor do ICorDebugObject](icordebugobjectvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-307">[ICorDebugObjectValue Interface](icordebugobjectvalue-interface.md)</span></span>\
 <span data-ttu-id="a4068-308">Uma subclasse de `ICorDebugValue` que representa um valor que contém um objeto.</span><span class="sxs-lookup"><span data-stu-id="a4068-308">A subclass of `ICorDebugValue` that represents a value that contains an object.</span></span>  
  
 <span data-ttu-id="a4068-309">[ICorDebugObjectValue2 Interface](icordebugobjectvalue2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-309">[ICorDebugObjectValue2 Interface](icordebugobjectvalue2-interface.md)</span></span>\
 <span data-ttu-id="a4068-310">Estende `ICorDebugObjectValue` para oferecer suporte a herança e substituição.</span><span class="sxs-lookup"><span data-stu-id="a4068-310">Extends `ICorDebugObjectValue` to support inheritance and overrides.</span></span>  
  
 <span data-ttu-id="a4068-311">[Interface de processo de iCorDebug](icordebugprocess-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-311">[ICorDebugProcess Interface](icordebugprocess-interface.md)</span></span>\
 <span data-ttu-id="a4068-312">Representa um processo que está executando o código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="a4068-312">Represents a process that is executing managed code.</span></span>  
  
 <span data-ttu-id="a4068-313">[ICorDebugProcess2 Interface](icordebugprocess2-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-313">[ICorDebugProcess2 Interface](icordebugprocess2-interface1.md)</span></span>\
 <span data-ttu-id="a4068-314">Uma extensão lógica de `ICorDebugProcess`.</span><span class="sxs-lookup"><span data-stu-id="a4068-314">A logical extension of `ICorDebugProcess`.</span></span>  
  
 <span data-ttu-id="a4068-315">[ICorDebugProcess3 Interface](icordebugprocess3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-315">[ICorDebugProcess3 Interface](icordebugprocess3-interface.md)</span></span>\
 <span data-ttu-id="a4068-316">Controla as notificações personalizadas do depurador.</span><span class="sxs-lookup"><span data-stu-id="a4068-316">Controls custom debugger notifications.</span></span>

 <span data-ttu-id="a4068-317">[ICorDebugProcess4 Interface](icordebugprocess4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-317">[ICorDebugProcess4 Interface](icordebugprocess4-interface.md)</span></span>\
 <span data-ttu-id="a4068-318">Fornece suporte para controle de execução fora do processo.</span><span class="sxs-lookup"><span data-stu-id="a4068-318">Provides support for out of process execution control.</span></span>
  
 <span data-ttu-id="a4068-319">[ICorDebugProcess5 Interface](icordebugprocess5-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-319">[ICorDebugProcess5 Interface](icordebugprocess5-interface.md)</span></span>\
 <span data-ttu-id="a4068-320">Estende a interface [ICorDebugProcess](icordebugprocess-interface.md) para oferecer suporte ao acesso ao heap gerenciado, para fornecer informações sobre coleta de lixo de objetos gerenciados e para determinar se um depurador carrega imagens do cache de imagem nativo local do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a4068-320">Extends the [ICorDebugProcess](icordebugprocess-interface.md) interface to support access to the managed heap, to provide information about garbage collection of managed objects, and to determine whether a debugger loads images from the application's local native image cache.</span></span>  
  
 <span data-ttu-id="a4068-321">[ICorDebugProcess6 Interface](icordebugprocess6-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-321">[ICorDebugProcess6 Interface](icordebugprocess6-interface.md)</span></span>\
 <span data-ttu-id="a4068-322">Logicamente, estende a interface [ICorDebugProcess](icordebugprocess-interface.md) para habilitar recursos como decodificação de eventos de depuração gerenciados que são codificados em eventos de depuração de exceção nativa e divisão de módulos virtuais.</span><span class="sxs-lookup"><span data-stu-id="a4068-322">Logically extends the [ICorDebugProcess](icordebugprocess-interface.md) interface to enable features such as decoding managed debug events that are encoded in native exception debug events and virtual module splitting.</span></span> <span data-ttu-id="a4068-323">**Disponível apenas no .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="a4068-323">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="a4068-324">[ICorDebugProcess7 Interface](icordebugprocess7-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-324">[ICorDebugProcess7 Interface](icordebugprocess7-interface.md)</span></span>\
 <span data-ttu-id="a4068-325">Fornece um método que configura o depurador para manipular atualizações de metadados na memória no processo de destino.</span><span class="sxs-lookup"><span data-stu-id="a4068-325">Provides a method that configures the debugger to handle in-memory metadata updates in the target process.</span></span>  
  
 <span data-ttu-id="a4068-326">[ICorDebugProcess8 Interface](icordebugprocess8-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-326">[ICorDebugProcess8 Interface](icordebugprocess8-interface.md)</span></span>\
 <span data-ttu-id="a4068-327">Logicamente, estende a interface [ICorDebugProcess](icordebugprocess-interface.md) para ativar ou desativar certos tipos de retornos de exceção [de ICorDebugManagedCallback2.](icordebugmanagedcallback2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-327">Logically extends the [ICorDebugProcess](icordebugprocess-interface.md) interface to enable or disable certain types of [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>  
  
 <span data-ttu-id="a4068-328">[ICorDebugProcessEnum Interface](icordebugprocessenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-328">[ICorDebugProcessEnum Interface](icordebugprocessenum-interface.md)</span></span>\
 <span data-ttu-id="a4068-329">Implementa métodos `ICorDebugEnum` e enumera matrizes de `ICorDebugProcess`.</span><span class="sxs-lookup"><span data-stu-id="a4068-329">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugProcess` arrays.</span></span>  
  
 <span data-ttu-id="a4068-330">[Interface de valor de iCorDebugReference](icordebugreferencevalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-330">[ICorDebugReferenceValue Interface](icordebugreferencevalue-interface.md)</span></span>\
 <span data-ttu-id="a4068-331">Uma subclasse de `ICorDebugValue` que oferece suporte a tipos de referência.</span><span class="sxs-lookup"><span data-stu-id="a4068-331">A subclass of `ICorDebugValue` that supports reference types.</span></span>  
  
 <span data-ttu-id="a4068-332">[ICorDebugRegisterSet Interface](icordebugregisterset-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-332">[ICorDebugRegisterSet Interface](icordebugregisterset-interface.md)</span></span>\
 <span data-ttu-id="a4068-333">Representa o conjunto de registros disponíveis no computador que está executando o código no momento.</span><span class="sxs-lookup"><span data-stu-id="a4068-333">Represents the set of registers available on the machine that is currently executing code.</span></span>  
  
 <span data-ttu-id="a4068-334">[ICorDebugRegisterSet2 Interface](icordebugregisterset2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-334">[ICorDebugRegisterSet2 Interface](icordebugregisterset2-interface.md)</span></span>\
 <span data-ttu-id="a4068-335">Estende os recursos de `ICorDebugRegisterSet` para as plataformas de hardware que possuem mais de 64 registros.</span><span class="sxs-lookup"><span data-stu-id="a4068-335">Extends the capabilities of `ICorDebugRegisterSet` for hardware platforms that have more than 64 registers.</span></span>  
  
 <span data-ttu-id="a4068-336">[Interface remota do ICorDebug](icordebugremote-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-336">[ICorDebugRemote Interface](icordebugremote-interface.md)</span></span>\
 <span data-ttu-id="a4068-337">Fornece a capacidade de iniciar ou anexar um depurador gerenciado a um processo remoto de destino.</span><span class="sxs-lookup"><span data-stu-id="a4068-337">Provides the ability to launch or attach a managed debugger to a remote target process.</span></span>  
  
 <span data-ttu-id="a4068-338">[Interface de destino remoto do ICorDebug](icordebugremotetarget-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-338">[ICorDebugRemoteTarget Interface](icordebugremotetarget-interface.md)</span></span>\
 <span data-ttu-id="a4068-339">Fornece métodos que permitem a você depurar aplicativos baseados no Silverlight no ambiente do CLR.</span><span class="sxs-lookup"><span data-stu-id="a4068-339">Provides methods that enable you to debug Silverlight-based applications in the CLR environment.</span></span>  
  
 <span data-ttu-id="a4068-340">[Interface de quadro unwindable unwindable ICorDebugExecução](icordebugruntimeunwindableframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-340">[ICorDebugRuntimeUnwindableFrame Interface](icordebugruntimeunwindableframe-interface.md)</span></span>\
 <span data-ttu-id="a4068-341">Fornece suporte para os métodos não gerenciados que exigem que o CLR (Common Language Runtime) desenrole um quadro.</span><span class="sxs-lookup"><span data-stu-id="a4068-341">Provides support for unmanaged methods that require the common language runtime (CLR) to unwind a frame.</span></span>  
  
 <span data-ttu-id="a4068-342">[ICorDebugStackWalk Interface](icordebugstackwalk-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-342">[ICorDebugStackWalk Interface](icordebugstackwalk-interface.md)</span></span>\
 <span data-ttu-id="a4068-343">Fornece métodos para colocar os métodos gerenciados, ou quadros, em uma pilha de thread.</span><span class="sxs-lookup"><span data-stu-id="a4068-343">Provides methods for getting the managed methods, or frames, on a thread’s stack.</span></span>  
  
 <span data-ttu-id="a4068-344">[ICorDebugStaticFieldSymbol Interface](icordebugstaticfieldsymbol-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-344">[ICorDebugStaticFieldSymbol Interface](icordebugstaticfieldsymbol-interface.md)</span></span>\
 <span data-ttu-id="a4068-345">Representa a informação do símbolo de depuração para um campo estático.</span><span class="sxs-lookup"><span data-stu-id="a4068-345">Represents the debug symbol information for a static field.</span></span> <span data-ttu-id="a4068-346">**Disponível apenas no .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="a4068-346">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="a4068-347">[ICorDebugStepper Interface](icordebugstepper-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-347">[ICorDebugStepper Interface](icordebugstepper-interface.md)</span></span>\
 <span data-ttu-id="a4068-348">Representa uma etapa na execução do código que é realizada por um depurador, serve como um identificador entre a emissão e a conclusão de um comando e fornece uma maneira de cancelar uma etapa.</span><span class="sxs-lookup"><span data-stu-id="a4068-348">Represents a step in code execution that is performed by a debugger, serves as an identifier between the issuance and completion of a command, and provides a way to cancel a step.</span></span>  
  
 <span data-ttu-id="a4068-349">[ICorDebugStepper2 Interface](icordebugstepper2-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-349">[ICorDebugStepper2 Interface](icordebugstepper2-interface1.md)</span></span>\
 <span data-ttu-id="a4068-350">Fornece suporte para a depuração JMC (Apenas Meu Código).</span><span class="sxs-lookup"><span data-stu-id="a4068-350">Provides support for Just My Code (JMC) debugging.</span></span>  
  
 <span data-ttu-id="a4068-351">[ICorDebugStepperEnum Interface](icordebugstepperenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-351">[ICorDebugStepperEnum Interface](icordebugstepperenum-interface.md)</span></span>\
 <span data-ttu-id="a4068-352">Implementa métodos `ICorDebugEnum` e enumera matrizes de `ICorDebugStepper`.</span><span class="sxs-lookup"><span data-stu-id="a4068-352">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugStepper` arrays.</span></span>  
  
 <span data-ttu-id="a4068-353">[Interface de valor do ICorDebugString](icordebugstringvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-353">[ICorDebugStringValue Interface](icordebugstringvalue-interface.md)</span></span>\
 <span data-ttu-id="a4068-354">Uma subclasse de `ICorDebugHeapValue` que se aplica a valores de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="a4068-354">A subclass of `ICorDebugHeapValue` that applies to string values.</span></span>  
  
 <span data-ttu-id="a4068-355">[ICorDebugSymbolProvider Interface](icordebugsymbolprovider-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-355">[ICorDebugSymbolProvider Interface](icordebugsymbolprovider-interface.md)</span></span>\
 <span data-ttu-id="a4068-356">Fornece métodos que podem ser usados para recuperar informações de símbolos de depuração.</span><span class="sxs-lookup"><span data-stu-id="a4068-356">Provides methods that can be used to retrieve debug symbol information.</span></span> <span data-ttu-id="a4068-357">**Disponível apenas no .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="a4068-357">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="a4068-358">[ICorDebugSymbolProvider2 Interface](icordebugsymbolprovider2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-358">[ICorDebugSymbolProvider2 Interface](icordebugsymbolprovider2-interface.md)</span></span>\
 <span data-ttu-id="a4068-359">Logicamente, estende a interface [ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md) para recuperar informações adicionais de símbolo de depuração.</span><span class="sxs-lookup"><span data-stu-id="a4068-359">Logically extends the [ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md) interface to retrieve additional debug symbol information.</span></span> <span data-ttu-id="a4068-360">**Disponível apenas no .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="a4068-360">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="a4068-361">[ICorDebugThread Interface](icordebugthread-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-361">[ICorDebugThread Interface](icordebugthread-interface.md)</span></span>\
 <span data-ttu-id="a4068-362">Representa um thread em um processo.</span><span class="sxs-lookup"><span data-stu-id="a4068-362">Represents a thread in a process.</span></span> <span data-ttu-id="a4068-363">O tempo de vida de uma instância `ICorDebugThread` é igual ao tempo de vida do thread que ela representa.</span><span class="sxs-lookup"><span data-stu-id="a4068-363">The lifetime of an `ICorDebugThread` instance is the same as the lifetime of the thread it represents.</span></span>  
  
 <span data-ttu-id="a4068-364">[ICorDebugThread2 Interface](icordebugthread2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-364">[ICorDebugThread2 Interface](icordebugthread2-interface.md)</span></span>\
 <span data-ttu-id="a4068-365">Serve como extensão lógica para `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="a4068-365">Serves as a logical extension to `ICorDebugThread`.</span></span>  
  
 <span data-ttu-id="a4068-366">[ICorDebugThread3 Interface](icordebugthread3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-366">[ICorDebugThread3 Interface](icordebugthread3-interface.md)</span></span>\
 <span data-ttu-id="a4068-367">Fornece o ponto de entrada para o [ICorDebugStackWalk](icordebugstackwalk-interface.md) e interfaces correspondentes.</span><span class="sxs-lookup"><span data-stu-id="a4068-367">Provides the entry point to the [ICorDebugStackWalk](icordebugstackwalk-interface.md) and corresponding interfaces.</span></span>  
  
 <span data-ttu-id="a4068-368">[ICorDebugThread4 Interface](icordebugthread4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-368">[ICorDebugThread4 Interface](icordebugthread4-interface.md)</span></span>\
 <span data-ttu-id="a4068-369">Fornece informações de bloqueio de thread.</span><span class="sxs-lookup"><span data-stu-id="a4068-369">Provides thread blocking information.</span></span>  
  
 <span data-ttu-id="a4068-370">[ICorDebugThreadEnum Interface](icordebugthreadenum-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-370">[ICorDebugThreadEnum Interface](icordebugthreadenum-interface1.md)</span></span>\
 <span data-ttu-id="a4068-371">Implementa métodos `ICorDebugEnum` e enumera matrizes de `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="a4068-371">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugThread` arrays.</span></span>  
  
 <span data-ttu-id="a4068-372">[ICorDebugType Interface](icordebugtype-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-372">[ICorDebugType Interface](icordebugtype-interface.md)</span></span>\
 <span data-ttu-id="a4068-373">Representa um tipo, que pode ser básico ou complexo (isto é, definido pelo usuário).</span><span class="sxs-lookup"><span data-stu-id="a4068-373">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="a4068-374">Se o tipo for genérico, `ICorDebugType` representará o tipo genérico instanciado.</span><span class="sxs-lookup"><span data-stu-id="a4068-374">If the type is generic, `ICorDebugType` represents the instantiated generic type.</span></span>  
  
 <span data-ttu-id="a4068-375">[ICorDebugType2 Interface](icordebugtype2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-375">[ICorDebugType2 Interface](icordebugtype2-interface.md)</span></span>\
 <span data-ttu-id="a4068-376">Estende a interface [ICorDebugType](icordebugtype-interface.md) para recuperar o identificador de tipo de um tipo base ou tipo complexo (definido pelo usuário).</span><span class="sxs-lookup"><span data-stu-id="a4068-376">Extends the [ICorDebugType](icordebugtype-interface.md) interface to retrieve the type identifier  of a base type or complex (user-defined) type.</span></span>  
  
 <span data-ttu-id="a4068-377">[ICorDebugTypeEnum Interface](icordebugtypeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-377">[ICorDebugTypeEnum Interface](icordebugtypeenum-interface.md)</span></span>\
 <span data-ttu-id="a4068-378">Implementa métodos `ICorDebugEnum` e enumera matrizes de `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="a4068-378">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugType` arrays.</span></span>  
  
 <span data-ttu-id="a4068-379">[Interface de retorno de chamada de iCorDebugUngerenciado](icordebugunmanagedcallback-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-379">[ICorDebugUnmanagedCallback Interface](icordebugunmanagedcallback-interface.md)</span></span>\
 <span data-ttu-id="a4068-380">Fornece notificação de eventos nativos que não estão diretamente relacionados ao CLR.</span><span class="sxs-lookup"><span data-stu-id="a4068-380">Provides notification of native events that are not directly related to the CLR.</span></span>  
  
 <span data-ttu-id="a4068-381">[Icordebugvalue](icordebugvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-381">[ICorDebugValue](icordebugvalue-interface.md)</span></span>\
 <span data-ttu-id="a4068-382">Representa um valor de leitura ou gravação no processo que está sendo depurado.</span><span class="sxs-lookup"><span data-stu-id="a4068-382">Represents a read or write value in the process being debugged.</span></span>  
  
 <span data-ttu-id="a4068-383">[ICorDebugValue2](icordebugvalue2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-383">[ICorDebugValue2](icordebugvalue2-interface.md)</span></span>\
 <span data-ttu-id="a4068-384">Estende `ICorDebugValue` para oferecer suporte a `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="a4068-384">Extends `ICorDebugValue` to provide support for `ICorDebugType`.</span></span>  
  
 <span data-ttu-id="a4068-385">[ICorDebugValue3 Interface](icordebugvalue3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-385">[ICorDebugValue3 Interface](icordebugvalue3-interface.md)</span></span>\
 <span data-ttu-id="a4068-386">Estende as interfaces "ICorDebugValue" e "ICorDebugValue2" para fornecer suporte para arrays maiores que 2 GB.</span><span class="sxs-lookup"><span data-stu-id="a4068-386">Extends the "ICorDebugValue" and "ICorDebugValue2" interfaces to provide support for arrays that are larger than 2 GB.</span></span>  
  
 <span data-ttu-id="a4068-387">[ICorDebugValueBreakpoint](icordebugvaluebreakpoint-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-387">[ICorDebugValueBreakpoint](icordebugvaluebreakpoint-interface.md)</span></span>\
 <span data-ttu-id="a4068-388">Estende `ICorDebugBreakpoint` para fornecer acesso a valores específicos.</span><span class="sxs-lookup"><span data-stu-id="a4068-388">Extends `ICorDebugBreakpoint` to provide access to specific values.</span></span>  
  
 <span data-ttu-id="a4068-389">[ICorDebugValueEnum](icordebugvalueenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-389">[ICorDebugValueEnum](icordebugvalueenum-interface.md)</span></span>\
 <span data-ttu-id="a4068-390">Implementa métodos `ICorDebugEnum` e enumera matrizes de `ICorDebugValue`.</span><span class="sxs-lookup"><span data-stu-id="a4068-390">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugValue` arrays.</span></span>  
  
 <span data-ttu-id="a4068-391">[ICorDebugVariableHome Interface](icordebugvariablehome-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-391">[ICorDebugVariableHome Interface](icordebugvariablehome-interface.md)</span></span>\
 <span data-ttu-id="a4068-392">Representa uma variável local ou argumento de uma função.</span><span class="sxs-lookup"><span data-stu-id="a4068-392">Represents a local variable or argument of a function.</span></span>  
  
 <span data-ttu-id="a4068-393">[ICorDebugVariableHomeEnum Interface](icordebugvariablehomeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-393">[ICorDebugVariableHomeEnum Interface](icordebugvariablehomeenum-interface.md)</span></span>\
 <span data-ttu-id="a4068-394">Fornece um enumerador para as variáveis e argumentos locais em uma função.</span><span class="sxs-lookup"><span data-stu-id="a4068-394">Provides an enumerator to the local variables and arguments in a function.</span></span>  
  
 <span data-ttu-id="a4068-395">[ICorDebugVariableSymbol Interface](icordebugvariablesymbol-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-395">[ICorDebugVariableSymbol Interface](icordebugvariablesymbol-interface.md)</span></span>\
 <span data-ttu-id="a4068-396">Recupera a informação do símbolo de depuração para uma variável.</span><span class="sxs-lookup"><span data-stu-id="a4068-396">Retrieves the debug symbol information for a variable.</span></span> <span data-ttu-id="a4068-397">**Disponível apenas no .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="a4068-397">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="a4068-398">[ICorDebugVirtualUnwinder Interface](icordebugvirtualunwinder-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-398">[ICorDebugVirtualUnwinder Interface](icordebugvirtualunwinder-interface.md)</span></span>\
 <span data-ttu-id="a4068-399">Fornece métodos para ajudar no desenrolar da pilha.</span><span class="sxs-lookup"><span data-stu-id="a4068-399">Provides methods to help in stack unwinding.</span></span> <span data-ttu-id="a4068-400">**Disponível apenas no .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="a4068-400">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="a4068-401">[ICorPublish Interface](icorpublish-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-401">[ICorPublish Interface](icorpublish-interface.md)</span></span>\
 <span data-ttu-id="a4068-402">Serve como a interface geral para os processos de publicação.</span><span class="sxs-lookup"><span data-stu-id="a4068-402">Serves as the general interface for the publishing processes.</span></span>  
  
 <span data-ttu-id="a4068-403">[Interface de domínio do ICorPublishApp](icorpublishappdomain-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-403">[ICorPublishAppDomain Interface](icorpublishappdomain-interface.md)</span></span>\
 <span data-ttu-id="a4068-404">Representa e fornece informações sobre um domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a4068-404">Represents and provides information about an application domain.</span></span>  
  
 <span data-ttu-id="a4068-405">[ICorPublishAppDomainEnum Interface](icorpublishappdomainenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-405">[ICorPublishAppDomainEnum Interface](icorpublishappdomainenum-interface.md)</span></span>\
 <span data-ttu-id="a4068-406">Fornece métodos que percorrem uma coleção de objetos `ICorPublishAppDomain` existentes em um processo.</span><span class="sxs-lookup"><span data-stu-id="a4068-406">Provides methods that traverse a collection of `ICorPublishAppDomain` objects that currently exist within a process.</span></span>  
  
 <span data-ttu-id="a4068-407">[ICorPublishEnum Interface](icorpublishenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-407">[ICorPublishEnum Interface](icorpublishenum-interface.md)</span></span>\
 <span data-ttu-id="a4068-408">Serve como a base abstrata para a publicação de enumeradores.</span><span class="sxs-lookup"><span data-stu-id="a4068-408">Serves as the abstract base for publishing enumerators.</span></span>  
  
 <span data-ttu-id="a4068-409">[ICorPublishProcess Interface](icorpublishprocess-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-409">[ICorPublishProcess Interface](icorpublishprocess-interface.md)</span></span>\
 <span data-ttu-id="a4068-410">Fornece métodos que acessam informações sobre um processo.</span><span class="sxs-lookup"><span data-stu-id="a4068-410">Provides methods that access information about a process.</span></span>  
  
 <span data-ttu-id="a4068-411">[ICorPublishProcessEnum Interface](icorpublishprocessenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-411">[ICorPublishProcessEnum Interface](icorpublishprocessenum-interface.md)</span></span>\
 <span data-ttu-id="a4068-412">Fornece métodos que percorrem uma coleção de objetos `ICorPublishProcess`.</span><span class="sxs-lookup"><span data-stu-id="a4068-412">Provides methods that traverse a collection of `ICorPublishProcess` objects.</span></span>  

 <span data-ttu-id="a4068-413">[ISOSDacInterface Interface](isosdacinterface-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-413">[ISOSDacInterface Interface](isosdacinterface-interface.md)</span></span>\
 <span data-ttu-id="a4068-414">Fornece métodos auxiliares para `SOS`acessar dados de .</span><span class="sxs-lookup"><span data-stu-id="a4068-414">Provides helper methods to access data from `SOS`.</span></span>

 <span data-ttu-id="a4068-415">[Interface DEdefinição de método IXCLRData](ixclrdatamethoddefinition-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-415">[IXCLRDataMethodDefinition Interface](ixclrdatamethoddefinition-interface.md)</span></span>\
 <span data-ttu-id="a4068-416">Fornece métodos para consultar informações sobre uma definição de método.</span><span class="sxs-lookup"><span data-stu-id="a4068-416">Provides methods for querying information about a method definition.</span></span>

 <span data-ttu-id="a4068-417">[IXCLRDataMethodInstance Interface](ixclrdatamethodinstance-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-417">[IXCLRDataMethodInstance Interface](ixclrdatamethodinstance-interface.md)</span></span>\
 <span data-ttu-id="a4068-418">Fornece métodos para consultar informações sobre uma instância do método.</span><span class="sxs-lookup"><span data-stu-id="a4068-418">Provides methods for querying information about a method instance.</span></span>

 <span data-ttu-id="a4068-419">[IXCLRDataModule Interface](ixclrdatamodule-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-419">[IXCLRDataModule Interface](ixclrdatamodule-interface.md)</span></span>\
 <span data-ttu-id="a4068-420">Fornece métodos para consultar informações sobre um módulo carregado.</span><span class="sxs-lookup"><span data-stu-id="a4068-420">Provides methods for querying information about a loaded module.</span></span>

 <span data-ttu-id="a4068-421">[IXCLRDataProcess Interface](ixclrdataprocess-interface.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-421">[IXCLRDataProcess Interface](ixclrdataprocess-interface.md)</span></span>\
 <span data-ttu-id="a4068-422">Fornece métodos para consultar informações sobre um processo.</span><span class="sxs-lookup"><span data-stu-id="a4068-422">Provides methods for querying information about a process.</span></span>
  
## <a name="related-sections"></a><span data-ttu-id="a4068-423">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="a4068-423">Related Sections</span></span>  
 <span data-ttu-id="a4068-424">[Co-classes de depuração](debugging-coclasses.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-424">[Debugging Coclasses](debugging-coclasses.md)</span></span>\
 <span data-ttu-id="a4068-425">[Depuração de funções estáticas globais](debugging-global-static-functions.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-425">[Debugging Global Static Functions](debugging-global-static-functions.md)</span></span>\
 <span data-ttu-id="a4068-426">[Depuração de enumerações](debugging-enumerations.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-426">[Debugging Enumerations](debugging-enumerations.md)</span></span>\
 <span data-ttu-id="a4068-427">[Estruturas de depuração](debugging-structures.md)</span><span class="sxs-lookup"><span data-stu-id="a4068-427">[Debugging Structures](debugging-structures.md)</span></span>\
