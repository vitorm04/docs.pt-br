---
title: Método ISymUnmanagedWriter5::MapTokenToSourceSpan
ms.date: 03/30/2017
ms.assetid: d0fbbf61-71c6-4fb1-8c9f-d619ca5d7d68
ms.openlocfilehash: f5898cab08f332314fb33684399dcb4f2ff71cc7
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83609450"
---
# <a name="isymunmanagedwriter5maptokentosourcespan-method"></a><span data-ttu-id="3a077-102">Método ISymUnmanagedWriter5::MapTokenToSourceSpan</span><span class="sxs-lookup"><span data-stu-id="3a077-102">ISymUnmanagedWriter5::MapTokenToSourceSpan Method</span></span>
<span data-ttu-id="3a077-103">Mapeia o token de metadados fornecido para o span de linha de origem fornecido no arquivo de origem especificado.</span><span class="sxs-lookup"><span data-stu-id="3a077-103">Maps the given metadata token to the given source line span in the specified source file.</span></span>  
  
 <span data-ttu-id="3a077-104">Deve ser chamado entre as chamadas para o [método OpenMapTokensToSourceSpans](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) e o [método CloseMapTokensToSourceSpans](isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span><span class="sxs-lookup"><span data-stu-id="3a077-104">Must be called between calls to [OpenMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) and [CloseMapTokensToSourceSpans Method](isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a077-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3a077-105">Syntax</span></span>  
  
```idl  
HRESULT MapTokenToSourceSpan(    [in] mdToken token,    [in] ISymUnmanagedDocumentWriter* document,    [in] ULONG32 line,    [in] ULONG32 column,    [in] ULONG32 endLine,    [in] ULONG32 endColumn);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3a077-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3a077-106">Parameters</span></span>  
  
|<span data-ttu-id="3a077-107">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="3a077-107">Parameter</span></span>|<span data-ttu-id="3a077-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="3a077-108">Description</span></span>|  
|---------------|-----------------|  
|`token`||  
|`document`||  
|`line`||  
|`column`||  
|`endLine`||  
|`endColumn`||  
  
## <a name="return-value"></a><span data-ttu-id="3a077-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="3a077-109">Return Value</span></span>  
 <span data-ttu-id="3a077-110">Retorna `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="3a077-110">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a077-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3a077-111">Requirements</span></span>  
 <span data-ttu-id="3a077-112">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="3a077-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a077-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="3a077-113">See also</span></span>

- [<span data-ttu-id="3a077-114">Interface ISymUnmanagedWriter5</span><span class="sxs-lookup"><span data-stu-id="3a077-114">ISymUnmanagedWriter5 Interface</span></span>](isymunmanagedwriter5-interface.md)
