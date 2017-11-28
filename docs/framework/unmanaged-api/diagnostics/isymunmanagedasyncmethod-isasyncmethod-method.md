---
title: "Método ISymUnmanagedAsyncMethod::IsAsyncMethod"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 670a7653-dac6-4171-98ee-d669e3adf4b2
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ce91552d7468579d9941c1da75c4d281999d66fd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedasyncmethodisasyncmethod-method"></a><span data-ttu-id="ae796-102">Método ISymUnmanagedAsyncMethod::IsAsyncMethod</span><span class="sxs-lookup"><span data-stu-id="ae796-102">ISymUnmanagedAsyncMethod::IsAsyncMethod Method</span></span>
<span data-ttu-id="ae796-103">Verifica se o método tem informações assíncrono ou não.</span><span class="sxs-lookup"><span data-stu-id="ae796-103">Checks if the method has async information or not.</span></span>  
  
 <span data-ttu-id="ae796-104">Se esse método retornar `FALSE` é inválido chamar outros métodos nessa interface.</span><span class="sxs-lookup"><span data-stu-id="ae796-104">If this method returns `FALSE` then it is invalid to call any other methods in this interface.</span></span> <span data-ttu-id="ae796-105">Eles serão retornar todos os `E_UNEXPECTED` nesse caso.</span><span class="sxs-lookup"><span data-stu-id="ae796-105">They will all return `E_UNEXPECTED` in this case.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae796-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ae796-106">Syntax</span></span>  
  
```idl  
HRESULT IsAsyncMethod(    [out, retval] BOOL* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ae796-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ae796-107">Parameters</span></span>  
  
|<span data-ttu-id="ae796-108">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="ae796-108">Parameter</span></span>|<span data-ttu-id="ae796-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="ae796-109">Description</span></span>|  
|---------------|-----------------|  
|`pRetVal`||  
  
## <a name="return-value"></a><span data-ttu-id="ae796-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="ae796-110">Return Value</span></span>  
 <span data-ttu-id="ae796-111">Retorna `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="ae796-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae796-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ae796-112">Requirements</span></span>  
 <span data-ttu-id="ae796-113">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ae796-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae796-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ae796-114">See Also</span></span>  
 [<span data-ttu-id="ae796-115">Interface ISymUnmanagedAsyncMethod</span><span class="sxs-lookup"><span data-stu-id="ae796-115">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
