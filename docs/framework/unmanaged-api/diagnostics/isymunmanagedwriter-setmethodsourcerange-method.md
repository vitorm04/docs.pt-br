---
title: Método ISymUnmanagedWriter::SetMethodSourceRange
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.SetMethodSourceRange
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::SetMethodSourceRange
helpviewer_keywords:
- SetMethodSourceRange method [.NET Framework debugging]
- ISymUnmanagedWriter::SetMethodSourceRange method [.NET Framework debugging]
ms.assetid: c698b86e-ace7-4b21-9549-f52d6a034959
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6e06695f5ba348315523c7414822ce87d594bdbc
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776597"
---
# <a name="isymunmanagedwritersetmethodsourcerange-method"></a><span data-ttu-id="ad44c-102">Método ISymUnmanagedWriter::SetMethodSourceRange</span><span class="sxs-lookup"><span data-stu-id="ad44c-102">ISymUnmanagedWriter::SetMethodSourceRange Method</span></span>
<span data-ttu-id="ad44c-103">Especifica os verdadeiros início e término de um método de dentro de um arquivo de origem.</span><span class="sxs-lookup"><span data-stu-id="ad44c-103">Specifies the true start and end of a method within a source file.</span></span> <span data-ttu-id="ad44c-104">Use esse método para especificar a extensão de um método independentemente dos pontos de sequência que existem dentro do método.</span><span class="sxs-lookup"><span data-stu-id="ad44c-104">Use this method to specify the extent of a method independently of the sequence points that exist within the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad44c-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ad44c-105">Syntax</span></span>  
  
```cpp  
HRESULT SetMethodSourceRange(  
    [in] ISymUnmanagedDocumentWriter  *startDoc,  
    [in] ULONG32                      startLine,  
    [in] ULONG32                      startColumn,  
    [in] ISymUnmanagedDocumentWriter  *endDoc,  
    [in] ULONG32                      endLine,  
    [in] ULONG32                      endColumn);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ad44c-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ad44c-106">Parameters</span></span>  
 `startDoc`  
 <span data-ttu-id="ad44c-107">[in] Um ponteiro para o documento que contém a posição inicial.</span><span class="sxs-lookup"><span data-stu-id="ad44c-107">[in] A pointer to the document containing the starting position.</span></span>  
  
 `startLine`  
 <span data-ttu-id="ad44c-108">[in] O número de linha inicial.</span><span class="sxs-lookup"><span data-stu-id="ad44c-108">[in] The starting line number.</span></span>  
  
 `startColumn`  
 <span data-ttu-id="ad44c-109">[in] A coluna inicial.</span><span class="sxs-lookup"><span data-stu-id="ad44c-109">[in] The starting column.</span></span>  
  
 `endDoc`  
 <span data-ttu-id="ad44c-110">[in] Um ponteiro para o documento que contém a posição final.</span><span class="sxs-lookup"><span data-stu-id="ad44c-110">[in] A pointer to the document containing the ending position.</span></span>  
  
 `endLine`  
 <span data-ttu-id="ad44c-111">[in] O número de linha final.</span><span class="sxs-lookup"><span data-stu-id="ad44c-111">[in] The ending line number.</span></span>  
  
 `endColumn`  
 <span data-ttu-id="ad44c-112">[in] O número de coluna final.</span><span class="sxs-lookup"><span data-stu-id="ad44c-112">[in] The ending column number.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ad44c-113">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="ad44c-113">Return Value</span></span>  
 <span data-ttu-id="ad44c-114">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="ad44c-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad44c-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ad44c-115">Requirements</span></span>  
 <span data-ttu-id="ad44c-116">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ad44c-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad44c-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ad44c-117">See also</span></span>

- [<span data-ttu-id="ad44c-118">Interface ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="ad44c-118">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
