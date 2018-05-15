---
title: Método ISymUnmanagedWriter5::CloseMapTokensToSourceSpans
ms.date: 03/30/2017
ms.assetid: f8a0c0a2-a11d-436c-aa85-bc110215cfd6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 653dd933066898c1954cfbcc57c0c0493e47b4be
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedwriter5closemaptokenstosourcespans-method"></a><span data-ttu-id="03c63-102">Método ISymUnmanagedWriter5::CloseMapTokensToSourceSpans</span><span class="sxs-lookup"><span data-stu-id="03c63-102">ISymUnmanagedWriter5::CloseMapTokensToSourceSpans Method</span></span>
<span data-ttu-id="03c63-103">Feche a seção de dados personalizada especial para informações de mapeamento de extensão de token para a fonte.</span><span class="sxs-lookup"><span data-stu-id="03c63-103">Close the special custom data section for token-to-source span mapping information.</span></span> <span data-ttu-id="03c63-104">Depois de fechado, não há mais informações de mapeamento podem ser adicionadas.</span><span class="sxs-lookup"><span data-stu-id="03c63-104">After it is closed, no more mapping information can be added.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03c63-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="03c63-105">Syntax</span></span>  
  
```idl  
HRESULT CloseMapTokensToSourceSpans();  
```  
  
## <a name="return-value"></a><span data-ttu-id="03c63-106">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="03c63-106">Return Value</span></span>  
 <span data-ttu-id="03c63-107">Retorna `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="03c63-107">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03c63-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="03c63-108">Requirements</span></span>  
 <span data-ttu-id="03c63-109">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="03c63-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03c63-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="03c63-110">See Also</span></span>  
 [<span data-ttu-id="03c63-111">Interface ISymUnmanagedWriter5</span><span class="sxs-lookup"><span data-stu-id="03c63-111">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)
