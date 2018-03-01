---
title: "Método ISymUnmanagedENCUpdate::UpdateMethodLines"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ISymUnmanagedENCUpdate.UpdateMethodLines
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::UpdateMethodLines
helpviewer_keywords:
- UpdateMethodLines method [.NET Framework debugging]
- ISymUnmanagedENCUpdate::UpdateMethodLines method [.NET Framework debugging]
ms.assetid: 275ef87b-0b53-49f9-af6b-58506335dc06
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2e8ffecba62b6531c852e6510013ba56b9258b64
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedencupdateupdatemethodlines-method"></a><span data-ttu-id="bb63f-102">Método ISymUnmanagedENCUpdate::UpdateMethodLines</span><span class="sxs-lookup"><span data-stu-id="bb63f-102">ISymUnmanagedENCUpdate::UpdateMethodLines Method</span></span>
<span data-ttu-id="bb63f-103">Permite atualizar as informações de linha para um método que não foi recompilado, mas cujas linhas foram movidos independentemente.</span><span class="sxs-lookup"><span data-stu-id="bb63f-103">Allows updating the line information for a method that has not been recompiled, but whose lines have moved independently.</span></span> <span data-ttu-id="bb63f-104">Um delta para cada instrução é permitida.</span><span class="sxs-lookup"><span data-stu-id="bb63f-104">A delta for each statement is allowed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb63f-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bb63f-105">Syntax</span></span>  
  
```  
HRESULT UpdateMethodLines(  
    [in]  mdMethodDef  mdMethodToken,  
    [in, size_is(cDeltas)] INT32*  pDeltas,  
    [in]  ULONG        cDeltas);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bb63f-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bb63f-106">Parameters</span></span>  
 `mdMethodToken`  
 <span data-ttu-id="bb63f-107">[in] Os metadados do token de método.</span><span class="sxs-lookup"><span data-stu-id="bb63f-107">[in] The metadata of the method token.</span></span>  
  
 `pDeltas`  
 <span data-ttu-id="bb63f-108">[in] Uma matriz de `INT32` valores que indicam os deltas para cada ponto de sequência no método.</span><span class="sxs-lookup"><span data-stu-id="bb63f-108">[in] An array of `INT32` values that indicates deltas for each sequence point in the method.</span></span>  
  
 `cDeltas`  
 <span data-ttu-id="bb63f-109">[in] Um `ULONG` que contém o tamanho do `pDeltas` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="bb63f-109">[in] A `ULONG` containing the size of the `pDeltas` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bb63f-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="bb63f-110">Return Value</span></span>  
 <span data-ttu-id="bb63f-111">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="bb63f-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb63f-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bb63f-112">Requirements</span></span>  
 <span data-ttu-id="bb63f-113">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="bb63f-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb63f-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bb63f-114">See Also</span></span>  
 [<span data-ttu-id="bb63f-115">Interface ISymUnmanagedENCUpdate</span><span class="sxs-lookup"><span data-stu-id="bb63f-115">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)
