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
ms.openlocfilehash: b765294826a5da4010cdd2db79b50667a6f1cdb4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446309"
---
# <a name="isymunmanagedscopegetnamespaces-method"></a><span data-ttu-id="273ff-102">Método ISymUnmanagedScope::GetNamespaces</span><span class="sxs-lookup"><span data-stu-id="273ff-102">ISymUnmanagedScope::GetNamespaces Method</span></span>
<span data-ttu-id="273ff-103">Obtém os namespaces que estão sendo usados nesse escopo.</span><span class="sxs-lookup"><span data-stu-id="273ff-103">Gets the namespaces that are being used within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="273ff-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="273ff-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNamespaces(  
    [in]  ULONG32  cNameSpaces,  
    [out] ULONG32  *pcNameSpaces,  
    [out, size_is(cNameSpaces),  
        length_is(*pcNameSpaces)]  
        ISymUnmanagedNamespace* namespaces[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="273ff-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="273ff-105">Parameters</span></span>  
 `cNameSpaces`  
 <span data-ttu-id="273ff-106">no O tamanho da matriz de `namespaces`.</span><span class="sxs-lookup"><span data-stu-id="273ff-106">[in] The size of the `namespaces` array.</span></span>  
  
 `pcNameSpaces`  
 <span data-ttu-id="273ff-107">fora Um ponteiro para um `ULONG32` que recebe o tamanho do buffer necessário para conter os namespaces.</span><span class="sxs-lookup"><span data-stu-id="273ff-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the namespaces.</span></span>  
  
 `namespaces`  
 <span data-ttu-id="273ff-108">fora A matriz que recebe os namespaces.</span><span class="sxs-lookup"><span data-stu-id="273ff-108">[out] The array that receives the namespaces.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="273ff-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="273ff-109">Return Value</span></span>  
 <span data-ttu-id="273ff-110">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="273ff-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="273ff-111">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="273ff-111">Requirements</span></span>  
 <span data-ttu-id="273ff-112">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="273ff-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="273ff-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="273ff-113">See also</span></span>

- [<span data-ttu-id="273ff-114">Interface ISymUnmanagedScope</span><span class="sxs-lookup"><span data-stu-id="273ff-114">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
