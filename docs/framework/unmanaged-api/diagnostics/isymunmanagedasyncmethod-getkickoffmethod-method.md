---
title: Método ISymUnmanagedAsyncMethod::GetKickoffMethod
ms.date: 03/30/2017
ms.assetid: ba084444-9e68-4cde-9388-54b950670987
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4599d41336778db8ce8dcf3ac567e4e2cc8833e6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59174935"
---
# <a name="isymunmanagedasyncmethodgetkickoffmethod-method"></a><span data-ttu-id="ce9a3-102">Método ISymUnmanagedAsyncMethod::GetKickoffMethod</span><span class="sxs-lookup"><span data-stu-id="ce9a3-102">ISymUnmanagedAsyncMethod::GetKickoffMethod Method</span></span>
<span data-ttu-id="ce9a3-103">Ver [método DefineKickoffMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span><span class="sxs-lookup"><span data-stu-id="ce9a3-103">See [DefineKickoffMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce9a3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ce9a3-104">Syntax</span></span>  
  
```idl  
HRESULT GetKickoffMethod(    [out, retval] mdToken* kickoffMethod);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ce9a3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ce9a3-105">Parameters</span></span>  
  
|<span data-ttu-id="ce9a3-106">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="ce9a3-106">Parameter</span></span>|<span data-ttu-id="ce9a3-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="ce9a3-107">Description</span></span>|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="ce9a3-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="ce9a3-108">Return Value</span></span>  
 <span data-ttu-id="ce9a3-109">Retorna `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="ce9a3-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce9a3-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ce9a3-110">Requirements</span></span>  
 <span data-ttu-id="ce9a3-111">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ce9a3-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce9a3-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ce9a3-112">See also</span></span>

- [<span data-ttu-id="ce9a3-113">Interface ISymUnmanagedAsyncMethod</span><span class="sxs-lookup"><span data-stu-id="ce9a3-113">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
