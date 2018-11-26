---
title: Método ISymUnmanagedENCUpdate::GetLocalVariables
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate.GetLocalVariables
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariables
helpviewer_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariables method [.NET Framework debugging]
- GetLocalVariables method [.NET Framework debugging]
ms.assetid: 5c8840be-ffea-447f-9c8d-178f1eaf8d06
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a53493d666cb16fcc9b407ca3a46072afa306b97
ms.sourcegitcommit: 35316b768394e56087483cde93f854ba607b63bc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2018
ms.locfileid: "52297550"
---
# <a name="isymunmanagedencupdategetlocalvariables-method"></a><span data-ttu-id="ca052-102">Método ISymUnmanagedENCUpdate::GetLocalVariables</span><span class="sxs-lookup"><span data-stu-id="ca052-102">ISymUnmanagedENCUpdate::GetLocalVariables Method</span></span>
<span data-ttu-id="ca052-103">Obtém as variáveis locais.</span><span class="sxs-lookup"><span data-stu-id="ca052-103">Gets the local variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca052-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ca052-104">Syntax</span></span>  
  
```  
HRESULT GetLocalVariables(  
    [in]  mdMethodDef  mdMethodToken,  
    [in]  ULONG        cLocals,  
    [out, size_is(cLocals), length_is(*pceltFetched)]  
        ISymUnmanagedVariable *rgLocals[],  
    [out] ULONG        *pceltFetched);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ca052-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ca052-105">Parameters</span></span>  
 `mdMethodToken`  
 <span data-ttu-id="ca052-106">[in] O token de metadados do método.</span><span class="sxs-lookup"><span data-stu-id="ca052-106">[in] The metadata token of the method.</span></span>  
  
 `cLocals`  
 <span data-ttu-id="ca052-107">[in] Um `ULONG` que indica o tamanho do `rgLocals` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="ca052-107">[in] A `ULONG` that indicates the size of the `rgLocals` parameter.</span></span>  
  
 `rgLocals`  
 <span data-ttu-id="ca052-108">[out] A matriz retornada de [ISymUnmanagedVariable](isymunmanagedvariable-interface.md) instâncias.</span><span class="sxs-lookup"><span data-stu-id="ca052-108">[out] The returned array of [ISymUnmanagedVariable](isymunmanagedvariable-interface.md) instances.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="ca052-109">[out] Um ponteiro para um `ULONG` que recebe o tamanho do `rgLocals` buffer necessário para conter os locais.</span><span class="sxs-lookup"><span data-stu-id="ca052-109">[out] A pointer to a `ULONG` that receives the size of the `rgLocals` buffer required to contain the locals.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ca052-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="ca052-110">Return Value</span></span>  
 <span data-ttu-id="ca052-111">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="ca052-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca052-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ca052-112">Requirements</span></span>  
 <span data-ttu-id="ca052-113">**Cabeçalho:** Corsym, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ca052-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca052-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ca052-114">See Also</span></span>  
 [<span data-ttu-id="ca052-115">Interface ISymUnmanagedENCUpdate</span><span class="sxs-lookup"><span data-stu-id="ca052-115">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)
