---
title: Método ICorDebugProcess::GetThreadContext
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetThreadContext
helpviewer_keywords:
- ICorDebugProcess::GetThreadContext method [.NET Framework debugging]
- GetThreadContext method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: 5b132ef1-8d4b-4525-89b3-54123596c194
topic_type:
- apiref
ms.openlocfilehash: 41c5116d23655730f3586dc656aa69c8ae817b6c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792620"
---
# <a name="icordebugprocessgetthreadcontext-method"></a><span data-ttu-id="a2c40-102">Método ICorDebugProcess::GetThreadContext</span><span class="sxs-lookup"><span data-stu-id="a2c40-102">ICorDebugProcess::GetThreadContext Method</span></span>
<span data-ttu-id="a2c40-103">Obtém o contexto para o thread determinado neste processo.</span><span class="sxs-lookup"><span data-stu-id="a2c40-103">Gets the context for the given thread in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2c40-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a2c40-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadContext(  
    [in] DWORD threadID,  
    [in] ULONG32 contextSize,  
    [in, out, length_is(contextSize), size_is(contextSize)]  
    BYTE context[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a2c40-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a2c40-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="a2c40-106">no A ID do thread para o qual recuperar o contexto.</span><span class="sxs-lookup"><span data-stu-id="a2c40-106">[in] The ID of the thread for which to retrieve the context.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="a2c40-107">no O tamanho da matriz de `context`.</span><span class="sxs-lookup"><span data-stu-id="a2c40-107">[in] The size of the `context` array.</span></span>  
  
 `context`  
 <span data-ttu-id="a2c40-108">[entrada, saída] Uma matriz de bytes que descreve o contexto do thread.</span><span class="sxs-lookup"><span data-stu-id="a2c40-108">[in, out] An array of bytes that describe the thread's context.</span></span>  
  
 <span data-ttu-id="a2c40-109">O contexto especifica a arquitetura do processador no qual o thread está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="a2c40-109">The context specifies the architecture of the processor on which the thread is executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a2c40-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="a2c40-110">Remarks</span></span>  
 <span data-ttu-id="a2c40-111">O depurador deve chamar esse método em vez do método Win32 `GetThreadContext`, pois o thread pode realmente estar em um estado "seqüestrado", no qual seu contexto foi alterado temporariamente.</span><span class="sxs-lookup"><span data-stu-id="a2c40-111">The debugger should call this method rather than the Win32 `GetThreadContext` method, because the thread may actually be in a "hijacked" state, in which its context has been temporarily changed.</span></span> <span data-ttu-id="a2c40-112">Esse método deve ser usado somente quando um thread estiver em código nativo.</span><span class="sxs-lookup"><span data-stu-id="a2c40-112">This method should be used only when a thread is in native code.</span></span> <span data-ttu-id="a2c40-113">Use [ICorDebugRegisterSet](icordebugregisterset-interface.md) para threads em código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="a2c40-113">Use [ICorDebugRegisterSet](icordebugregisterset-interface.md) for threads in managed code.</span></span>  
  
 <span data-ttu-id="a2c40-114">Os dados retornados são uma estrutura de contexto para a plataforma atual.</span><span class="sxs-lookup"><span data-stu-id="a2c40-114">The data returned is a context structure for the current platform.</span></span> <span data-ttu-id="a2c40-115">Assim como ocorre com o método de `GetThreadContext` do Win32, o chamador deve inicializar o parâmetro `context` antes de chamar esse método.</span><span class="sxs-lookup"><span data-stu-id="a2c40-115">Just as with the Win32 `GetThreadContext` method, the caller should initialize the `context` parameter before calling this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2c40-116">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="a2c40-116">Requirements</span></span>  
 <span data-ttu-id="a2c40-117">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2c40-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2c40-118">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a2c40-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a2c40-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a2c40-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a2c40-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2c40-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
