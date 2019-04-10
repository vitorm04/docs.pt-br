---
title: Método ICorDebugThread4::GetCurrentCustomDebuggerNotification
ms.date: 03/30/2017
api_name:
- ICorDebugThread4.GetCurrentCustomDebuggerNotification Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread4::GetCurrentCustomDebuggerNotification
helpviewer_keywords:
- GetCurrentCustomDebuggerNotification method [.NET Framework debugging]
- ICorDebugThread4::GetCurrentCustomDebuggerNotification method [.NET Framework debugging]
ms.assetid: 57e0f2d2-5f0e-4e2d-99ec-3f26632eb693
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f626ff6e562bd9bc94440f31e9470a45cc32cfbd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59216321"
---
# <a name="icordebugthread4getcurrentcustomdebuggernotification-method"></a><span data-ttu-id="b2745-102">Método ICorDebugThread4::GetCurrentCustomDebuggerNotification</span><span class="sxs-lookup"><span data-stu-id="b2745-102">ICorDebugThread4::GetCurrentCustomDebuggerNotification Method</span></span>

<span data-ttu-id="b2745-103">Obtém a atual [ICorDebugManagedCallback3::CustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) objeto no thread atual.</span><span class="sxs-lookup"><span data-stu-id="b2745-103">Gets the current [ICorDebugManagedCallback3::CustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) object on the current thread.</span></span>

## <a name="syntax"></a><span data-ttu-id="b2745-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b2745-104">Syntax</span></span>

```cpp
HRESULT GetCurrentCustomDebuggerNotification(
    [out] ICorDebugValue **ppNotificationObject
    );
```

## <a name="parameters"></a><span data-ttu-id="b2745-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b2745-105">Parameters</span></span>

`ppNotificationObject`\
<span data-ttu-id="b2745-106">[out] Um ponteiro para a atual `ICorDebugManagedCallback3::CustomNotification` objeto no thread atual.</span><span class="sxs-lookup"><span data-stu-id="b2745-106">[out] A pointer to the current `ICorDebugManagedCallback3::CustomNotification` object on the current thread.</span></span>

## <a name="remarks"></a><span data-ttu-id="b2745-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="b2745-107">Remarks</span></span>

<span data-ttu-id="b2745-108">O valor de `ppNotificationObject` será nulo se o método não é chamado de dentro um `ICorDebugManagedCallback3::CustomNotification` retorno de chamada, ou se não existe nenhum objeto de notificação atual.</span><span class="sxs-lookup"><span data-stu-id="b2745-108">The value of `ppNotificationObject` is null if the method is not called from within a `ICorDebugManagedCallback3::CustomNotification` callback, or if no current notification object exists.</span></span>

## <a name="requirements"></a><span data-ttu-id="b2745-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b2745-109">Requirements</span></span>

<span data-ttu-id="b2745-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2745-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="b2745-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b2745-111">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="b2745-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b2745-112">**Library:** CorGuids.lib</span></span>

**<span data-ttu-id="b2745-113">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="b2745-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]

## <a name="see-also"></a><span data-ttu-id="b2745-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b2745-114">See also</span></span>

- [<span data-ttu-id="b2745-115">Interface ICorDebugThread4</span><span class="sxs-lookup"><span data-stu-id="b2745-115">ICorDebugThread4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)
- [<span data-ttu-id="b2745-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="b2745-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="b2745-117">Depuração</span><span class="sxs-lookup"><span data-stu-id="b2745-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
