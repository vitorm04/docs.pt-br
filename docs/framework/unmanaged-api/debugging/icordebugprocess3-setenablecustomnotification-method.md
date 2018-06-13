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
ms.openlocfilehash: 2a84061cff7cc5dbdeba1e0e66396e04a8f345cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423150"
---
# <a name="icordebugprocess3setenablecustomnotification-method"></a><span data-ttu-id="662e0-102">Método ICorDebugProcess3::SetEnableCustomNotification</span><span class="sxs-lookup"><span data-stu-id="662e0-102">ICorDebugProcess3::SetEnableCustomNotification Method</span></span>
<span data-ttu-id="662e0-103">Ativa e desativa as notificações do depurador personalizados do tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="662e0-103">Enables and disables custom debugger notifications of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="662e0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="662e0-104">Syntax</span></span>  
  
```  
HRESULT SetEnableCustomNotification(ICorDebugClass * pClass,  
                                    BOOL fEnable);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="662e0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="662e0-105">Parameters</span></span>  
 `pClass`  
 <span data-ttu-id="662e0-106">[in] O tipo que especifica as notificações do depurador personalizados.</span><span class="sxs-lookup"><span data-stu-id="662e0-106">[in] The type that specifies custom debugger notifications.</span></span>  
  
 `fEnable`  
 <span data-ttu-id="662e0-107">[in] `true` para habilitar as notificações do depurador personalizados; `false` para desabilitar notificações.</span><span class="sxs-lookup"><span data-stu-id="662e0-107">[in] `true` to enable custom debugger notifications; `false` to disable notifications.</span></span> <span data-ttu-id="662e0-108">O valor padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="662e0-108">The default value is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="662e0-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="662e0-109">Remarks</span></span>  
 <span data-ttu-id="662e0-110">Quando `fEnable` é definido como `true`, chamadas para o <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> gatilho método um [Icordebugmanagedcallback3](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="662e0-110">When `fEnable` is set to `true`, calls to the <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> method trigger an [ICorDebugManagedCallback3::CustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) callback.</span></span> <span data-ttu-id="662e0-111">As notificações estão desabilitadas por padrão. Portanto, o depurador deve especificar quaisquer tipos de notificação, ele conhece e deseja controlar.</span><span class="sxs-lookup"><span data-stu-id="662e0-111">Notifications are disabled by default; therefore, the debugger must specify any notification types it knows about and wants to handle.</span></span> <span data-ttu-id="662e0-112">Porque o [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) classe está no escopo do domínio de aplicativo, o depurador deve chamar `SetEnableCustomNotification` para cada domínio de aplicativo do processo se deseja receber a notificação em todo o processo.</span><span class="sxs-lookup"><span data-stu-id="662e0-112">Because the [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) class is scoped by application domain, the debugger must call `SetEnableCustomNotification` for every application domain in the process if it wants to receive the notification across the entire process.</span></span>  
  
 <span data-ttu-id="662e0-113">Começando com o [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], o somente de notificação com suporte é uma notificação de dependência entre threads.</span><span class="sxs-lookup"><span data-stu-id="662e0-113">Starting with the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], the only supported notification is a cross-thread dependency notification.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="662e0-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="662e0-114">Requirements</span></span>  
 <span data-ttu-id="662e0-115">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="662e0-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="662e0-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="662e0-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="662e0-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="662e0-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="662e0-118">**Versões do .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="662e0-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="662e0-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="662e0-119">See Also</span></span>  
 [<span data-ttu-id="662e0-120">Interface ICorDebugProcess3</span><span class="sxs-lookup"><span data-stu-id="662e0-120">ICorDebugProcess3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md)  
 [<span data-ttu-id="662e0-121">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="662e0-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="662e0-122">Depuração</span><span class="sxs-lookup"><span data-stu-id="662e0-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
