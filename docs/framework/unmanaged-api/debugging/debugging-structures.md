---
title: Estruturas de depuração
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged structures [.NET Framework], debugging
- debugging structures [.NET Framework]
- structures [.NET Framework debugging]
ms.assetid: 173ba2c2-ab34-49ae-b6a8-e5c49882bf05
ms.openlocfilehash: 05a321d5025f03d6a0378b462178bf06c0291f48
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123028"
---
# <a name="debugging-structures"></a><span data-ttu-id="6fd74-102">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="6fd74-102">Debugging Structures</span></span>

<span data-ttu-id="6fd74-103">Esta seção descreve as estruturas não gerenciadas que a API de depuração usa.</span><span class="sxs-lookup"><span data-stu-id="6fd74-103">This section describes the unmanaged structures that the debugging API uses.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="6fd74-104">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="6fd74-104">In This Section</span></span>
 <span data-ttu-id="6fd74-105">[Estrutura CLRDATA_ADDRESS_RANGE](../../../../docs/framework/unmanaged-api/debugging/clrdata-address-range-structure.md) Define um intervalo de endereços.</span><span class="sxs-lookup"><span data-stu-id="6fd74-105">[CLRDATA_ADDRESS_RANGE Structure](../../../../docs/framework/unmanaged-api/debugging/clrdata-address-range-structure.md) Defines an address range.</span></span>

 <span data-ttu-id="6fd74-106">[Estrutura CLRDATA_IL_ADDRESS_MAP](../../../../docs/framework/unmanaged-api/debugging/clrdata-il-address-map-structure.md) Define um IL para o mapeamento de endereços</span><span class="sxs-lookup"><span data-stu-id="6fd74-106">[CLRDATA_IL_ADDRESS_MAP Structure](../../../../docs/framework/unmanaged-api/debugging/clrdata-il-address-map-structure.md) Defines an IL to address mapping</span></span>

 <span data-ttu-id="6fd74-107">[Estrutura CLR_DEBUGGING_VERSION](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-version-structure.md) Define a versão do produto do Common Language Runtime (CLR) para fins de depuração.</span><span class="sxs-lookup"><span data-stu-id="6fd74-107">[CLR_DEBUGGING_VERSION Structure](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-version-structure.md) Defines the product version of the common language runtime (CLR) for debugging purposes.</span></span>

 <span data-ttu-id="6fd74-108">[Estrutura CodeChunkInfo](../../../../docs/framework/unmanaged-api/debugging/codechunkinfo-structure.md) Representa uma única parte do código na memória.</span><span class="sxs-lookup"><span data-stu-id="6fd74-108">[CodeChunkInfo Structure](../../../../docs/framework/unmanaged-api/debugging/codechunkinfo-structure.md) Represents a single chunk of code in memory.</span></span>

 <span data-ttu-id="6fd74-109">[COR_ACTIVE_FUNCTION](cor-active-function-structure.md) Contém informações sobre as funções que estão atualmente ativas em quadros de um thread.</span><span class="sxs-lookup"><span data-stu-id="6fd74-109">[COR_ACTIVE_FUNCTION](cor-active-function-structure.md) Contains information about the functions that are currently active in a thread's frames.</span></span>

 <span data-ttu-id="6fd74-110">[Estrutura COR_ARRAY_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md) Fornece informações sobre o layout de um objeto de matriz na memória.</span><span class="sxs-lookup"><span data-stu-id="6fd74-110">[COR_ARRAY_LAYOUT Structure](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md) Provides information about the layout of an array object in memory.</span></span>

 <span data-ttu-id="6fd74-111">[COR_DEBUG_IL_TO_NATIVE_MAP](cor-debug-il-to-native-map-structure.md) Contém os deslocamentos que são usados para mapear o código MSIL (Microsoft Intermediate Language) para o código nativo.</span><span class="sxs-lookup"><span data-stu-id="6fd74-111">[COR_DEBUG_IL_TO_NATIVE_MAP](cor-debug-il-to-native-map-structure.md) Contains the offsets that are used to map Microsoft intermediate language (MSIL) code to native code.</span></span>

 <span data-ttu-id="6fd74-112">[COR_DEBUG_STEP_RANGE](cor-debug-step-range-structure.md) Contém as informações de deslocamento de um intervalo de código.</span><span class="sxs-lookup"><span data-stu-id="6fd74-112">[COR_DEBUG_STEP_RANGE](cor-debug-step-range-structure.md) Contains the offset information for a range of code.</span></span>

 <span data-ttu-id="6fd74-113">[Estrutura COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) Fornece informações sobre um campo em um objeto.</span><span class="sxs-lookup"><span data-stu-id="6fd74-113">[COR_FIELD Structure](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) Provides information about a field in an object.</span></span>

 <span data-ttu-id="6fd74-114">[Estrutura COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) Contém informações sobre um objeto que deve ser coletado pelo lixo.</span><span class="sxs-lookup"><span data-stu-id="6fd74-114">[COR_GC_REFERENCE Structure](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) Contains information about an object that is to be garbage-collected.</span></span>

 <span data-ttu-id="6fd74-115">[Estrutura COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) Fornece informações gerais sobre o heap de coleta de lixo, incluindo se ele é enumerável.</span><span class="sxs-lookup"><span data-stu-id="6fd74-115">[COR_HEAPINFO Structure](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) Provides general information about the garbage collection heap, including whether it is enumerable.</span></span>

 <span data-ttu-id="6fd74-116">[Estrutura COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) Fornece informações sobre um objeto no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="6fd74-116">[COR_HEAPOBJECT Structure](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) Provides information about an object on the managed heap.</span></span>

 <span data-ttu-id="6fd74-117">[COR_IL_MAP](cor-il-map-structure.md) Especifica alterações no deslocamento relativo de uma função.</span><span class="sxs-lookup"><span data-stu-id="6fd74-117">[COR_IL_MAP](cor-il-map-structure.md) Specifies changes in the relative offset of a function.</span></span>

 <span data-ttu-id="6fd74-118">[Estrutura COR_SEGMENT](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) Contém informações sobre uma região de memória no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="6fd74-118">[COR_SEGMENT Structure](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) Contains information about a region of memory in the managed heap.</span></span>

 <span data-ttu-id="6fd74-119">[Estrutura COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) Contém um identificador de tipo.</span><span class="sxs-lookup"><span data-stu-id="6fd74-119">[COR_TYPEID Structure](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) Contains a type identifier.</span></span>

 <span data-ttu-id="6fd74-120">[Estrutura COR_TYPE_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md) Fornece informações sobre o layout de um objeto na memória.</span><span class="sxs-lookup"><span data-stu-id="6fd74-120">[COR_TYPE_LAYOUT Structure](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md) Provides information about the layout of an object in memory.</span></span>

 <span data-ttu-id="6fd74-121">[COR_VERSION](cor-version-structure.md) Armazena o número de versão padrão de quatro partes do Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="6fd74-121">[COR_VERSION](cor-version-structure.md) Stores the standard four-part version number of the common language runtime.</span></span>

 <span data-ttu-id="6fd74-122">[Estrutura CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) Define um objeto que está bloqueando um thread e o motivo pelo qual o thread é bloqueado.</span><span class="sxs-lookup"><span data-stu-id="6fd74-122">[CorDebugBlockingObject Structure](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) Defines an object that is blocking a thread and the reason why the thread is blocked.</span></span>

 <span data-ttu-id="6fd74-123">[Estrutura CorDebugEHClause](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md) Representa uma cláusula de tratamento de exceção (EH) para uma determinada linguagem intermediária (IL).</span><span class="sxs-lookup"><span data-stu-id="6fd74-123">[CorDebugEHClause Structure](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md) Represents an exception handling (EH) clause for a given piece of intermediate language (IL).</span></span>

 <span data-ttu-id="6fd74-124">[Estrutura CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) Representa informações de quadros de pilha de um objeto de exceção.</span><span class="sxs-lookup"><span data-stu-id="6fd74-124">[CorDebugExceptionObjectStackFrame Structure](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) Represents stack frame information from an exception object.</span></span>

 <span data-ttu-id="6fd74-125">[Estrutura CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) Mapeia um GUID de Windows Runtime para seu objeto [ICorDebugType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md) correspondente.</span><span class="sxs-lookup"><span data-stu-id="6fd74-125">[CorDebugGuidToTypeMapping Structure](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) Maps a Windows Runtime GUID to its corresponding [ICorDebugType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md) object.</span></span>

 <span data-ttu-id="6fd74-126">[Estrutura DacpGetModuleAddress](../../../../docs/framework/unmanaged-api/debugging/dacpgetmoduleaddress-structure.md) Define o contêiner para uma solicitação de endereço de módulo.</span><span class="sxs-lookup"><span data-stu-id="6fd74-126">[DacpGetModuleAddress Structure](../../../../docs/framework/unmanaged-api/debugging/dacpgetmoduleaddress-structure.md) Defines the container for a module address request.</span></span>

 <span data-ttu-id="6fd74-127">[Estrutura DacpMethodDescData](../../../../docs/framework/unmanaged-api/debugging/dacpmethoddescdata-structure.md) Define um buffer de transporte para as informações de tempo de execução de um método.</span><span class="sxs-lookup"><span data-stu-id="6fd74-127">[DacpMethodDescData Structure](../../../../docs/framework/unmanaged-api/debugging/dacpmethoddescdata-structure.md) Defines a transport buffer for a method's runtime information.</span></span>

 <span data-ttu-id="6fd74-128">[Estrutura DacpModuleData](../../../../docs/framework/unmanaged-api/debugging/dacpmoduledata-structure.md) Define um buffer de transporte para as informações de tempo de execução de um módulo.</span><span class="sxs-lookup"><span data-stu-id="6fd74-128">[DacpModuleData Structure](../../../../docs/framework/unmanaged-api/debugging/dacpmoduledata-structure.md) Defines a transport buffer for a module's runtime information.</span></span>

 <span data-ttu-id="6fd74-129">[Estrutura DacpReJitData](../../../../docs/framework/unmanaged-api/debugging/dacprejitdata-structure.md) Define as informações básicas sobre um determinado método de instrumento do criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="6fd74-129">[DacpReJitData Structure](../../../../docs/framework/unmanaged-api/debugging/dacprejitdata-structure.md) Defines the basic information about a given profiler-instrumented method.</span></span>

 <span data-ttu-id="6fd74-130">[Estrutura StackTrace_SimpleContext](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md) Fornece um contexto simples que pode ser usado no lugar de uma estrutura de `CONTEXT` completa.</span><span class="sxs-lookup"><span data-stu-id="6fd74-130">[StackTrace_SimpleContext Structure](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md) Provides a simple context that can be used in place of a full `CONTEXT` structure.</span></span>

## <a name="related-sections"></a><span data-ttu-id="6fd74-131">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="6fd74-131">Related Sections</span></span>

 [<span data-ttu-id="6fd74-132">Depurando coclasses</span><span class="sxs-lookup"><span data-stu-id="6fd74-132">Debugging Coclasses</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)

 [<span data-ttu-id="6fd74-133">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="6fd74-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

 [<span data-ttu-id="6fd74-134">Depurando funções estáticas globais</span><span class="sxs-lookup"><span data-stu-id="6fd74-134">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)

 [<span data-ttu-id="6fd74-135">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="6fd74-135">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)

 [<span data-ttu-id="6fd74-136">Depuração</span><span class="sxs-lookup"><span data-stu-id="6fd74-136">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
