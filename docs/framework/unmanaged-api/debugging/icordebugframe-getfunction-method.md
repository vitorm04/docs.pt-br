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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8f801dae69f16f2848b4ffa30f458c084fe9750a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754889"
---
# <a name="icordebugframegetfunction-method"></a><span data-ttu-id="c829c-102">Método ICorDebugFrame::GetFunction</span><span class="sxs-lookup"><span data-stu-id="c829c-102">ICorDebugFrame::GetFunction Method</span></span>
<span data-ttu-id="c829c-103">Obtém a função que contém o código associado a esse registro de ativação.</span><span class="sxs-lookup"><span data-stu-id="c829c-103">Gets the function that contains the code associated with this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c829c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c829c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunction (  
    [out] ICorDebugFunction  **ppFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c829c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c829c-105">Parameters</span></span>  
 `ppFunction`  
 <span data-ttu-id="c829c-106">[out] Um ponteiro para o endereço de um objeto ICorDebugFunction que representa a função que contém o código associado a esse registro de ativação.</span><span class="sxs-lookup"><span data-stu-id="c829c-106">[out] A pointer to the address of an ICorDebugFunction object that represents the function containing the code associated with this stack frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c829c-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="c829c-107">Remarks</span></span>  
 <span data-ttu-id="c829c-108">O `GetFunction` método poderá falhar se o quadro não está associado a qualquer função específica.</span><span class="sxs-lookup"><span data-stu-id="c829c-108">The `GetFunction` method may fail if the frame is not associated with any particular function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c829c-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c829c-109">Requirements</span></span>  
 <span data-ttu-id="c829c-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c829c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c829c-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c829c-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c829c-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c829c-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c829c-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c829c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
