---
title: Método ISymUnmanagedReader::GetDocuments
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetDocuments
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetDocuments
helpviewer_keywords:
- GetDocuments method [.NET Framework debugging]
- ISymUnmanagedReader::GetDocuments method [.NET Framework debugging]
ms.assetid: e3b73a3f-d089-4101-a9a9-5e0765d05b61
topic_type:
- apiref
ms.openlocfilehash: c26c0a5f8c597613266e2e6d1998edfca8f17b82
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448332"
---
# <a name="isymunmanagedreadergetdocuments-method"></a><span data-ttu-id="f4e3b-102">Método ISymUnmanagedReader::GetDocuments</span><span class="sxs-lookup"><span data-stu-id="f4e3b-102">ISymUnmanagedReader::GetDocuments Method</span></span>
<span data-ttu-id="f4e3b-103">Retorna uma matriz de todos os documentos definidos no repositório de símbolos.</span><span class="sxs-lookup"><span data-stu-id="f4e3b-103">Returns an array of all the documents defined in the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4e3b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f4e3b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDocuments (  
    [in]  ULONG32  cDocs,  
    [out] ULONG32  *pcDocs,  
    [out, size_is (cDocs),  
        length_is (*pcDocs)] ISymUnmanagedDocument *pDocs[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f4e3b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f4e3b-105">Parameters</span></span>  
 `cDocs`  
 <span data-ttu-id="f4e3b-106">no O tamanho da matriz de `pDocs`.</span><span class="sxs-lookup"><span data-stu-id="f4e3b-106">[in] The size of the `pDocs` array.</span></span>  
  
 `pcDocs`  
 <span data-ttu-id="f4e3b-107">fora Um ponteiro para uma variável que recebe o comprimento da matriz.</span><span class="sxs-lookup"><span data-stu-id="f4e3b-107">[out] A pointer to a variable that receives the array length.</span></span>  
  
 `pDocs`  
 <span data-ttu-id="f4e3b-108">fora Um ponteiro para uma variável que recebe a matriz de documentos.</span><span class="sxs-lookup"><span data-stu-id="f4e3b-108">[out] A pointer to a variable that receives the document array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f4e3b-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="f4e3b-109">Return Value</span></span>  
 <span data-ttu-id="f4e3b-110">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="f4e3b-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4e3b-111">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="f4e3b-111">Requirements</span></span>  
 <span data-ttu-id="f4e3b-112">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="f4e3b-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4e3b-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f4e3b-113">See also</span></span>

- [<span data-ttu-id="f4e3b-114">Interface ISymUnmanagedReader</span><span class="sxs-lookup"><span data-stu-id="f4e3b-114">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
