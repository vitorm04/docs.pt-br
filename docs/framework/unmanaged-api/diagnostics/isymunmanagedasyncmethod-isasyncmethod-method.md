---
title: Método ISymUnmanagedAsyncMethod::IsAsyncMethod
ms.date: 03/30/2017
ms.assetid: 670a7653-dac6-4171-98ee-d669e3adf4b2
ms.openlocfilehash: 91b4c2688dadf12fa4a835a662622267d7831cf8
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441793"
---
# <a name="isymunmanagedasyncmethodisasyncmethod-method"></a><span data-ttu-id="91b6e-102">Método ISymUnmanagedAsyncMethod::IsAsyncMethod</span><span class="sxs-lookup"><span data-stu-id="91b6e-102">ISymUnmanagedAsyncMethod::IsAsyncMethod Method</span></span>
<span data-ttu-id="91b6e-103">Verifica se o método tem informações assíncronas ou não.</span><span class="sxs-lookup"><span data-stu-id="91b6e-103">Checks if the method has async information or not.</span></span>  
  
 <span data-ttu-id="91b6e-104">Se esse método retornar `FALSE` , ele será inválido para chamar outros métodos nesta interface.</span><span class="sxs-lookup"><span data-stu-id="91b6e-104">If this method returns `FALSE` then it is invalid to call any other methods in this interface.</span></span> <span data-ttu-id="91b6e-105">Eles serão retornados `E_UNEXPECTED` nesse caso.</span><span class="sxs-lookup"><span data-stu-id="91b6e-105">They will all return `E_UNEXPECTED` in this case.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91b6e-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="91b6e-106">Syntax</span></span>  
  
```idl  
HRESULT IsAsyncMethod(    [out, retval] BOOL* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="91b6e-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="91b6e-107">Parameters</span></span>  
  
|<span data-ttu-id="91b6e-108">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="91b6e-108">Parameter</span></span>|<span data-ttu-id="91b6e-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="91b6e-109">Description</span></span>|  
|---------------|-----------------|  
|`pRetVal`||  
  
## <a name="return-value"></a><span data-ttu-id="91b6e-110">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="91b6e-110">Return Value</span></span>  
 <span data-ttu-id="91b6e-111">Retorna `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="91b6e-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91b6e-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="91b6e-112">Requirements</span></span>  
 <span data-ttu-id="91b6e-113">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="91b6e-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91b6e-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="91b6e-114">See also</span></span>

- [<span data-ttu-id="91b6e-115">Interface ISymUnmanagedAsyncMethod</span><span class="sxs-lookup"><span data-stu-id="91b6e-115">ISymUnmanagedAsyncMethod Interface</span></span>](isymunmanagedasyncmethod-interface.md)
