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
ms.openlocfilehash: ef7619316cae46df350bd75a2c6838828f7e9c82
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67747188"
---
# <a name="icordebugregistersetgetthreadcontext-method"></a><span data-ttu-id="dbaa7-102">Método ICorDebugRegisterSet::GetThreadContext</span><span class="sxs-lookup"><span data-stu-id="dbaa7-102">ICorDebugRegisterSet::GetThreadContext Method</span></span>
<span data-ttu-id="dbaa7-103">Obtém o contexto do thread atual.</span><span class="sxs-lookup"><span data-stu-id="dbaa7-103">Gets the context of the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbaa7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dbaa7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadContext(  
    [in] ULONG32 contextSize,  
    [in, out, length_is(contextSize),  
        size_is(contextSize)] BYTE context[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dbaa7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="dbaa7-105">Parameters</span></span>  
 `contextSize`  
 <span data-ttu-id="dbaa7-106">[in] O tamanho, em bytes, da `context` matriz.</span><span class="sxs-lookup"><span data-stu-id="dbaa7-106">[in] The size, in bytes, of the `context` array.</span></span>  
  
 `context`  
 <span data-ttu-id="dbaa7-107">[no, out] Uma matriz de bytes que compõem o Win32 `CONTEXT` estrutura para a plataforma atual.</span><span class="sxs-lookup"><span data-stu-id="dbaa7-107">[in, out] An array of bytes that compose the Win32 `CONTEXT` structure for the current platform.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dbaa7-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="dbaa7-108">Remarks</span></span>  
 <span data-ttu-id="dbaa7-109">O depurador deve chamar essa função em vez do Win32 `GetThreadContext` funcionar, porque o thread pode estar em um estado "sequestrado" onde seu contexto foi alterado temporariamente.</span><span class="sxs-lookup"><span data-stu-id="dbaa7-109">The debugger should call this function instead of the Win32 `GetThreadContext` function, because the thread may be in a "hijacked" state where its context has been temporarily changed.</span></span> <span data-ttu-id="dbaa7-110">Os dados retornados são Win32 `CONTEXT` estrutura para a plataforma atual.</span><span class="sxs-lookup"><span data-stu-id="dbaa7-110">The data returned is a Win32 `CONTEXT` structure for the current platform.</span></span>  
  
 <span data-ttu-id="dbaa7-111">Para quadros de não-folha, os clientes devem verificar quais registros são válidos por meio [icordebugregisterset:: Getregistersavailable](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregistersavailable-method.md).</span><span class="sxs-lookup"><span data-stu-id="dbaa7-111">For non-leaf frames, clients should check which registers are valid by using [ICorDebugRegisterSet::GetRegistersAvailable](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregistersavailable-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dbaa7-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="dbaa7-112">Requirements</span></span>  
 <span data-ttu-id="dbaa7-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dbaa7-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dbaa7-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dbaa7-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dbaa7-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dbaa7-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dbaa7-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dbaa7-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbaa7-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dbaa7-117">See also</span></span>

- [<span data-ttu-id="dbaa7-118">Interface ICorDebugRegisterSet</span><span class="sxs-lookup"><span data-stu-id="dbaa7-118">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
- [<span data-ttu-id="dbaa7-119">Interface ICorDebugRegisterSet2</span><span class="sxs-lookup"><span data-stu-id="dbaa7-119">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
