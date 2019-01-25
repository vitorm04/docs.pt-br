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
ms.openlocfilehash: 668b3849af9be24e019dc472a0b80067f0e1e0c1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54612730"
---
# <a name="icordebugregistersetgetthreadcontext-method"></a><span data-ttu-id="7b5fa-102">Método ICorDebugRegisterSet::GetThreadContext</span><span class="sxs-lookup"><span data-stu-id="7b5fa-102">ICorDebugRegisterSet::GetThreadContext Method</span></span>
<span data-ttu-id="7b5fa-103">Obtém o contexto do thread atual.</span><span class="sxs-lookup"><span data-stu-id="7b5fa-103">Gets the context of the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b5fa-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7b5fa-104">Syntax</span></span>  
  
```  
HRESULT GetThreadContext(  
    [in] ULONG32 contextSize,  
    [in, out, length_is(contextSize),  
        size_is(contextSize)] BYTE context[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7b5fa-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7b5fa-105">Parameters</span></span>  
 `contextSize`  
 <span data-ttu-id="7b5fa-106">[in] O tamanho, em bytes, da `context` matriz.</span><span class="sxs-lookup"><span data-stu-id="7b5fa-106">[in] The size, in bytes, of the `context` array.</span></span>  
  
 `context`  
 <span data-ttu-id="7b5fa-107">[no, out] Uma matriz de bytes que compõem o Win32 `CONTEXT` estrutura para a plataforma atual.</span><span class="sxs-lookup"><span data-stu-id="7b5fa-107">[in, out] An array of bytes that compose the Win32 `CONTEXT` structure for the current platform.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7b5fa-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="7b5fa-108">Remarks</span></span>  
 <span data-ttu-id="7b5fa-109">O depurador deve chamar essa função em vez do Win32 `GetThreadContext` funcionar, porque o thread pode estar em um estado "sequestrado" onde seu contexto foi alterado temporariamente.</span><span class="sxs-lookup"><span data-stu-id="7b5fa-109">The debugger should call this function instead of the Win32 `GetThreadContext` function, because the thread may be in a "hijacked" state where its context has been temporarily changed.</span></span> <span data-ttu-id="7b5fa-110">Os dados retornados são Win32 `CONTEXT` estrutura para a plataforma atual.</span><span class="sxs-lookup"><span data-stu-id="7b5fa-110">The data returned is a Win32 `CONTEXT` structure for the current platform.</span></span>  
  
 <span data-ttu-id="7b5fa-111">Para quadros de não-folha, os clientes devem verificar quais registros são válidos por meio [icordebugregisterset:: Getregistersavailable](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregistersavailable-method.md).</span><span class="sxs-lookup"><span data-stu-id="7b5fa-111">For non-leaf frames, clients should check which registers are valid by using [ICorDebugRegisterSet::GetRegistersAvailable](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregistersavailable-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b5fa-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7b5fa-112">Requirements</span></span>  
 <span data-ttu-id="7b5fa-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b5fa-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b5fa-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7b5fa-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7b5fa-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7b5fa-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7b5fa-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b5fa-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b5fa-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7b5fa-117">See also</span></span>
- [<span data-ttu-id="7b5fa-118">Interface ICorDebugRegisterSet</span><span class="sxs-lookup"><span data-stu-id="7b5fa-118">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
- [<span data-ttu-id="7b5fa-119">Interface ICorDebugRegisterSet2</span><span class="sxs-lookup"><span data-stu-id="7b5fa-119">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
