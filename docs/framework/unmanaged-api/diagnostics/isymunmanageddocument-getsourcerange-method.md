---
title: Método ISymUnmanagedDocument::GetSourceRange
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetSourceRange
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetSourceRange
helpviewer_keywords:
- ISymUnmanagedDocument::GetSourceRange method [.NET Framework debugging]
- GetSourceRange method [.NET Framework debugging]
ms.assetid: 20fefee7-1040-41ba-93dc-bd42f68b90c2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 981048c10be27900f011afeab55d1c5eb523f734
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776672"
---
# <a name="isymunmanageddocumentgetsourcerange-method"></a><span data-ttu-id="943c9-102">Método ISymUnmanagedDocument::GetSourceRange</span><span class="sxs-lookup"><span data-stu-id="943c9-102">ISymUnmanagedDocument::GetSourceRange Method</span></span>
<span data-ttu-id="943c9-103">Retorna o intervalo especificado da origem inserida para o buffer fornecido.</span><span class="sxs-lookup"><span data-stu-id="943c9-103">Returns the specified range of the embedded source into the given buffer.</span></span> <span data-ttu-id="943c9-104">O buffer deve ser grande o suficiente para manter o código-fonte.</span><span class="sxs-lookup"><span data-stu-id="943c9-104">The buffer must be large enough to hold the source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="943c9-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="943c9-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSourceRange(  
    [in]  ULONG32  startLine,  
    [in]  ULONG32  startColumn,  
    [in]  ULONG32  endLine,  
    [in]  ULONG32  endColumn,  
    [in]  ULONG32  cSourceBytes,  
    [out] ULONG32  *pcSourceBytes,  
    [out, size_is(cSourceBytes),  
        length_is(*pcSourceBytes)] BYTE source[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="943c9-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="943c9-106">Parameters</span></span>  
 `startLine`  
 <span data-ttu-id="943c9-107">[in] A linha inicial no documento atual.</span><span class="sxs-lookup"><span data-stu-id="943c9-107">[in] The starting line in the current document.</span></span>  
  
 `startColumn`  
 <span data-ttu-id="943c9-108">[in] A coluna inicial no documento atual.</span><span class="sxs-lookup"><span data-stu-id="943c9-108">[in] The starting column in the current document.</span></span>  
  
 `endLine`  
 <span data-ttu-id="943c9-109">[in] A linha final no documento atual.</span><span class="sxs-lookup"><span data-stu-id="943c9-109">[in] The final line in the current document.</span></span>  
  
 `endColumn`  
 <span data-ttu-id="943c9-110">[in] A coluna final no documento atual.</span><span class="sxs-lookup"><span data-stu-id="943c9-110">[in] The final column in the current document.</span></span>  
  
 `cSourceBytes`  
 <span data-ttu-id="943c9-111">[in] O tamanho da fonte, em bytes.</span><span class="sxs-lookup"><span data-stu-id="943c9-111">[in] The size of the source, in bytes.</span></span>  
  
 `pcSourceBytes`  
 <span data-ttu-id="943c9-112">[out] Um ponteiro para uma variável que recebe o tamanho da fonte.</span><span class="sxs-lookup"><span data-stu-id="943c9-112">[out] A pointer to a variable that receives the source size.</span></span>  
  
 `source`  
 <span data-ttu-id="943c9-113">[out] O tamanho e o comprimento do intervalo especificado do documento de origem, em bytes.</span><span class="sxs-lookup"><span data-stu-id="943c9-113">[out] The size and length of the specified range of the source document, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="943c9-114">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="943c9-114">Return Value</span></span>  
 <span data-ttu-id="943c9-115">S_OK se o método for bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="943c9-115">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="943c9-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="943c9-116">See also</span></span>

- [<span data-ttu-id="943c9-117">Interface ISymUnmanagedDocument</span><span class="sxs-lookup"><span data-stu-id="943c9-117">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
