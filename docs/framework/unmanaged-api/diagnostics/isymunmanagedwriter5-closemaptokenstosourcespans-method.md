---
title: Método ISymUnmanagedWriter5::CloseMapTokensToSourceSpans
ms.date: 03/30/2017
ms.assetid: f8a0c0a2-a11d-436c-aa85-bc110215cfd6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ce4b41854d5d9324169b1873f431ef81c0a4c5be
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54677912"
---
# <a name="isymunmanagedwriter5closemaptokenstosourcespans-method"></a><span data-ttu-id="69946-102">Método ISymUnmanagedWriter5::CloseMapTokensToSourceSpans</span><span class="sxs-lookup"><span data-stu-id="69946-102">ISymUnmanagedWriter5::CloseMapTokensToSourceSpans Method</span></span>
<span data-ttu-id="69946-103">Feche a seção de dados personalizados especiais para informações de mapeamento de extensão de fonte de token.</span><span class="sxs-lookup"><span data-stu-id="69946-103">Close the special custom data section for token-to-source span mapping information.</span></span> <span data-ttu-id="69946-104">Depois que ele é fechado, não há mais informações de mapeamento podem ser adicionadas.</span><span class="sxs-lookup"><span data-stu-id="69946-104">After it is closed, no more mapping information can be added.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69946-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="69946-105">Syntax</span></span>  
  
```idl  
HRESULT CloseMapTokensToSourceSpans();  
```  
  
## <a name="return-value"></a><span data-ttu-id="69946-106">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="69946-106">Return Value</span></span>  
 <span data-ttu-id="69946-107">Retorna `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="69946-107">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69946-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="69946-108">Requirements</span></span>  
 <span data-ttu-id="69946-109">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="69946-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69946-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="69946-110">See also</span></span>
- [<span data-ttu-id="69946-111">Interface ISymUnmanagedWriter5</span><span class="sxs-lookup"><span data-stu-id="69946-111">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)
