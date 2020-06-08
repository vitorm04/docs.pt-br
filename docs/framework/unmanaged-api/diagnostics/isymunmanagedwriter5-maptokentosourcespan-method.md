---
title: Método ISymUnmanagedWriter5::MapTokenToSourceSpan
ms.date: 03/30/2017
ms.assetid: d0fbbf61-71c6-4fb1-8c9f-d619ca5d7d68
ms.openlocfilehash: 0f00dd34ffbdd58a46260132d8d7ace74ec2f294
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501671"
---
# <a name="isymunmanagedwriter5maptokentosourcespan-method"></a><span data-ttu-id="e404a-102">Método ISymUnmanagedWriter5::MapTokenToSourceSpan</span><span class="sxs-lookup"><span data-stu-id="e404a-102">ISymUnmanagedWriter5::MapTokenToSourceSpan Method</span></span>
<span data-ttu-id="e404a-103">Mapeia o token de metadados fornecido para o span de linha de origem fornecido no arquivo de origem especificado.</span><span class="sxs-lookup"><span data-stu-id="e404a-103">Maps the given metadata token to the given source line span in the specified source file.</span></span>  
  
 <span data-ttu-id="e404a-104">Deve ser chamado entre as chamadas para o [método OpenMapTokensToSourceSpans](isymunmanagedwriter5-openmaptokenstosourcespans-method.md) e o [método CloseMapTokensToSourceSpans](isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span><span class="sxs-lookup"><span data-stu-id="e404a-104">Must be called between calls to [OpenMapTokensToSourceSpans Method](isymunmanagedwriter5-openmaptokenstosourcespans-method.md) and [CloseMapTokensToSourceSpans Method](isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e404a-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e404a-105">Syntax</span></span>  
  
```idl  
HRESULT MapTokenToSourceSpan(    [in] mdToken token,    [in] ISymUnmanagedDocumentWriter* document,    [in] ULONG32 line,    [in] ULONG32 column,    [in] ULONG32 endLine,    [in] ULONG32 endColumn);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e404a-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e404a-106">Parameters</span></span>  
  
|<span data-ttu-id="e404a-107">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="e404a-107">Parameter</span></span>|<span data-ttu-id="e404a-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="e404a-108">Description</span></span>|  
|---------------|-----------------|  
|`token`||  
|`document`||  
|`line`||  
|`column`||  
|`endLine`||  
|`endColumn`||  
  
## <a name="return-value"></a><span data-ttu-id="e404a-109">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="e404a-109">Return Value</span></span>  
 <span data-ttu-id="e404a-110">Retorna `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="e404a-110">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e404a-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e404a-111">Requirements</span></span>  
 <span data-ttu-id="e404a-112">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="e404a-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e404a-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="e404a-113">See also</span></span>

- [<span data-ttu-id="e404a-114">Interface ISymUnmanagedWriter5</span><span class="sxs-lookup"><span data-stu-id="e404a-114">ISymUnmanagedWriter5 Interface</span></span>](isymunmanagedwriter5-interface.md)
