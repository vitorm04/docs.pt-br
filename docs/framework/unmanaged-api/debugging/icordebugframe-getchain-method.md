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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 64de770676cdd02375e854acb8af7feecb28dfeb
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754117"
---
# <a name="icordebugframegetchain-method"></a><span data-ttu-id="fd438-102">Método ICorDebugFrame::GetChain</span><span class="sxs-lookup"><span data-stu-id="fd438-102">ICorDebugFrame::GetChain Method</span></span>
<span data-ttu-id="fd438-103">Obtém um ponteiro para a cadeia que esse quadro é uma parte do.</span><span class="sxs-lookup"><span data-stu-id="fd438-103">Gets a pointer to the chain this frame is a part of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd438-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fd438-104">Syntax</span></span>  
  
```cpp  
HRESULT GetChain (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fd438-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fd438-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="fd438-106">[out] Um ponteiro para o endereço de um objeto de ICorDebugChain que representa a cadeia que contém este quadro.</span><span class="sxs-lookup"><span data-stu-id="fd438-106">[out] A pointer to the address of an ICorDebugChain object that represents the chain containing this frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd438-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fd438-107">Requirements</span></span>  
 <span data-ttu-id="fd438-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fd438-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd438-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fd438-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fd438-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fd438-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fd438-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd438-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
