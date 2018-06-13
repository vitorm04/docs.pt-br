---
title: Método ISymUnmanagedAsyncMethod::IsAsyncMethod
ms.date: 03/30/2017
ms.assetid: 670a7653-dac6-4171-98ee-d669e3adf4b2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3f5bf8252986ffa90ea5380d5342595cb91e5419
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33424935"
---
# <a name="isymunmanagedasyncmethodisasyncmethod-method"></a><span data-ttu-id="b4df6-102">Método ISymUnmanagedAsyncMethod::IsAsyncMethod</span><span class="sxs-lookup"><span data-stu-id="b4df6-102">ISymUnmanagedAsyncMethod::IsAsyncMethod Method</span></span>
<span data-ttu-id="b4df6-103">Verifica se o método tem informações assíncrono ou não.</span><span class="sxs-lookup"><span data-stu-id="b4df6-103">Checks if the method has async information or not.</span></span>  
  
 <span data-ttu-id="b4df6-104">Se esse método retornar `FALSE` é inválido chamar outros métodos nessa interface.</span><span class="sxs-lookup"><span data-stu-id="b4df6-104">If this method returns `FALSE` then it is invalid to call any other methods in this interface.</span></span> <span data-ttu-id="b4df6-105">Eles serão retornar todos os `E_UNEXPECTED` nesse caso.</span><span class="sxs-lookup"><span data-stu-id="b4df6-105">They will all return `E_UNEXPECTED` in this case.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4df6-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b4df6-106">Syntax</span></span>  
  
```idl  
HRESULT IsAsyncMethod(    [out, retval] BOOL* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b4df6-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b4df6-107">Parameters</span></span>  
  
|<span data-ttu-id="b4df6-108">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="b4df6-108">Parameter</span></span>|<span data-ttu-id="b4df6-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="b4df6-109">Description</span></span>|  
|---------------|-----------------|  
|`pRetVal`||  
  
## <a name="return-value"></a><span data-ttu-id="b4df6-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="b4df6-110">Return Value</span></span>  
 <span data-ttu-id="b4df6-111">Retorna `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="b4df6-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4df6-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b4df6-112">Requirements</span></span>  
 <span data-ttu-id="b4df6-113">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b4df6-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4df6-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b4df6-114">See Also</span></span>  
 [<span data-ttu-id="b4df6-115">Interface ISymUnmanagedAsyncMethod</span><span class="sxs-lookup"><span data-stu-id="b4df6-115">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
