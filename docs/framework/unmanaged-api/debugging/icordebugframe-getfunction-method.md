---
title: "Método ICorDebugFrame::GetFunction"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFrame.GetFunction
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFrame::GetFunction
helpviewer_keywords:
- GetFunction method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetFunction method [.NET Framework debugging]
ms.assetid: 879d2311-0ff1-4616-a8b3-959ea5868b2e
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8d48ac730f22459a71b126126a7418e73805c7e1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugframegetfunction-method"></a><span data-ttu-id="1cbc5-102">Método ICorDebugFrame::GetFunction</span><span class="sxs-lookup"><span data-stu-id="1cbc5-102">ICorDebugFrame::GetFunction Method</span></span>
<span data-ttu-id="1cbc5-103">Obtém a função que contém o código associado deste quadro de pilhas.</span><span class="sxs-lookup"><span data-stu-id="1cbc5-103">Gets the function that contains the code associated with this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1cbc5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1cbc5-104">Syntax</span></span>  
  
```  
HRESULT GetFunction (  
    [out] ICorDebugFunction  **ppFunction  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1cbc5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1cbc5-105">Parameters</span></span>  
 `ppFunction`  
 <span data-ttu-id="1cbc5-106">[out] Um ponteiro para o endereço de um objeto ICorDebugFunction que representa a função que contém o código associado deste quadro de pilhas.</span><span class="sxs-lookup"><span data-stu-id="1cbc5-106">[out] A pointer to the address of an ICorDebugFunction object that represents the function containing the code associated with this stack frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1cbc5-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="1cbc5-107">Remarks</span></span>  
 <span data-ttu-id="1cbc5-108">O `GetFunction` método poderá falhar se o quadro não está associado a qualquer função específica.</span><span class="sxs-lookup"><span data-stu-id="1cbc5-108">The `GetFunction` method may fail if the frame is not associated with any particular function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1cbc5-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1cbc5-109">Requirements</span></span>  
 <span data-ttu-id="1cbc5-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1cbc5-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1cbc5-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1cbc5-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1cbc5-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1cbc5-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1cbc5-113">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1cbc5-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
