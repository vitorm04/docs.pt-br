---
title: "Método ICorDebugThread::CreateStepper"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread.CreateStepper
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread::CreateStepper
helpviewer_keywords:
- ICorDebugThread::CreateStepper method [.NET Framework debugging]
- CreateStepper method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 4657443f-dd12-431b-a648-175c23f13c83
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b66c3e536104a46b65c92fe038fb5a92d79db299
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugthreadcreatestepper-method"></a><span data-ttu-id="f2c08-102">Método ICorDebugThread::CreateStepper</span><span class="sxs-lookup"><span data-stu-id="f2c08-102">ICorDebugThread::CreateStepper Method</span></span>
<span data-ttu-id="f2c08-103">Cria um objeto de ICorDebugStepper que permite percorrer o quadro ativo desse ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="f2c08-103">Creates an ICorDebugStepper object that allows stepping through the active frame of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2c08-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f2c08-104">Syntax</span></span>  
  
```  
HRESULT CreateStepper (  
    [out] ICorDebugStepper **ppStepper  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f2c08-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f2c08-105">Parameters</span></span>  
 `ppStepper`  
 <span data-ttu-id="f2c08-106">[out] Um ponteiro para o endereço de uma `ICorDebugStepper` objeto que permite percorrer o quadro ativo deste thread.</span><span class="sxs-lookup"><span data-stu-id="f2c08-106">[out] A pointer to the address of an `ICorDebugStepper` object that allows stepping through the active frame of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f2c08-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="f2c08-107">Remarks</span></span>  
 <span data-ttu-id="f2c08-108">O quadro ativo pode ser o código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="f2c08-108">The active frame may be unmanaged code.</span></span>  
  
 <span data-ttu-id="f2c08-109">O `ICorDebugStepper` interface deve ser usada para executar a revisão atual.</span><span class="sxs-lookup"><span data-stu-id="f2c08-109">The `ICorDebugStepper` interface must be used to perform the actual stepping.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2c08-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f2c08-110">Requirements</span></span>  
 <span data-ttu-id="f2c08-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2c08-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2c08-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f2c08-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f2c08-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f2c08-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f2c08-114">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2c08-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
