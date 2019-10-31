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
ms.openlocfilehash: ba4375511fe7f5aaee032c4e132de54808041111
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122440"
---
# <a name="icordebugthread4getcurrentcustomdebuggernotification-method"></a><span data-ttu-id="3519a-102">Método ICorDebugThread4::GetCurrentCustomDebuggerNotification</span><span class="sxs-lookup"><span data-stu-id="3519a-102">ICorDebugThread4::GetCurrentCustomDebuggerNotification Method</span></span>

<span data-ttu-id="3519a-103">Obtém o objeto [ICorDebugManagedCallback3:: CustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) atual no thread atual.</span><span class="sxs-lookup"><span data-stu-id="3519a-103">Gets the current [ICorDebugManagedCallback3::CustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) object on the current thread.</span></span>

## <a name="syntax"></a><span data-ttu-id="3519a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3519a-104">Syntax</span></span>

```cpp
HRESULT GetCurrentCustomDebuggerNotification(
    [out] ICorDebugValue **ppNotificationObject
    );
```

## <a name="parameters"></a><span data-ttu-id="3519a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3519a-105">Parameters</span></span>

`ppNotificationObject`\
<span data-ttu-id="3519a-106">fora Um ponteiro para o objeto de `ICorDebugManagedCallback3::CustomNotification` atual no thread atual.</span><span class="sxs-lookup"><span data-stu-id="3519a-106">[out] A pointer to the current `ICorDebugManagedCallback3::CustomNotification` object on the current thread.</span></span>

## <a name="remarks"></a><span data-ttu-id="3519a-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="3519a-107">Remarks</span></span>

<span data-ttu-id="3519a-108">O valor de `ppNotificationObject` será nulo se o método não for chamado de dentro de um retorno de chamada `ICorDebugManagedCallback3::CustomNotification` ou se não existir nenhum objeto de notificação atual.</span><span class="sxs-lookup"><span data-stu-id="3519a-108">The value of `ppNotificationObject` is null if the method is not called from within a `ICorDebugManagedCallback3::CustomNotification` callback, or if no current notification object exists.</span></span>

## <a name="requirements"></a><span data-ttu-id="3519a-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3519a-109">Requirements</span></span>

<span data-ttu-id="3519a-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3519a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="3519a-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3519a-111">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="3519a-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3519a-112">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="3519a-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3519a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="3519a-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3519a-114">See also</span></span>

- [<span data-ttu-id="3519a-115">Interface ICorDebugThread4</span><span class="sxs-lookup"><span data-stu-id="3519a-115">ICorDebugThread4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)
- [<span data-ttu-id="3519a-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="3519a-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="3519a-117">Depuração</span><span class="sxs-lookup"><span data-stu-id="3519a-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
