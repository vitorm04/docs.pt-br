---
title: "Método ISymUnmanagedScope::GetNamespaces"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedScope.GetNamespaces
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedScope::GetNamespaces
helpviewer_keywords:
- GetNamespaces method, ISymUnmanagedScope interface [.NET Framework debugging]
- ISymUnmanagedScope::GetNamespaces method [.NET Framework debugging]
ms.assetid: c44b0440-04bd-460a-84fb-41afecf44503
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 641ce6c4587f9f23743a3c1b5a1aeb6fb77edde7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedscopegetnamespaces-method"></a><span data-ttu-id="9e816-102">Método ISymUnmanagedScope::GetNamespaces</span><span class="sxs-lookup"><span data-stu-id="9e816-102">ISymUnmanagedScope::GetNamespaces Method</span></span>
<span data-ttu-id="9e816-103">Obtém os namespaces que estão sendo usados dentro desse escopo.</span><span class="sxs-lookup"><span data-stu-id="9e816-103">Gets the namespaces that are being used within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e816-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9e816-104">Syntax</span></span>  
  
```  
HRESULT GetNamespaces(  
    [in]  ULONG32  cNameSpaces,  
    [out] ULONG32  *pcNameSpaces,  
    [out, size_is(cNameSpaces),  
        length_is(*pcNameSpaces)]  
        ISymUnmanagedNamespace* namespaces[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9e816-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9e816-105">Parameters</span></span>  
 `cNameSpaces`  
 <span data-ttu-id="9e816-106">[in] O tamanho do `namespaces` matriz.</span><span class="sxs-lookup"><span data-stu-id="9e816-106">[in] The size of the `namespaces` array.</span></span>  
  
 `pcNameSpaces`  
 <span data-ttu-id="9e816-107">[out] Um ponteiro para um `ULONG32` que recebe o tamanho do buffer necessário para conter os namespaces.</span><span class="sxs-lookup"><span data-stu-id="9e816-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the namespaces.</span></span>  
  
 `namespaces`  
 <span data-ttu-id="9e816-108">[out] A matriz que recebe os namespaces.</span><span class="sxs-lookup"><span data-stu-id="9e816-108">[out] The array that receives the namespaces.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9e816-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="9e816-109">Return Value</span></span>  
 <span data-ttu-id="9e816-110">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="9e816-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e816-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9e816-111">Requirements</span></span>  
 <span data-ttu-id="9e816-112">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="9e816-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e816-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9e816-113">See Also</span></span>  
 [<span data-ttu-id="9e816-114">Interface ISymUnmanagedScope</span><span class="sxs-lookup"><span data-stu-id="9e816-114">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
