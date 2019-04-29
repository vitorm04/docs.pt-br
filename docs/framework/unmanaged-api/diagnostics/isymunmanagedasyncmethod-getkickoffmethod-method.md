---
title: Método ISymUnmanagedAsyncMethod::GetKickoffMethod
ms.date: 03/30/2017
ms.assetid: ba084444-9e68-4cde-9388-54b950670987
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4599d41336778db8ce8dcf3ac567e4e2cc8833e6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61940199"
---
# <a name="isymunmanagedasyncmethodgetkickoffmethod-method"></a><span data-ttu-id="31be0-102">Método ISymUnmanagedAsyncMethod::GetKickoffMethod</span><span class="sxs-lookup"><span data-stu-id="31be0-102">ISymUnmanagedAsyncMethod::GetKickoffMethod Method</span></span>
<span data-ttu-id="31be0-103">Ver [método DefineKickoffMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span><span class="sxs-lookup"><span data-stu-id="31be0-103">See [DefineKickoffMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31be0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="31be0-104">Syntax</span></span>  
  
```idl  
HRESULT GetKickoffMethod(    [out, retval] mdToken* kickoffMethod);  
```  
  
## <a name="parameters"></a><span data-ttu-id="31be0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="31be0-105">Parameters</span></span>  
  
|<span data-ttu-id="31be0-106">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="31be0-106">Parameter</span></span>|<span data-ttu-id="31be0-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="31be0-107">Description</span></span>|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="31be0-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="31be0-108">Return Value</span></span>  
 <span data-ttu-id="31be0-109">Retorna `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="31be0-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31be0-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="31be0-110">Requirements</span></span>  
 <span data-ttu-id="31be0-111">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="31be0-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31be0-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="31be0-112">See also</span></span>

- [<span data-ttu-id="31be0-113">Interface ISymUnmanagedAsyncMethod</span><span class="sxs-lookup"><span data-stu-id="31be0-113">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
