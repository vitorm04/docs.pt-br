---
title: Método ICorDebugThread::CreateStepper
ms.date: 03/30/2017
api_name:
- ICorDebugThread.CreateStepper
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::CreateStepper
helpviewer_keywords:
- ICorDebugThread::CreateStepper method [.NET Framework debugging]
- CreateStepper method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 4657443f-dd12-431b-a648-175c23f13c83
topic_type:
- apiref
ms.openlocfilehash: d1b058aef66ed32c2cadcc3cfd72320dd8eb7729
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133586"
---
# <a name="icordebugthreadcreatestepper-method"></a><span data-ttu-id="0126f-102">Método ICorDebugThread::CreateStepper</span><span class="sxs-lookup"><span data-stu-id="0126f-102">ICorDebugThread::CreateStepper Method</span></span>
<span data-ttu-id="0126f-103">Cria um objeto ICorDebugStepper que permite percorrer o quadro ativo desse ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="0126f-103">Creates an ICorDebugStepper object that allows stepping through the active frame of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0126f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0126f-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateStepper (  
    [out] ICorDebugStepper **ppStepper  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0126f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0126f-105">Parameters</span></span>  
 `ppStepper`  
 <span data-ttu-id="0126f-106">fora Um ponteiro para o endereço de um objeto de `ICorDebugStepper` que permite percorrer o quadro ativo desse thread.</span><span class="sxs-lookup"><span data-stu-id="0126f-106">[out] A pointer to the address of an `ICorDebugStepper` object that allows stepping through the active frame of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0126f-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="0126f-107">Remarks</span></span>  
 <span data-ttu-id="0126f-108">O quadro ativo pode ser um código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="0126f-108">The active frame may be unmanaged code.</span></span>  
  
 <span data-ttu-id="0126f-109">A interface `ICorDebugStepper` deve ser usada para executar a depuração real.</span><span class="sxs-lookup"><span data-stu-id="0126f-109">The `ICorDebugStepper` interface must be used to perform the actual stepping.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0126f-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0126f-110">Requirements</span></span>  
 <span data-ttu-id="0126f-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0126f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0126f-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0126f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0126f-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0126f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0126f-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0126f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
