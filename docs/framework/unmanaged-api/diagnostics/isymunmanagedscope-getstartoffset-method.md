---
title: Método ISymUnmanagedScope::GetStartOffset
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetStartOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetStartOffset
helpviewer_keywords:
- GetStartOffset method, ISymUnmanagedScope interface [.NET Framework debugging]
- ISymUnmanagedScope::GetStartOffset method [.NET Framework debugging]
ms.assetid: da6bbc75-94d1-4354-9722-0d455b4428fb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2b81ac93c67d59c294f22eb825527fa9982d9124
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54721091"
---
# <a name="isymunmanagedscopegetstartoffset-method"></a><span data-ttu-id="c9679-102">Método ISymUnmanagedScope::GetStartOffset</span><span class="sxs-lookup"><span data-stu-id="c9679-102">ISymUnmanagedScope::GetStartOffset Method</span></span>
<span data-ttu-id="c9679-103">Obtém o deslocamento de início para esse escopo.</span><span class="sxs-lookup"><span data-stu-id="c9679-103">Gets the start offset for this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9679-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c9679-104">Syntax</span></span>  
  
```  
HRESULT GetStartOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c9679-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c9679-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="c9679-106">[out] Um ponteiro para um `ULONG32` que contém o deslocamento inicial.</span><span class="sxs-lookup"><span data-stu-id="c9679-106">[out] A pointer to a `ULONG32` that contains the starting offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c9679-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="c9679-107">Return Value</span></span>  
 <span data-ttu-id="c9679-108">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="c9679-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9679-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c9679-109">Requirements</span></span>  
 <span data-ttu-id="c9679-110">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c9679-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9679-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c9679-111">See also</span></span>
- [<span data-ttu-id="c9679-112">Interface ISymUnmanagedScope</span><span class="sxs-lookup"><span data-stu-id="c9679-112">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
- [<span data-ttu-id="c9679-113">Método GetEndOffset</span><span class="sxs-lookup"><span data-stu-id="c9679-113">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getendoffset-method.md)
