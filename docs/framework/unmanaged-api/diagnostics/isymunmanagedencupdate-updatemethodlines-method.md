---
title: Método ISymUnmanagedENCUpdate::UpdateMethodLines
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 54789003f7454a65449e55ea4d990edd672d9c1b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67774689"
---
# <a name="isymunmanagedencupdateupdatemethodlines-method"></a><span data-ttu-id="b177a-102">Método ISymUnmanagedENCUpdate::UpdateMethodLines</span><span class="sxs-lookup"><span data-stu-id="b177a-102">ISymUnmanagedENCUpdate::UpdateMethodLines Method</span></span>
<span data-ttu-id="b177a-103">Permite atualizar as informações de linha para um método que não foram recompilado, mas cujas linhas foram movidas de forma independente.</span><span class="sxs-lookup"><span data-stu-id="b177a-103">Allows updating the line information for a method that has not been recompiled, but whose lines have moved independently.</span></span> <span data-ttu-id="b177a-104">Um delta para cada instrução é permitido.</span><span class="sxs-lookup"><span data-stu-id="b177a-104">A delta for each statement is allowed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b177a-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b177a-105">Syntax</span></span>  
  
```cpp  
HRESULT UpdateMethodLines(  
    [in]  mdMethodDef  mdMethodToken,  
    [in, size_is(cDeltas)] INT32*  pDeltas,  
    [in]  ULONG        cDeltas);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b177a-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b177a-106">Parameters</span></span>  
 `mdMethodToken`  
 <span data-ttu-id="b177a-107">[in] Os metadados do token de método.</span><span class="sxs-lookup"><span data-stu-id="b177a-107">[in] The metadata of the method token.</span></span>  
  
 `pDeltas`  
 <span data-ttu-id="b177a-108">[in] Uma matriz de `INT32` valores que indicam os deltas para cada ponto de sequência no método.</span><span class="sxs-lookup"><span data-stu-id="b177a-108">[in] An array of `INT32` values that indicates deltas for each sequence point in the method.</span></span>  
  
 `cDeltas`  
 <span data-ttu-id="b177a-109">[in] Um `ULONG` que contém o tamanho de `pDeltas` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="b177a-109">[in] A `ULONG` containing the size of the `pDeltas` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b177a-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="b177a-110">Return Value</span></span>  
 <span data-ttu-id="b177a-111">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="b177a-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b177a-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b177a-112">Requirements</span></span>  
 <span data-ttu-id="b177a-113">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b177a-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b177a-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b177a-114">See also</span></span>

- [<span data-ttu-id="b177a-115">Interface ISymUnmanagedENCUpdate</span><span class="sxs-lookup"><span data-stu-id="b177a-115">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)
