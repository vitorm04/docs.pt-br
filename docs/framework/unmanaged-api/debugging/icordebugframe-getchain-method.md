---
title: Método ICorDebugFrame::GetChain
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetChain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetChain
helpviewer_keywords:
- ICorDebugFrame::GetChain method [.NET Framework debugging]
- GetChain method [.NET Framework debugging]
ms.assetid: e28e51d3-8f73-494f-bcd4-48bac239fbe1
topic_type:
- apiref
ms.openlocfilehash: 9677fd14f50cf93eac7eeaef784082d45e8884c7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137681"
---
# <a name="icordebugframegetchain-method"></a><span data-ttu-id="f0d05-102">Método ICorDebugFrame::GetChain</span><span class="sxs-lookup"><span data-stu-id="f0d05-102">ICorDebugFrame::GetChain Method</span></span>
<span data-ttu-id="f0d05-103">Obtém um ponteiro para a cadeia em que este quadro faz parte.</span><span class="sxs-lookup"><span data-stu-id="f0d05-103">Gets a pointer to the chain this frame is a part of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0d05-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f0d05-104">Syntax</span></span>  
  
```cpp  
HRESULT GetChain (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f0d05-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f0d05-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="f0d05-106">fora Um ponteiro para o endereço de um objeto ICorDebugChain que representa a cadeia que contém esse quadro.</span><span class="sxs-lookup"><span data-stu-id="f0d05-106">[out] A pointer to the address of an ICorDebugChain object that represents the chain containing this frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0d05-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f0d05-107">Requirements</span></span>  
 <span data-ttu-id="f0d05-108">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0d05-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0d05-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f0d05-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f0d05-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f0d05-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f0d05-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0d05-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
