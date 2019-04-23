---
title: Método ISymUnmanagedScope::GetNamespaces
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetNamespaces
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetNamespaces
helpviewer_keywords:
- GetNamespaces method, ISymUnmanagedScope interface [.NET Framework debugging]
- ISymUnmanagedScope::GetNamespaces method [.NET Framework debugging]
ms.assetid: c44b0440-04bd-460a-84fb-41afecf44503
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3dc3c842bbb4b86b82d03848751673400bed193b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59213032"
---
# <a name="isymunmanagedscopegetnamespaces-method"></a><span data-ttu-id="33c99-102">Método ISymUnmanagedScope::GetNamespaces</span><span class="sxs-lookup"><span data-stu-id="33c99-102">ISymUnmanagedScope::GetNamespaces Method</span></span>
<span data-ttu-id="33c99-103">Obtém os namespaces que estão sendo usados dentro desse escopo.</span><span class="sxs-lookup"><span data-stu-id="33c99-103">Gets the namespaces that are being used within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33c99-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="33c99-104">Syntax</span></span>  
  
```  
HRESULT GetNamespaces(  
    [in]  ULONG32  cNameSpaces,  
    [out] ULONG32  *pcNameSpaces,  
    [out, size_is(cNameSpaces),  
        length_is(*pcNameSpaces)]  
        ISymUnmanagedNamespace* namespaces[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="33c99-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="33c99-105">Parameters</span></span>  
 `cNameSpaces`  
 <span data-ttu-id="33c99-106">[in] O tamanho do `namespaces` matriz.</span><span class="sxs-lookup"><span data-stu-id="33c99-106">[in] The size of the `namespaces` array.</span></span>  
  
 `pcNameSpaces`  
 <span data-ttu-id="33c99-107">[out] Um ponteiro para um `ULONG32` que recebe o tamanho do buffer necessário para conter os namespaces.</span><span class="sxs-lookup"><span data-stu-id="33c99-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the namespaces.</span></span>  
  
 `namespaces`  
 <span data-ttu-id="33c99-108">[out] A matriz que recebe os namespaces.</span><span class="sxs-lookup"><span data-stu-id="33c99-108">[out] The array that receives the namespaces.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="33c99-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="33c99-109">Return Value</span></span>  
 <span data-ttu-id="33c99-110">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="33c99-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33c99-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="33c99-111">Requirements</span></span>  
 <span data-ttu-id="33c99-112">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="33c99-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33c99-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="33c99-113">See also</span></span>

- [<span data-ttu-id="33c99-114">Interface ISymUnmanagedScope</span><span class="sxs-lookup"><span data-stu-id="33c99-114">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
