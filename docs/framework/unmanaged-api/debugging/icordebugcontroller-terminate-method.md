---
title: Método ICorDebugController::Terminate
ms.date: 03/30/2017
api_name:
- ICorDebugController.Terminate
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Terminate
helpviewer_keywords:
- Terminate method, ICorDebugController interface [.NET Framework debugging]
- ICorDebugController::Terminate method [.NET Framework debugging]
ms.assetid: 4275af0c-b5a7-4e4c-97c9-7e41f36b2dd8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c7a95f09d1baebed65bae994550431d88ba0dfc9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugcontrollerterminate-method"></a><span data-ttu-id="911f0-102">Método ICorDebugController::Terminate</span><span class="sxs-lookup"><span data-stu-id="911f0-102">ICorDebugController::Terminate Method</span></span>
<span data-ttu-id="911f0-103">Encerra o processo com o código de saída especificado.</span><span class="sxs-lookup"><span data-stu-id="911f0-103">Terminates the process with the specified exit code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="911f0-104">Esse método é um wrapper para o Win32 `TerminateProcess` função.</span><span class="sxs-lookup"><span data-stu-id="911f0-104">This method is a wrapper for the Win32 `TerminateProcess` function.</span></span> <span data-ttu-id="911f0-105">Portanto, `Terminate` usa o código de saída da mesma forma que o Win32 `TerminateProcess` função utiliza.</span><span class="sxs-lookup"><span data-stu-id="911f0-105">Thus, `Terminate` uses the exit code in the same way that the Win32 `TerminateProcess` function uses it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="911f0-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="911f0-106">Syntax</span></span>  
  
```  
HRESULT Terminate (  
    [in] UINT exitCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="911f0-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="911f0-107">Parameters</span></span>  
 `exitCode`  
 <span data-ttu-id="911f0-108">[in] Um valor numérico que é o código de saída.</span><span class="sxs-lookup"><span data-stu-id="911f0-108">[in] A numeric value that is the exit code.</span></span> <span data-ttu-id="911f0-109">Os valores numéricos válidos são definidos no WinBase.</span><span class="sxs-lookup"><span data-stu-id="911f0-109">The valid numeric values are defined in Winbase.h.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="911f0-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="911f0-110">Remarks</span></span>  
 <span data-ttu-id="911f0-111">Se o processo será interrompido quando `Terminate` é chamado, o processo deve continuar usando o [Icordebugcontroller](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) método para que o depurador recebe uma confirmação do encerramento por meio de [ : Exitprocess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) ou [: Exitappdomain](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitappdomain-method.md) retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="911f0-111">If the process is stopped when `Terminate` is called, the process should be continued by using the [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) method so that the debugger receives confirmation of the termination through the [ICorDebugManagedCallback::ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) or [ICorDebugManagedCallback::ExitAppDomain](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitappdomain-method.md) callback.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="911f0-112">Este método não é implementado por um domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="911f0-112">This method is not implemented by an application domain.</span></span> <span data-ttu-id="911f0-113">Ou seja, ele não é implementado no <xref:System.AppDomain> nível.</span><span class="sxs-lookup"><span data-stu-id="911f0-113">That is, it is not implemented at the <xref:System.AppDomain> level.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="911f0-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="911f0-114">Requirements</span></span>  
 <span data-ttu-id="911f0-115">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="911f0-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="911f0-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="911f0-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="911f0-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="911f0-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="911f0-118">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="911f0-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="911f0-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="911f0-119">See Also</span></span>  
 
