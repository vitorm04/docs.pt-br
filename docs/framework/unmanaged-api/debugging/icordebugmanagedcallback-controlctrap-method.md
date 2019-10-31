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
ms.openlocfilehash: da35db8a943fda5fb3fbf4126684bb9cb7243001
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137420"
---
# <a name="icordebugmanagedcallbackcontrolctrap-method"></a><span data-ttu-id="0855e-102">Método ICorDebugManagedCallback::ControlCTrap</span><span class="sxs-lookup"><span data-stu-id="0855e-102">ICorDebugManagedCallback::ControlCTrap Method</span></span>
<span data-ttu-id="0855e-103">Notifica o depurador de que um CTRL + C foi interceptado no processo que está sendo depurado.</span><span class="sxs-lookup"><span data-stu-id="0855e-103">Notifies the debugger that a CTRL+C is trapped in the process that is being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0855e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0855e-104">Syntax</span></span>  
  
```cpp  
HRESULT ControlCTrap (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0855e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0855e-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="0855e-106">no Um ponteiro para um objeto ICorDebugProcess que representa o processo no qual o CTRL + C é interceptado.</span><span class="sxs-lookup"><span data-stu-id="0855e-106">[in] A pointer to an ICorDebugProcess object that represents the process in which the CTRL+C is trapped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0855e-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="0855e-107">Return Value</span></span>  
  
|<span data-ttu-id="0855e-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0855e-108">HRESULT</span></span>|<span data-ttu-id="0855e-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="0855e-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0855e-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="0855e-110">S_OK</span></span>|<span data-ttu-id="0855e-111">O depurador manipulará a interceptação CTRL + C.</span><span class="sxs-lookup"><span data-stu-id="0855e-111">The debugger will handle the CTRL+C trap.</span></span>|  
|<span data-ttu-id="0855e-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="0855e-112">S_FALSE</span></span>|<span data-ttu-id="0855e-113">O depurador não tratará a interceptação CTRL + C.</span><span class="sxs-lookup"><span data-stu-id="0855e-113">The debugger will not handle the CTRL+C trap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0855e-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="0855e-114">Remarks</span></span>  
 <span data-ttu-id="0855e-115">Todos os domínios de aplicativo no processo são interrompidos para este retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="0855e-115">All application domains within the process are stopped for this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0855e-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0855e-116">Requirements</span></span>  
 <span data-ttu-id="0855e-117">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0855e-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0855e-118">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0855e-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0855e-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0855e-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0855e-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0855e-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0855e-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0855e-121">See also</span></span>

- [<span data-ttu-id="0855e-122">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="0855e-122">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
