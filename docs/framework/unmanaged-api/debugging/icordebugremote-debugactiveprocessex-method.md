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
ms.openlocfilehash: 83cc4eadca7c337c06c5fbf9f0e74306c2b9cb99
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131282"
---
# <a name="icordebugremotedebugactiveprocessex-method"></a><span data-ttu-id="b55e4-102">Método ICorDebugRemote::DebugActiveProcessEx</span><span class="sxs-lookup"><span data-stu-id="b55e4-102">ICorDebugRemote::DebugActiveProcessEx Method</span></span>
<span data-ttu-id="b55e4-103">Inicia um processo em um computador remoto sob o depurador.</span><span class="sxs-lookup"><span data-stu-id="b55e4-103">Launches a process on a remote machine under the debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b55e4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b55e4-104">Syntax</span></span>  
  
```cpp  
HRESULT DebugActiveProcessEx (  
    [in]  ICorDebugRemoteTarget *   pRemoteTarget,  
    [in]  DWORD                     dwProcessId,  
    [in]  BOOL                      fWin32Attach,  
    [out] ICorDebugProcess **       ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b55e4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b55e4-105">Parameters</span></span>  
 `pRemoteTarget`  
 <span data-ttu-id="b55e4-106">no Ponteiro para uma [interface ICorDebugRemoteTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md).</span><span class="sxs-lookup"><span data-stu-id="b55e4-106">[in] Pointer to an [ICorDebugRemoteTarget Interface](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md).</span></span> <span data-ttu-id="b55e4-107">Esse parâmetro é usado para determinar o computador no qual o processo está em execução.</span><span class="sxs-lookup"><span data-stu-id="b55e4-107">This parameter is used to determine the machine on which the process is running.</span></span>  
  
 `id`  
 <span data-ttu-id="b55e4-108">no A ID do processo ao qual o depurador deve ser anexado.</span><span class="sxs-lookup"><span data-stu-id="b55e4-108">[in] The ID of the process to which the debugger is to be attached.</span></span>  
  
 `win32Attach`  
 <span data-ttu-id="b55e4-109">[in] `true` se o depurador deve se comportar como o depurador do Win32 para o processo e expedir os retornos de chamada não gerenciados; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="b55e4-109">[in] `true` if the debugger should behave as the Win32 debugger for the process and dispatch the unmanaged callbacks; otherwise, `false`.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="b55e4-110">fora Um ponteiro para o endereço de um objeto "ICorDebugProcess" que representa o processo ao qual o depurador foi anexado.</span><span class="sxs-lookup"><span data-stu-id="b55e4-110">[out] A pointer to the address of an "ICorDebugProcess" object that represents the process to which the debugger has been attached.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b55e4-111">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="b55e4-111">Return Value</span></span>  
 <span data-ttu-id="b55e4-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="b55e4-112">S_OK</span></span>  
 <span data-ttu-id="b55e4-113">Anexado com êxito ao processo no computador remoto.</span><span class="sxs-lookup"><span data-stu-id="b55e4-113">Successfully attached to the process on the remote machine.</span></span>  
  
 <span data-ttu-id="b55e4-114">E_FAIL (ou outros códigos de retorno de E_)</span><span class="sxs-lookup"><span data-stu-id="b55e4-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="b55e4-115">Não é possível anexar ao processo no computador remoto.</span><span class="sxs-lookup"><span data-stu-id="b55e4-115">Unable to attach to the process on the remote machine.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b55e4-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="b55e4-116">Remarks</span></span>  
 <span data-ttu-id="b55e4-117">Não há suporte para a depuração de modo misto no Silverlight.</span><span class="sxs-lookup"><span data-stu-id="b55e4-117">Mixed-mode debugging is not supported in Silverlight.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b55e4-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b55e4-118">Requirements</span></span>  
 <span data-ttu-id="b55e4-119">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b55e4-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b55e4-120">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b55e4-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b55e4-121">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b55e4-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b55e4-122">**Versões do .NET Framework:** 4,5, 4, 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="b55e4-122">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b55e4-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b55e4-123">See also</span></span>

- [<span data-ttu-id="b55e4-124">Interface ICorDebugRemote</span><span class="sxs-lookup"><span data-stu-id="b55e4-124">ICorDebugRemote Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)
- [<span data-ttu-id="b55e4-125">Interface ICorDebug</span><span class="sxs-lookup"><span data-stu-id="b55e4-125">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

- [<span data-ttu-id="b55e4-126">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="b55e4-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
