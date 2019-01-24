---
title: Método ISymUnmanagedAsyncMethod::GetKickoffMethod
ms.date: 03/30/2017
ms.assetid: ba084444-9e68-4cde-9388-54b950670987
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f20039318d6e1230ccc0fbd203fc44686806bb2e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54604464"
---
# <a name="isymunmanagedasyncmethodgetkickoffmethod-method"></a><span data-ttu-id="63f7b-102">Método ISymUnmanagedAsyncMethod::GetKickoffMethod</span><span class="sxs-lookup"><span data-stu-id="63f7b-102">ISymUnmanagedAsyncMethod::GetKickoffMethod Method</span></span>
<span data-ttu-id="63f7b-103">Ver [método DefineKickoffMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span><span class="sxs-lookup"><span data-stu-id="63f7b-103">See [DefineKickoffMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63f7b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="63f7b-104">Syntax</span></span>  
  
```idl  
HRESULT GetKickoffMethod(    [out, retval] mdToken* kickoffMethod);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="63f7b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="63f7b-105">Parameters</span></span>  
  
|<span data-ttu-id="63f7b-106">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="63f7b-106">Parameter</span></span>|<span data-ttu-id="63f7b-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="63f7b-107">Description</span></span>|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="63f7b-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="63f7b-108">Return Value</span></span>  
 <span data-ttu-id="63f7b-109">Retorna `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="63f7b-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63f7b-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="63f7b-110">Requirements</span></span>  
 <span data-ttu-id="63f7b-111">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="63f7b-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63f7b-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="63f7b-112">See also</span></span>
- [<span data-ttu-id="63f7b-113">Interface ISymUnmanagedAsyncMethod</span><span class="sxs-lookup"><span data-stu-id="63f7b-113">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
