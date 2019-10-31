---
title: 'Método IcorDebugVariableHome:: GetLiveRange'
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
ms.openlocfilehash: a8b8955d2f4c164031974f0d9021fb766ff2c030
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125123"
---
# <a name="icordebugvariablehomegetliverange-method"></a><span data-ttu-id="7e8fc-102">Método IcorDebugVariableHome:: GetLiveRange</span><span class="sxs-lookup"><span data-stu-id="7e8fc-102">IcorDebugVariableHome::GetLiveRange Method</span></span>
<span data-ttu-id="7e8fc-103">Obtém o intervalo nativo no qual essa variável está ativa.</span><span class="sxs-lookup"><span data-stu-id="7e8fc-103">Gets the native range over which this variable is live.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e8fc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7e8fc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLiveRange(  
    [out] ULONG32* pStartOffset,  
    [out] ULONG32 *pEndOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7e8fc-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7e8fc-105">Parameters</span></span>  
 `pStartOffset`  
 <span data-ttu-id="7e8fc-106">fora O deslocamento lógico no qual a variável é ativada pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="7e8fc-106">[out] The logical offset at which the variable is first live.</span></span>  
  
 `pEndOffset`  
 <span data-ttu-id="7e8fc-107">fora O deslocamento lógico imediatamente após o ponto em que a variável é o último Live.</span><span class="sxs-lookup"><span data-stu-id="7e8fc-107">[out] The logical offset immediately after the point at which the variable is last live.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e8fc-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7e8fc-108">Requirements</span></span>  
 <span data-ttu-id="7e8fc-109">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e8fc-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e8fc-110">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7e8fc-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7e8fc-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7e8fc-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7e8fc-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e8fc-112">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e8fc-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7e8fc-113">See also</span></span>

- [<span data-ttu-id="7e8fc-114">Interface ICorDebugVariableHome</span><span class="sxs-lookup"><span data-stu-id="7e8fc-114">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
