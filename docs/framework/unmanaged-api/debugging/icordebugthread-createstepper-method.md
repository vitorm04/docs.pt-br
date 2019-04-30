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
ms.openlocfilehash: 89182739633984011aaab3d7900d376b6db5ef99
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61987176"
---
# <a name="icordebugthreadcreatestepper-method"></a><span data-ttu-id="ef560-102">Método ICorDebugThread::CreateStepper</span><span class="sxs-lookup"><span data-stu-id="ef560-102">ICorDebugThread::CreateStepper Method</span></span>
<span data-ttu-id="ef560-103">Cria um objeto de ICorDebugStepper que permite percorrer o quadro ativo deste ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="ef560-103">Creates an ICorDebugStepper object that allows stepping through the active frame of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef560-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ef560-104">Syntax</span></span>  
  
```  
HRESULT CreateStepper (  
    [out] ICorDebugStepper **ppStepper  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ef560-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ef560-105">Parameters</span></span>  
 `ppStepper`  
 <span data-ttu-id="ef560-106">[out] Um ponteiro para o endereço de um `ICorDebugStepper` objeto que permite percorrer o quadro ativo desse thread.</span><span class="sxs-lookup"><span data-stu-id="ef560-106">[out] A pointer to the address of an `ICorDebugStepper` object that allows stepping through the active frame of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ef560-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="ef560-107">Remarks</span></span>  
 <span data-ttu-id="ef560-108">O quadro ativo pode ser o código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="ef560-108">The active frame may be unmanaged code.</span></span>  
  
 <span data-ttu-id="ef560-109">O `ICorDebugStepper` interface deve ser usada para realizar a depuração real.</span><span class="sxs-lookup"><span data-stu-id="ef560-109">The `ICorDebugStepper` interface must be used to perform the actual stepping.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef560-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ef560-110">Requirements</span></span>  
 <span data-ttu-id="ef560-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ef560-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef560-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ef560-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ef560-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ef560-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ef560-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef560-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
