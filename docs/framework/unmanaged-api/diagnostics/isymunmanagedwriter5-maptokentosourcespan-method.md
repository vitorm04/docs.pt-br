---
title: Método ISymUnmanagedWriter5::MapTokenToSourceSpan
ms.date: 03/30/2017
ms.assetid: d0fbbf61-71c6-4fb1-8c9f-d619ca5d7d68
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 158ff204d57c3b08ced91d397ef71f24c5f44248
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54499204"
---
# <a name="isymunmanagedwriter5maptokentosourcespan-method"></a><span data-ttu-id="cba50-102">Método ISymUnmanagedWriter5::MapTokenToSourceSpan</span><span class="sxs-lookup"><span data-stu-id="cba50-102">ISymUnmanagedWriter5::MapTokenToSourceSpan Method</span></span>
<span data-ttu-id="cba50-103">Mapeia o token de metadados fornecidos para a linha de origem determinado span no arquivo de origem especificado.</span><span class="sxs-lookup"><span data-stu-id="cba50-103">Maps the given metadata token to the given source line span in the specified source file.</span></span>  
  
 <span data-ttu-id="cba50-104">Deve ser chamado entre as chamadas para [método OpenMapTokensToSourceSpans](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) e [método CloseMapTokensToSourceSpans](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span><span class="sxs-lookup"><span data-stu-id="cba50-104">Must be called between calls to [OpenMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) and [CloseMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cba50-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cba50-105">Syntax</span></span>  
  
```idl  
HRESULT MapTokenToSourceSpan(    [in] mdToken token,    [in] ISymUnmanagedDocumentWriter* document,    [in] ULONG32 line,    [in] ULONG32 column,    [in] ULONG32 endLine,    [in] ULONG32 endColumn);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cba50-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cba50-106">Parameters</span></span>  
  
|<span data-ttu-id="cba50-107">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="cba50-107">Parameter</span></span>|<span data-ttu-id="cba50-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="cba50-108">Description</span></span>|  
|---------------|-----------------|  
|`token`||  
|`document`||  
|`line`||  
|`column`||  
|`endLine`||  
|`endColumn`||  
  
## <a name="return-value"></a><span data-ttu-id="cba50-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="cba50-109">Return Value</span></span>  
 <span data-ttu-id="cba50-110">Retorna `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="cba50-110">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cba50-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cba50-111">Requirements</span></span>  
 <span data-ttu-id="cba50-112">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="cba50-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cba50-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cba50-113">See also</span></span>
- [<span data-ttu-id="cba50-114">Interface ISymUnmanagedWriter5</span><span class="sxs-lookup"><span data-stu-id="cba50-114">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)
