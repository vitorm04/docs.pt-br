---
title: Método ICorDebugManagedCallback::Break
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.Break
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::Break
helpviewer_keywords:
- Break method [.NET Framework debugging]
- ICorDebugManagedCallback::Break method [.NET Framework debugging]
ms.assetid: 7d78a301-82b3-43b2-9d65-3cda3285ae97
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bab20301c5413f8bbe95d44b87e06d3b3870c9e7
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57377697"
---
# <a name="icordebugmanagedcallbackbreak-method"></a><span data-ttu-id="084df-102">Método ICorDebugManagedCallback::Break</span><span class="sxs-lookup"><span data-stu-id="084df-102">ICorDebugManagedCallback::Break Method</span></span>

<span data-ttu-id="084df-103">Notifica o depurador quando uma <xref:System.Reflection.Emit.OpCodes.Break> instrução no fluxo de código é executada.</span><span class="sxs-lookup"><span data-stu-id="084df-103">Notifies the debugger when a <xref:System.Reflection.Emit.OpCodes.Break> instruction in the code stream is executed.</span></span>

## <a name="syntax"></a><span data-ttu-id="084df-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="084df-104">Syntax</span></span>

```cpp
HRESULT Break (
    [in] ICorDebugAppDomain *pAppDomain,
    [in] ICorDebugThread    *thread
);
```

## <a name="parameters"></a><span data-ttu-id="084df-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="084df-105">Parameters</span></span>

`pAppDomain`\
<span data-ttu-id="084df-106">[in] Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio de aplicativo que contém a instrução break.</span><span class="sxs-lookup"><span data-stu-id="084df-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the break instruction.</span></span>

`thread`\
<span data-ttu-id="084df-107">[in] Um ponteiro para um objeto de ICorDebugThread que representa o thread que contém a instrução break.</span><span class="sxs-lookup"><span data-stu-id="084df-107">[in] A pointer to an ICorDebugThread object that represents the thread that contains the break instruction.</span></span>

## <a name="requirements"></a><span data-ttu-id="084df-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="084df-108">Requirements</span></span>

<span data-ttu-id="084df-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="084df-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="084df-110">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="084df-110">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="084df-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="084df-111">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="084df-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="084df-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="084df-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="084df-113">See also</span></span>

- [<span data-ttu-id="084df-114">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="084df-114">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)