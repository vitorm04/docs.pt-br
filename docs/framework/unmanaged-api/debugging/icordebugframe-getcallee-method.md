---
title: Método ICorDebugFrame::GetCallee
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetCallee
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetCallee
helpviewer_keywords:
- ICorDebugFrame::GetCallee method [.NET Framework debugging]
- GetCallee method, ICorDebugFrame interface [.NET Framework debugging]
ms.assetid: 92d8136d-0436-4c7e-a6b2-80765f892a0d
topic_type:
- apiref
ms.openlocfilehash: 51ac10f936db129282720f2bcae8729f56735b59
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205376"
---
# <a name="icordebugframegetcallee-method"></a><span data-ttu-id="696e8-102">Método ICorDebugFrame::GetCallee</span><span class="sxs-lookup"><span data-stu-id="696e8-102">ICorDebugFrame::GetCallee Method</span></span>
<span data-ttu-id="696e8-103">Obtém um ponteiro para o objeto ICorDebugFrame na cadeia atual que esse quadro chamou.</span><span class="sxs-lookup"><span data-stu-id="696e8-103">Gets a pointer to the ICorDebugFrame object in the current chain that this frame called.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="696e8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="696e8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCallee (  
    [out] ICorDebugFrame     **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="696e8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="696e8-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="696e8-106">fora Um ponteiro para o endereço de um `ICorDebugFrame` objeto que representa o quadro chamado.</span><span class="sxs-lookup"><span data-stu-id="696e8-106">[out] A pointer to the address of an `ICorDebugFrame` object that represents the called frame.</span></span> <span data-ttu-id="696e8-107">Esse valor será nulo se o quadro de chamada for o quadro interno na cadeia atual.</span><span class="sxs-lookup"><span data-stu-id="696e8-107">This value is null if the calling frame is the innermost frame in the current chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="696e8-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="696e8-108">Requirements</span></span>  
 <span data-ttu-id="696e8-109">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="696e8-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="696e8-110">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="696e8-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="696e8-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="696e8-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="696e8-112">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="696e8-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
