---
title: "Método ISymUnmanagedAsyncMethod::GetAsyncStepInfo"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 3ef5b4b8-4ac7-4906-849b-f932c5e3db07
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f999e8cfba38ff4b4b15baea7ca9fa89606cb0ce
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedasyncmethodgetasyncstepinfo-method"></a><span data-ttu-id="c790b-102">Método ISymUnmanagedAsyncMethod::GetAsyncStepInfo</span><span class="sxs-lookup"><span data-stu-id="c790b-102">ISymUnmanagedAsyncMethod::GetAsyncStepInfo Method</span></span>
<span data-ttu-id="c790b-103">Consulte [método DefineAsyncStepInfo](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span><span class="sxs-lookup"><span data-stu-id="c790b-103">See [DefineAsyncStepInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c790b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c790b-104">Syntax</span></span>  
  
```idl  
HRESULT GetAsyncStepInfo(    [in] ULONG32 cStepInfo,    [out] ULONG32 *pcStepInfo,    [in, size_is(cStepInfo)] ULONG32 yieldOffsets[],    [in, size_is(cStepInfo)] ULONG32 breakpointOffset[],    [in, size_is(cStepInfo)] mdToken breakpointMethod[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c790b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c790b-105">Parameters</span></span>  
  
|<span data-ttu-id="c790b-106">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="c790b-106">Parameter</span></span>|<span data-ttu-id="c790b-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="c790b-107">Description</span></span>|  
|---------------|-----------------|  
|`cStepInfo`||  
|`pcStepInfo`||  
|`yieldOffsets`||  
|`breakpointOffset`||  
|`breakpointMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="c790b-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="c790b-108">Return Value</span></span>  
 <span data-ttu-id="c790b-109">Retorna `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="c790b-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c790b-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c790b-110">Requirements</span></span>  
 <span data-ttu-id="c790b-111">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c790b-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c790b-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c790b-112">See Also</span></span>  
 [<span data-ttu-id="c790b-113">Interface ISymUnmanagedAsyncMethod</span><span class="sxs-lookup"><span data-stu-id="c790b-113">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
