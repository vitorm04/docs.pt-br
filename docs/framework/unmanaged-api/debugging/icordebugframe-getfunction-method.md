---
title: Método ICorDebugFrame::GetFunction
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetFunction
helpviewer_keywords:
- GetFunction method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetFunction method [.NET Framework debugging]
ms.assetid: 879d2311-0ff1-4616-a8b3-959ea5868b2e
topic_type:
- apiref
ms.openlocfilehash: 39175e338e4fd98dd4af1325138da732ed81c764
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137917"
---
# <a name="icordebugframegetfunction-method"></a><span data-ttu-id="10331-102">Método ICorDebugFrame::GetFunction</span><span class="sxs-lookup"><span data-stu-id="10331-102">ICorDebugFrame::GetFunction Method</span></span>
<span data-ttu-id="10331-103">Obtém a função que contém o código associado a este quadro de pilhas.</span><span class="sxs-lookup"><span data-stu-id="10331-103">Gets the function that contains the code associated with this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10331-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="10331-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunction (  
    [out] ICorDebugFunction  **ppFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="10331-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="10331-105">Parameters</span></span>  
 `ppFunction`  
 <span data-ttu-id="10331-106">fora Um ponteiro para o endereço de um objeto ICorDebugFunction que representa a função que contém o código associado a esse quadro de pilhas.</span><span class="sxs-lookup"><span data-stu-id="10331-106">[out] A pointer to the address of an ICorDebugFunction object that represents the function containing the code associated with this stack frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="10331-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="10331-107">Remarks</span></span>  
 <span data-ttu-id="10331-108">O método `GetFunction` poderá falhar se o quadro não estiver associado a nenhuma função específica.</span><span class="sxs-lookup"><span data-stu-id="10331-108">The `GetFunction` method may fail if the frame is not associated with any particular function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10331-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="10331-109">Requirements</span></span>  
 <span data-ttu-id="10331-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="10331-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10331-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="10331-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="10331-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="10331-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="10331-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10331-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
