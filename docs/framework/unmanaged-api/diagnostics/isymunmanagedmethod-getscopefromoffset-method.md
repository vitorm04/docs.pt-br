---
title: Método ISymUnmanagedMethod::GetScopeFromOffset
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetScopeFromOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetScopeFromOffset
helpviewer_keywords:
- GetScopeFromOffset method [.NET Framework debugging]
- ISymUnmanagedMethod::GetScopeFromOffset method [.NET Framework debugging]
ms.assetid: d14cf210-81f8-46e1-8b19-6ddec0ba8b11
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5422e781ab2f494e85f637219aa540bf4ac34cb8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54629729"
---
# <a name="isymunmanagedmethodgetscopefromoffset-method"></a><span data-ttu-id="6ce11-102">Método ISymUnmanagedMethod::GetScopeFromOffset</span><span class="sxs-lookup"><span data-stu-id="6ce11-102">ISymUnmanagedMethod::GetScopeFromOffset Method</span></span>
<span data-ttu-id="6ce11-103">Obtém o escopo léxico mais delimitador dentro desse método que inclui o deslocamento especificado.</span><span class="sxs-lookup"><span data-stu-id="6ce11-103">Gets the most enclosing lexical scope within this method that encloses the given offset.</span></span> <span data-ttu-id="6ce11-104">Isso pode ser usado para iniciar a pesquisa de variável local.</span><span class="sxs-lookup"><span data-stu-id="6ce11-104">This can be used to start local variable searches.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ce11-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6ce11-105">Syntax</span></span>  
  
```  
HRESULT GetScopeFromOffset(  
    [in]  ULONG32 offset,  
    [out, retval] ISymUnmanagedScope**  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6ce11-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6ce11-106">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="6ce11-107">[in] Um `ULONG` que contém o deslocamento.</span><span class="sxs-lookup"><span data-stu-id="6ce11-107">[in] A `ULONG` that contains the offset.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="6ce11-108">[out] Um ponteiro que é definido para retornado [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="6ce11-108">[out] A pointer that is set to the returned [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6ce11-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="6ce11-109">Return Value</span></span>  
 <span data-ttu-id="6ce11-110">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="6ce11-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ce11-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6ce11-111">Requirements</span></span>  
 <span data-ttu-id="6ce11-112">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="6ce11-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ce11-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6ce11-113">See also</span></span>
- [<span data-ttu-id="6ce11-114">Interface ISymUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="6ce11-114">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
