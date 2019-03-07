---
title: Método IcorDebugVariableHome::GetLiveRange
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetLiveRange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetLiveRange
helpviewer_keywords:
- ICorDebugVariableHome::GetLiveRange method [.NET Framework debugging]
- GetLiveRange method, ICorDebugVariableFrame interface [.NET Framework debugging]
ms.assetid: 87277e1a-1595-4729-9e25-d1c3ac18ce5f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 06c8ae378c10eda986740dfb73f3bf60ea8647a6
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57468839"
---
# <a name="icordebugvariablehomegetliverange-method"></a><span data-ttu-id="85c9b-102">Método IcorDebugVariableHome::GetLiveRange</span><span class="sxs-lookup"><span data-stu-id="85c9b-102">IcorDebugVariableHome::GetLiveRange Method</span></span>
<span data-ttu-id="85c9b-103">Obtém o intervalo nativo através da qual esta variável está ativo.</span><span class="sxs-lookup"><span data-stu-id="85c9b-103">Gets the native range over which this variable is live.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85c9b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="85c9b-104">Syntax</span></span>  
  
```  
HRESULT GetLiveRange(  
    [out] ULONG32* pStartOffset,  
    [out] ULONG32 *pEndOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="85c9b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="85c9b-105">Parameters</span></span>  
 `pStartOffset`  
 <span data-ttu-id="85c9b-106">[out] O deslocamento lógico no qual a variável é primeiro ao vivo.</span><span class="sxs-lookup"><span data-stu-id="85c9b-106">[out] The logical offset at which the variable is first live.</span></span>  
  
 `pEndOffset`  
 <span data-ttu-id="85c9b-107">[out] O deslocamento lógico imediatamente após o ponto em que a variável é passada ao vivo.</span><span class="sxs-lookup"><span data-stu-id="85c9b-107">[out] The logical offset immediately after the point at which the variable is last live.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85c9b-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="85c9b-108">Requirements</span></span>  
 <span data-ttu-id="85c9b-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85c9b-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85c9b-110">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="85c9b-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="85c9b-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="85c9b-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="85c9b-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85c9b-112">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85c9b-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="85c9b-113">See also</span></span>
- [<span data-ttu-id="85c9b-114">Interface ICorDebugVariableHome</span><span class="sxs-lookup"><span data-stu-id="85c9b-114">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
