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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a179b68e2196eeadc712ae8f7d023b2943533335
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471063"
---
# <a name="icordebugframegetcallee-method"></a><span data-ttu-id="250d0-102">Método ICorDebugFrame::GetCallee</span><span class="sxs-lookup"><span data-stu-id="250d0-102">ICorDebugFrame::GetCallee Method</span></span>
<span data-ttu-id="250d0-103">Obtém um ponteiro para o objeto ICorDebugFrame na cadeia de atual deste quadro de chamada.</span><span class="sxs-lookup"><span data-stu-id="250d0-103">Gets a pointer to the ICorDebugFrame object in the current chain that this frame called.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="250d0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="250d0-104">Syntax</span></span>  
  
```  
HRESULT GetCallee (  
    [out] ICorDebugFrame     **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="250d0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="250d0-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="250d0-106">[out] Um ponteiro para o endereço de um `ICorDebugFrame` objeto que representa o quadro de chamada.</span><span class="sxs-lookup"><span data-stu-id="250d0-106">[out] A pointer to the address of an `ICorDebugFrame` object that represents the called frame.</span></span> <span data-ttu-id="250d0-107">Esse valor será nulo se o quadro de chamada é o quadro mais interno da cadeia atual.</span><span class="sxs-lookup"><span data-stu-id="250d0-107">This value is null if the calling frame is the innermost frame in the current chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="250d0-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="250d0-108">Requirements</span></span>  
 <span data-ttu-id="250d0-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="250d0-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="250d0-110">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="250d0-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="250d0-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="250d0-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="250d0-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="250d0-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
