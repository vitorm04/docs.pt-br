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
ms.openlocfilehash: 2b65a621541f2b4a800f6b3708a6b257374c5866
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugprocessisossuspended-method"></a><span data-ttu-id="e5518-102">Método ICorDebugProcess::IsOSSuspended</span><span class="sxs-lookup"><span data-stu-id="e5518-102">ICorDebugProcess::IsOSSuspended Method</span></span>
<span data-ttu-id="e5518-103">Obtém um valor que indica se o thread especificado foi suspenso como resultado o depurador interromper este processo.</span><span class="sxs-lookup"><span data-stu-id="e5518-103">Gets a value that indicates whether the specified thread has been suspended as a result of the debugger stopping this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5518-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e5518-104">Syntax</span></span>  
  
```  
HRESULT IsOSSuspended(  
    [in]  DWORD threadID,  
    [out] BOOL  *pbSuspended);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e5518-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e5518-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="e5518-106">[in] A ID do thread em questão.</span><span class="sxs-lookup"><span data-stu-id="e5518-106">[in] The ID of thread in question.</span></span>  
  
 `pbSuspended`  
 <span data-ttu-id="e5518-107">[out] Um ponteiro para um valor booliano que é `true` se o thread especificado tiver sido suspenso; caso contrário \*`pbSuspended` é `false`.</span><span class="sxs-lookup"><span data-stu-id="e5518-107">[out] A pointer to a Boolean value that is `true` if the specified thread has been suspended; otherwise \*`pbSuspended` is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e5518-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="e5518-108">Remarks</span></span>  
 <span data-ttu-id="e5518-109">Quando o thread especificado foi suspenso como resultado o depurador interromper este processo, Win32 do thread especificado suspender a contagem é incrementado em um.</span><span class="sxs-lookup"><span data-stu-id="e5518-109">When the specified thread has been suspended as a result of the debugger stopping this process, the specified thread's Win32 suspend count is incremented by one.</span></span> <span data-ttu-id="e5518-110">A interface do usuário do depurador (UI) poderá querer colocar essas informações em conta se ele exibe o sistema operacional (SO) suspender a contagem de thread para o usuário.</span><span class="sxs-lookup"><span data-stu-id="e5518-110">The debugger user interface (UI) may want to take this information into account if it displays the operating system (OS) suspend count of the thread to the user.</span></span>  
  
 <span data-ttu-id="e5518-111">O `IsOSSuspended` método apenas faz sentido no contexto de depuração não gerenciada.</span><span class="sxs-lookup"><span data-stu-id="e5518-111">The `IsOSSuspended` method makes sense only in the context of unmanaged debugging.</span></span> <span data-ttu-id="e5518-112">Durante a depuração gerenciada, threads são cooperativamente suspenso em vez de suspenso pelo sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="e5518-112">During managed debugging, threads are cooperatively suspended rather than OS-suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5518-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e5518-113">Requirements</span></span>  
 <span data-ttu-id="e5518-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5518-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5518-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e5518-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e5518-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e5518-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e5518-117">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5518-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
