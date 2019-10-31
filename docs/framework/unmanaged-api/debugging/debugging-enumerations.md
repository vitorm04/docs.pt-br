---
title: Declarando enumerações
ms.date: 03/30/2017
helpviewer_keywords:
- debugging enumerations [.NET Framework]
- unmanaged enumerations [.NET Framework], debugging
- enumerations [.NET Framework debugging]
ms.assetid: 3af9f584-f1b4-4154-aeaa-8fce7c9f8b50
ms.openlocfilehash: 7948b78da1db5267ce53364af1e4a26ff73801e0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124325"
---
# <a name="debugging-enumerations"></a><span data-ttu-id="c3de9-102">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="c3de9-102">Debugging Enumerations</span></span>
<span data-ttu-id="c3de9-103">Esta seção descreve as enumerações não gerenciadas que a API de depuração utiliza.</span><span class="sxs-lookup"><span data-stu-id="c3de9-103">This section describes the unmanaged enumerations that the debugging API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c3de9-104">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="c3de9-104">In This Section</span></span>  
 [<span data-ttu-id="c3de9-105">Enumeração CLR_DEBUGGING_PROCESS_FLAGS</span><span class="sxs-lookup"><span data-stu-id="c3de9-105">CLR_DEBUGGING_PROCESS_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-process-flags-enumeration.md)  
 <span data-ttu-id="c3de9-106">Fornece valores que são usados pelo método [ICLRDebugging:: OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c3de9-106">Provides values that are used by the [ICLRDebugging::OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) method.</span></span>  
  
 [<span data-ttu-id="c3de9-107">Enumeração CLRDataEnumMemoryFlags</span><span class="sxs-lookup"><span data-stu-id="c3de9-107">CLRDataEnumMemoryFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/clrdataenummemoryflags-enumeration.md)  
 <span data-ttu-id="c3de9-108">Indica quais regiões de memória uma chamada para o método [ICLRDataEnumMemoryRegions:: EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) deve incluir.</span><span class="sxs-lookup"><span data-stu-id="c3de9-108">Indicates which memory regions a call to the [ICLRDataEnumMemoryRegions::EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) method should include.</span></span>  
  
 [<span data-ttu-id="c3de9-109">Enumeração COR_PUB_ENUMPROCESS</span><span class="sxs-lookup"><span data-stu-id="c3de9-109">COR_PUB_ENUMPROCESS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-pub-enumprocess-enumeration.md)  
 <span data-ttu-id="c3de9-110">Identifica o tipo de processo que será enumerado.</span><span class="sxs-lookup"><span data-stu-id="c3de9-110">Identifies the type of process to be enumerated.</span></span>  
  
 [<span data-ttu-id="c3de9-111">Enumeração CorDebugBlockingReason</span><span class="sxs-lookup"><span data-stu-id="c3de9-111">CorDebugBlockingReason Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingreason-enumeration.md)  
 <span data-ttu-id="c3de9-112">Especifica os motivos pelos quais um thread pode ficar bloqueado em um determinado objeto.</span><span class="sxs-lookup"><span data-stu-id="c3de9-112">Specifies the reasons why a thread may become blocked on a given object.</span></span>  
  
 <span data-ttu-id="c3de9-113">CorDebugChainReason</span><span class="sxs-lookup"><span data-stu-id="c3de9-113">CorDebugChainReason</span></span>  
 <span data-ttu-id="c3de9-114">Indica o motivo ou os motivos para o início de uma cadeia de chamadas.</span><span class="sxs-lookup"><span data-stu-id="c3de9-114">Indicates the reason or reasons for the initiation of a call chain.</span></span>  
  
 [<span data-ttu-id="c3de9-115">Enumeração CorDebugCodeInvokeKind</span><span class="sxs-lookup"><span data-stu-id="c3de9-115">CorDebugCodeInvokeKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokekind-enumeration.md)  
 <span data-ttu-id="c3de9-116">Descreve como uma função exportada invoca código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="c3de9-116">Describes how an exported function invokes managed code.</span></span>  
  
 [<span data-ttu-id="c3de9-117">Enumeração CorDebugCodeInvokePurpose</span><span class="sxs-lookup"><span data-stu-id="c3de9-117">CorDebugCodeInvokePurpose Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokepurpose-enumeration.md)  
 <span data-ttu-id="c3de9-118">Descreve por que uma função exportada chama código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="c3de9-118">Describes why an exported function calls managed code.</span></span>  
  
 <span data-ttu-id="c3de9-119">CorDebugCreateProcessFlags</span><span class="sxs-lookup"><span data-stu-id="c3de9-119">CorDebugCreateProcessFlags</span></span>  
 <span data-ttu-id="c3de9-120">Fornece opções de depuração adicionais que podem ser usadas em uma chamada para o método [ICorDebug:: CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c3de9-120">Provides additional debugging options that can be used in a call to the [ICorDebug::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) method.</span></span>  
  
 [<span data-ttu-id="c3de9-121">Enumeração CorDebugDebugEventKind</span><span class="sxs-lookup"><span data-stu-id="c3de9-121">CorDebugDebugEventKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md)  
 <span data-ttu-id="c3de9-122">Indica o tipo de evento cujas informações são decodificadas pelo método [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c3de9-122">Indicates the type of event whose information is decoded by the [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) method.</span></span>  
  
 [<span data-ttu-id="c3de9-123">Enumeração CorDebugDecodeEventFlagsWindows</span><span class="sxs-lookup"><span data-stu-id="c3de9-123">CorDebugDecodeEventFlagsWindows Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugdecodeeventflagswindows-enumeration.md)  
 <span data-ttu-id="c3de9-124">Fornece informações adicionais sobre eventos de depuração na plataforma Windows.</span><span class="sxs-lookup"><span data-stu-id="c3de9-124">Provides additional information about debug events on the Windows platform.</span></span>  
  
 <span data-ttu-id="c3de9-125">CorDebugExceptionCallbackType</span><span class="sxs-lookup"><span data-stu-id="c3de9-125">CorDebugExceptionCallbackType</span></span>  
 <span data-ttu-id="c3de9-126">Indica o tipo de retorno de chamada que é feito de um evento [ICorDebugManagedCallback2:: Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c3de9-126">Indicates the type of callback that is made from an [ICorDebugManagedCallback2::Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md) event.</span></span>  
  
 [<span data-ttu-id="c3de9-127">Enumeração CorDebugExceptionFlags</span><span class="sxs-lookup"><span data-stu-id="c3de9-127">CorDebugExceptionFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md)  
 <span data-ttu-id="c3de9-128">Fornece informações adicionais sobre uma exceção.</span><span class="sxs-lookup"><span data-stu-id="c3de9-128">Provides additional information about an exception.</span></span>  
  
 <span data-ttu-id="c3de9-129">CorDebugExceptionUnwindCallbackType</span><span class="sxs-lookup"><span data-stu-id="c3de9-129">CorDebugExceptionUnwindCallbackType</span></span>  
 <span data-ttu-id="c3de9-130">Indica o evento que está sendo sinalizado pelo retorno de chamada durante a fase de desenrolamento.</span><span class="sxs-lookup"><span data-stu-id="c3de9-130">Indicates the event that is being signaled by the callback during the unwind phase.</span></span>  
  
 [<span data-ttu-id="c3de9-131">Enumeração CorDebugGCType</span><span class="sxs-lookup"><span data-stu-id="c3de9-131">CorDebugGCType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebuggctype-enumeration.md)  
 <span data-ttu-id="c3de9-132">Indica se o coletor de lixo está sendo executado em uma estação de trabalho ou em um servidor.</span><span class="sxs-lookup"><span data-stu-id="c3de9-132">Indicates whether the garbage collector is running on a workstation or a server.</span></span>  
  
 [<span data-ttu-id="c3de9-133">Enumeração CorDebugGenerationTypes</span><span class="sxs-lookup"><span data-stu-id="c3de9-133">CorDebugGenerationTypes Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebuggenerationtypes-enumeration.md)  
 <span data-ttu-id="c3de9-134">Especifica a geração de uma região de memória no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="c3de9-134">Specifies the generation of a region of memory on the managed heap.</span></span>  
  
 <span data-ttu-id="c3de9-135">CorDebugHandleType</span><span class="sxs-lookup"><span data-stu-id="c3de9-135">CorDebugHandleType</span></span>  
 <span data-ttu-id="c3de9-136">Indica o tipo de manipulação.</span><span class="sxs-lookup"><span data-stu-id="c3de9-136">Indicates the handle type.</span></span>  
  
 [<span data-ttu-id="c3de9-137">Enumeração CorDebugIlToNativeMappingTypes</span><span class="sxs-lookup"><span data-stu-id="c3de9-137">CorDebugIlToNativeMappingTypes Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md)  
 <span data-ttu-id="c3de9-138">Indica se uma faixa específica de instruções nativas corresponde a uma região de código especial.</span><span class="sxs-lookup"><span data-stu-id="c3de9-138">Indicates whether a particular range of native instructions corresponds to a special code region.</span></span>  
  
 <span data-ttu-id="c3de9-139">CorDebugIntercept</span><span class="sxs-lookup"><span data-stu-id="c3de9-139">CorDebugIntercept</span></span>  
 <span data-ttu-id="c3de9-140">Indica os tipos de código que podem ser entrados.</span><span class="sxs-lookup"><span data-stu-id="c3de9-140">Indicates the types of code that can be stepped into.</span></span>  
  
 [<span data-ttu-id="c3de9-141">Enumeração CorDebugInterfaceVersion</span><span class="sxs-lookup"><span data-stu-id="c3de9-141">CorDebugInterfaceVersion Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md)  
 <span data-ttu-id="c3de9-142">Especifica uma versão do .NET Framework ou a versão do .NET Framework na qual uma interface foi introduzida.</span><span class="sxs-lookup"><span data-stu-id="c3de9-142">Specifies either a version of the .NET Framework, or the version of the .NET Framework in which an interface was introduced.</span></span>  
  
 <span data-ttu-id="c3de9-143">CorDebugInternalFrameType</span><span class="sxs-lookup"><span data-stu-id="c3de9-143">CorDebugInternalFrameType</span></span>  
 <span data-ttu-id="c3de9-144">Identifica o tipo de quadro de pilha.</span><span class="sxs-lookup"><span data-stu-id="c3de9-144">Identifies the type of stack frame.</span></span>  
  
 [<span data-ttu-id="c3de9-145">Enumeração CorDebugJITCompilerFlags</span><span class="sxs-lookup"><span data-stu-id="c3de9-145">CorDebugJITCompilerFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md)  
 <span data-ttu-id="c3de9-146">Contém valores que influenciam o comportamento do compilador just-in-time (JIT) gerenciado.</span><span class="sxs-lookup"><span data-stu-id="c3de9-146">Contains values that influence the behavior of the managed just-in-time (JIT) compiler.</span></span>  
  
 [<span data-ttu-id="c3de9-147">Enumeração CorDebugJITCompilerFlagsDeprecated</span><span class="sxs-lookup"><span data-stu-id="c3de9-147">CorDebugJITCompilerFlagsDeprecated Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflagsdeprecated-enumeration.md)  
 <span data-ttu-id="c3de9-148">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="c3de9-148">Obsolete.</span></span> <span data-ttu-id="c3de9-149">Em vez disso, use o membro `CORDEBUG_JIT_DEFAULT` da enumeração [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="c3de9-149">Use the `CORDEBUG_JIT_DEFAULT` member of the [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) enumeration instead.</span></span>  
  
 <span data-ttu-id="c3de9-150">CorDebugMappingResult</span><span class="sxs-lookup"><span data-stu-id="c3de9-150">CorDebugMappingResult</span></span>  
 <span data-ttu-id="c3de9-151">Fornece os detalhes sobre como o valor do ponteiro de instrução (IP) foi obtido.</span><span class="sxs-lookup"><span data-stu-id="c3de9-151">Provides the details of how the value of the instruction pointer (IP) was obtained.</span></span>  
  
 [<span data-ttu-id="c3de9-152">Enumeração CorDebugMDAFlags</span><span class="sxs-lookup"><span data-stu-id="c3de9-152">CorDebugMDAFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugmdaflags-enumeration.md)  
 <span data-ttu-id="c3de9-153">Especifica o status do thread no qual o assistente de depuração gerenciada (MDA) é disparado.</span><span class="sxs-lookup"><span data-stu-id="c3de9-153">Specifies the status of the thread on which the managed debugging assistant (MDA) is fired.</span></span>  
  
 [<span data-ttu-id="c3de9-154">Enumeração CorDebugNGenPolicy</span><span class="sxs-lookup"><span data-stu-id="c3de9-154">CorDebugNGenPolicy Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md)  
 <span data-ttu-id="c3de9-155">Fornece um valor que determina se um depurador carrega imagens nativas (NGen) do cache de imagens nativas.</span><span class="sxs-lookup"><span data-stu-id="c3de9-155">Provides a value that determines whether a debugger loads native (NGen) images from the native image cache.</span></span>  
  
 [<span data-ttu-id="c3de9-156">Enumeração CorDebugPlatform</span><span class="sxs-lookup"><span data-stu-id="c3de9-156">CorDebugPlatform Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md)  
 <span data-ttu-id="c3de9-157">Fornece valores de plataforma de destino que são usados pelo método [ICorDebugDataTarget:: GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c3de9-157">Provides target platform values that are used by the [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) method.</span></span>  
  
 [<span data-ttu-id="c3de9-158">Enumeração CorDebugRecordFormat</span><span class="sxs-lookup"><span data-stu-id="c3de9-158">CorDebugRecordFormat Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
 <span data-ttu-id="c3de9-159">Descreve o formato dos dados em uma matriz de bytes que contém informações sobre um evento de depuração de exceção nativo.</span><span class="sxs-lookup"><span data-stu-id="c3de9-159">Describes the format of the data in a byte array that contains information about a native exception debug event.</span></span>  
  
 <span data-ttu-id="c3de9-160">CorDebugRegister</span><span class="sxs-lookup"><span data-stu-id="c3de9-160">CorDebugRegister</span></span>  
 <span data-ttu-id="c3de9-161">Especifica os registros associados a uma determinada arquitetura de processador.</span><span class="sxs-lookup"><span data-stu-id="c3de9-161">Specifies the registers associated with a given processor architecture.</span></span>  
  
 [<span data-ttu-id="c3de9-162">Enumeração CorDebugSetContextFlag</span><span class="sxs-lookup"><span data-stu-id="c3de9-162">CorDebugSetContextFlag Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugsetcontextflag-enumeration.md)  
 <span data-ttu-id="c3de9-163">Indica se o contexto é do quadro ativo (ou folha) na pilha ou se foi computado pelo desenrolamento de outro quadro.</span><span class="sxs-lookup"><span data-stu-id="c3de9-163">Indicates whether the context is from the active (or leaf) frame on the stack or has been computed by unwinding from another frame.</span></span>  
  
 [<span data-ttu-id="c3de9-164">Enumeração CorDebugStateChange</span><span class="sxs-lookup"><span data-stu-id="c3de9-164">CorDebugStateChange Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugstatechange-enumeration.md)  
 <span data-ttu-id="c3de9-165">Descreve a quantidade de dados armazenados em cache que devem ser descartados com base em alterações no processo.</span><span class="sxs-lookup"><span data-stu-id="c3de9-165">Describes the amount of cached data that must be discarded based on changes to the process.</span></span>  
  
 <span data-ttu-id="c3de9-166">CorDebugStepReason</span><span class="sxs-lookup"><span data-stu-id="c3de9-166">CorDebugStepReason</span></span>  
 <span data-ttu-id="c3de9-167">Indica o resultado de uma etapa individual.</span><span class="sxs-lookup"><span data-stu-id="c3de9-167">Indicates the outcome of an individual step.</span></span>  
  
 <span data-ttu-id="c3de9-168">CorDebugThreadState</span><span class="sxs-lookup"><span data-stu-id="c3de9-168">CorDebugThreadState</span></span>  
 <span data-ttu-id="c3de9-169">Especifica o estado de um thread para depuração.</span><span class="sxs-lookup"><span data-stu-id="c3de9-169">Specifies the state of a thread for debugging.</span></span>  
  
 <span data-ttu-id="c3de9-170">\>CorDebugUnmappedStop</span><span class="sxs-lookup"><span data-stu-id="c3de9-170">\>CorDebugUnmappedStop</span></span>  
 <span data-ttu-id="c3de9-171">Especifica o tipo de código não mapeado que pode disparar uma interrupção na execução do código pelo passador.</span><span class="sxs-lookup"><span data-stu-id="c3de9-171">Specifies the type of unmapped code that can trigger a halt in code execution by the stepper.</span></span>  
  
 <span data-ttu-id="c3de9-172">CorDebugUserState</span><span class="sxs-lookup"><span data-stu-id="c3de9-172">CorDebugUserState</span></span>  
 <span data-ttu-id="c3de9-173">Indica o estado do usuário de um thread.</span><span class="sxs-lookup"><span data-stu-id="c3de9-173">Indicates the user state of a thread.</span></span>  
  
 [<span data-ttu-id="c3de9-174">Enumeração CorGCReferenceType</span><span class="sxs-lookup"><span data-stu-id="c3de9-174">CorGCReferenceType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md)  
 <span data-ttu-id="c3de9-175">Identifica a fonte de um objeto para ser coletado do lixo.</span><span class="sxs-lookup"><span data-stu-id="c3de9-175">Identifies the source of an object to be garbage-collected.</span></span>  
  
 [<span data-ttu-id="c3de9-176">Enumeração ILCodeKind</span><span class="sxs-lookup"><span data-stu-id="c3de9-176">ILCodeKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md)  
 <span data-ttu-id="c3de9-177">Fornece valores que especificam se o depurador é capaz de acessar variáveis locais ou o código incluído na instrumentação ReJIT do criador de perfis.</span><span class="sxs-lookup"><span data-stu-id="c3de9-177">Provides values that specify whether the debugger is able to access local variables or code added in profiler ReJIT instrumentation.</span></span>  
  
 [<span data-ttu-id="c3de9-178">Enumeração LoggingLevelEnum</span><span class="sxs-lookup"><span data-stu-id="c3de9-178">LoggingLevelEnum Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/logginglevelenum-enumeration.md)  
 <span data-ttu-id="c3de9-179">Indica o nível de severidade de uma mensagem descritiva que é escrita no log de eventos quando um thread gerenciado registrar um evento.</span><span class="sxs-lookup"><span data-stu-id="c3de9-179">Indicates the severity level of a descriptive message that is written to the event log when a managed thread logs an event.</span></span>  
  
 [<span data-ttu-id="c3de9-180">Enumeração LogSwitchCallReason</span><span class="sxs-lookup"><span data-stu-id="c3de9-180">LogSwitchCallReason Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/logswitchcallreason-enumeration.md)  
 <span data-ttu-id="c3de9-181">Indica a operação que foi realizada em uma alternação entre depuração/rastreamento.</span><span class="sxs-lookup"><span data-stu-id="c3de9-181">Indicates the operation that was performed on a debugging/tracing switch.</span></span>  
  
 [<span data-ttu-id="c3de9-182">Enumeração VariableLocationType</span><span class="sxs-lookup"><span data-stu-id="c3de9-182">VariableLocationType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)  
 <span data-ttu-id="c3de9-183">Indica o tipo de local nativo de uma variável.</span><span class="sxs-lookup"><span data-stu-id="c3de9-183">Indicates the native location type of a variable.</span></span>  
  
 [<span data-ttu-id="c3de9-184">Enumeração WriteableMetadataUpdateMode</span><span class="sxs-lookup"><span data-stu-id="c3de9-184">WriteableMetadataUpdateMode Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/writeablemetadataupdatemode-enumeration.md)  
 <span data-ttu-id="c3de9-185">Fornece valores que especificam se as atualizações na memória para metadados estão visíveis para um depurador.</span><span class="sxs-lookup"><span data-stu-id="c3de9-185">Provides values that specify whether in-memory updates to metadata are visible to a debugger.</span></span> 

 <span data-ttu-id="c3de9-186">[Enumeração ClrDataSourceType](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md) Fornece valores que são usados pela estrutura CLRDATA_IL_ADDRESS_MAP.</span><span class="sxs-lookup"><span data-stu-id="c3de9-186">[ClrDataSourceType Enumeration](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md) Provides values that are used by the CLRDATA_IL_ADDRESS_MAP structure.</span></span>

## <a name="related-sections"></a><span data-ttu-id="c3de9-187">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="c3de9-187">Related Sections</span></span>  
 [<span data-ttu-id="c3de9-188">Depurando coclasses</span><span class="sxs-lookup"><span data-stu-id="c3de9-188">Debugging Coclasses</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [<span data-ttu-id="c3de9-189">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="c3de9-189">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
  
 [<span data-ttu-id="c3de9-190">Depurando funções estáticas globais</span><span class="sxs-lookup"><span data-stu-id="c3de9-190">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)  
  
 [<span data-ttu-id="c3de9-191">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="c3de9-191">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
