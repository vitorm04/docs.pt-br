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
ms.openlocfilehash: bd1f101e2e9cf9baeb28290c7607ccab3d8d7440
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61939679"
---
# <a name="isymunmanagedencupdateupdatemethodlines-method"></a><span data-ttu-id="6df89-102">Método ISymUnmanagedENCUpdate::UpdateMethodLines</span><span class="sxs-lookup"><span data-stu-id="6df89-102">ISymUnmanagedENCUpdate::UpdateMethodLines Method</span></span>
<span data-ttu-id="6df89-103">Permite atualizar as informações de linha para um método que não foram recompilado, mas cujas linhas foram movidas de forma independente.</span><span class="sxs-lookup"><span data-stu-id="6df89-103">Allows updating the line information for a method that has not been recompiled, but whose lines have moved independently.</span></span> <span data-ttu-id="6df89-104">Um delta para cada instrução é permitido.</span><span class="sxs-lookup"><span data-stu-id="6df89-104">A delta for each statement is allowed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6df89-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6df89-105">Syntax</span></span>  
  
```  
HRESULT UpdateMethodLines(  
    [in]  mdMethodDef  mdMethodToken,  
    [in, size_is(cDeltas)] INT32*  pDeltas,  
    [in]  ULONG        cDeltas);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6df89-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6df89-106">Parameters</span></span>  
 `mdMethodToken`  
 <span data-ttu-id="6df89-107">[in] Os metadados do token de método.</span><span class="sxs-lookup"><span data-stu-id="6df89-107">[in] The metadata of the method token.</span></span>  
  
 `pDeltas`  
 <span data-ttu-id="6df89-108">[in] Uma matriz de `INT32` valores que indicam os deltas para cada ponto de sequência no método.</span><span class="sxs-lookup"><span data-stu-id="6df89-108">[in] An array of `INT32` values that indicates deltas for each sequence point in the method.</span></span>  
  
 `cDeltas`  
 <span data-ttu-id="6df89-109">[in] Um `ULONG` que contém o tamanho de `pDeltas` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="6df89-109">[in] A `ULONG` containing the size of the `pDeltas` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6df89-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="6df89-110">Return Value</span></span>  
 <span data-ttu-id="6df89-111">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="6df89-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6df89-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6df89-112">Requirements</span></span>  
 <span data-ttu-id="6df89-113">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="6df89-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6df89-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6df89-114">See also</span></span>

- [<span data-ttu-id="6df89-115">Interface ISymUnmanagedENCUpdate</span><span class="sxs-lookup"><span data-stu-id="6df89-115">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)
