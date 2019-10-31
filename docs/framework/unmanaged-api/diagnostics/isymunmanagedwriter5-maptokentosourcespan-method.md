---
title: Método ISymUnmanagedWriter5::MapTokenToSourceSpan
ms.date: 03/30/2017
ms.assetid: d0fbbf61-71c6-4fb1-8c9f-d619ca5d7d68
ms.openlocfilehash: 876804e7b825443116b1f44a02a685a73153915c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121620"
---
# <a name="isymunmanagedwriter5maptokentosourcespan-method"></a><span data-ttu-id="8f685-102">Método ISymUnmanagedWriter5::MapTokenToSourceSpan</span><span class="sxs-lookup"><span data-stu-id="8f685-102">ISymUnmanagedWriter5::MapTokenToSourceSpan Method</span></span>
<span data-ttu-id="8f685-103">Mapeia o token de metadados fornecido para o span de linha de origem fornecido no arquivo de origem especificado.</span><span class="sxs-lookup"><span data-stu-id="8f685-103">Maps the given metadata token to the given source line span in the specified source file.</span></span>  
  
 <span data-ttu-id="8f685-104">Deve ser chamado entre as chamadas para o [método OpenMapTokensToSourceSpans](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) e o [método CloseMapTokensToSourceSpans](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span><span class="sxs-lookup"><span data-stu-id="8f685-104">Must be called between calls to [OpenMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) and [CloseMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f685-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8f685-105">Syntax</span></span>  
  
```idl  
HRESULT MapTokenToSourceSpan(    [in] mdToken token,    [in] ISymUnmanagedDocumentWriter* document,    [in] ULONG32 line,    [in] ULONG32 column,    [in] ULONG32 endLine,    [in] ULONG32 endColumn);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8f685-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8f685-106">Parameters</span></span>  
  
|<span data-ttu-id="8f685-107">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="8f685-107">Parameter</span></span>|<span data-ttu-id="8f685-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="8f685-108">Description</span></span>|  
|---------------|-----------------|  
|`token`||  
|`document`||  
|`line`||  
|`column`||  
|`endLine`||  
|`endColumn`||  
  
## <a name="return-value"></a><span data-ttu-id="8f685-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="8f685-109">Return Value</span></span>  
 <span data-ttu-id="8f685-110">Retorna `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="8f685-110">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f685-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8f685-111">Requirements</span></span>  
 <span data-ttu-id="8f685-112">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="8f685-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f685-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8f685-113">See also</span></span>

- [<span data-ttu-id="8f685-114">Interface ISymUnmanagedWriter5</span><span class="sxs-lookup"><span data-stu-id="8f685-114">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)
