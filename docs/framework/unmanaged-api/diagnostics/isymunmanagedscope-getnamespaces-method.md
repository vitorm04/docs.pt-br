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
ms.openlocfilehash: d2c64d7ead2f7ce3d76b40f4fdc604506ee85561
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777882"
---
# <a name="isymunmanagedscopegetnamespaces-method"></a><span data-ttu-id="da8e0-102">Método ISymUnmanagedScope::GetNamespaces</span><span class="sxs-lookup"><span data-stu-id="da8e0-102">ISymUnmanagedScope::GetNamespaces Method</span></span>
<span data-ttu-id="da8e0-103">Obtém os namespaces que estão sendo usados dentro desse escopo.</span><span class="sxs-lookup"><span data-stu-id="da8e0-103">Gets the namespaces that are being used within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da8e0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="da8e0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNamespaces(  
    [in]  ULONG32  cNameSpaces,  
    [out] ULONG32  *pcNameSpaces,  
    [out, size_is(cNameSpaces),  
        length_is(*pcNameSpaces)]  
        ISymUnmanagedNamespace* namespaces[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="da8e0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="da8e0-105">Parameters</span></span>  
 `cNameSpaces`  
 <span data-ttu-id="da8e0-106">[in] O tamanho do `namespaces` matriz.</span><span class="sxs-lookup"><span data-stu-id="da8e0-106">[in] The size of the `namespaces` array.</span></span>  
  
 `pcNameSpaces`  
 <span data-ttu-id="da8e0-107">[out] Um ponteiro para um `ULONG32` que recebe o tamanho do buffer necessário para conter os namespaces.</span><span class="sxs-lookup"><span data-stu-id="da8e0-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the namespaces.</span></span>  
  
 `namespaces`  
 <span data-ttu-id="da8e0-108">[out] A matriz que recebe os namespaces.</span><span class="sxs-lookup"><span data-stu-id="da8e0-108">[out] The array that receives the namespaces.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="da8e0-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="da8e0-109">Return Value</span></span>  
 <span data-ttu-id="da8e0-110">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="da8e0-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da8e0-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="da8e0-111">Requirements</span></span>  
 <span data-ttu-id="da8e0-112">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="da8e0-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da8e0-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="da8e0-113">See also</span></span>

- [<span data-ttu-id="da8e0-114">Interface ISymUnmanagedScope</span><span class="sxs-lookup"><span data-stu-id="da8e0-114">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
