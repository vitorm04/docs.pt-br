---
title: Método ICorDebugRegisterSet::GetThreadContext
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.GetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::GetThreadContext
helpviewer_keywords:
- GetThreadContext method, ICorDebugRegisterSet interface [.NET Framework debugging]
- ICorDebugRegisterSet::GetThreadContext method [.NET Framework debugging]
ms.assetid: 0f63400b-dc1c-48d6-b51a-75c3f7f28e03
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 632d3912bae28da22e701078bb47d2d8dbfd3644
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423397"
---
# <a name="icordebugregistersetgetthreadcontext-method"></a><span data-ttu-id="14017-102">Método ICorDebugRegisterSet::GetThreadContext</span><span class="sxs-lookup"><span data-stu-id="14017-102">ICorDebugRegisterSet::GetThreadContext Method</span></span>
<span data-ttu-id="14017-103">Obtém o contexto do thread atual.</span><span class="sxs-lookup"><span data-stu-id="14017-103">Gets the context of the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14017-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="14017-104">Syntax</span></span>  
  
```  
HRESULT GetThreadContext(  
    [in] ULONG32 contextSize,  
    [in, out, length_is(contextSize),  
        size_is(contextSize)] BYTE context[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="14017-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="14017-105">Parameters</span></span>  
 `contextSize`  
 <span data-ttu-id="14017-106">[in] O tamanho, em bytes, do `context` matriz.</span><span class="sxs-lookup"><span data-stu-id="14017-106">[in] The size, in bytes, of the `context` array.</span></span>  
  
 `context`  
 <span data-ttu-id="14017-107">[out no] Uma matriz de bytes que compõem o Win32 `CONTEXT` estrutura para a plataforma atual.</span><span class="sxs-lookup"><span data-stu-id="14017-107">[in, out] An array of bytes that compose the Win32 `CONTEXT` structure for the current platform.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="14017-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="14017-108">Remarks</span></span>  
 <span data-ttu-id="14017-109">O depurador deve chamar essa função em vez do Win32 `GetThreadContext` funcionar, porque o thread pode estar em um estado "capturado" onde seu contexto foi alterado temporariamente.</span><span class="sxs-lookup"><span data-stu-id="14017-109">The debugger should call this function instead of the Win32 `GetThreadContext` function, because the thread may be in a "hijacked" state where its context has been temporarily changed.</span></span> <span data-ttu-id="14017-110">Os dados retornados são Win32 `CONTEXT` estrutura para a plataforma atual.</span><span class="sxs-lookup"><span data-stu-id="14017-110">The data returned is a Win32 `CONTEXT` structure for the current platform.</span></span>  
  
 <span data-ttu-id="14017-111">Para os quadros de não-folha, os clientes devem verificar quais registros são válidos usando [: Getregistersavailable](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregistersavailable-method.md).</span><span class="sxs-lookup"><span data-stu-id="14017-111">For non-leaf frames, clients should check which registers are valid by using [ICorDebugRegisterSet::GetRegistersAvailable](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregistersavailable-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14017-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="14017-112">Requirements</span></span>  
 <span data-ttu-id="14017-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14017-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14017-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="14017-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="14017-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="14017-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="14017-116">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14017-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14017-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="14017-117">See Also</span></span>  
 [<span data-ttu-id="14017-118">Interface ICorDebugRegisterSet</span><span class="sxs-lookup"><span data-stu-id="14017-118">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)  
 [<span data-ttu-id="14017-119">Interface ICorDebugRegisterSet2</span><span class="sxs-lookup"><span data-stu-id="14017-119">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
