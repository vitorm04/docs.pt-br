---
title: Método ICorDebugThread::GetActiveChain
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetActiveChain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetActiveChain
helpviewer_keywords:
- ICorDebugThread::GetActiveChain method [.NET Framework debugging]
- GetActiveChain method [.NET Framework debugging]
ms.assetid: f50de1f7-40ef-4949-b542-1d9a61f7bfef
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b05f5a3f29c7b72ed83c1456175f68ef9b986e3e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61987175"
---
# <a name="icordebugthreadgetactivechain-method"></a><span data-ttu-id="02a58-102">Método ICorDebugThread::GetActiveChain</span><span class="sxs-lookup"><span data-stu-id="02a58-102">ICorDebugThread::GetActiveChain Method</span></span>
<span data-ttu-id="02a58-103">Obtém um ponteiro de interface para a cadeia da pilha (mais recente) ativa neste objeto ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="02a58-103">Gets an interface pointer to the active (most recent) stack chain on this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02a58-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="02a58-104">Syntax</span></span>  
  
```  
HRESULT GetActiveChain (  
    [out] ICorDebugChain **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="02a58-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="02a58-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="02a58-106">[out] Um ponteiro para o endereço de um objeto ICorDebugChain que representa a cadeia da pilha.</span><span class="sxs-lookup"><span data-stu-id="02a58-106">[out] A pointer to the address of an ICorDebugChain object that represents the stack chain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="02a58-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="02a58-107">Remarks</span></span>  
 <span data-ttu-id="02a58-108">O `ppChain` parâmetro será nulo se nenhuma cadeia de pilha está ativa no momento.</span><span class="sxs-lookup"><span data-stu-id="02a58-108">The `ppChain` parameter is null if no stack chain is currently active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02a58-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="02a58-109">Requirements</span></span>  
 <span data-ttu-id="02a58-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="02a58-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02a58-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="02a58-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="02a58-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="02a58-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="02a58-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02a58-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
