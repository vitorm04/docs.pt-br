---
title: Método ICorDebugProcess::IsOSSuspended
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.IsOSSuspended
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::IsOSSuspended
helpviewer_keywords:
- IsOSSuspended method [.NET Framework debugging]
- ICorDebugProcess::IsOSSuspended method [.NET Framework debugging]
ms.assetid: 83406cb2-5797-4402-872d-89c9516aefec
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 039dc0d9befb038e643abc4e2524c133234f460b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775557"
---
# <a name="icordebugprocessisossuspended-method"></a><span data-ttu-id="5a99e-102">Método ICorDebugProcess::IsOSSuspended</span><span class="sxs-lookup"><span data-stu-id="5a99e-102">ICorDebugProcess::IsOSSuspended Method</span></span>
<span data-ttu-id="5a99e-103">Obtém um valor que indica se o thread especificado foi suspenso como resultado o depurador interromper este processo.</span><span class="sxs-lookup"><span data-stu-id="5a99e-103">Gets a value that indicates whether the specified thread has been suspended as a result of the debugger stopping this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a99e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5a99e-104">Syntax</span></span>  
  
```  
HRESULT IsOSSuspended(  
    [in]  DWORD threadID,  
    [out] BOOL  *pbSuspended);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5a99e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5a99e-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="5a99e-106">[in] A ID do thread em questão.</span><span class="sxs-lookup"><span data-stu-id="5a99e-106">[in] The ID of thread in question.</span></span>  
  
 `pbSuspended`  
 <span data-ttu-id="5a99e-107">[out] Um ponteiro para um valor booliano que será `true` se o thread especificado tiver sido suspenso; caso contrário \*`pbSuspended` é `false`.</span><span class="sxs-lookup"><span data-stu-id="5a99e-107">[out] A pointer to a Boolean value that is `true` if the specified thread has been suspended; otherwise \*`pbSuspended` is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5a99e-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="5a99e-108">Remarks</span></span>  
 <span data-ttu-id="5a99e-109">Quando o thread especificado foi suspenso como resultado o depurador interromper esse processo, a contagem de suspensões Win32 do thread especificado é incrementado em um.</span><span class="sxs-lookup"><span data-stu-id="5a99e-109">When the specified thread has been suspended as a result of the debugger stopping this process, the specified thread's Win32 suspend count is incremented by one.</span></span> <span data-ttu-id="5a99e-110">Da interface de usuário (IU) do depurador poderá querer colocar essas informações em conta se ela exibir o sistema operacional (SO) suspender a contagem do thread para o usuário.</span><span class="sxs-lookup"><span data-stu-id="5a99e-110">The debugger user interface (UI) may want to take this information into account if it displays the operating system (OS) suspend count of the thread to the user.</span></span>  
  
 <span data-ttu-id="5a99e-111">O `IsOSSuspended` método só faz sentido no contexto de depuração não gerenciada.</span><span class="sxs-lookup"><span data-stu-id="5a99e-111">The `IsOSSuspended` method makes sense only in the context of unmanaged debugging.</span></span> <span data-ttu-id="5a99e-112">Durante a depuração gerenciada, os threads são cooperativamente suspenso em vez de suspenso pelo sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="5a99e-112">During managed debugging, threads are cooperatively suspended rather than OS-suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a99e-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5a99e-113">Requirements</span></span>  
 <span data-ttu-id="5a99e-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5a99e-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a99e-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5a99e-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5a99e-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5a99e-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5a99e-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a99e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
