---
title: Método ICorDebugManagedCallback::ControlCTrap
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.ControlCTrap
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::ControlCTrap
helpviewer_keywords:
- ICorDebugManagedCallback::ControlCTrap method [.NET Framework debugging]
- ControlCTrap method [.NET Framework debugging]
ms.assetid: 0500854e-2121-43d9-a028-64312da35258
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a9758de5c2801f2c55b7eca149569016ec5b9243
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugmanagedcallbackcontrolctrap-method"></a><span data-ttu-id="0f7f4-102">Método ICorDebugManagedCallback::ControlCTrap</span><span class="sxs-lookup"><span data-stu-id="0f7f4-102">ICorDebugManagedCallback::ControlCTrap Method</span></span>
<span data-ttu-id="0f7f4-103">Notifica o depurador que um CTRL + C é retido no processo que está sendo depurado.</span><span class="sxs-lookup"><span data-stu-id="0f7f4-103">Notifies the debugger that a CTRL+C is trapped in the process that is being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f7f4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0f7f4-104">Syntax</span></span>  
  
```  
HRESULT ControlCTrap (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0f7f4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0f7f4-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="0f7f4-106">[in] Um ponteiro para um objeto ICorDebugProcess que representa o processo no qual o CTRL + C é retida.</span><span class="sxs-lookup"><span data-stu-id="0f7f4-106">[in] A pointer to an ICorDebugProcess object that represents the process in which the CTRL+C is trapped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0f7f4-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="0f7f4-107">Return Value</span></span>  
  
|<span data-ttu-id="0f7f4-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0f7f4-108">HRESULT</span></span>|<span data-ttu-id="0f7f4-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="0f7f4-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0f7f4-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="0f7f4-110">S_OK</span></span>|<span data-ttu-id="0f7f4-111">O depurador tratará a interceptação CTRL + C.</span><span class="sxs-lookup"><span data-stu-id="0f7f4-111">The debugger will handle the CTRL+C trap.</span></span>|  
|<span data-ttu-id="0f7f4-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="0f7f4-112">S_FALSE</span></span>|<span data-ttu-id="0f7f4-113">O depurador não tratará a interceptação CTRL + C.</span><span class="sxs-lookup"><span data-stu-id="0f7f4-113">The debugger will not handle the CTRL+C trap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0f7f4-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="0f7f4-114">Remarks</span></span>  
 <span data-ttu-id="0f7f4-115">Todos os domínios de aplicativo dentro do processo são interrompidos para esse retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="0f7f4-115">All application domains within the process are stopped for this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f7f4-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0f7f4-116">Requirements</span></span>  
 <span data-ttu-id="0f7f4-117">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f7f4-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f7f4-118">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0f7f4-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0f7f4-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0f7f4-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0f7f4-120">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f7f4-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f7f4-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0f7f4-121">See Also</span></span>  
 [<span data-ttu-id="0f7f4-122">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="0f7f4-122">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
