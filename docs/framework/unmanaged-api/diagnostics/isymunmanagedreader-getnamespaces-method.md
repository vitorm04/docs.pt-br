---
title: Método ISymUnmanagedReader::GetNamespaces
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetNamespaces
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetNamespaces
helpviewer_keywords:
- ISymUnmanagedReader::GetNamespaces method [.NET Framework debugging]
- GetNamespaces method, ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: 3feb4796-2fab-45ce-beca-6f5bc530b971
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 570532433483e9d0a08f4d685087c0736e135390
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59076725"
---
# <a name="isymunmanagedreadergetnamespaces-method"></a><span data-ttu-id="4af31-102">Método ISymUnmanagedReader::GetNamespaces</span><span class="sxs-lookup"><span data-stu-id="4af31-102">ISymUnmanagedReader::GetNamespaces Method</span></span>
<span data-ttu-id="4af31-103">Obtém os namespaces definidos no escopo global dentro desse repositório de símbolos.</span><span class="sxs-lookup"><span data-stu-id="4af31-103">Gets the namespaces defined at global scope within this symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4af31-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4af31-104">Syntax</span></span>  
  
```  
HRESULT GetNamespaces (  
    [in]  ULONG32  cNameSpaces,  
    [out] ULONG32  *pcNameSpaces,  
    [out, size_is (cNameSpaces),  
        length_is (*pcNameSpaces)]  
        ISymUnmanagedNamespace*  namespaces[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4af31-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4af31-105">Parameters</span></span>  
 `cNameSpaces`  
 <span data-ttu-id="4af31-106">[in] O tamanho da matriz de namespaces.</span><span class="sxs-lookup"><span data-stu-id="4af31-106">[in] The size of the namespaces array.</span></span>  
  
 `pcNameSpaces`  
 <span data-ttu-id="4af31-107">[out] Um ponteiro para uma variável que recebe o comprimento da lista de namespace.</span><span class="sxs-lookup"><span data-stu-id="4af31-107">[out] A pointer to a variable that receives the length of the namespace list.</span></span>  
  
 `namespaces`  
 <span data-ttu-id="4af31-108">[out] Um ponteiro para uma variável que recebe a lista de namespaces.</span><span class="sxs-lookup"><span data-stu-id="4af31-108">[out] A pointer to a variable that receives the namespace list.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4af31-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="4af31-109">Return Value</span></span>  
 <span data-ttu-id="4af31-110">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="4af31-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4af31-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4af31-111">Requirements</span></span>  
 <span data-ttu-id="4af31-112">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="4af31-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4af31-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4af31-113">See also</span></span>

- [<span data-ttu-id="4af31-114">Interface ISymUnmanagedReader</span><span class="sxs-lookup"><span data-stu-id="4af31-114">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
