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
ms.openlocfilehash: a8a377074ca1005ad8089dfd8e2a6a464bb86f60
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791361"
---
# <a name="icordebugthread4getcurrentcustomdebuggernotification-method"></a><span data-ttu-id="480e6-102">Método ICorDebugThread4::GetCurrentCustomDebuggerNotification</span><span class="sxs-lookup"><span data-stu-id="480e6-102">ICorDebugThread4::GetCurrentCustomDebuggerNotification Method</span></span>

<span data-ttu-id="480e6-103">Obtém o objeto [ICorDebugManagedCallback3:: CustomNotification](icordebugmanagedcallback3-customnotification-method.md) atual no thread atual.</span><span class="sxs-lookup"><span data-stu-id="480e6-103">Gets the current [ICorDebugManagedCallback3::CustomNotification](icordebugmanagedcallback3-customnotification-method.md) object on the current thread.</span></span>

## <a name="syntax"></a><span data-ttu-id="480e6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="480e6-104">Syntax</span></span>

```cpp
HRESULT GetCurrentCustomDebuggerNotification(
    [out] ICorDebugValue **ppNotificationObject
    );
```

## <a name="parameters"></a><span data-ttu-id="480e6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="480e6-105">Parameters</span></span>

`ppNotificationObject`\
<span data-ttu-id="480e6-106">fora Um ponteiro para o objeto de `ICorDebugManagedCallback3::CustomNotification` atual no thread atual.</span><span class="sxs-lookup"><span data-stu-id="480e6-106">[out] A pointer to the current `ICorDebugManagedCallback3::CustomNotification` object on the current thread.</span></span>

## <a name="remarks"></a><span data-ttu-id="480e6-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="480e6-107">Remarks</span></span>

<span data-ttu-id="480e6-108">O valor de `ppNotificationObject` será nulo se o método não for chamado de dentro de um retorno de chamada `ICorDebugManagedCallback3::CustomNotification` ou se não existir nenhum objeto de notificação atual.</span><span class="sxs-lookup"><span data-stu-id="480e6-108">The value of `ppNotificationObject` is null if the method is not called from within a `ICorDebugManagedCallback3::CustomNotification` callback, or if no current notification object exists.</span></span>

## <a name="requirements"></a><span data-ttu-id="480e6-109">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="480e6-109">Requirements</span></span>

<span data-ttu-id="480e6-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="480e6-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="480e6-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="480e6-111">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="480e6-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="480e6-112">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="480e6-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="480e6-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="480e6-114">Veja também</span><span class="sxs-lookup"><span data-stu-id="480e6-114">See also</span></span>

- [<span data-ttu-id="480e6-115">Interface ICorDebugThread4</span><span class="sxs-lookup"><span data-stu-id="480e6-115">ICorDebugThread4 Interface</span></span>](icordebugthread4-interface.md)
- [<span data-ttu-id="480e6-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="480e6-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="480e6-117">Depuração</span><span class="sxs-lookup"><span data-stu-id="480e6-117">Debugging</span></span>](index.md)
