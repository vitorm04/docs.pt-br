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
ms.openlocfilehash: 85e65f6a3ec13c2acc31b8f87dbe4b4476ffc2a5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427869"
---
# <a name="isymunmanagedwritersetmethodsourcerange-method"></a><span data-ttu-id="6dbe8-102">Método ISymUnmanagedWriter::SetMethodSourceRange</span><span class="sxs-lookup"><span data-stu-id="6dbe8-102">ISymUnmanagedWriter::SetMethodSourceRange Method</span></span>
<span data-ttu-id="6dbe8-103">Especifica os verdadeiros início e término de um método de dentro de um arquivo de origem.</span><span class="sxs-lookup"><span data-stu-id="6dbe8-103">Specifies the true start and end of a method within a source file.</span></span> <span data-ttu-id="6dbe8-104">Use esse método para especificar a extensão de um método independentemente dos pontos de sequência que existem dentro do método.</span><span class="sxs-lookup"><span data-stu-id="6dbe8-104">Use this method to specify the extent of a method independently of the sequence points that exist within the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6dbe8-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6dbe8-105">Syntax</span></span>  
  
```cpp  
HRESULT SetMethodSourceRange(  
    [in] ISymUnmanagedDocumentWriter  *startDoc,  
    [in] ULONG32                      startLine,  
    [in] ULONG32                      startColumn,  
    [in] ISymUnmanagedDocumentWriter  *endDoc,  
    [in] ULONG32                      endLine,  
    [in] ULONG32                      endColumn);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6dbe8-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6dbe8-106">Parameters</span></span>  
 `startDoc`  
 <span data-ttu-id="6dbe8-107">no Um ponteiro para o documento que contém a posição inicial.</span><span class="sxs-lookup"><span data-stu-id="6dbe8-107">[in] A pointer to the document containing the starting position.</span></span>  
  
 `startLine`  
 <span data-ttu-id="6dbe8-108">no O número da linha inicial.</span><span class="sxs-lookup"><span data-stu-id="6dbe8-108">[in] The starting line number.</span></span>  
  
 `startColumn`  
 <span data-ttu-id="6dbe8-109">no A coluna inicial.</span><span class="sxs-lookup"><span data-stu-id="6dbe8-109">[in] The starting column.</span></span>  
  
 `endDoc`  
 <span data-ttu-id="6dbe8-110">no Um ponteiro para o documento que contém a posição final.</span><span class="sxs-lookup"><span data-stu-id="6dbe8-110">[in] A pointer to the document containing the ending position.</span></span>  
  
 `endLine`  
 <span data-ttu-id="6dbe8-111">no O número da linha final.</span><span class="sxs-lookup"><span data-stu-id="6dbe8-111">[in] The ending line number.</span></span>  
  
 `endColumn`  
 <span data-ttu-id="6dbe8-112">no O número da coluna final.</span><span class="sxs-lookup"><span data-stu-id="6dbe8-112">[in] The ending column number.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6dbe8-113">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="6dbe8-113">Return Value</span></span>  
 <span data-ttu-id="6dbe8-114">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="6dbe8-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6dbe8-115">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="6dbe8-115">Requirements</span></span>  
 <span data-ttu-id="6dbe8-116">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="6dbe8-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6dbe8-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6dbe8-117">See also</span></span>

- [<span data-ttu-id="6dbe8-118">Interface ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="6dbe8-118">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
