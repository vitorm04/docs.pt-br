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
ms.openlocfilehash: 3f7e5fceacc3fefa9267a9d7f989e745c392322e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33414119"
---
# <a name="icordebuginternalframegetframetype-method"></a><span data-ttu-id="a87da-102">Método ICorDebugInternalFrame::GetFrameType</span><span class="sxs-lookup"><span data-stu-id="a87da-102">ICorDebugInternalFrame::GetFrameType Method</span></span>
<span data-ttu-id="a87da-103">Obtém o tipo deste quadro interno.</span><span class="sxs-lookup"><span data-stu-id="a87da-103">Gets the type of this internal frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a87da-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a87da-104">Syntax</span></span>  
  
```  
HRESULT GetFrameType (  
    [out] CorDebugInternalFrameType  *pType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a87da-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a87da-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="a87da-106">[out] Um ponteiro para um valor da enumeração CorDebugInternalFrameType que indica o tipo de quadro internos representado por esse `ICorDebugInternalFrame` objeto.</span><span class="sxs-lookup"><span data-stu-id="a87da-106">[out] A pointer to a value of the CorDebugInternalFrameType enumeration that indicates the type of internal frame represented by this `ICorDebugInternalFrame` object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a87da-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="a87da-107">Remarks</span></span>  
 <span data-ttu-id="a87da-108">O tipo de quadro internos nunca será STUBFRAME_NONE.</span><span class="sxs-lookup"><span data-stu-id="a87da-108">The internal frame type will never be STUBFRAME_NONE.</span></span> <span data-ttu-id="a87da-109">Depuradores normalmente devem ignorar os tipos de quadro internos não reconhecido.</span><span class="sxs-lookup"><span data-stu-id="a87da-109">Debuggers should gracefully ignore unrecognized internal frame types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a87da-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a87da-110">Requirements</span></span>  
 <span data-ttu-id="a87da-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a87da-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a87da-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a87da-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a87da-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a87da-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a87da-114">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a87da-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
