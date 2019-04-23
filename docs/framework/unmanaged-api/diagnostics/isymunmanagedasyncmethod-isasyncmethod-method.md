---
title: Método ISymUnmanagedAsyncMethod::IsAsyncMethod
ms.date: 03/30/2017
ms.assetid: 670a7653-dac6-4171-98ee-d669e3adf4b2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e5cddf34f1a6277e966901c9692bff63e26a3b8e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59136728"
---
# <a name="isymunmanagedasyncmethodisasyncmethod-method"></a><span data-ttu-id="36e4f-102">Método ISymUnmanagedAsyncMethod::IsAsyncMethod</span><span class="sxs-lookup"><span data-stu-id="36e4f-102">ISymUnmanagedAsyncMethod::IsAsyncMethod Method</span></span>
<span data-ttu-id="36e4f-103">Verifica se o método tem informações de async ou não.</span><span class="sxs-lookup"><span data-stu-id="36e4f-103">Checks if the method has async information or not.</span></span>  
  
 <span data-ttu-id="36e4f-104">Se esse método retornar `FALSE` é inválido chamar quaisquer outros métodos nessa interface.</span><span class="sxs-lookup"><span data-stu-id="36e4f-104">If this method returns `FALSE` then it is invalid to call any other methods in this interface.</span></span> <span data-ttu-id="36e4f-105">Eles serão retornam todos os `E_UNEXPECTED` nesse caso.</span><span class="sxs-lookup"><span data-stu-id="36e4f-105">They will all return `E_UNEXPECTED` in this case.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36e4f-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="36e4f-106">Syntax</span></span>  
  
```idl  
HRESULT IsAsyncMethod(    [out, retval] BOOL* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="36e4f-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="36e4f-107">Parameters</span></span>  
  
|<span data-ttu-id="36e4f-108">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="36e4f-108">Parameter</span></span>|<span data-ttu-id="36e4f-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="36e4f-109">Description</span></span>|  
|---------------|-----------------|  
|`pRetVal`||  
  
## <a name="return-value"></a><span data-ttu-id="36e4f-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="36e4f-110">Return Value</span></span>  
 <span data-ttu-id="36e4f-111">Retorna `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="36e4f-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36e4f-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="36e4f-112">Requirements</span></span>  
 <span data-ttu-id="36e4f-113">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="36e4f-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36e4f-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="36e4f-114">See also</span></span>

- [<span data-ttu-id="36e4f-115">Interface ISymUnmanagedAsyncMethod</span><span class="sxs-lookup"><span data-stu-id="36e4f-115">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
