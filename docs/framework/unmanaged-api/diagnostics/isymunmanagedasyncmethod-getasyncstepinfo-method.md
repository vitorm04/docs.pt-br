---
title: Método ISymUnmanagedAsyncMethod::GetAsyncStepInfo
ms.date: 03/30/2017
ms.assetid: 3ef5b4b8-4ac7-4906-849b-f932c5e3db07
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 34792ddc7d32c89f6572a48e4636a63881611b88
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57473546"
---
# <a name="isymunmanagedasyncmethodgetasyncstepinfo-method"></a><span data-ttu-id="4c9d9-102">Método ISymUnmanagedAsyncMethod::GetAsyncStepInfo</span><span class="sxs-lookup"><span data-stu-id="4c9d9-102">ISymUnmanagedAsyncMethod::GetAsyncStepInfo Method</span></span>
<span data-ttu-id="4c9d9-103">Ver [método DefineAsyncStepInfo](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span><span class="sxs-lookup"><span data-stu-id="4c9d9-103">See [DefineAsyncStepInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c9d9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4c9d9-104">Syntax</span></span>  
  
```idl  
HRESULT GetAsyncStepInfo(    [in] ULONG32 cStepInfo,    [out] ULONG32 *pcStepInfo,    [in, size_is(cStepInfo)] ULONG32 yieldOffsets[],    [in, size_is(cStepInfo)] ULONG32 breakpointOffset[],    [in, size_is(cStepInfo)] mdToken breakpointMethod[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4c9d9-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4c9d9-105">Parameters</span></span>  
  
|<span data-ttu-id="4c9d9-106">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="4c9d9-106">Parameter</span></span>|<span data-ttu-id="4c9d9-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="4c9d9-107">Description</span></span>|  
|---------------|-----------------|  
|`cStepInfo`||  
|`pcStepInfo`||  
|`yieldOffsets`||  
|`breakpointOffset`||  
|`breakpointMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="4c9d9-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="4c9d9-108">Return Value</span></span>  
 <span data-ttu-id="4c9d9-109">Retorna `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="4c9d9-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c9d9-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4c9d9-110">Requirements</span></span>  
 <span data-ttu-id="4c9d9-111">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="4c9d9-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c9d9-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4c9d9-112">See also</span></span>
- [<span data-ttu-id="4c9d9-113">Interface ISymUnmanagedAsyncMethod</span><span class="sxs-lookup"><span data-stu-id="4c9d9-113">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
