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
ms.openlocfilehash: e0c72cd6e7dce784064f7653ba35e488061d9fd7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67773584"
---
# <a name="isymunmanagedreadergetnamespaces-method"></a><span data-ttu-id="3b55d-102">Método ISymUnmanagedReader::GetNamespaces</span><span class="sxs-lookup"><span data-stu-id="3b55d-102">ISymUnmanagedReader::GetNamespaces Method</span></span>
<span data-ttu-id="3b55d-103">Obtém os namespaces definidos no escopo global dentro desse repositório de símbolos.</span><span class="sxs-lookup"><span data-stu-id="3b55d-103">Gets the namespaces defined at global scope within this symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b55d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3b55d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNamespaces (  
    [in]  ULONG32  cNameSpaces,  
    [out] ULONG32  *pcNameSpaces,  
    [out, size_is (cNameSpaces),  
        length_is (*pcNameSpaces)]  
        ISymUnmanagedNamespace*  namespaces[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3b55d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3b55d-105">Parameters</span></span>  
 `cNameSpaces`  
 <span data-ttu-id="3b55d-106">[in] O tamanho da matriz de namespaces.</span><span class="sxs-lookup"><span data-stu-id="3b55d-106">[in] The size of the namespaces array.</span></span>  
  
 `pcNameSpaces`  
 <span data-ttu-id="3b55d-107">[out] Um ponteiro para uma variável que recebe o comprimento da lista de namespace.</span><span class="sxs-lookup"><span data-stu-id="3b55d-107">[out] A pointer to a variable that receives the length of the namespace list.</span></span>  
  
 `namespaces`  
 <span data-ttu-id="3b55d-108">[out] Um ponteiro para uma variável que recebe a lista de namespaces.</span><span class="sxs-lookup"><span data-stu-id="3b55d-108">[out] A pointer to a variable that receives the namespace list.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3b55d-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="3b55d-109">Return Value</span></span>  
 <span data-ttu-id="3b55d-110">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="3b55d-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b55d-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3b55d-111">Requirements</span></span>  
 <span data-ttu-id="3b55d-112">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="3b55d-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b55d-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3b55d-113">See also</span></span>

- [<span data-ttu-id="3b55d-114">Interface ISymUnmanagedReader</span><span class="sxs-lookup"><span data-stu-id="3b55d-114">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
