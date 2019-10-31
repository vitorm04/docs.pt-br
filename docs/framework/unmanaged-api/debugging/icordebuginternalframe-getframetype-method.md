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
ms.openlocfilehash: b7a33fd6e2178e0e9188b81f516b231702fb6460
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122721"
---
# <a name="icordebuginternalframegetframetype-method"></a><span data-ttu-id="7ab20-102">Método ICorDebugInternalFrame::GetFrameType</span><span class="sxs-lookup"><span data-stu-id="7ab20-102">ICorDebugInternalFrame::GetFrameType Method</span></span>
<span data-ttu-id="7ab20-103">Obtém o tipo deste quadro interno.</span><span class="sxs-lookup"><span data-stu-id="7ab20-103">Gets the type of this internal frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ab20-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7ab20-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFrameType (  
    [out] CorDebugInternalFrameType  *pType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7ab20-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7ab20-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="7ab20-106">fora Um ponteiro para um valor da enumeração CorDebugInternalFrameType que indica o tipo de quadro interno representado por esse objeto de `ICorDebugInternalFrame`.</span><span class="sxs-lookup"><span data-stu-id="7ab20-106">[out] A pointer to a value of the CorDebugInternalFrameType enumeration that indicates the type of internal frame represented by this `ICorDebugInternalFrame` object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7ab20-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="7ab20-107">Remarks</span></span>  
 <span data-ttu-id="7ab20-108">O tipo de quadro interno nunca será STUBFRAME_NONE.</span><span class="sxs-lookup"><span data-stu-id="7ab20-108">The internal frame type will never be STUBFRAME_NONE.</span></span> <span data-ttu-id="7ab20-109">Os depuradores devem ignorar normalmente os tipos de quadro internos não reconhecidos.</span><span class="sxs-lookup"><span data-stu-id="7ab20-109">Debuggers should gracefully ignore unrecognized internal frame types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ab20-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7ab20-110">Requirements</span></span>  
 <span data-ttu-id="7ab20-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ab20-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ab20-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7ab20-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7ab20-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7ab20-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7ab20-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ab20-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
