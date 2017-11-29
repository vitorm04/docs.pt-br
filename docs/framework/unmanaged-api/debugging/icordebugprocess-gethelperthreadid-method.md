---
title: "Método ICorDebugProcess::GetHelperThreadID"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess.GetHelperThreadID
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess::GetHelperThreadID
helpviewer_keywords:
- GetHelperThreadID method [.NET Framework debugging]
- ICorDebugProcess::GetHelperThreadID method [.NET Framework debugging]
ms.assetid: 84e1e605-37c1-49a5-8e12-35db85654622
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 092e99cb1d5534cee56db08b5a2eedaaa2fc4724
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugprocessgethelperthreadid-method"></a><span data-ttu-id="88c54-102">Método ICorDebugProcess::GetHelperThreadID</span><span class="sxs-lookup"><span data-stu-id="88c54-102">ICorDebugProcess::GetHelperThreadID Method</span></span>
<span data-ttu-id="88c54-103">Obtém a ID do thread do sistema operacional (SO) do thread de auxiliar interno do depurador.</span><span class="sxs-lookup"><span data-stu-id="88c54-103">Gets the operating system (OS) thread ID of the debugger's internal helper thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88c54-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="88c54-104">Syntax</span></span>  
  
```  
HRESULT GetHelperThreadID (  
    [out] DWORD *pThreadID  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="88c54-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="88c54-105">Parameters</span></span>  
 `pThreadID`  
 <span data-ttu-id="88c54-106">[out] ID do thread de auxiliar interno do depurador do thread de um ponteiro para o sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="88c54-106">[out] A pointer to the OS thread ID of the debugger's internal helper thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="88c54-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="88c54-107">Remarks</span></span>  
 <span data-ttu-id="88c54-108">Durante a depuração gerenciado e não gerenciado, é responsabilidade do depurador para garantir que o thread com a ID especificada permanece em execução, se ele atinja um ponto de interrupção colocado pelo depurador.</span><span class="sxs-lookup"><span data-stu-id="88c54-108">During managed and unmanaged debugging, it is the debugger's responsibility to ensure that the thread with the specified ID remains running if it hits a breakpoint placed by the debugger.</span></span> <span data-ttu-id="88c54-109">Um depurador também pode querer ocultar esse thread do usuário.</span><span class="sxs-lookup"><span data-stu-id="88c54-109">A debugger may also wish to hide this thread from the user.</span></span> <span data-ttu-id="88c54-110">Se nenhum thread auxiliar ainda não existe no processo, o `GetHelperThreadID` método retorna zero em *`pThreadID`.</span><span class="sxs-lookup"><span data-stu-id="88c54-110">If no helper thread exists in the process yet, the `GetHelperThreadID` method returns zero in *`pThreadID`.</span></span>  
  
 <span data-ttu-id="88c54-111">Você não pode armazenar em cache a ID do thread do thread auxiliar, pois ele pode ser alterado ao longo do tempo.</span><span class="sxs-lookup"><span data-stu-id="88c54-111">You cannot cache the thread ID of the helper thread, because it may change over time.</span></span> <span data-ttu-id="88c54-112">Você deve consultar novamente a ID do thread em todos os eventos de interrupção.</span><span class="sxs-lookup"><span data-stu-id="88c54-112">You must re-query the thread ID at every stopping event.</span></span>  
  
 <span data-ttu-id="88c54-113">A ID do thread de thread do auxiliar do depurador estará correta em todos os não gerenciados [Icordebugmanagedcallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md) eventos, permitindo que um depurador determinar a ID do thread de seu thread auxiliar e ocultá-lo do usuário.</span><span class="sxs-lookup"><span data-stu-id="88c54-113">The thread ID of the debugger's helper thread will be correct on every unmanaged [ICorDebugManagedCallback::CreateThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md) event, thus allowing a debugger to determine the thread ID of its helper thread and hide it from the user.</span></span> <span data-ttu-id="88c54-114">Um thread que é identificado como um thread auxiliar durante um não gerenciado `ICorDebugManagedCallback::CreateThread` evento nunca será executado o código de usuário gerenciado.</span><span class="sxs-lookup"><span data-stu-id="88c54-114">A thread that is identified as a helper thread during an unmanaged `ICorDebugManagedCallback::CreateThread` event will never run managed user code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88c54-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="88c54-115">Requirements</span></span>  
 <span data-ttu-id="88c54-116">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="88c54-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88c54-117">**Cabeçalho:** CorDebug.idl.</span><span class="sxs-lookup"><span data-stu-id="88c54-117">**Header:** CorDebug.idl.</span></span> <span data-ttu-id="88c54-118">CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="88c54-118">CorDebug.h</span></span>  
  
 <span data-ttu-id="88c54-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="88c54-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="88c54-120">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88c54-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
