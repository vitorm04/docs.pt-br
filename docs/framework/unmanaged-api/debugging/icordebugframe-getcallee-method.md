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
ms.openlocfilehash: b83dec65e1dd4fc610be3190e8126e6d9d38a6e8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121218"
---
# <a name="icordebugframegetcallee-method"></a><span data-ttu-id="d5967-102">Método ICorDebugFrame::GetCallee</span><span class="sxs-lookup"><span data-stu-id="d5967-102">ICorDebugFrame::GetCallee Method</span></span>
<span data-ttu-id="d5967-103">Obtém um ponteiro para o objeto ICorDebugFrame na cadeia atual que esse quadro chamou.</span><span class="sxs-lookup"><span data-stu-id="d5967-103">Gets a pointer to the ICorDebugFrame object in the current chain that this frame called.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5967-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d5967-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCallee (  
    [out] ICorDebugFrame     **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d5967-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d5967-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="d5967-106">fora Um ponteiro para o endereço de um objeto de `ICorDebugFrame` que representa o quadro chamado.</span><span class="sxs-lookup"><span data-stu-id="d5967-106">[out] A pointer to the address of an `ICorDebugFrame` object that represents the called frame.</span></span> <span data-ttu-id="d5967-107">Esse valor será nulo se o quadro de chamada for o quadro interno na cadeia atual.</span><span class="sxs-lookup"><span data-stu-id="d5967-107">This value is null if the calling frame is the innermost frame in the current chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5967-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d5967-108">Requirements</span></span>  
 <span data-ttu-id="d5967-109">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5967-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5967-110">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d5967-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d5967-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d5967-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d5967-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5967-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
