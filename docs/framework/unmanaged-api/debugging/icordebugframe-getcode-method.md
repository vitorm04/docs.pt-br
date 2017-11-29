---
title: "Método ICorDebugFrame::GetCode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFrame.GetCode
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFrame::GetCode
helpviewer_keywords:
- GetCode method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetCode method [.NET Framework debugging]
ms.assetid: fbaa0794-a031-4015-8beb-2749e47ac340
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e4538526f0358e7fa5259e87cbdf46abdb662475
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugframegetcode-method"></a><span data-ttu-id="78b27-102">Método ICorDebugFrame::GetCode</span><span class="sxs-lookup"><span data-stu-id="78b27-102">ICorDebugFrame::GetCode Method</span></span>
<span data-ttu-id="78b27-103">Obtém um ponteiro para o código associado deste quadro de pilhas.</span><span class="sxs-lookup"><span data-stu-id="78b27-103">Gets a pointer to the code associated with this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78b27-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="78b27-104">Syntax</span></span>  
  
```  
HRESULT GetCode (  
    [out] ICorDebugCode      **ppCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="78b27-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="78b27-105">Parameters</span></span>  
 `ppCode`  
 <span data-ttu-id="78b27-106">[out] Um ponteiro para o endereço de um objeto ICorDebugCode que representa o código associado a este quadro.</span><span class="sxs-lookup"><span data-stu-id="78b27-106">[out] A pointer to the address of an ICorDebugCode object that represents the code associated with this frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78b27-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="78b27-107">Requirements</span></span>  
 <span data-ttu-id="78b27-108">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78b27-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78b27-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="78b27-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="78b27-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="78b27-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="78b27-111">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78b27-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
