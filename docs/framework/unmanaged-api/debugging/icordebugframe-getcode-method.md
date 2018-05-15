---
title: Método ICorDebugFrame::GetCode
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetCode
helpviewer_keywords:
- GetCode method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetCode method [.NET Framework debugging]
ms.assetid: fbaa0794-a031-4015-8beb-2749e47ac340
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 15206fbd7724383b1ec6df123790d3171e58e9f7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugframegetcode-method"></a><span data-ttu-id="deda8-102">Método ICorDebugFrame::GetCode</span><span class="sxs-lookup"><span data-stu-id="deda8-102">ICorDebugFrame::GetCode Method</span></span>
<span data-ttu-id="deda8-103">Obtém um ponteiro para o código associado deste quadro de pilhas.</span><span class="sxs-lookup"><span data-stu-id="deda8-103">Gets a pointer to the code associated with this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="deda8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="deda8-104">Syntax</span></span>  
  
```  
HRESULT GetCode (  
    [out] ICorDebugCode      **ppCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="deda8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="deda8-105">Parameters</span></span>  
 `ppCode`  
 <span data-ttu-id="deda8-106">[out] Um ponteiro para o endereço de um objeto ICorDebugCode que representa o código associado a este quadro.</span><span class="sxs-lookup"><span data-stu-id="deda8-106">[out] A pointer to the address of an ICorDebugCode object that represents the code associated with this frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="deda8-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="deda8-107">Requirements</span></span>  
 <span data-ttu-id="deda8-108">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="deda8-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="deda8-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="deda8-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="deda8-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="deda8-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="deda8-111">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="deda8-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
