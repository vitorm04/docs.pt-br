---
title: Método ISymUnmanagedNamespace::GetNamespaces
ms.date: 03/30/2017
api_name:
- ISymUnmanagedNamespace.GetNamespaces
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedNamespace::GetNamespaces
helpviewer_keywords:
- ISymUnmanagedNamespace::GetNamespaces method [.NET Framework debugging]
- GetNamespaces method, ISymUnmanagedNamespace interface [.NET Framework debugging]
ms.assetid: 0ea9d9af-8709-4a46-872b-f54d9e840088
topic_type:
- apiref
ms.openlocfilehash: da2906187c02bbc7a35c937663e3fc7db1ebda13
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433889"
---
# <a name="isymunmanagednamespacegetnamespaces-method"></a><span data-ttu-id="39f96-102">Método ISymUnmanagedNamespace::GetNamespaces</span><span class="sxs-lookup"><span data-stu-id="39f96-102">ISymUnmanagedNamespace::GetNamespaces Method</span></span>
<span data-ttu-id="39f96-103">Obtém os filhos deste namespace.</span><span class="sxs-lookup"><span data-stu-id="39f96-103">Gets the children of this namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39f96-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="39f96-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNamespaces(  
    [in]  ULONG32  cNameSpaces,  
    [out] ULONG32  *pcNameSpaces,  
    [out, size_is(cNameSpaces), length_is(*pcNameSpaces)]  
        ISymUnmanagedNamespace* namespaces[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="39f96-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="39f96-105">Parameters</span></span>  
 `cNameSpaces`  
 <span data-ttu-id="39f96-106">no Um `ULONG32` que indica o tamanho da matriz de `namespaces`.</span><span class="sxs-lookup"><span data-stu-id="39f96-106">[in] A `ULONG32` that indicates the size of the `namespaces` array.</span></span>  
  
 `pcNameSpaces`  
 <span data-ttu-id="39f96-107">fora Um ponteiro para um `ULONG32` que recebe o tamanho, em caracteres, do buffer necessário para conter os namespaces.</span><span class="sxs-lookup"><span data-stu-id="39f96-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the namespaces.</span></span>  
  
 `namespaces`  
 <span data-ttu-id="39f96-108">fora Um ponteiro para o buffer que contém os namespaces.</span><span class="sxs-lookup"><span data-stu-id="39f96-108">[out] A pointer to the buffer that contains the namespaces.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="39f96-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="39f96-109">Return Value</span></span>  
 <span data-ttu-id="39f96-110">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="39f96-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39f96-111">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="39f96-111">Requirements</span></span>  
 <span data-ttu-id="39f96-112">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="39f96-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39f96-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="39f96-113">See also</span></span>

- [<span data-ttu-id="39f96-114">Interface ISymUnmanagedNamespace</span><span class="sxs-lookup"><span data-stu-id="39f96-114">ISymUnmanagedNamespace Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)
