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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f86cc83936dd8150ca6b3f28c9b6a624278e2b36
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33406263"
---
# <a name="icordebugcanlaunchorattach-method"></a><span data-ttu-id="131c8-102">Método ICorDebug::CanLaunchOrAttach</span><span class="sxs-lookup"><span data-stu-id="131c8-102">ICorDebug::CanLaunchOrAttach Method</span></span>
<span data-ttu-id="131c8-103">Retorna um HRESULT que indica se iniciar um novo processo ou anexar ao processo existente especificado é possíveis dentro do contexto da configuração do computador e o tempo de execução atual.</span><span class="sxs-lookup"><span data-stu-id="131c8-103">Returns an HRESULT that indicates whether launching a new process or attaching to the specified existing process is possible within the context of the current machine and runtime configuration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="131c8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="131c8-104">Syntax</span></span>  
  
```  
HRESULT CanLaunchOrAttach (  
    [in] DWORD      dwProcessId,  
    [in] BOOL       win32DebuggingEnabled  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="131c8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="131c8-105">Parameters</span></span>  
 `dwProcessId`  
 <span data-ttu-id="131c8-106">[in] A ID de um processo existente.</span><span class="sxs-lookup"><span data-stu-id="131c8-106">[in] The ID of an existing process.</span></span>  
  
 `win32DebuggingEnabled`  
 <span data-ttu-id="131c8-107">[in] Passar `true` se você planeja iniciar com Win32 depuração habilitada ou anexar com Win32 depuração habilitada; caso contrário, passe `false`.</span><span class="sxs-lookup"><span data-stu-id="131c8-107">[in] Pass in `true` if you plan to launch with Win32 debugging enabled, or to attach with Win32 debugging enabled; otherwise, pass `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="131c8-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="131c8-108">Return Value</span></span>  
 <span data-ttu-id="131c8-109">S_OK se os serviços de depuração determinam que iniciar um novo processo ou anexar ao processo determinado é possível, as informações sobre a configuração de máquina e tempo de execução atual.</span><span class="sxs-lookup"><span data-stu-id="131c8-109">S_OK if the debugging services determine that launching a new process or attaching to the given process is possible, given the information about the current machine and runtime configuration.</span></span> <span data-ttu-id="131c8-110">Os valores HRESULT possíveis são:</span><span class="sxs-lookup"><span data-stu-id="131c8-110">Possible HRESULT values are:</span></span>  
  
-   <span data-ttu-id="131c8-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="131c8-111">S_OK</span></span>  
  
-   <span data-ttu-id="131c8-112">CORDBG_E_DEBUGGING_NOT_POSSIBLE</span><span class="sxs-lookup"><span data-stu-id="131c8-112">CORDBG_E_DEBUGGING_NOT_POSSIBLE</span></span>  
  
-   <span data-ttu-id="131c8-113">CORDBG_E_KERNEL_DEBUGGER_PRESENT</span><span class="sxs-lookup"><span data-stu-id="131c8-113">CORDBG_E_KERNEL_DEBUGGER_PRESENT</span></span>  
  
-   <span data-ttu-id="131c8-114">CORDBG_E_KERNEL_DEBUGGER_ENABLED</span><span class="sxs-lookup"><span data-stu-id="131c8-114">CORDBG_E_KERNEL_DEBUGGER_ENABLED</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="131c8-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="131c8-115">Remarks</span></span>  
 <span data-ttu-id="131c8-116">Esse método é meramente informativo.</span><span class="sxs-lookup"><span data-stu-id="131c8-116">This method is purely informational.</span></span> <span data-ttu-id="131c8-117">A interface não irá parar de iniciar ou anexar a um processo, independentemente do valor retornado por `CanLaunchOrAttach`.</span><span class="sxs-lookup"><span data-stu-id="131c8-117">The interface will not stop you from launching or attaching to a process, regardless of the value returned by `CanLaunchOrAttach`.</span></span>  
  
 <span data-ttu-id="131c8-118">Se você planeja iniciar com Win32 depuração habilitada ou anexar com Win32 depuração habilitada, transmitir `true` para `win32DebuggingEnabled`.</span><span class="sxs-lookup"><span data-stu-id="131c8-118">If you plan to launch with Win32 debugging enabled or attach with Win32 debugging enabled, pass `true` for `win32DebuggingEnabled`.</span></span> <span data-ttu-id="131c8-119">O HRESULT retornado pelo `CanLaunchOrAttach` pode ser diferente se você usar essa opção.</span><span class="sxs-lookup"><span data-stu-id="131c8-119">The HRESULT returned by `CanLaunchOrAttach` might differ if you use this option.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="131c8-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="131c8-120">Requirements</span></span>  
 <span data-ttu-id="131c8-121">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="131c8-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="131c8-122">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="131c8-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="131c8-123">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="131c8-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="131c8-124">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="131c8-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="131c8-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="131c8-125">See Also</span></span>  
 [<span data-ttu-id="131c8-126">Interface ICorDebug</span><span class="sxs-lookup"><span data-stu-id="131c8-126">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
