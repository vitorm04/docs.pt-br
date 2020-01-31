---
title: Método ICorDebugProcess::SetThreadContext
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.SetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::SetThreadContext
helpviewer_keywords:
- ICorDebugProcess::SetThreadContext method [.NET Framework debugging]
- SetThreadContext method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: a7b50175-2bf1-40be-8f65-64aec7aa1247
topic_type:
- apiref
ms.openlocfilehash: 66d544bbc0511ea76565376c8f10294f1758026b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792565"
---
# <a name="icordebugprocesssetthreadcontext-method"></a><span data-ttu-id="c0b81-102">Método ICorDebugProcess::SetThreadContext</span><span class="sxs-lookup"><span data-stu-id="c0b81-102">ICorDebugProcess::SetThreadContext Method</span></span>
<span data-ttu-id="c0b81-103">Define o contexto para o thread fornecido nesse processo.</span><span class="sxs-lookup"><span data-stu-id="c0b81-103">Sets the context for the given thread in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0b81-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c0b81-104">Syntax</span></span>  
  
```cpp  
HRESULT SetThreadContext(  
    [in] DWORD threadID,  
    [in] ULONG32 contextSize,  
    [in, length_is(contextSize), size_is(contextSize)]  
    BYTE context[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c0b81-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c0b81-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="c0b81-106">no A ID do thread para o qual definir o contexto.</span><span class="sxs-lookup"><span data-stu-id="c0b81-106">[in] The ID of the thread for which to set the context.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="c0b81-107">no O tamanho da matriz de `context`.</span><span class="sxs-lookup"><span data-stu-id="c0b81-107">[in] The size of the `context` array.</span></span>  
  
 `context`  
 <span data-ttu-id="c0b81-108">no Uma matriz de bytes que descreve o contexto do thread.</span><span class="sxs-lookup"><span data-stu-id="c0b81-108">[in] An array of bytes that describe the thread's context.</span></span>  
  
 <span data-ttu-id="c0b81-109">O contexto especifica a arquitetura do processador no qual o thread está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="c0b81-109">The context specifies the architecture of the processor on which the thread is executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c0b81-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="c0b81-110">Remarks</span></span>  
 <span data-ttu-id="c0b81-111">O depurador deve chamar esse método em vez da função de `SetThreadContext` do Win32, porque o thread pode realmente estar em um estado "seqüestrado", no qual seu contexto foi alterado temporariamente.</span><span class="sxs-lookup"><span data-stu-id="c0b81-111">The debugger should call this method rather than the Win32 `SetThreadContext` function, because the thread may actually be in a "hijacked" state, in which its context has been temporarily changed.</span></span> <span data-ttu-id="c0b81-112">Esse método deve ser usado somente quando um thread estiver em código nativo.</span><span class="sxs-lookup"><span data-stu-id="c0b81-112">This method should be used only when a thread is in native code.</span></span> <span data-ttu-id="c0b81-113">Use [ICorDebugRegisterSet](icordebugregisterset-interface.md) para threads em código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="c0b81-113">Use [ICorDebugRegisterSet](icordebugregisterset-interface.md) for threads in managed code.</span></span> <span data-ttu-id="c0b81-114">Nunca é necessário modificar o contexto de um thread durante um evento de depuração OOB (fora de banda).</span><span class="sxs-lookup"><span data-stu-id="c0b81-114">You should never need to modify the context of a thread during an out-of-band (OOB) debug event.</span></span>  
  
 <span data-ttu-id="c0b81-115">Os dados passados devem ser uma estrutura de contexto para a plataforma atual.</span><span class="sxs-lookup"><span data-stu-id="c0b81-115">The data passed must be a context structure for the current platform.</span></span>  
  
 <span data-ttu-id="c0b81-116">Esse método pode corromper o tempo de execução se for usado de forma inadequada.</span><span class="sxs-lookup"><span data-stu-id="c0b81-116">This method can corrupt the runtime if used improperly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0b81-117">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="c0b81-117">Requirements</span></span>  
 <span data-ttu-id="c0b81-118">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c0b81-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0b81-119">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c0b81-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c0b81-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c0b81-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c0b81-121">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0b81-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
