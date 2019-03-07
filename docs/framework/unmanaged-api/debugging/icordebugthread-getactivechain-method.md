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
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57483310"
---
# <a name="icordebugthreadgetactivechain-method"></a><span data-ttu-id="0e9f8-102">Método ICorDebugThread::GetActiveChain</span><span class="sxs-lookup"><span data-stu-id="0e9f8-102">ICorDebugThread::GetActiveChain Method</span></span>
<span data-ttu-id="0e9f8-103">Obtém um ponteiro de interface para a cadeia da pilha (mais recente) ativa neste objeto ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="0e9f8-103">Gets an interface pointer to the active (most recent) stack chain on this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e9f8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0e9f8-104">Syntax</span></span>  
  
```  
HRESULT GetActiveChain (  
    [out] ICorDebugChain **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0e9f8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0e9f8-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="0e9f8-106">[out] Um ponteiro para o endereço de um objeto ICorDebugChain que representa a cadeia da pilha.</span><span class="sxs-lookup"><span data-stu-id="0e9f8-106">[out] A pointer to the address of an ICorDebugChain object that represents the stack chain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0e9f8-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="0e9f8-107">Remarks</span></span>  
 <span data-ttu-id="0e9f8-108">O `ppChain` parâmetro será nulo se nenhuma cadeia de pilha está ativa no momento.</span><span class="sxs-lookup"><span data-stu-id="0e9f8-108">The `ppChain` parameter is null if no stack chain is currently active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e9f8-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0e9f8-109">Requirements</span></span>  
 <span data-ttu-id="0e9f8-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e9f8-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e9f8-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0e9f8-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0e9f8-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0e9f8-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0e9f8-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e9f8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
