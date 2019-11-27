---
title: Método ISymUnmanagedDocumentWriter::SetSource
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocumentWriter.SetSource
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocumentWriter::SetSource
helpviewer_keywords:
- ISymUnmanagedDocumentWriter::SetSource method [.NET Framework debugging]
- SetSource method [.NET Framework debugging]
ms.assetid: ea5b9d9f-ff06-4bd3-8de5-6435343aba59
topic_type:
- apiref
ms.openlocfilehash: ff18f95bd6b4cfde5aaa4d3f6f68b58fd37c04b3
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449074"
---
# <a name="isymunmanageddocumentwritersetsource-method"></a><span data-ttu-id="94465-102">Método ISymUnmanagedDocumentWriter::SetSource</span><span class="sxs-lookup"><span data-stu-id="94465-102">ISymUnmanagedDocumentWriter::SetSource Method</span></span>
<span data-ttu-id="94465-103">Define a fonte incorporada para um documento que está sendo gravado.</span><span class="sxs-lookup"><span data-stu-id="94465-103">Sets embedded source for a document that is being written.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94465-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="94465-104">Syntax</span></span>  
  
```cpp  
HRESULT SetSource(  
    [in]  ULONG32  sourceSize,  
    [in, size_is(sourceSize)] BYTE  source[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="94465-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="94465-105">Parameters</span></span>  
 `sourceSize`  
 <span data-ttu-id="94465-106">no Um `ULONG32` que contém o tamanho do buffer de `source`.</span><span class="sxs-lookup"><span data-stu-id="94465-106">[in] A `ULONG32` that contains the size of the `source` buffer.</span></span>  
  
 `source`  
 <span data-ttu-id="94465-107">no O buffer que armazena a fonte inserida.</span><span class="sxs-lookup"><span data-stu-id="94465-107">[in] The buffer that stores the embedded source.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="94465-108">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="94465-108">Return Value</span></span>  
 <span data-ttu-id="94465-109">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="94465-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94465-110">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="94465-110">Requirements</span></span>  
 <span data-ttu-id="94465-111">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="94465-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94465-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="94465-112">See also</span></span>

- [<span data-ttu-id="94465-113">Interface ISymUnmanagedDocumentWriter</span><span class="sxs-lookup"><span data-stu-id="94465-113">ISymUnmanagedDocumentWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocumentwriter-interface.md)
