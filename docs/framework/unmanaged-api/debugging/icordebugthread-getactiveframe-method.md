---
title: Método ICorDebugThread::GetActiveFrame
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetActiveFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetActiveFrame
helpviewer_keywords:
- ICorDebugThread::GetActiveFrame method [.NET Framework debugging]
- GetActiveFrame method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 8d6d3a1a-fef6-4f2f-a22c-3bdd30d70e07
topic_type:
- apiref
ms.openlocfilehash: d623893bd77e46832b0bd823ed60c23e4eee29ba
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133534"
---
# <a name="icordebugthreadgetactiveframe-method"></a><span data-ttu-id="4ca4b-102">Método ICorDebugThread::GetActiveFrame</span><span class="sxs-lookup"><span data-stu-id="4ca4b-102">ICorDebugThread::GetActiveFrame Method</span></span>
<span data-ttu-id="4ca4b-103">Obtém um ponteiro de interface para o quadro ativo (mais recente) neste objeto ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="4ca4b-103">Gets an interface pointer to the active (most recent) frame on this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ca4b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4ca4b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetActiveFrame (  
    [out] ICorDebugFrame   **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4ca4b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4ca4b-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="4ca4b-106">fora Um ponteiro para o endereço de um objeto de interface ICorDebugFrame que representa um quadro.</span><span class="sxs-lookup"><span data-stu-id="4ca4b-106">[out] A pointer to the address of an ICorDebugFrame interface object that represents a frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4ca4b-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="4ca4b-107">Remarks</span></span>  
 <span data-ttu-id="4ca4b-108">O parâmetro `ppFrame` será nulo se nenhum quadro estiver ativo no momento.</span><span class="sxs-lookup"><span data-stu-id="4ca4b-108">The `ppFrame` parameter is null if no frame is currently active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ca4b-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4ca4b-109">Requirements</span></span>  
 <span data-ttu-id="4ca4b-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4ca4b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ca4b-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4ca4b-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4ca4b-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4ca4b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4ca4b-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ca4b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
