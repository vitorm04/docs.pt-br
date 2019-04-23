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
ms.openlocfilehash: c4c8dd8795fc3699176490ea0bb9b2e999038afb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59124872"
---
# <a name="icordebugcontrollerterminate-method"></a><span data-ttu-id="c6e1f-102">Método ICorDebugController::Terminate</span><span class="sxs-lookup"><span data-stu-id="c6e1f-102">ICorDebugController::Terminate Method</span></span>
<span data-ttu-id="c6e1f-103">Encerra o processo com o código de saída especificado.</span><span class="sxs-lookup"><span data-stu-id="c6e1f-103">Terminates the process with the specified exit code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c6e1f-104">Esse método é um wrapper do Win32 `TerminateProcess` função.</span><span class="sxs-lookup"><span data-stu-id="c6e1f-104">This method is a wrapper for the Win32 `TerminateProcess` function.</span></span> <span data-ttu-id="c6e1f-105">Portanto, `Terminate` usa o código de saída da mesma forma que o Win32 `TerminateProcess` função utiliza.</span><span class="sxs-lookup"><span data-stu-id="c6e1f-105">Thus, `Terminate` uses the exit code in the same way that the Win32 `TerminateProcess` function uses it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6e1f-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c6e1f-106">Syntax</span></span>  
  
```  
HRESULT Terminate (  
    [in] UINT exitCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c6e1f-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c6e1f-107">Parameters</span></span>  
 `exitCode`  
 <span data-ttu-id="c6e1f-108">[in] Um valor numérico que é o código de saída.</span><span class="sxs-lookup"><span data-stu-id="c6e1f-108">[in] A numeric value that is the exit code.</span></span> <span data-ttu-id="c6e1f-109">Os valores numéricos válidos são definidos em Winbase.</span><span class="sxs-lookup"><span data-stu-id="c6e1f-109">The valid numeric values are defined in Winbase.h.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c6e1f-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="c6e1f-110">Remarks</span></span>  
 <span data-ttu-id="c6e1f-111">Se o processo é interrompido quando `Terminate` é chamado, o processo deve ser continuado, usando o [icordebugcontroller:: continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) método para que o depurador recebe uma confirmação do encerramento por meio do [ Icordebugmanagedcallback:: Exitprocess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) ou [icordebugmanagedcallback:: Exitappdomain](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitappdomain-method.md) retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="c6e1f-111">If the process is stopped when `Terminate` is called, the process should be continued by using the [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) method so that the debugger receives confirmation of the termination through the [ICorDebugManagedCallback::ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) or [ICorDebugManagedCallback::ExitAppDomain](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitappdomain-method.md) callback.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c6e1f-112">Este método não é implementado por um domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c6e1f-112">This method is not implemented by an application domain.</span></span> <span data-ttu-id="c6e1f-113">Ou seja, ele não está implementado de <xref:System.AppDomain> nível.</span><span class="sxs-lookup"><span data-stu-id="c6e1f-113">That is, it is not implemented at the <xref:System.AppDomain> level.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6e1f-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c6e1f-114">Requirements</span></span>  
 <span data-ttu-id="c6e1f-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c6e1f-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6e1f-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c6e1f-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c6e1f-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c6e1f-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c6e1f-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6e1f-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6e1f-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c6e1f-119">See also</span></span>
