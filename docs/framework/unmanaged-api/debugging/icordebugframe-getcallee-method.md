---
title: "Método ICorDebugFrame::GetCallee"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFrame.GetCallee
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFrame::GetCallee
helpviewer_keywords:
- ICorDebugFrame::GetCallee method [.NET Framework debugging]
- GetCallee method, ICorDebugFrame interface [.NET Framework debugging]
ms.assetid: 92d8136d-0436-4c7e-a6b2-80765f892a0d
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 079d598e54f429fa4dd0b5c0c4cadbe2c66c1d50
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugframegetcallee-method"></a><span data-ttu-id="a00fb-102">Método ICorDebugFrame::GetCallee</span><span class="sxs-lookup"><span data-stu-id="a00fb-102">ICorDebugFrame::GetCallee Method</span></span>
<span data-ttu-id="a00fb-103">Obtém um ponteiro para o objeto ICorDebugFrame da atual cadeia que este quadro chamado.</span><span class="sxs-lookup"><span data-stu-id="a00fb-103">Gets a pointer to the ICorDebugFrame object in the current chain that this frame called.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a00fb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a00fb-104">Syntax</span></span>  
  
```  
HRESULT GetCallee (  
    [out] ICorDebugFrame     **ppFrame  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a00fb-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a00fb-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="a00fb-106">[out] Um ponteiro para o endereço de uma `ICorDebugFrame` objeto que representa o quadro chamado.</span><span class="sxs-lookup"><span data-stu-id="a00fb-106">[out] A pointer to the address of an `ICorDebugFrame` object that represents the called frame.</span></span> <span data-ttu-id="a00fb-107">Esse valor será nulo se o quadro de chamada é o quadro interno da atual cadeia.</span><span class="sxs-lookup"><span data-stu-id="a00fb-107">This value is null if the calling frame is the innermost frame in the current chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a00fb-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a00fb-108">Requirements</span></span>  
 <span data-ttu-id="a00fb-109">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a00fb-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a00fb-110">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a00fb-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a00fb-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a00fb-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a00fb-112">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a00fb-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
