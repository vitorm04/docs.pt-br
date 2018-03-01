---
title: "Método ICorDebugFrame::GetFunctionToken"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugFrame.GetFunctionToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetFunctionToken
helpviewer_keywords:
- ICorDebugFrame::GetFunctionToken method [.NET Framework debugging]
- GetFunctionToken method [.NET Framework debugging]
ms.assetid: a46925b3-3bf8-404f-9f30-a86ae41032c1
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9d36606dfffb6ff5872ee88f00d3d94f3ececce5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugframegetfunctiontoken-method"></a><span data-ttu-id="38442-102">Método ICorDebugFrame::GetFunctionToken</span><span class="sxs-lookup"><span data-stu-id="38442-102">ICorDebugFrame::GetFunctionToken Method</span></span>
<span data-ttu-id="38442-103">Obtém o token de metadados para a função que contém o código associado deste quadro de pilhas.</span><span class="sxs-lookup"><span data-stu-id="38442-103">Gets the metadata token for the function that contains the code associated with this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38442-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="38442-104">Syntax</span></span>  
  
```  
HRESULT GetFunctionToken (  
    [out] mdMethodDef        *pToken  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="38442-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="38442-105">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="38442-106">[out] Um ponteiro para um `mdMethodDef` token que referencia os metadados para a função.</span><span class="sxs-lookup"><span data-stu-id="38442-106">[out] A pointer to an `mdMethodDef` token that references the metadata for the function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38442-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="38442-107">Requirements</span></span>  
 <span data-ttu-id="38442-108">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38442-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38442-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="38442-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="38442-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="38442-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="38442-111">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38442-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
