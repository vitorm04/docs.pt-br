---
title: Método ISymUnmanagedAsyncMethod::IsAsyncMethod
ms.date: 03/30/2017
ms.assetid: 670a7653-dac6-4171-98ee-d669e3adf4b2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 460d6781405b6042262d50e1aa79ee8c77f781a7
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57489716"
---
# <a name="isymunmanagedasyncmethodisasyncmethod-method"></a><span data-ttu-id="56b25-102">Método ISymUnmanagedAsyncMethod::IsAsyncMethod</span><span class="sxs-lookup"><span data-stu-id="56b25-102">ISymUnmanagedAsyncMethod::IsAsyncMethod Method</span></span>
<span data-ttu-id="56b25-103">Verifica se o método tem informações de async ou não.</span><span class="sxs-lookup"><span data-stu-id="56b25-103">Checks if the method has async information or not.</span></span>  
  
 <span data-ttu-id="56b25-104">Se esse método retornar `FALSE` é inválido chamar quaisquer outros métodos nessa interface.</span><span class="sxs-lookup"><span data-stu-id="56b25-104">If this method returns `FALSE` then it is invalid to call any other methods in this interface.</span></span> <span data-ttu-id="56b25-105">Eles serão retornam todos os `E_UNEXPECTED` nesse caso.</span><span class="sxs-lookup"><span data-stu-id="56b25-105">They will all return `E_UNEXPECTED` in this case.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56b25-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="56b25-106">Syntax</span></span>  
  
```idl  
HRESULT IsAsyncMethod(    [out, retval] BOOL* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="56b25-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="56b25-107">Parameters</span></span>  
  
|<span data-ttu-id="56b25-108">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="56b25-108">Parameter</span></span>|<span data-ttu-id="56b25-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="56b25-109">Description</span></span>|  
|---------------|-----------------|  
|`pRetVal`||  
  
## <a name="return-value"></a><span data-ttu-id="56b25-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="56b25-110">Return Value</span></span>  
 <span data-ttu-id="56b25-111">Retorna `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="56b25-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56b25-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="56b25-112">Requirements</span></span>  
 <span data-ttu-id="56b25-113">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="56b25-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56b25-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="56b25-114">See also</span></span>
- [<span data-ttu-id="56b25-115">Interface ISymUnmanagedAsyncMethod</span><span class="sxs-lookup"><span data-stu-id="56b25-115">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
