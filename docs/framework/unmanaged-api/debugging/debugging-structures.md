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
ms.openlocfilehash: 6c7415920d34fc231bf82dd00199c7e01eec7a73
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="debugging-structures"></a><span data-ttu-id="5540d-102">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="5540d-102">Debugging Structures</span></span>
<span data-ttu-id="5540d-103">Esta seção descreve as estruturas não gerenciadas que a API de depuração usa.</span><span class="sxs-lookup"><span data-stu-id="5540d-103">This section describes the unmanaged structures that the debugging API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5540d-104">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="5540d-104">In This Section</span></span>  
 [<span data-ttu-id="5540d-105">Estrutura CLR_DEBUGGING_VERSION</span><span class="sxs-lookup"><span data-stu-id="5540d-105">CLR_DEBUGGING_VERSION Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-version-structure.md)  
 <span data-ttu-id="5540d-106">Define a versão do produto do CLR (Common Language Runtime) para fins de depuração.</span><span class="sxs-lookup"><span data-stu-id="5540d-106">Defines the product version of the common language runtime (CLR) for debugging purposes.</span></span>  
  
 [<span data-ttu-id="5540d-107">Estrutura1 CodeChunkInfo</span><span class="sxs-lookup"><span data-stu-id="5540d-107">CodeChunkInfo Structure1</span></span>](../../../../docs/framework/unmanaged-api/debugging/codechunkinfo-structure.md)  
 <span data-ttu-id="5540d-108">Representa uma única parte de código na memória.</span><span class="sxs-lookup"><span data-stu-id="5540d-108">Represents a single chunk of code in memory.</span></span>  
  
 [<span data-ttu-id="5540d-109">Estrutura CorDebugBlockingObject</span><span class="sxs-lookup"><span data-stu-id="5540d-109">CorDebugBlockingObject Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md)  
 <span data-ttu-id="5540d-110">Define um objeto que está bloqueando um thread e o motivo pelo qual o segmento está bloqueado.</span><span class="sxs-lookup"><span data-stu-id="5540d-110">Defines an object that is blocking a thread and the reason why the thread is blocked.</span></span>  
  
 [<span data-ttu-id="5540d-111">Estrutura CorDebugEHClause</span><span class="sxs-lookup"><span data-stu-id="5540d-111">CorDebugEHClause Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md)  
 <span data-ttu-id="5540d-112">Representa uma cláusula de tratamento de exceções para um determinado pedaço de IL (Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="5540d-112">Represents an exception handling (EH) clause for a given piece of intermediate language (IL).</span></span>  
  
 [<span data-ttu-id="5540d-113">Estrutura CorDebugExceptionObjectStackFrame</span><span class="sxs-lookup"><span data-stu-id="5540d-113">CorDebugExceptionObjectStackFrame Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md)  
 <span data-ttu-id="5540d-114">Representa informações de quadro de pilha de um objeto de exceção.</span><span class="sxs-lookup"><span data-stu-id="5540d-114">Represents stack frame information from an exception object.</span></span>  
  
 [<span data-ttu-id="5540d-115">Estrutura CorDebugExceptionObjectStackFrame</span><span class="sxs-lookup"><span data-stu-id="5540d-115">CorDebugExceptionObjectStackFrame Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md)  
 <span data-ttu-id="5540d-116">Mapeia um [!INCLUDE[wrt](../../../../includes/wrt-md.md)] GUID correspondente [ICorDebugType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md) objeto.</span><span class="sxs-lookup"><span data-stu-id="5540d-116">Maps a [!INCLUDE[wrt](../../../../includes/wrt-md.md)] GUID to its corresponding [ICorDebugType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md) object.</span></span>  
  
 <span data-ttu-id="5540d-117">COR_ACTIVE_FUNCTION</span><span class="sxs-lookup"><span data-stu-id="5540d-117">COR_ACTIVE_FUNCTION</span></span>  
 <span data-ttu-id="5540d-118">Contém informações sobre as funções que estão atualmente ativas nos quadros de um thread.</span><span class="sxs-lookup"><span data-stu-id="5540d-118">Contains information about the functions that are currently active in a thread's frames.</span></span>  
  
 [<span data-ttu-id="5540d-119">Estrutura COR_ARRAY_LAYOUT</span><span class="sxs-lookup"><span data-stu-id="5540d-119">COR_ARRAY_LAYOUT Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md)  
 <span data-ttu-id="5540d-120">Fornece informações sobre o layout de um objeto matriz na memória.</span><span class="sxs-lookup"><span data-stu-id="5540d-120">Provides information about the layout of an array object in memory.</span></span>  
  
 <span data-ttu-id="5540d-121">COR_DEBUG_IL_TO_NATIVE_MAP</span><span class="sxs-lookup"><span data-stu-id="5540d-121">COR_DEBUG_IL_TO_NATIVE_MAP</span></span>  
 <span data-ttu-id="5540d-122">Contém os deslocamentos que são usados ​​para mapear o código da MSIL (Microsoft intermediate language) para o código nativo.</span><span class="sxs-lookup"><span data-stu-id="5540d-122">Contains the offsets that are used to map Microsoft intermediate language (MSIL) code to native code.</span></span>  
  
 <span data-ttu-id="5540d-123">COR_DEBUG_STEP_RANGE</span><span class="sxs-lookup"><span data-stu-id="5540d-123">COR_DEBUG_STEP_RANGE</span></span>  
 <span data-ttu-id="5540d-124">Contém as informações de deslocamento para um intervalo de código.</span><span class="sxs-lookup"><span data-stu-id="5540d-124">Contains the offset information for a range of code.</span></span>  
  
 [<span data-ttu-id="5540d-125">Estrutura COR_FIELD</span><span class="sxs-lookup"><span data-stu-id="5540d-125">COR_FIELD Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md)  
 <span data-ttu-id="5540d-126">Fornece informações sobre um campo em um objeto.</span><span class="sxs-lookup"><span data-stu-id="5540d-126">Provides information about a field in an object.</span></span>  
  
 [<span data-ttu-id="5540d-127">Estrutura COR_GC_REFERENCE</span><span class="sxs-lookup"><span data-stu-id="5540d-127">COR_GC_REFERENCE Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md)  
 <span data-ttu-id="5540d-128">Contém informações sobre um objeto que será coletado como lixo.</span><span class="sxs-lookup"><span data-stu-id="5540d-128">Contains information about an object that is to be garbage-collected.</span></span>  
  
 [<span data-ttu-id="5540d-129">Estrutura COR_HEAPINFO</span><span class="sxs-lookup"><span data-stu-id="5540d-129">COR_HEAPINFO Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md)  
 <span data-ttu-id="5540d-130">Fornece informações gerais sobre o heap de coleta de lixo, incluindo se é enumerável.</span><span class="sxs-lookup"><span data-stu-id="5540d-130">Provides general information about the garbage collection heap, including whether it is enumerable.</span></span>  
  
 [<span data-ttu-id="5540d-131">Estrutura COR_HEAPOBJECT</span><span class="sxs-lookup"><span data-stu-id="5540d-131">COR_HEAPOBJECT Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)  
 <span data-ttu-id="5540d-132">Fornece informações sobre um objeto no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="5540d-132">Provides information about an object on the managed heap.</span></span>  
  
 <span data-ttu-id="5540d-133">COR_IL_MAP</span><span class="sxs-lookup"><span data-stu-id="5540d-133">COR_IL_MAP</span></span>  
 <span data-ttu-id="5540d-134">Especifica mudanças no deslocamento relativo de uma função.</span><span class="sxs-lookup"><span data-stu-id="5540d-134">Specifies changes in the relative offset of a function.</span></span>  
  
 [<span data-ttu-id="5540d-135">Estrutura COR_SEGMENT</span><span class="sxs-lookup"><span data-stu-id="5540d-135">COR_SEGMENT Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md)  
 <span data-ttu-id="5540d-136">Contém informações sobre uma região da memória no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="5540d-136">Contains information about a region of memory in the managed heap.</span></span>  
  
 [<span data-ttu-id="5540d-137">Estrutura COR_TYPEID</span><span class="sxs-lookup"><span data-stu-id="5540d-137">COR_TYPEID Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)  
 <span data-ttu-id="5540d-138">Contém um identificador de tipo.</span><span class="sxs-lookup"><span data-stu-id="5540d-138">Contains a type identifier.</span></span>  
  
 [<span data-ttu-id="5540d-139">Estrutura COR_TYPE_LAYOUT</span><span class="sxs-lookup"><span data-stu-id="5540d-139">COR_TYPE_LAYOUT Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md)  
 <span data-ttu-id="5540d-140">Fornece informações sobre o layout de um objeto na memória.</span><span class="sxs-lookup"><span data-stu-id="5540d-140">Provides information about the layout of an object in memory.</span></span>  
  
 <span data-ttu-id="5540d-141">COR_VERSION</span><span class="sxs-lookup"><span data-stu-id="5540d-141">COR_VERSION</span></span>  
 <span data-ttu-id="5540d-142">Armazena o número da versão com quatro partes padrão do CLR.</span><span class="sxs-lookup"><span data-stu-id="5540d-142">Stores the standard four-part version number of the common language runtime.</span></span>  
  
 [<span data-ttu-id="5540d-143">Estrutura StackTrace_SimpleContext</span><span class="sxs-lookup"><span data-stu-id="5540d-143">StackTrace_SimpleContext Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md)  
 <span data-ttu-id="5540d-144">Fornece um contexto simples que pode ser usado em lugar de uma estrutura `CONTEXT` completa.</span><span class="sxs-lookup"><span data-stu-id="5540d-144">Provides a simple context that can be used in place of a full `CONTEXT` structure.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="5540d-145">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="5540d-145">Related Sections</span></span>  
 [<span data-ttu-id="5540d-146">Depurando coclasses</span><span class="sxs-lookup"><span data-stu-id="5540d-146">Debugging Coclasses</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [<span data-ttu-id="5540d-147">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="5540d-147">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
  
 [<span data-ttu-id="5540d-148">Depurando funções estáticas globais</span><span class="sxs-lookup"><span data-stu-id="5540d-148">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)  
  
 [<span data-ttu-id="5540d-149">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="5540d-149">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
  
 [<span data-ttu-id="5540d-150">Depuração</span><span class="sxs-lookup"><span data-stu-id="5540d-150">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
