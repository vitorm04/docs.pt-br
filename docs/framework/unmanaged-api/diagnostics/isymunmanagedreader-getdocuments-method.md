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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: efcf5b6673fbdc37fad99d082f91ab3077abbea9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59130592"
---
# <a name="isymunmanagedreadergetdocuments-method"></a><span data-ttu-id="9593b-102">Método ISymUnmanagedReader::GetDocuments</span><span class="sxs-lookup"><span data-stu-id="9593b-102">ISymUnmanagedReader::GetDocuments Method</span></span>
<span data-ttu-id="9593b-103">Retorna uma matriz de todos os documentos definidos no repositório de símbolos.</span><span class="sxs-lookup"><span data-stu-id="9593b-103">Returns an array of all the documents defined in the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9593b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9593b-104">Syntax</span></span>  
  
```  
HRESULT GetDocuments (  
    [in]  ULONG32  cDocs,  
    [out] ULONG32  *pcDocs,  
    [out, size_is (cDocs),  
        length_is (*pcDocs)] ISymUnmanagedDocument *pDocs[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9593b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9593b-105">Parameters</span></span>  
 `cDocs`  
 <span data-ttu-id="9593b-106">[in] O tamanho do `pDocs` matriz.</span><span class="sxs-lookup"><span data-stu-id="9593b-106">[in] The size of the `pDocs` array.</span></span>  
  
 `pcDocs`  
 <span data-ttu-id="9593b-107">[out] Um ponteiro para uma variável que recebe o comprimento da matriz.</span><span class="sxs-lookup"><span data-stu-id="9593b-107">[out] A pointer to a variable that receives the array length.</span></span>  
  
 `pDocs`  
 <span data-ttu-id="9593b-108">[out] Um ponteiro para uma variável que recebe a matriz de documento.</span><span class="sxs-lookup"><span data-stu-id="9593b-108">[out] A pointer to a variable that receives the document array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9593b-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="9593b-109">Return Value</span></span>  
 <span data-ttu-id="9593b-110">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="9593b-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9593b-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9593b-111">Requirements</span></span>  
 <span data-ttu-id="9593b-112">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="9593b-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9593b-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9593b-113">See also</span></span>

- [<span data-ttu-id="9593b-114">Interface ISymUnmanagedReader</span><span class="sxs-lookup"><span data-stu-id="9593b-114">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
