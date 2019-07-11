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
ms.openlocfilehash: ca64e392b930ed57691f05ae771bbaf305df8eb3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754066"
---
# <a name="icordebugframegetcode-method"></a><span data-ttu-id="0f942-102">Método ICorDebugFrame::GetCode</span><span class="sxs-lookup"><span data-stu-id="0f942-102">ICorDebugFrame::GetCode Method</span></span>
<span data-ttu-id="0f942-103">Obtém um ponteiro para o código associado a esse registro de ativação.</span><span class="sxs-lookup"><span data-stu-id="0f942-103">Gets a pointer to the code associated with this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f942-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0f942-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCode (  
    [out] ICorDebugCode      **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0f942-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0f942-105">Parameters</span></span>  
 `ppCode`  
 <span data-ttu-id="0f942-106">[out] Um ponteiro para o endereço de um objeto ICorDebugCode que representa o código associado a este quadro.</span><span class="sxs-lookup"><span data-stu-id="0f942-106">[out] A pointer to the address of an ICorDebugCode object that represents the code associated with this frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f942-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0f942-107">Requirements</span></span>  
 <span data-ttu-id="0f942-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f942-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f942-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0f942-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0f942-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0f942-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0f942-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f942-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
