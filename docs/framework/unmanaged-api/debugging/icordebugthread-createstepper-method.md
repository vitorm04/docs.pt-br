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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 95a00e8646589e7897636c1698b7c2647cd233fd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771809"
---
# <a name="icordebugthreadcreatestepper-method"></a><span data-ttu-id="b2757-102">Método ICorDebugThread::CreateStepper</span><span class="sxs-lookup"><span data-stu-id="b2757-102">ICorDebugThread::CreateStepper Method</span></span>
<span data-ttu-id="b2757-103">Cria um objeto de ICorDebugStepper que permite percorrer o quadro ativo deste ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="b2757-103">Creates an ICorDebugStepper object that allows stepping through the active frame of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2757-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b2757-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateStepper (  
    [out] ICorDebugStepper **ppStepper  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b2757-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b2757-105">Parameters</span></span>  
 `ppStepper`  
 <span data-ttu-id="b2757-106">[out] Um ponteiro para o endereço de um `ICorDebugStepper` objeto que permite percorrer o quadro ativo desse thread.</span><span class="sxs-lookup"><span data-stu-id="b2757-106">[out] A pointer to the address of an `ICorDebugStepper` object that allows stepping through the active frame of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b2757-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="b2757-107">Remarks</span></span>  
 <span data-ttu-id="b2757-108">O quadro ativo pode ser o código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="b2757-108">The active frame may be unmanaged code.</span></span>  
  
 <span data-ttu-id="b2757-109">O `ICorDebugStepper` interface deve ser usada para realizar a depuração real.</span><span class="sxs-lookup"><span data-stu-id="b2757-109">The `ICorDebugStepper` interface must be used to perform the actual stepping.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2757-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b2757-110">Requirements</span></span>  
 <span data-ttu-id="b2757-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2757-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2757-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b2757-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b2757-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b2757-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b2757-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2757-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
