---
title: "Método IcorDebugVariableHome::GetLiveRange"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorDebugVariableHome.GetLiveRange
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugVariableHome::GetLiveRange
helpviewer_keywords:
- ICorDebugVariableHome::GetLiveRange method [.NET Framework debugging]
- GetLiveRange method, ICorDebugVariableFrame interface [.NET Framework debugging]
ms.assetid: 87277e1a-1595-4729-9e25-d1c3ac18ce5f
topic_type: apiref
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8554bf2667f3542b3164b60eaed998087fe175d5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugvariablehomegetliverange-method"></a><span data-ttu-id="328ae-102">Método IcorDebugVariableHome::GetLiveRange</span><span class="sxs-lookup"><span data-stu-id="328ae-102">IcorDebugVariableHome::GetLiveRange Method</span></span>
<span data-ttu-id="328ae-103">Obtém o intervalo nativo através da qual esta variável está ativo.</span><span class="sxs-lookup"><span data-stu-id="328ae-103">Gets the native range over which this variable is live.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="328ae-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="328ae-104">Syntax</span></span>  
  
```  
HRESULT GetLiveRange(  
    [out] ULONG32* pStartOffset,  
    [out] ULONG32 *pEndOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="328ae-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="328ae-105">Parameters</span></span>  
 `pStartOffset`  
 <span data-ttu-id="328ae-106">[out] O deslocamento lógico em que a variável é primeiro ao vivo.</span><span class="sxs-lookup"><span data-stu-id="328ae-106">[out] The logical offset at which the variable is first live.</span></span>  
  
 `pEndOffset`  
 <span data-ttu-id="328ae-107">[out] O deslocamento lógico imediatamente após o ponto em que a variável seja o última ao vivo.</span><span class="sxs-lookup"><span data-stu-id="328ae-107">[out] The logical offset immediately after the point at which the variable is last live.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="328ae-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="328ae-108">Requirements</span></span>  
 <span data-ttu-id="328ae-109">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="328ae-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="328ae-110">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="328ae-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="328ae-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="328ae-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="328ae-112">**Versões do .NET framework:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="328ae-112">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="328ae-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="328ae-113">See Also</span></span>  
 [<span data-ttu-id="328ae-114">Interface ICorDebugVariableHome</span><span class="sxs-lookup"><span data-stu-id="328ae-114">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
