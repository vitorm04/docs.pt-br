---
title: Método ICorDebugProcess::GetHelperThreadID
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetHelperThreadID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetHelperThreadID
helpviewer_keywords:
- GetHelperThreadID method [.NET Framework debugging]
- ICorDebugProcess::GetHelperThreadID method [.NET Framework debugging]
ms.assetid: 84e1e605-37c1-49a5-8e12-35db85654622
topic_type:
- apiref
ms.openlocfilehash: d38a59b23d47cbaf57dc21e121d56530a514d354
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128855"
---
# <a name="icordebugprocessgethelperthreadid-method"></a><span data-ttu-id="ff4a6-102">Método ICorDebugProcess::GetHelperThreadID</span><span class="sxs-lookup"><span data-stu-id="ff4a6-102">ICorDebugProcess::GetHelperThreadID Method</span></span>
<span data-ttu-id="ff4a6-103">Obtém a ID do thread do sistema operacional (SO) do thread auxiliar interno do depurador.</span><span class="sxs-lookup"><span data-stu-id="ff4a6-103">Gets the operating system (OS) thread ID of the debugger's internal helper thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff4a6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ff4a6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHelperThreadID (  
    [out] DWORD *pThreadID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ff4a6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ff4a6-105">Parameters</span></span>  
 `pThreadID`  
 <span data-ttu-id="ff4a6-106">fora Um ponteiro para a ID de thread do sistema operacional do thread auxiliar interno do depurador.</span><span class="sxs-lookup"><span data-stu-id="ff4a6-106">[out] A pointer to the OS thread ID of the debugger's internal helper thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ff4a6-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="ff4a6-107">Remarks</span></span>  
 <span data-ttu-id="ff4a6-108">Durante a depuração gerenciada e não gerenciada, é responsabilidade do depurador garantir que o thread com a ID especificada permaneça em execução se atingir um ponto de interrupção colocado pelo depurador.</span><span class="sxs-lookup"><span data-stu-id="ff4a6-108">During managed and unmanaged debugging, it is the debugger's responsibility to ensure that the thread with the specified ID remains running if it hits a breakpoint placed by the debugger.</span></span> <span data-ttu-id="ff4a6-109">Um depurador também pode desejar ocultar esse thread do usuário.</span><span class="sxs-lookup"><span data-stu-id="ff4a6-109">A debugger may also wish to hide this thread from the user.</span></span> <span data-ttu-id="ff4a6-110">Se nenhum thread auxiliar existir no processo ainda, o método `GetHelperThreadID` retornará zero em \*`pThreadID`.</span><span class="sxs-lookup"><span data-stu-id="ff4a6-110">If no helper thread exists in the process yet, the `GetHelperThreadID` method returns zero in \*`pThreadID`.</span></span>  
  
 <span data-ttu-id="ff4a6-111">Não é possível armazenar em cache a ID do thread auxiliar, pois ela pode mudar ao longo do tempo.</span><span class="sxs-lookup"><span data-stu-id="ff4a6-111">You cannot cache the thread ID of the helper thread, because it may change over time.</span></span> <span data-ttu-id="ff4a6-112">Você deve consultar novamente a ID do thread em cada evento de parada.</span><span class="sxs-lookup"><span data-stu-id="ff4a6-112">You must re-query the thread ID at every stopping event.</span></span>  
  
 <span data-ttu-id="ff4a6-113">A ID de thread do thread auxiliar do depurador estará correta em cada evento [ICorDebugManagedCallback:: CreateThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md) não gerenciado, permitindo que um depurador determine a ID do thread do seu thread auxiliar e o oculte do usuário.</span><span class="sxs-lookup"><span data-stu-id="ff4a6-113">The thread ID of the debugger's helper thread will be correct on every unmanaged [ICorDebugManagedCallback::CreateThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md) event, thus allowing a debugger to determine the thread ID of its helper thread and hide it from the user.</span></span> <span data-ttu-id="ff4a6-114">Um thread que é identificado como um thread auxiliar durante um evento de `ICorDebugManagedCallback::CreateThread` não gerenciado nunca executará código de usuário gerenciado.</span><span class="sxs-lookup"><span data-stu-id="ff4a6-114">A thread that is identified as a helper thread during an unmanaged `ICorDebugManagedCallback::CreateThread` event will never run managed user code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff4a6-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ff4a6-115">Requirements</span></span>  
 <span data-ttu-id="ff4a6-116">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff4a6-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff4a6-117">**Cabeçalho:** CorDebug. idl.</span><span class="sxs-lookup"><span data-stu-id="ff4a6-117">**Header:** CorDebug.idl.</span></span> <span data-ttu-id="ff4a6-118">CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ff4a6-118">CorDebug.h</span></span>  
  
 <span data-ttu-id="ff4a6-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ff4a6-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ff4a6-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff4a6-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
