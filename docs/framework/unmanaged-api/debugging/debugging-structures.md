---
title: Estruturas de depuração
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged structures [.NET Framework], debugging
- debugging structures [.NET Framework]
- structures [.NET Framework debugging]
ms.assetid: 173ba2c2-ab34-49ae-b6a8-e5c49882bf05
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 23aa619d666f2e0b9eb67ab4cf8d4f92761865d3
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2019
ms.locfileid: "54415319"
---
# <a name="debugging-structures"></a><span data-ttu-id="96752-102">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="96752-102">Debugging Structures</span></span>
<span data-ttu-id="96752-103">Esta seção descreve as estruturas não gerenciadas que a API de depuração usa.</span><span class="sxs-lookup"><span data-stu-id="96752-103">This section describes the unmanaged structures that the debugging API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="96752-104">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="96752-104">In This Section</span></span>  
 [<span data-ttu-id="96752-105">Estrutura CLR_DEBUGGING_VERSION</span><span class="sxs-lookup"><span data-stu-id="96752-105">CLR_DEBUGGING_VERSION Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-version-structure.md)  
 <span data-ttu-id="96752-106">Define a versão do produto do CLR (Common Language Runtime) para fins de depuração.</span><span class="sxs-lookup"><span data-stu-id="96752-106">Defines the product version of the common language runtime (CLR) for debugging purposes.</span></span>  
  
 [<span data-ttu-id="96752-107">Estrutura1 CodeChunkInfo</span><span class="sxs-lookup"><span data-stu-id="96752-107">CodeChunkInfo Structure1</span></span>](../../../../docs/framework/unmanaged-api/debugging/codechunkinfo-structure.md)  
 <span data-ttu-id="96752-108">Representa uma única parte de código na memória.</span><span class="sxs-lookup"><span data-stu-id="96752-108">Represents a single chunk of code in memory.</span></span>  
  
 [<span data-ttu-id="96752-109">Estrutura CorDebugBlockingObject</span><span class="sxs-lookup"><span data-stu-id="96752-109">CorDebugBlockingObject Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md)  
 <span data-ttu-id="96752-110">Define um objeto que está bloqueando um thread e o motivo pelo qual o segmento está bloqueado.</span><span class="sxs-lookup"><span data-stu-id="96752-110">Defines an object that is blocking a thread and the reason why the thread is blocked.</span></span>  
  
 [<span data-ttu-id="96752-111">Estrutura CorDebugEHClause</span><span class="sxs-lookup"><span data-stu-id="96752-111">CorDebugEHClause Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md)  
 <span data-ttu-id="96752-112">Representa uma cláusula de tratamento de exceções para um determinado pedaço de IL (Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="96752-112">Represents an exception handling (EH) clause for a given piece of intermediate language (IL).</span></span>  
  
 [<span data-ttu-id="96752-113">Estrutura CorDebugExceptionObjectStackFrame</span><span class="sxs-lookup"><span data-stu-id="96752-113">CorDebugExceptionObjectStackFrame Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md)  
 <span data-ttu-id="96752-114">Representa informações de quadro de pilha de um objeto de exceção.</span><span class="sxs-lookup"><span data-stu-id="96752-114">Represents stack frame information from an exception object.</span></span>  
  
 [<span data-ttu-id="96752-115">Estrutura CorDebugExceptionObjectStackFrame</span><span class="sxs-lookup"><span data-stu-id="96752-115">CorDebugExceptionObjectStackFrame Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md)  
 <span data-ttu-id="96752-116">Mapas de um [!INCLUDE[wrt](../../../../includes/wrt-md.md)] GUID para seus respectivos [ICorDebugType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md) objeto.</span><span class="sxs-lookup"><span data-stu-id="96752-116">Maps a [!INCLUDE[wrt](../../../../includes/wrt-md.md)] GUID to its corresponding [ICorDebugType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md) object.</span></span>  
  
 <span data-ttu-id="96752-117">COR_ACTIVE_FUNCTION</span><span class="sxs-lookup"><span data-stu-id="96752-117">COR_ACTIVE_FUNCTION</span></span>  
 <span data-ttu-id="96752-118">Contém informações sobre as funções que estão atualmente ativas nos quadros de um thread.</span><span class="sxs-lookup"><span data-stu-id="96752-118">Contains information about the functions that are currently active in a thread's frames.</span></span>  
  
 [<span data-ttu-id="96752-119">Estrutura COR_ARRAY_LAYOUT</span><span class="sxs-lookup"><span data-stu-id="96752-119">COR_ARRAY_LAYOUT Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md)  
 <span data-ttu-id="96752-120">Fornece informações sobre o layout de um objeto matriz na memória.</span><span class="sxs-lookup"><span data-stu-id="96752-120">Provides information about the layout of an array object in memory.</span></span>  
  
 <span data-ttu-id="96752-121">COR_DEBUG_IL_TO_NATIVE_MAP</span><span class="sxs-lookup"><span data-stu-id="96752-121">COR_DEBUG_IL_TO_NATIVE_MAP</span></span>  
 <span data-ttu-id="96752-122">Contém os deslocamentos que são usados ​​para mapear o código da MSIL (Microsoft intermediate language) para o código nativo.</span><span class="sxs-lookup"><span data-stu-id="96752-122">Contains the offsets that are used to map Microsoft intermediate language (MSIL) code to native code.</span></span>  
  
 <span data-ttu-id="96752-123">COR_DEBUG_STEP_RANGE</span><span class="sxs-lookup"><span data-stu-id="96752-123">COR_DEBUG_STEP_RANGE</span></span>  
 <span data-ttu-id="96752-124">Contém as informações de deslocamento para um intervalo de código.</span><span class="sxs-lookup"><span data-stu-id="96752-124">Contains the offset information for a range of code.</span></span>  
  
 [<span data-ttu-id="96752-125">Estrutura COR_FIELD</span><span class="sxs-lookup"><span data-stu-id="96752-125">COR_FIELD Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md)  
 <span data-ttu-id="96752-126">Fornece informações sobre um campo em um objeto.</span><span class="sxs-lookup"><span data-stu-id="96752-126">Provides information about a field in an object.</span></span>  
  
 [<span data-ttu-id="96752-127">Estrutura COR_GC_REFERENCE</span><span class="sxs-lookup"><span data-stu-id="96752-127">COR_GC_REFERENCE Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md)  
 <span data-ttu-id="96752-128">Contém informações sobre um objeto que será coletado como lixo.</span><span class="sxs-lookup"><span data-stu-id="96752-128">Contains information about an object that is to be garbage-collected.</span></span>  
  
 [<span data-ttu-id="96752-129">Estrutura COR_HEAPINFO</span><span class="sxs-lookup"><span data-stu-id="96752-129">COR_HEAPINFO Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md)  
 <span data-ttu-id="96752-130">Fornece informações gerais sobre o heap de coleta de lixo, incluindo se é enumerável.</span><span class="sxs-lookup"><span data-stu-id="96752-130">Provides general information about the garbage collection heap, including whether it is enumerable.</span></span>  
  
 [<span data-ttu-id="96752-131">Estrutura COR_HEAPOBJECT</span><span class="sxs-lookup"><span data-stu-id="96752-131">COR_HEAPOBJECT Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)  
 <span data-ttu-id="96752-132">Fornece informações sobre um objeto no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="96752-132">Provides information about an object on the managed heap.</span></span>  
  
 <span data-ttu-id="96752-133">COR_IL_MAP</span><span class="sxs-lookup"><span data-stu-id="96752-133">COR_IL_MAP</span></span>  
 <span data-ttu-id="96752-134">Especifica mudanças no deslocamento relativo de uma função.</span><span class="sxs-lookup"><span data-stu-id="96752-134">Specifies changes in the relative offset of a function.</span></span>  
  
 [<span data-ttu-id="96752-135">Estrutura COR_SEGMENT</span><span class="sxs-lookup"><span data-stu-id="96752-135">COR_SEGMENT Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md)  
 <span data-ttu-id="96752-136">Contém informações sobre uma região da memória no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="96752-136">Contains information about a region of memory in the managed heap.</span></span>  
  
 [<span data-ttu-id="96752-137">Estrutura COR_TYPEID</span><span class="sxs-lookup"><span data-stu-id="96752-137">COR_TYPEID Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)  
 <span data-ttu-id="96752-138">Contém um identificador de tipo.</span><span class="sxs-lookup"><span data-stu-id="96752-138">Contains a type identifier.</span></span>  
  
 [<span data-ttu-id="96752-139">Estrutura COR_TYPE_LAYOUT</span><span class="sxs-lookup"><span data-stu-id="96752-139">COR_TYPE_LAYOUT Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md)  
 <span data-ttu-id="96752-140">Fornece informações sobre o layout de um objeto na memória.</span><span class="sxs-lookup"><span data-stu-id="96752-140">Provides information about the layout of an object in memory.</span></span>  
  
 <span data-ttu-id="96752-141">COR_VERSION</span><span class="sxs-lookup"><span data-stu-id="96752-141">COR_VERSION</span></span>  
 <span data-ttu-id="96752-142">Armazena o número da versão com quatro partes padrão do CLR.</span><span class="sxs-lookup"><span data-stu-id="96752-142">Stores the standard four-part version number of the common language runtime.</span></span>  
  
 [<span data-ttu-id="96752-143">Estrutura StackTrace_SimpleContext</span><span class="sxs-lookup"><span data-stu-id="96752-143">StackTrace_SimpleContext Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md)  
 <span data-ttu-id="96752-144">Fornece um contexto simples que pode ser usado em lugar de uma estrutura `CONTEXT` completa.</span><span class="sxs-lookup"><span data-stu-id="96752-144">Provides a simple context that can be used in place of a full `CONTEXT` structure.</span></span>

 <span data-ttu-id="96752-145">[Estrutura CLRDATA_ADDRESS_RANGE](../../../../docs/framework/unmanaged-api/debugging/clrdata-address-range-structure.md) define um intervalo de endereços.</span><span class="sxs-lookup"><span data-stu-id="96752-145">[CLRDATA_ADDRESS_RANGE Structure](../../../../docs/framework/unmanaged-api/debugging/clrdata-address-range-structure.md) Defines an address range.</span></span>
 
 <span data-ttu-id="96752-146">[Estrutura CLRDATA_IL_ADDRESS_MAP](../../../../docs/framework/unmanaged-api/debugging/clrdata-il-address-map-structure.md) define um IL para o mapeamento de endereço</span><span class="sxs-lookup"><span data-stu-id="96752-146">[CLRDATA_IL_ADDRESS_MAP Structure](../../../../docs/framework/unmanaged-api/debugging/clrdata-il-address-map-structure.md) Defines an IL to address mapping</span></span>
 
 <span data-ttu-id="96752-147">[Estrutura DacpGetModuleAddress](../../../../docs/framework/unmanaged-api/debugging/dacpgetmoduleaddress-structure.md) define o contêiner para uma solicitação de endereço do módulo.</span><span class="sxs-lookup"><span data-stu-id="96752-147">[DacpGetModuleAddress Structure](../../../../docs/framework/unmanaged-api/debugging/dacpgetmoduleaddress-structure.md) Defines the container for a module address request.</span></span>

  
## <a name="related-sections"></a><span data-ttu-id="96752-148">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="96752-148">Related Sections</span></span>  
 [<span data-ttu-id="96752-149">Depurando coclasses</span><span class="sxs-lookup"><span data-stu-id="96752-149">Debugging Coclasses</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [<span data-ttu-id="96752-150">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="96752-150">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
  
 [<span data-ttu-id="96752-151">Depurando funções estáticas globais</span><span class="sxs-lookup"><span data-stu-id="96752-151">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)  
  
 [<span data-ttu-id="96752-152">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="96752-152">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
  
 [<span data-ttu-id="96752-153">Depuração</span><span class="sxs-lookup"><span data-stu-id="96752-153">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
