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
ms.openlocfilehash: 21da69d4bff0f17eb607dda45fb7dbafea8c59f7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128765"
---
# <a name="icordebugprocessisossuspended-method"></a><span data-ttu-id="e0117-102">Método ICorDebugProcess::IsOSSuspended</span><span class="sxs-lookup"><span data-stu-id="e0117-102">ICorDebugProcess::IsOSSuspended Method</span></span>
<span data-ttu-id="e0117-103">Obtém um valor que indica se o thread especificado foi suspenso como resultado do depurador parar esse processo.</span><span class="sxs-lookup"><span data-stu-id="e0117-103">Gets a value that indicates whether the specified thread has been suspended as a result of the debugger stopping this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0117-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e0117-104">Syntax</span></span>  
  
```cpp  
HRESULT IsOSSuspended(  
    [in]  DWORD threadID,  
    [out] BOOL  *pbSuspended);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e0117-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e0117-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="e0117-106">no A ID do thread em questão.</span><span class="sxs-lookup"><span data-stu-id="e0117-106">[in] The ID of thread in question.</span></span>  
  
 `pbSuspended`  
 <span data-ttu-id="e0117-107">fora Um ponteiro para um valor booliano `true` se o thread especificado tiver sido suspenso; caso contrário, \*`pbSuspended` será `false`.</span><span class="sxs-lookup"><span data-stu-id="e0117-107">[out] A pointer to a Boolean value that is `true` if the specified thread has been suspended; otherwise \*`pbSuspended` is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e0117-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="e0117-108">Remarks</span></span>  
 <span data-ttu-id="e0117-109">Quando o thread especificado tiver sido suspenso como resultado do depurador parar esse processo, a contagem de suspensões do Win32 do thread especificado será incrementada em um.</span><span class="sxs-lookup"><span data-stu-id="e0117-109">When the specified thread has been suspended as a result of the debugger stopping this process, the specified thread's Win32 suspend count is incremented by one.</span></span> <span data-ttu-id="e0117-110">A interface do usuário do depurador pode querer levar essas informações em conta se ele exibir a contagem de suspensões do sistema operacional (SO) do thread para o usuário.</span><span class="sxs-lookup"><span data-stu-id="e0117-110">The debugger user interface (UI) may want to take this information into account if it displays the operating system (OS) suspend count of the thread to the user.</span></span>  
  
 <span data-ttu-id="e0117-111">O método `IsOSSuspended` faz sentido apenas no contexto de depuração não gerenciada.</span><span class="sxs-lookup"><span data-stu-id="e0117-111">The `IsOSSuspended` method makes sense only in the context of unmanaged debugging.</span></span> <span data-ttu-id="e0117-112">Durante a depuração gerenciada, OS threads são suspensos de cooperabilidade em vez do so suspenso.</span><span class="sxs-lookup"><span data-stu-id="e0117-112">During managed debugging, threads are cooperatively suspended rather than OS-suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0117-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e0117-113">Requirements</span></span>  
 <span data-ttu-id="e0117-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0117-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0117-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e0117-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e0117-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e0117-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e0117-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0117-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
