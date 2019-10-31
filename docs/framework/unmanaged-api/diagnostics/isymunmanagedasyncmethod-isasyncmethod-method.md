---
title: Método ISymUnmanagedAsyncMethod::IsAsyncMethod
ms.date: 03/30/2017
ms.assetid: 670a7653-dac6-4171-98ee-d669e3adf4b2
ms.openlocfilehash: 0ea4c21e9e6a49d7bbbad5e1853598c440cd6410
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129205"
---
# <a name="isymunmanagedasyncmethodisasyncmethod-method"></a><span data-ttu-id="d2bcd-102">Método ISymUnmanagedAsyncMethod::IsAsyncMethod</span><span class="sxs-lookup"><span data-stu-id="d2bcd-102">ISymUnmanagedAsyncMethod::IsAsyncMethod Method</span></span>
<span data-ttu-id="d2bcd-103">Verifica se o método tem informações assíncronas ou não.</span><span class="sxs-lookup"><span data-stu-id="d2bcd-103">Checks if the method has async information or not.</span></span>  
  
 <span data-ttu-id="d2bcd-104">Se esse método retornar `FALSE`, ele não será válido para chamar outros métodos nesta interface.</span><span class="sxs-lookup"><span data-stu-id="d2bcd-104">If this method returns `FALSE` then it is invalid to call any other methods in this interface.</span></span> <span data-ttu-id="d2bcd-105">Eles serão retornados `E_UNEXPECTED` nesse caso.</span><span class="sxs-lookup"><span data-stu-id="d2bcd-105">They will all return `E_UNEXPECTED` in this case.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2bcd-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d2bcd-106">Syntax</span></span>  
  
```idl  
HRESULT IsAsyncMethod(    [out, retval] BOOL* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d2bcd-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d2bcd-107">Parameters</span></span>  
  
|<span data-ttu-id="d2bcd-108">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="d2bcd-108">Parameter</span></span>|<span data-ttu-id="d2bcd-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="d2bcd-109">Description</span></span>|  
|---------------|-----------------|  
|`pRetVal`||  
  
## <a name="return-value"></a><span data-ttu-id="d2bcd-110">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="d2bcd-110">Return Value</span></span>  
 <span data-ttu-id="d2bcd-111">Retorna `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="d2bcd-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2bcd-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d2bcd-112">Requirements</span></span>  
 <span data-ttu-id="d2bcd-113">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="d2bcd-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2bcd-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d2bcd-114">See also</span></span>

- [<span data-ttu-id="d2bcd-115">Interface ISymUnmanagedAsyncMethod</span><span class="sxs-lookup"><span data-stu-id="d2bcd-115">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
