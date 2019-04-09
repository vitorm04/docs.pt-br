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
ms.openlocfilehash: 7f4794fb0383435f828626497036ad3458df2173
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59204985"
---
# <a name="icordebugmanagedcallbackcontrolctrap-method"></a><span data-ttu-id="4c0b0-102">Método ICorDebugManagedCallback::ControlCTrap</span><span class="sxs-lookup"><span data-stu-id="4c0b0-102">ICorDebugManagedCallback::ControlCTrap Method</span></span>
<span data-ttu-id="4c0b0-103">Notifica o depurador que um CTRL + C é interceptado no processo que está sendo depurado.</span><span class="sxs-lookup"><span data-stu-id="4c0b0-103">Notifies the debugger that a CTRL+C is trapped in the process that is being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c0b0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4c0b0-104">Syntax</span></span>  
  
```  
HRESULT ControlCTrap (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4c0b0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4c0b0-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="4c0b0-106">[in] Um ponteiro para um objeto ICorDebugProcess que representa o processo no qual o CTRL + C é interceptada.</span><span class="sxs-lookup"><span data-stu-id="4c0b0-106">[in] A pointer to an ICorDebugProcess object that represents the process in which the CTRL+C is trapped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4c0b0-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="4c0b0-107">Return Value</span></span>  
  
|<span data-ttu-id="4c0b0-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4c0b0-108">HRESULT</span></span>|<span data-ttu-id="4c0b0-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="4c0b0-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4c0b0-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="4c0b0-110">S_OK</span></span>|<span data-ttu-id="4c0b0-111">O depurador irá manipular a interceptação CTRL + C.</span><span class="sxs-lookup"><span data-stu-id="4c0b0-111">The debugger will handle the CTRL+C trap.</span></span>|  
|<span data-ttu-id="4c0b0-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="4c0b0-112">S_FALSE</span></span>|<span data-ttu-id="4c0b0-113">O depurador não manipulará a interceptação CTRL + C.</span><span class="sxs-lookup"><span data-stu-id="4c0b0-113">The debugger will not handle the CTRL+C trap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4c0b0-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="4c0b0-114">Remarks</span></span>  
 <span data-ttu-id="4c0b0-115">Todos os domínios de aplicativo dentro do processo são interrompidos para esse retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="4c0b0-115">All application domains within the process are stopped for this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c0b0-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4c0b0-116">Requirements</span></span>  
 <span data-ttu-id="4c0b0-117">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c0b0-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c0b0-118">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4c0b0-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4c0b0-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4c0b0-119">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="4c0b0-120">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="4c0b0-120">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4c0b0-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4c0b0-121">See also</span></span>

- [<span data-ttu-id="4c0b0-122">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="4c0b0-122">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
