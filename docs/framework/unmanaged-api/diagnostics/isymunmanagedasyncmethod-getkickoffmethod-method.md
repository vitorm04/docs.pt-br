---
title: "Método ISymUnmanagedAsyncMethod::GetKickoffMethod"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: ba084444-9e68-4cde-9388-54b950670987
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 866632b3916cd2e35e7832c4d58b5988fa350c52
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedasyncmethodgetkickoffmethod-method"></a><span data-ttu-id="c8ea7-102">Método ISymUnmanagedAsyncMethod::GetKickoffMethod</span><span class="sxs-lookup"><span data-stu-id="c8ea7-102">ISymUnmanagedAsyncMethod::GetKickoffMethod Method</span></span>
<span data-ttu-id="c8ea7-103">Consulte [método DefineKickoffMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span><span class="sxs-lookup"><span data-stu-id="c8ea7-103">See [DefineKickoffMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8ea7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c8ea7-104">Syntax</span></span>  
  
```idl  
HRESULT GetKickoffMethod(    [out, retval] mdToken* kickoffMethod);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c8ea7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c8ea7-105">Parameters</span></span>  
  
|<span data-ttu-id="c8ea7-106">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="c8ea7-106">Parameter</span></span>|<span data-ttu-id="c8ea7-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="c8ea7-107">Description</span></span>|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="c8ea7-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="c8ea7-108">Return Value</span></span>  
 <span data-ttu-id="c8ea7-109">Retorna `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="c8ea7-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8ea7-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c8ea7-110">Requirements</span></span>  
 <span data-ttu-id="c8ea7-111">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c8ea7-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8ea7-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c8ea7-112">See Also</span></span>  
 [<span data-ttu-id="c8ea7-113">Interface ISymUnmanagedAsyncMethod</span><span class="sxs-lookup"><span data-stu-id="c8ea7-113">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
