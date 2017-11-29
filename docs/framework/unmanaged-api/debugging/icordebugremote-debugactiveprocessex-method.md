---
title: "Método ICorDebugRemote::DebugActiveProcessEx"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugRemote.DebugActiveProcessEx
api_location: CorDebug.dll
api_type: COM
f1_keywords: ICorDebugRemoteTarget::DebugActiveProcessEx
helpviewer_keywords:
- ICorDebugRemote::DebugActiveProcessEx method [.NET Framework debugging]
- DebugActiveProcessEx method, ICorDebugRemote interface [.NET Framework debugging]
ms.assetid: b0df5c5d-9a2e-47bf-894c-6f8a9fe24a1f
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6a0fe75c29334501bbccc101f5fa079501536ce5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugremotedebugactiveprocessex-method"></a><span data-ttu-id="ce7c2-102">Método ICorDebugRemote::DebugActiveProcessEx</span><span class="sxs-lookup"><span data-stu-id="ce7c2-102">ICorDebugRemote::DebugActiveProcessEx Method</span></span>
<span data-ttu-id="ce7c2-103">Inicia um processo em um computador remoto sob o depurador.</span><span class="sxs-lookup"><span data-stu-id="ce7c2-103">Launches a process on a remote machine under the debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce7c2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ce7c2-104">Syntax</span></span>  
  
```  
HRESULT DebugActiveProcessEx (  
    [in]  ICorDebugRemoteTarget *   pRemoteTarget,  
    [in]  DWORD                     dwProcessId,  
    [in]  BOOL                      fWin32Attach,  
    [out] ICorDebugProcess **       ppProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ce7c2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ce7c2-105">Parameters</span></span>  
 `pRemoteTarget`  
 <span data-ttu-id="ce7c2-106">[in] Ponteiro para um [Interface ICorDebugRemoteTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md).</span><span class="sxs-lookup"><span data-stu-id="ce7c2-106">[in] Pointer to an [ICorDebugRemoteTarget Interface](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md).</span></span> <span data-ttu-id="ce7c2-107">Esse parâmetro é usado para determinar a máquina na qual o processo está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="ce7c2-107">This parameter is used to determine the machine on which the process is running.</span></span>  
  
 `id`  
 <span data-ttu-id="ce7c2-108">[in] A ID do processo ao qual o depurador será anexada.</span><span class="sxs-lookup"><span data-stu-id="ce7c2-108">[in] The ID of the process to which the debugger is to be attached.</span></span>  
  
 `win32Attach`  
 <span data-ttu-id="ce7c2-109">[in] `true` se o depurador deve se comportar conforme o depurador do Win32 para o processo e distribuir os retornos de chamada não gerenciados; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="ce7c2-109">[in] `true` if the debugger should behave as the Win32 debugger for the process and dispatch the unmanaged callbacks; otherwise, `false`.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="ce7c2-110">[out] Um ponteiro para o endereço de um objeto de "ICorDebugProcess" que representa o processo ao qual o depurador foi anexado.</span><span class="sxs-lookup"><span data-stu-id="ce7c2-110">[out] A pointer to the address of an "ICorDebugProcess" object that represents the process to which the debugger has been attached.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ce7c2-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="ce7c2-111">Return Value</span></span>  
 <span data-ttu-id="ce7c2-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="ce7c2-112">S_OK</span></span>  
 <span data-ttu-id="ce7c2-113">Anexado com êxito o processo no computador remoto.</span><span class="sxs-lookup"><span data-stu-id="ce7c2-113">Successfully attached to the process on the remote machine.</span></span>  
  
 <span data-ttu-id="ce7c2-114">E_FAIL (ou outros códigos de retorno E_)</span><span class="sxs-lookup"><span data-stu-id="ce7c2-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="ce7c2-115">Não é possível anexar ao processo no computador remoto.</span><span class="sxs-lookup"><span data-stu-id="ce7c2-115">Unable to attach to the process on the remote machine.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ce7c2-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="ce7c2-116">Remarks</span></span>  
 <span data-ttu-id="ce7c2-117">Não há suporte para a depuração de modo misto no Silverlight.</span><span class="sxs-lookup"><span data-stu-id="ce7c2-117">Mixed-mode debugging is not supported in Silverlight.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce7c2-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ce7c2-118">Requirements</span></span>  
 <span data-ttu-id="ce7c2-119">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce7c2-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce7c2-120">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ce7c2-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ce7c2-121">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ce7c2-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ce7c2-122">**Versões do .NET framework:** 4.5, 4, 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="ce7c2-122">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce7c2-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ce7c2-123">See Also</span></span>  
 [<span data-ttu-id="ce7c2-124">Interface ICorDebugRemote</span><span class="sxs-lookup"><span data-stu-id="ce7c2-124">ICorDebugRemote Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)  
 [<span data-ttu-id="ce7c2-125">Interface ICorDebug</span><span class="sxs-lookup"><span data-stu-id="ce7c2-125">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
    
 [<span data-ttu-id="ce7c2-126">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="ce7c2-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
