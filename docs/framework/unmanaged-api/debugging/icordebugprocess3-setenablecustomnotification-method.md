---
title: Método ICorDebugProcess3::SetEnableCustomNotification
ms.date: 03/30/2017
api_name:
- ICorDebugProcess3.SetEnableCustomNotification Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess3::SetEnableCustomNotification
helpviewer_keywords:
- ICorDebugProcess3::SetEnableCustomNotification method [.NET Framework debugging]
- SetEnableCustomNotification method [.NET Framework debugging]
ms.assetid: afd88ee9-2589-4461-a75a-9b6fe55a2525
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7501a8a0f8368049c87b3c90e1e707e12773a853
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54531636"
---
# <a name="icordebugprocess3setenablecustomnotification-method"></a><span data-ttu-id="106e6-102">Método ICorDebugProcess3::SetEnableCustomNotification</span><span class="sxs-lookup"><span data-stu-id="106e6-102">ICorDebugProcess3::SetEnableCustomNotification Method</span></span>
<span data-ttu-id="106e6-103">Habilita e desabilita as notificações do depurador personalizados do tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="106e6-103">Enables and disables custom debugger notifications of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="106e6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="106e6-104">Syntax</span></span>  
  
```  
HRESULT SetEnableCustomNotification(ICorDebugClass * pClass,  
                                    BOOL fEnable);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="106e6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="106e6-105">Parameters</span></span>  
 `pClass`  
 <span data-ttu-id="106e6-106">[in] O tipo que especifica as notificações do depurador personalizados.</span><span class="sxs-lookup"><span data-stu-id="106e6-106">[in] The type that specifies custom debugger notifications.</span></span>  
  
 `fEnable`  
 <span data-ttu-id="106e6-107">[in] `true` para habilitar as notificações do depurador personalizados; `false` desabilitar as notificações.</span><span class="sxs-lookup"><span data-stu-id="106e6-107">[in] `true` to enable custom debugger notifications; `false` to disable notifications.</span></span> <span data-ttu-id="106e6-108">O valor padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="106e6-108">The default value is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="106e6-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="106e6-109">Remarks</span></span>  
 <span data-ttu-id="106e6-110">Quando `fEnable` é definido como `true`, chamadas para o <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> gatilho de método um [ICorDebugManagedCallback3::CustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="106e6-110">When `fEnable` is set to `true`, calls to the <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> method trigger an [ICorDebugManagedCallback3::CustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) callback.</span></span> <span data-ttu-id="106e6-111">As notificações estão desabilitadas por padrão. Portanto, o depurador deve especificar qualquer tipo de notificação, ele conhece e deseja tratar.</span><span class="sxs-lookup"><span data-stu-id="106e6-111">Notifications are disabled by default; therefore, the debugger must specify any notification types it knows about and wants to handle.</span></span> <span data-ttu-id="106e6-112">Porque o [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) classe está no escopo por domínio de aplicativo, o depurador deve chamar `SetEnableCustomNotification` para cada domínio de aplicativo no processo de se desejam receber a notificação em todo o processo.</span><span class="sxs-lookup"><span data-stu-id="106e6-112">Because the [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) class is scoped by application domain, the debugger must call `SetEnableCustomNotification` for every application domain in the process if it wants to receive the notification across the entire process.</span></span>  
  
 <span data-ttu-id="106e6-113">Começando com o [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], o somente notificação com suporte é uma notificação de dependência entre threads.</span><span class="sxs-lookup"><span data-stu-id="106e6-113">Starting with the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], the only supported notification is a cross-thread dependency notification.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="106e6-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="106e6-114">Requirements</span></span>  
 <span data-ttu-id="106e6-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="106e6-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="106e6-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="106e6-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="106e6-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="106e6-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="106e6-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="106e6-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="106e6-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="106e6-119">See also</span></span>
- [<span data-ttu-id="106e6-120">Interface ICorDebugProcess3</span><span class="sxs-lookup"><span data-stu-id="106e6-120">ICorDebugProcess3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md)
- [<span data-ttu-id="106e6-121">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="106e6-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="106e6-122">Depuração</span><span class="sxs-lookup"><span data-stu-id="106e6-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
