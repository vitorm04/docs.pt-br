---
title: Método ICorDebugInternalFrame::GetFrameType
ms.date: 03/30/2017
api_name:
- ICorDebugInternalFrame.GetFrameType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame::GetFrameType
helpviewer_keywords:
- GetFrameType method [.NET Framework debugging]
- ICorDebugInternalFrame::GetFrameType method [.NET Framework debugging]
ms.assetid: da278a29-dc2e-4bf7-96ce-801bdc4d7025
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a0b6f0550bad534379b562c3df9da9ab917f5270
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57493031"
---
# <a name="icordebuginternalframegetframetype-method"></a><span data-ttu-id="12ade-102">Método ICorDebugInternalFrame::GetFrameType</span><span class="sxs-lookup"><span data-stu-id="12ade-102">ICorDebugInternalFrame::GetFrameType Method</span></span>
<span data-ttu-id="12ade-103">Obtém o tipo deste quadro interno.</span><span class="sxs-lookup"><span data-stu-id="12ade-103">Gets the type of this internal frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12ade-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="12ade-104">Syntax</span></span>  
  
```  
HRESULT GetFrameType (  
    [out] CorDebugInternalFrameType  *pType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="12ade-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="12ade-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="12ade-106">[out] Um ponteiro para um valor que indica o tipo de quadro interno representado por esta enumeração CorDebugInternalFrameType `ICorDebugInternalFrame` objeto.</span><span class="sxs-lookup"><span data-stu-id="12ade-106">[out] A pointer to a value of the CorDebugInternalFrameType enumeration that indicates the type of internal frame represented by this `ICorDebugInternalFrame` object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="12ade-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="12ade-107">Remarks</span></span>  
 <span data-ttu-id="12ade-108">O tipo de quadro interno nunca serão STUBFRAME_NONE.</span><span class="sxs-lookup"><span data-stu-id="12ade-108">The internal frame type will never be STUBFRAME_NONE.</span></span> <span data-ttu-id="12ade-109">Depuradores normalmente devem ignorar os tipos de quadro interno não reconhecido.</span><span class="sxs-lookup"><span data-stu-id="12ade-109">Debuggers should gracefully ignore unrecognized internal frame types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12ade-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="12ade-110">Requirements</span></span>  
 <span data-ttu-id="12ade-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12ade-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12ade-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="12ade-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="12ade-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="12ade-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="12ade-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12ade-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
