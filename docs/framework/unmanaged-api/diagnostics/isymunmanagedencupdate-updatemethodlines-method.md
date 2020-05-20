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
ms.openlocfilehash: 9a490299c24f44b59da682f714f4b696fde3cba5
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614507"
---
# <a name="isymunmanagedencupdateupdatemethodlines-method"></a><span data-ttu-id="7c34b-102">Método ISymUnmanagedENCUpdate::UpdateMethodLines</span><span class="sxs-lookup"><span data-stu-id="7c34b-102">ISymUnmanagedENCUpdate::UpdateMethodLines Method</span></span>
<span data-ttu-id="7c34b-103">Permite atualizar as informações de linha de um método que não foi recompilado, mas cujas linhas foram movidas de forma independente.</span><span class="sxs-lookup"><span data-stu-id="7c34b-103">Allows updating the line information for a method that has not been recompiled, but whose lines have moved independently.</span></span> <span data-ttu-id="7c34b-104">Um Delta para cada instrução é permitido.</span><span class="sxs-lookup"><span data-stu-id="7c34b-104">A delta for each statement is allowed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c34b-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7c34b-105">Syntax</span></span>  
  
```cpp  
HRESULT UpdateMethodLines(  
    [in]  mdMethodDef  mdMethodToken,  
    [in, size_is(cDeltas)] INT32*  pDeltas,  
    [in]  ULONG        cDeltas);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7c34b-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7c34b-106">Parameters</span></span>  
 `mdMethodToken`  
 <span data-ttu-id="7c34b-107">no Os metadados do token do método.</span><span class="sxs-lookup"><span data-stu-id="7c34b-107">[in] The metadata of the method token.</span></span>  
  
 `pDeltas`  
 <span data-ttu-id="7c34b-108">no Uma matriz de `INT32` valores que indica deltas para cada ponto de sequência no método.</span><span class="sxs-lookup"><span data-stu-id="7c34b-108">[in] An array of `INT32` values that indicates deltas for each sequence point in the method.</span></span>  
  
 `cDeltas`  
 <span data-ttu-id="7c34b-109">no Um `ULONG` valor que contém o tamanho do `pDeltas` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="7c34b-109">[in] A `ULONG` containing the size of the `pDeltas` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7c34b-110">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="7c34b-110">Return Value</span></span>  
 <span data-ttu-id="7c34b-111">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="7c34b-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c34b-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7c34b-112">Requirements</span></span>  
 <span data-ttu-id="7c34b-113">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="7c34b-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c34b-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="7c34b-114">See also</span></span>

- [<span data-ttu-id="7c34b-115">Interface ISymUnmanagedENCUpdate</span><span class="sxs-lookup"><span data-stu-id="7c34b-115">ISymUnmanagedENCUpdate Interface</span></span>](isymunmanagedencupdate-interface.md)
