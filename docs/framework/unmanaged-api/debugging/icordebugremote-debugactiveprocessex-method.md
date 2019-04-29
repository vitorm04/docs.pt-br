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
ms.openlocfilehash: 45b919d90454c9424cadb1d4dfc3b0dfb09e5053
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61782766"
---
# <a name="icordebugremotedebugactiveprocessex-method"></a><span data-ttu-id="8496f-102">Método ICorDebugRemote::DebugActiveProcessEx</span><span class="sxs-lookup"><span data-stu-id="8496f-102">ICorDebugRemote::DebugActiveProcessEx Method</span></span>
<span data-ttu-id="8496f-103">Inicia um processo em um computador remoto sob o depurador.</span><span class="sxs-lookup"><span data-stu-id="8496f-103">Launches a process on a remote machine under the debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8496f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8496f-104">Syntax</span></span>  
  
```  
HRESULT DebugActiveProcessEx (  
    [in]  ICorDebugRemoteTarget *   pRemoteTarget,  
    [in]  DWORD                     dwProcessId,  
    [in]  BOOL                      fWin32Attach,  
    [out] ICorDebugProcess **       ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8496f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8496f-105">Parameters</span></span>  
 `pRemoteTarget`  
 <span data-ttu-id="8496f-106">[in] Ponteiro para um [Interface ICorDebugRemoteTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md).</span><span class="sxs-lookup"><span data-stu-id="8496f-106">[in] Pointer to an [ICorDebugRemoteTarget Interface](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md).</span></span> <span data-ttu-id="8496f-107">Esse parâmetro é usado para determinar a máquina na qual o processo está em execução.</span><span class="sxs-lookup"><span data-stu-id="8496f-107">This parameter is used to determine the machine on which the process is running.</span></span>  
  
 `id`  
 <span data-ttu-id="8496f-108">[in] A ID do processo ao qual o depurador deve ser anexado.</span><span class="sxs-lookup"><span data-stu-id="8496f-108">[in] The ID of the process to which the debugger is to be attached.</span></span>  
  
 `win32Attach`  
 <span data-ttu-id="8496f-109">[in] `true` se o depurador deve se comportar como o depurador do Win32 para o processo e expedir os retornos de chamada não gerenciados; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="8496f-109">[in] `true` if the debugger should behave as the Win32 debugger for the process and dispatch the unmanaged callbacks; otherwise, `false`.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="8496f-110">[out] Um ponteiro para o endereço de um objeto de "ICorDebugProcess" que representa o processo ao qual o depurador foi anexado.</span><span class="sxs-lookup"><span data-stu-id="8496f-110">[out] A pointer to the address of an "ICorDebugProcess" object that represents the process to which the debugger has been attached.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8496f-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="8496f-111">Return Value</span></span>  
 <span data-ttu-id="8496f-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="8496f-112">S_OK</span></span>  
 <span data-ttu-id="8496f-113">Anexado com êxito o processo no computador remoto.</span><span class="sxs-lookup"><span data-stu-id="8496f-113">Successfully attached to the process on the remote machine.</span></span>  
  
 <span data-ttu-id="8496f-114">E_FAIL (ou outros códigos de retorno e _)</span><span class="sxs-lookup"><span data-stu-id="8496f-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="8496f-115">Não é possível anexar ao processo no computador remoto.</span><span class="sxs-lookup"><span data-stu-id="8496f-115">Unable to attach to the process on the remote machine.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8496f-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="8496f-116">Remarks</span></span>  
 <span data-ttu-id="8496f-117">Não há suporte para a depuração de modo misto no Silverlight.</span><span class="sxs-lookup"><span data-stu-id="8496f-117">Mixed-mode debugging is not supported in Silverlight.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8496f-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8496f-118">Requirements</span></span>  
 <span data-ttu-id="8496f-119">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8496f-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8496f-120">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8496f-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8496f-121">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8496f-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8496f-122">**Versões do .NET framework:** 4.5, 4, 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="8496f-122">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8496f-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8496f-123">See also</span></span>

- [<span data-ttu-id="8496f-124">Interface ICorDebugRemote</span><span class="sxs-lookup"><span data-stu-id="8496f-124">ICorDebugRemote Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)
- [<span data-ttu-id="8496f-125">Interface ICorDebug</span><span class="sxs-lookup"><span data-stu-id="8496f-125">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

- [<span data-ttu-id="8496f-126">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="8496f-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
