---
title: Método ISymUnmanagedWriter5::MapTokenToSourceSpan
ms.date: 03/30/2017
ms.assetid: d0fbbf61-71c6-4fb1-8c9f-d619ca5d7d68
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7751ed951c213c52c68125543622ed110124f5b1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427937"
---
# <a name="isymunmanagedwriter5maptokentosourcespan-method"></a><span data-ttu-id="d5525-102">Método ISymUnmanagedWriter5::MapTokenToSourceSpan</span><span class="sxs-lookup"><span data-stu-id="d5525-102">ISymUnmanagedWriter5::MapTokenToSourceSpan Method</span></span>
<span data-ttu-id="d5525-103">Mapeia o token de metadados fornecidos para a linha de origem span no arquivo de origem especificado.</span><span class="sxs-lookup"><span data-stu-id="d5525-103">Maps the given metadata token to the given source line span in the specified source file.</span></span>  
  
 <span data-ttu-id="d5525-104">Deve ser chamado entre as chamadas para [método OpenMapTokensToSourceSpans](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) e [método CloseMapTokensToSourceSpans](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span><span class="sxs-lookup"><span data-stu-id="d5525-104">Must be called between calls to [OpenMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) and [CloseMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5525-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d5525-105">Syntax</span></span>  
  
```idl  
HRESULT MapTokenToSourceSpan(    [in] mdToken token,    [in] ISymUnmanagedDocumentWriter* document,    [in] ULONG32 line,    [in] ULONG32 column,    [in] ULONG32 endLine,    [in] ULONG32 endColumn);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d5525-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d5525-106">Parameters</span></span>  
  
|<span data-ttu-id="d5525-107">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="d5525-107">Parameter</span></span>|<span data-ttu-id="d5525-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="d5525-108">Description</span></span>|  
|---------------|-----------------|  
|`token`||  
|`document`||  
|`line`||  
|`column`||  
|`endLine`||  
|`endColumn`||  
  
## <a name="return-value"></a><span data-ttu-id="d5525-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="d5525-109">Return Value</span></span>  
 <span data-ttu-id="d5525-110">Retorna `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="d5525-110">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5525-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d5525-111">Requirements</span></span>  
 <span data-ttu-id="d5525-112">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d5525-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5525-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d5525-113">See Also</span></span>  
 [<span data-ttu-id="d5525-114">Interface ISymUnmanagedWriter5</span><span class="sxs-lookup"><span data-stu-id="d5525-114">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)
