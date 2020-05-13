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
ms.openlocfilehash: 76ad1c0ac421f05cf30f6d3d1f3e65848796a0c7
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378693"
---
# <a name="icordebugthread4getcurrentcustomdebuggernotification-method"></a><span data-ttu-id="e9fd9-102">Método ICorDebugThread4::GetCurrentCustomDebuggerNotification</span><span class="sxs-lookup"><span data-stu-id="e9fd9-102">ICorDebugThread4::GetCurrentCustomDebuggerNotification Method</span></span>

<span data-ttu-id="e9fd9-103">Obtém o objeto [ICorDebugManagedCallback3:: CustomNotification](icordebugmanagedcallback3-customnotification-method.md) atual no thread atual.</span><span class="sxs-lookup"><span data-stu-id="e9fd9-103">Gets the current [ICorDebugManagedCallback3::CustomNotification](icordebugmanagedcallback3-customnotification-method.md) object on the current thread.</span></span>

## <a name="syntax"></a><span data-ttu-id="e9fd9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e9fd9-104">Syntax</span></span>

```cpp
HRESULT GetCurrentCustomDebuggerNotification(
    [out] ICorDebugValue **ppNotificationObject
    );
```

## <a name="parameters"></a><span data-ttu-id="e9fd9-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e9fd9-105">Parameters</span></span>

`ppNotificationObject`\
<span data-ttu-id="e9fd9-106">fora Um ponteiro para o `ICorDebugManagedCallback3::CustomNotification` objeto atual no thread atual.</span><span class="sxs-lookup"><span data-stu-id="e9fd9-106">[out] A pointer to the current `ICorDebugManagedCallback3::CustomNotification` object on the current thread.</span></span>

## <a name="remarks"></a><span data-ttu-id="e9fd9-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="e9fd9-107">Remarks</span></span>

<span data-ttu-id="e9fd9-108">O valor de `ppNotificationObject` será NULL se o método não for chamado de dentro de um `ICorDebugManagedCallback3::CustomNotification` retorno de chamada ou se não existir nenhum objeto de notificação atual.</span><span class="sxs-lookup"><span data-stu-id="e9fd9-108">The value of `ppNotificationObject` is null if the method is not called from within a `ICorDebugManagedCallback3::CustomNotification` callback, or if no current notification object exists.</span></span>

## <a name="requirements"></a><span data-ttu-id="e9fd9-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e9fd9-109">Requirements</span></span>

<span data-ttu-id="e9fd9-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9fd9-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="e9fd9-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e9fd9-111">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="e9fd9-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e9fd9-112">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="e9fd9-113">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9fd9-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="e9fd9-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="e9fd9-114">See also</span></span>

- [<span data-ttu-id="e9fd9-115">Interface ICorDebugThread4</span><span class="sxs-lookup"><span data-stu-id="e9fd9-115">ICorDebugThread4 Interface</span></span>](icordebugthread4-interface.md)
- [<span data-ttu-id="e9fd9-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="e9fd9-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="e9fd9-117">Depuração</span><span class="sxs-lookup"><span data-stu-id="e9fd9-117">Debugging</span></span>](index.md)
