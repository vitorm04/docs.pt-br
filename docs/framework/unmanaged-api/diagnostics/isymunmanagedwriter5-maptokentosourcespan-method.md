---
title: Método ISymUnmanagedWriter5::MapTokenToSourceSpan
ms.date: 03/30/2017
ms.assetid: d0fbbf61-71c6-4fb1-8c9f-d619ca5d7d68
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 08c219dd033b39fc07159875b184cdf70e3aa3ed
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59181513"
---
# <a name="isymunmanagedwriter5maptokentosourcespan-method"></a><span data-ttu-id="127ca-102">Método ISymUnmanagedWriter5::MapTokenToSourceSpan</span><span class="sxs-lookup"><span data-stu-id="127ca-102">ISymUnmanagedWriter5::MapTokenToSourceSpan Method</span></span>
<span data-ttu-id="127ca-103">Mapeia o token de metadados fornecidos para a linha de origem determinado span no arquivo de origem especificado.</span><span class="sxs-lookup"><span data-stu-id="127ca-103">Maps the given metadata token to the given source line span in the specified source file.</span></span>  
  
 <span data-ttu-id="127ca-104">Deve ser chamado entre as chamadas para [método OpenMapTokensToSourceSpans](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) e [método CloseMapTokensToSourceSpans](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span><span class="sxs-lookup"><span data-stu-id="127ca-104">Must be called between calls to [OpenMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) and [CloseMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="127ca-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="127ca-105">Syntax</span></span>  
  
```idl  
HRESULT MapTokenToSourceSpan(    [in] mdToken token,    [in] ISymUnmanagedDocumentWriter* document,    [in] ULONG32 line,    [in] ULONG32 column,    [in] ULONG32 endLine,    [in] ULONG32 endColumn);  
```  
  
## <a name="parameters"></a><span data-ttu-id="127ca-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="127ca-106">Parameters</span></span>  
  
|<span data-ttu-id="127ca-107">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="127ca-107">Parameter</span></span>|<span data-ttu-id="127ca-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="127ca-108">Description</span></span>|  
|---------------|-----------------|  
|`token`||  
|`document`||  
|`line`||  
|`column`||  
|`endLine`||  
|`endColumn`||  
  
## <a name="return-value"></a><span data-ttu-id="127ca-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="127ca-109">Return Value</span></span>  
 <span data-ttu-id="127ca-110">Retorna `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="127ca-110">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="127ca-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="127ca-111">Requirements</span></span>  
 <span data-ttu-id="127ca-112">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="127ca-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="127ca-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="127ca-113">See also</span></span>

- [<span data-ttu-id="127ca-114">Interface ISymUnmanagedWriter5</span><span class="sxs-lookup"><span data-stu-id="127ca-114">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)
