---
title: "Método ISymUnmanagedReader::GetNamespaces"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader.GetNamespaces
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader::GetNamespaces
helpviewer_keywords:
- ISymUnmanagedReader::GetNamespaces method [.NET Framework debugging]
- GetNamespaces method, ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: 3feb4796-2fab-45ce-beca-6f5bc530b971
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c4404977fab42fb46292440473cd30f6cb162d6b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedreadergetnamespaces-method"></a><span data-ttu-id="2aaee-102">Método ISymUnmanagedReader::GetNamespaces</span><span class="sxs-lookup"><span data-stu-id="2aaee-102">ISymUnmanagedReader::GetNamespaces Method</span></span>
<span data-ttu-id="2aaee-103">Obtém os namespaces definidos no escopo global esse armazenamento de símbolo.</span><span class="sxs-lookup"><span data-stu-id="2aaee-103">Gets the namespaces defined at global scope within this symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2aaee-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2aaee-104">Syntax</span></span>  
  
```  
HRESULT GetNamespaces (  
    [in]  ULONG32  cNameSpaces,  
    [out] ULONG32  *pcNameSpaces,  
    [out, size_is (cNameSpaces),  
        length_is (*pcNameSpaces)]  
        ISymUnmanagedNamespace*  namespaces[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2aaee-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2aaee-105">Parameters</span></span>  
 `cNameSpaces`  
 <span data-ttu-id="2aaee-106">[in] O tamanho da matriz de namespaces.</span><span class="sxs-lookup"><span data-stu-id="2aaee-106">[in] The size of the namespaces array.</span></span>  
  
 `pcNameSpaces`  
 <span data-ttu-id="2aaee-107">[out] Um ponteiro para uma variável que recebe o comprimento da lista de namespace.</span><span class="sxs-lookup"><span data-stu-id="2aaee-107">[out] A pointer to a variable that receives the length of the namespace list.</span></span>  
  
 `namespaces`  
 <span data-ttu-id="2aaee-108">[out] Um ponteiro para uma variável que recebe a lista de namespace.</span><span class="sxs-lookup"><span data-stu-id="2aaee-108">[out] A pointer to a variable that receives the namespace list.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2aaee-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="2aaee-109">Return Value</span></span>  
 <span data-ttu-id="2aaee-110">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="2aaee-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2aaee-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2aaee-111">Requirements</span></span>  
 <span data-ttu-id="2aaee-112">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="2aaee-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2aaee-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2aaee-113">See Also</span></span>  
 [<span data-ttu-id="2aaee-114">Interface ISymUnmanagedReader</span><span class="sxs-lookup"><span data-stu-id="2aaee-114">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
