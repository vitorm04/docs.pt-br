---
title: Método ICorDebugRemote::DebugActiveProcessEx
ms.date: 03/30/2017
api_name:
- ICorDebugRemote.DebugActiveProcessEx
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemoteTarget::DebugActiveProcessEx
helpviewer_keywords:
- ICorDebugRemote::DebugActiveProcessEx method [.NET Framework debugging]
- DebugActiveProcessEx method, ICorDebugRemote interface [.NET Framework debugging]
ms.assetid: b0df5c5d-9a2e-47bf-894c-6f8a9fe24a1f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e0e3cdbff5054ec990c40c333ed4bd4029a91f12
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420798"
---
# <a name="icordebugremotedebugactiveprocessex-method"></a><span data-ttu-id="4ff1d-102">Método ICorDebugRemote::DebugActiveProcessEx</span><span class="sxs-lookup"><span data-stu-id="4ff1d-102">ICorDebugRemote::DebugActiveProcessEx Method</span></span>
<span data-ttu-id="4ff1d-103">Inicia um processo em um computador remoto sob o depurador.</span><span class="sxs-lookup"><span data-stu-id="4ff1d-103">Launches a process on a remote machine under the debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ff1d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4ff1d-104">Syntax</span></span>  
  
```  
HRESULT DebugActiveProcessEx (  
    [in]  ICorDebugRemoteTarget *   pRemoteTarget,  
    [in]  DWORD                     dwProcessId,  
    [in]  BOOL                      fWin32Attach,  
    [out] ICorDebugProcess **       ppProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4ff1d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4ff1d-105">Parameters</span></span>  
 `pRemoteTarget`  
 <span data-ttu-id="4ff1d-106">[in] Ponteiro para um [Interface ICorDebugRemoteTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md).</span><span class="sxs-lookup"><span data-stu-id="4ff1d-106">[in] Pointer to an [ICorDebugRemoteTarget Interface](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md).</span></span> <span data-ttu-id="4ff1d-107">Esse parâmetro é usado para determinar a máquina na qual o processo está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="4ff1d-107">This parameter is used to determine the machine on which the process is running.</span></span>  
  
 `id`  
 <span data-ttu-id="4ff1d-108">[in] A ID do processo ao qual o depurador será anexada.</span><span class="sxs-lookup"><span data-stu-id="4ff1d-108">[in] The ID of the process to which the debugger is to be attached.</span></span>  
  
 `win32Attach`  
 <span data-ttu-id="4ff1d-109">[in] `true` se o depurador deve se comportar conforme o depurador do Win32 para o processo e distribuir os retornos de chamada não gerenciados; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="4ff1d-109">[in] `true` if the debugger should behave as the Win32 debugger for the process and dispatch the unmanaged callbacks; otherwise, `false`.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="4ff1d-110">[out] Um ponteiro para o endereço de um objeto de "ICorDebugProcess" que representa o processo ao qual o depurador foi anexado.</span><span class="sxs-lookup"><span data-stu-id="4ff1d-110">[out] A pointer to the address of an "ICorDebugProcess" object that represents the process to which the debugger has been attached.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4ff1d-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="4ff1d-111">Return Value</span></span>  
 <span data-ttu-id="4ff1d-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="4ff1d-112">S_OK</span></span>  
 <span data-ttu-id="4ff1d-113">Anexado com êxito o processo no computador remoto.</span><span class="sxs-lookup"><span data-stu-id="4ff1d-113">Successfully attached to the process on the remote machine.</span></span>  
  
 <span data-ttu-id="4ff1d-114">E_FAIL (ou outros códigos de retorno E_)</span><span class="sxs-lookup"><span data-stu-id="4ff1d-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="4ff1d-115">Não é possível anexar ao processo no computador remoto.</span><span class="sxs-lookup"><span data-stu-id="4ff1d-115">Unable to attach to the process on the remote machine.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4ff1d-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="4ff1d-116">Remarks</span></span>  
 <span data-ttu-id="4ff1d-117">Não há suporte para a depuração de modo misto no Silverlight.</span><span class="sxs-lookup"><span data-stu-id="4ff1d-117">Mixed-mode debugging is not supported in Silverlight.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ff1d-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4ff1d-118">Requirements</span></span>  
 <span data-ttu-id="4ff1d-119">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4ff1d-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ff1d-120">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4ff1d-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4ff1d-121">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4ff1d-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4ff1d-122">**Versões do .NET framework:** 4.5, 4, 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="4ff1d-122">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ff1d-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4ff1d-123">See Also</span></span>  
 [<span data-ttu-id="4ff1d-124">Interface ICorDebugRemote</span><span class="sxs-lookup"><span data-stu-id="4ff1d-124">ICorDebugRemote Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)  
 [<span data-ttu-id="4ff1d-125">Interface ICorDebug</span><span class="sxs-lookup"><span data-stu-id="4ff1d-125">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
    
 [<span data-ttu-id="4ff1d-126">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="4ff1d-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
