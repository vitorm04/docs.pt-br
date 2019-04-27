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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cd5e30d08e667dcd5a8be1f9502462f28290068e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61987734"
---
# <a name="icordebugprocessgethelperthreadid-method"></a><span data-ttu-id="08cc4-102">Método ICorDebugProcess::GetHelperThreadID</span><span class="sxs-lookup"><span data-stu-id="08cc4-102">ICorDebugProcess::GetHelperThreadID Method</span></span>
<span data-ttu-id="08cc4-103">Obtém a ID do thread do sistema operacional (SO) do thread de auxiliar interno do depurador.</span><span class="sxs-lookup"><span data-stu-id="08cc4-103">Gets the operating system (OS) thread ID of the debugger's internal helper thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08cc4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="08cc4-104">Syntax</span></span>  
  
```  
HRESULT GetHelperThreadID (  
    [out] DWORD *pThreadID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="08cc4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="08cc4-105">Parameters</span></span>  
 `pThreadID`  
 <span data-ttu-id="08cc4-106">[out] ID do thread de auxiliar interno do depurador do thread de um ponteiro para o sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="08cc4-106">[out] A pointer to the OS thread ID of the debugger's internal helper thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="08cc4-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="08cc4-107">Remarks</span></span>  
 <span data-ttu-id="08cc4-108">Durante a depuração de gerenciados e não gerenciados, é responsabilidade do depurador para garantir que o thread com a ID especificada permaneça em execução, se ele atingir um ponto de interrupção colocado pelo depurador.</span><span class="sxs-lookup"><span data-stu-id="08cc4-108">During managed and unmanaged debugging, it is the debugger's responsibility to ensure that the thread with the specified ID remains running if it hits a breakpoint placed by the debugger.</span></span> <span data-ttu-id="08cc4-109">Um depurador também pode desejar ocultar esse thread do usuário.</span><span class="sxs-lookup"><span data-stu-id="08cc4-109">A debugger may also wish to hide this thread from the user.</span></span> <span data-ttu-id="08cc4-110">Se nenhum thread auxiliar ainda não existe no processo, o `GetHelperThreadID` método retorna zero em \*`pThreadID`.</span><span class="sxs-lookup"><span data-stu-id="08cc4-110">If no helper thread exists in the process yet, the `GetHelperThreadID` method returns zero in \*`pThreadID`.</span></span>  
  
 <span data-ttu-id="08cc4-111">Você não pode armazenar em cache a ID do thread do thread auxiliar, pois isso pode mudar ao longo do tempo.</span><span class="sxs-lookup"><span data-stu-id="08cc4-111">You cannot cache the thread ID of the helper thread, because it may change over time.</span></span> <span data-ttu-id="08cc4-112">Você deve consultar novamente a ID do thread em todos os eventos de interrupção.</span><span class="sxs-lookup"><span data-stu-id="08cc4-112">You must re-query the thread ID at every stopping event.</span></span>  
  
 <span data-ttu-id="08cc4-113">A ID do thread de thread do auxiliar do depurador esteja correta em todos os não gerenciados [icordebugmanagedcallback:: CreateThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md) eventos, permitindo assim que um depurador determinar a ID do thread de seu thread auxiliar e ocultá-lo do usuário.</span><span class="sxs-lookup"><span data-stu-id="08cc4-113">The thread ID of the debugger's helper thread will be correct on every unmanaged [ICorDebugManagedCallback::CreateThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md) event, thus allowing a debugger to determine the thread ID of its helper thread and hide it from the user.</span></span> <span data-ttu-id="08cc4-114">Um thread que é identificado como um thread auxiliar durante um não-gerenciado `ICorDebugManagedCallback::CreateThread` evento nunca será executado o código de usuário gerenciado.</span><span class="sxs-lookup"><span data-stu-id="08cc4-114">A thread that is identified as a helper thread during an unmanaged `ICorDebugManagedCallback::CreateThread` event will never run managed user code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08cc4-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="08cc4-115">Requirements</span></span>  
 <span data-ttu-id="08cc4-116">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08cc4-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08cc4-117">**Cabeçalho:** CorDebug.idl.</span><span class="sxs-lookup"><span data-stu-id="08cc4-117">**Header:** CorDebug.idl.</span></span> <span data-ttu-id="08cc4-118">CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="08cc4-118">CorDebug.h</span></span>  
  
 <span data-ttu-id="08cc4-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="08cc4-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="08cc4-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08cc4-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
