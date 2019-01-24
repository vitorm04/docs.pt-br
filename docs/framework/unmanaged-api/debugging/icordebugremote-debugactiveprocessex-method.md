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
ms.openlocfilehash: eb085cc486c307a308258709f4c58619597bc202
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54608382"
---
# <a name="icordebugremotedebugactiveprocessex-method"></a><span data-ttu-id="61972-102">Método ICorDebugRemote::DebugActiveProcessEx</span><span class="sxs-lookup"><span data-stu-id="61972-102">ICorDebugRemote::DebugActiveProcessEx Method</span></span>
<span data-ttu-id="61972-103">Inicia um processo em um computador remoto sob o depurador.</span><span class="sxs-lookup"><span data-stu-id="61972-103">Launches a process on a remote machine under the debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61972-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="61972-104">Syntax</span></span>  
  
```  
HRESULT DebugActiveProcessEx (  
    [in]  ICorDebugRemoteTarget *   pRemoteTarget,  
    [in]  DWORD                     dwProcessId,  
    [in]  BOOL                      fWin32Attach,  
    [out] ICorDebugProcess **       ppProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="61972-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="61972-105">Parameters</span></span>  
 `pRemoteTarget`  
 <span data-ttu-id="61972-106">[in] Ponteiro para um [Interface ICorDebugRemoteTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md).</span><span class="sxs-lookup"><span data-stu-id="61972-106">[in] Pointer to an [ICorDebugRemoteTarget Interface](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md).</span></span> <span data-ttu-id="61972-107">Esse parâmetro é usado para determinar a máquina na qual o processo está em execução.</span><span class="sxs-lookup"><span data-stu-id="61972-107">This parameter is used to determine the machine on which the process is running.</span></span>  
  
 `id`  
 <span data-ttu-id="61972-108">[in] A ID do processo ao qual o depurador deve ser anexado.</span><span class="sxs-lookup"><span data-stu-id="61972-108">[in] The ID of the process to which the debugger is to be attached.</span></span>  
  
 `win32Attach`  
 <span data-ttu-id="61972-109">[in] `true` se o depurador deve se comportar como o depurador do Win32 para o processo e expedir os retornos de chamada não gerenciados; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="61972-109">[in] `true` if the debugger should behave as the Win32 debugger for the process and dispatch the unmanaged callbacks; otherwise, `false`.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="61972-110">[out] Um ponteiro para o endereço de um objeto de "ICorDebugProcess" que representa o processo ao qual o depurador foi anexado.</span><span class="sxs-lookup"><span data-stu-id="61972-110">[out] A pointer to the address of an "ICorDebugProcess" object that represents the process to which the debugger has been attached.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="61972-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="61972-111">Return Value</span></span>  
 <span data-ttu-id="61972-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="61972-112">S_OK</span></span>  
 <span data-ttu-id="61972-113">Anexado com êxito o processo no computador remoto.</span><span class="sxs-lookup"><span data-stu-id="61972-113">Successfully attached to the process on the remote machine.</span></span>  
  
 <span data-ttu-id="61972-114">E_FAIL (ou outros códigos de retorno e _)</span><span class="sxs-lookup"><span data-stu-id="61972-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="61972-115">Não é possível anexar ao processo no computador remoto.</span><span class="sxs-lookup"><span data-stu-id="61972-115">Unable to attach to the process on the remote machine.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="61972-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="61972-116">Remarks</span></span>  
 <span data-ttu-id="61972-117">Não há suporte para a depuração de modo misto no Silverlight.</span><span class="sxs-lookup"><span data-stu-id="61972-117">Mixed-mode debugging is not supported in Silverlight.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61972-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="61972-118">Requirements</span></span>  
 <span data-ttu-id="61972-119">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61972-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61972-120">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="61972-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="61972-121">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="61972-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="61972-122">**Versões do .NET framework:** 4.5, 4, 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="61972-122">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61972-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="61972-123">See also</span></span>
- [<span data-ttu-id="61972-124">Interface ICorDebugRemote</span><span class="sxs-lookup"><span data-stu-id="61972-124">ICorDebugRemote Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)
- [<span data-ttu-id="61972-125">Interface ICorDebug</span><span class="sxs-lookup"><span data-stu-id="61972-125">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

- [<span data-ttu-id="61972-126">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="61972-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
