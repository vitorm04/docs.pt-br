---
title: Método ICorDebug::CanLaunchOrAttach
ms.date: 03/30/2017
api_name:
- ICorDebug.CanLaunchOrAttach
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::CanLaunchOrAttach
helpviewer_keywords:
- ICorDebug::CanLaunchOrAttach method [.NET Framework debugging]
- CanLaunchOrAttach method [.NET Framework debugging]
ms.assetid: ca7723db-7c07-4cdd-bd92-fba34928b623
topic_type:
- apiref
ms.openlocfilehash: 805f9a5d1f2590a06bfa929c152bdfd13900531a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134278"
---
# <a name="icordebugcanlaunchorattach-method"></a><span data-ttu-id="a6223-102">Método ICorDebug::CanLaunchOrAttach</span><span class="sxs-lookup"><span data-stu-id="a6223-102">ICorDebug::CanLaunchOrAttach Method</span></span>
<span data-ttu-id="a6223-103">Retorna um HRESULT que indica se é possível iniciar um novo processo ou anexar ao processo existente especificado no contexto da configuração atual do computador e do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="a6223-103">Returns an HRESULT that indicates whether launching a new process or attaching to the specified existing process is possible within the context of the current machine and runtime configuration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6223-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a6223-104">Syntax</span></span>  
  
```cpp  
HRESULT CanLaunchOrAttach (  
    [in] DWORD      dwProcessId,  
    [in] BOOL       win32DebuggingEnabled  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a6223-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a6223-105">Parameters</span></span>  
 `dwProcessId`  
 <span data-ttu-id="a6223-106">no A ID de um processo existente.</span><span class="sxs-lookup"><span data-stu-id="a6223-106">[in] The ID of an existing process.</span></span>  
  
 `win32DebuggingEnabled`  
 <span data-ttu-id="a6223-107">no Passe `true` se você planeja iniciar com a depuração do Win32 habilitada ou para anexar com a depuração do Win32 habilitada; caso contrário, passe `false`.</span><span class="sxs-lookup"><span data-stu-id="a6223-107">[in] Pass in `true` if you plan to launch with Win32 debugging enabled, or to attach with Win32 debugging enabled; otherwise, pass `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a6223-108">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="a6223-108">Return Value</span></span>  
 <span data-ttu-id="a6223-109">S_OK se os serviços de depuração determinarem que a inicialização de um novo processo ou a anexação ao processo fornecido é possível, dadas as informações sobre o computador atual e a configuração de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="a6223-109">S_OK if the debugging services determine that launching a new process or attaching to the given process is possible, given the information about the current machine and runtime configuration.</span></span> <span data-ttu-id="a6223-110">Os possíveis valores HRESULT são:</span><span class="sxs-lookup"><span data-stu-id="a6223-110">Possible HRESULT values are:</span></span>  
  
- <span data-ttu-id="a6223-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="a6223-111">S_OK</span></span>  
  
- <span data-ttu-id="a6223-112">CORDBG_E_DEBUGGING_NOT_POSSIBLE</span><span class="sxs-lookup"><span data-stu-id="a6223-112">CORDBG_E_DEBUGGING_NOT_POSSIBLE</span></span>  
  
- <span data-ttu-id="a6223-113">CORDBG_E_KERNEL_DEBUGGER_PRESENT</span><span class="sxs-lookup"><span data-stu-id="a6223-113">CORDBG_E_KERNEL_DEBUGGER_PRESENT</span></span>  
  
- <span data-ttu-id="a6223-114">CORDBG_E_KERNEL_DEBUGGER_ENABLED</span><span class="sxs-lookup"><span data-stu-id="a6223-114">CORDBG_E_KERNEL_DEBUGGER_ENABLED</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a6223-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="a6223-115">Remarks</span></span>  
 <span data-ttu-id="a6223-116">Esse método é puramente informativo.</span><span class="sxs-lookup"><span data-stu-id="a6223-116">This method is purely informational.</span></span> <span data-ttu-id="a6223-117">A interface não o impedirá de iniciar ou anexar a um processo, independentemente do valor retornado por `CanLaunchOrAttach`.</span><span class="sxs-lookup"><span data-stu-id="a6223-117">The interface will not stop you from launching or attaching to a process, regardless of the value returned by `CanLaunchOrAttach`.</span></span>  
  
 <span data-ttu-id="a6223-118">Se você planeja iniciar com a depuração do Win32 habilitada ou anexar com a depuração do Win32 habilitada, passe `true` para `win32DebuggingEnabled`.</span><span class="sxs-lookup"><span data-stu-id="a6223-118">If you plan to launch with Win32 debugging enabled or attach with Win32 debugging enabled, pass `true` for `win32DebuggingEnabled`.</span></span> <span data-ttu-id="a6223-119">O HRESULT retornado por `CanLaunchOrAttach` pode ser diferente se você usar essa opção.</span><span class="sxs-lookup"><span data-stu-id="a6223-119">The HRESULT returned by `CanLaunchOrAttach` might differ if you use this option.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6223-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a6223-120">Requirements</span></span>  
 <span data-ttu-id="a6223-121">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6223-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6223-122">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a6223-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a6223-123">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a6223-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a6223-124">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6223-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6223-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a6223-125">See also</span></span>

- [<span data-ttu-id="a6223-126">Interface ICorDebug</span><span class="sxs-lookup"><span data-stu-id="a6223-126">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
