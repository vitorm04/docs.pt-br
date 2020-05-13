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
ms.openlocfilehash: 7bf73266f0269cfcd5371c5155856800036cc066
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209832"
---
# <a name="icordebugframegetfunction-method"></a><span data-ttu-id="02192-102">Método ICorDebugFrame::GetFunction</span><span class="sxs-lookup"><span data-stu-id="02192-102">ICorDebugFrame::GetFunction Method</span></span>
<span data-ttu-id="02192-103">Obtém a função que contém o código associado a este quadro de pilhas.</span><span class="sxs-lookup"><span data-stu-id="02192-103">Gets the function that contains the code associated with this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02192-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="02192-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunction (  
    [out] ICorDebugFunction  **ppFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="02192-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="02192-105">Parameters</span></span>  
 `ppFunction`  
 <span data-ttu-id="02192-106">fora Um ponteiro para o endereço de um objeto ICorDebugFunction que representa a função que contém o código associado a esse quadro de pilhas.</span><span class="sxs-lookup"><span data-stu-id="02192-106">[out] A pointer to the address of an ICorDebugFunction object that represents the function containing the code associated with this stack frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="02192-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="02192-107">Remarks</span></span>  
 <span data-ttu-id="02192-108">O `GetFunction` método poderá falhar se o quadro não estiver associado a nenhuma função específica.</span><span class="sxs-lookup"><span data-stu-id="02192-108">The `GetFunction` method may fail if the frame is not associated with any particular function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02192-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="02192-109">Requirements</span></span>  
 <span data-ttu-id="02192-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="02192-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02192-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="02192-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="02192-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="02192-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="02192-113">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02192-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
