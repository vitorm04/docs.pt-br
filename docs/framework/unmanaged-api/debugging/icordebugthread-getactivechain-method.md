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
ms.openlocfilehash: 70e79378ad8eb2599199a1f7bc57cf530c9b4dd3
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379689"
---
# <a name="icordebugthreadgetactivechain-method"></a><span data-ttu-id="c2701-102">Método ICorDebugThread::GetActiveChain</span><span class="sxs-lookup"><span data-stu-id="c2701-102">ICorDebugThread::GetActiveChain Method</span></span>
<span data-ttu-id="c2701-103">Obtém um ponteiro de interface para a cadeia de pilha ativa (mais recente) neste objeto ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="c2701-103">Gets an interface pointer to the active (most recent) stack chain on this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2701-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c2701-104">Syntax</span></span>  
  
```cpp  
HRESULT GetActiveChain (  
    [out] ICorDebugChain **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c2701-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c2701-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="c2701-106">fora Um ponteiro para o endereço de um objeto ICorDebugChain que representa a cadeia de pilha.</span><span class="sxs-lookup"><span data-stu-id="c2701-106">[out] A pointer to the address of an ICorDebugChain object that represents the stack chain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c2701-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="c2701-107">Remarks</span></span>  
 <span data-ttu-id="c2701-108">O `ppChain` parâmetro será NULL se nenhuma cadeia de pilha estiver ativa no momento.</span><span class="sxs-lookup"><span data-stu-id="c2701-108">The `ppChain` parameter is null if no stack chain is currently active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2701-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c2701-109">Requirements</span></span>  
 <span data-ttu-id="c2701-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2701-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2701-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c2701-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c2701-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c2701-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c2701-113">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2701-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
