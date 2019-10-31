---
title: Método ISymUnmanagedWriter5::CloseMapTokensToSourceSpans
ms.date: 03/30/2017
ms.assetid: f8a0c0a2-a11d-436c-aa85-bc110215cfd6
ms.openlocfilehash: 43c35596d31842b85bbdc96a63413a176a59a172
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121650"
---
# <a name="isymunmanagedwriter5closemaptokenstosourcespans-method"></a><span data-ttu-id="cf2fa-102">Método ISymUnmanagedWriter5::CloseMapTokensToSourceSpans</span><span class="sxs-lookup"><span data-stu-id="cf2fa-102">ISymUnmanagedWriter5::CloseMapTokensToSourceSpans Method</span></span>
<span data-ttu-id="cf2fa-103">Feche a seção de dados personalizados especiais para obter informações de mapeamento de token para origem.</span><span class="sxs-lookup"><span data-stu-id="cf2fa-103">Close the special custom data section for token-to-source span mapping information.</span></span> <span data-ttu-id="cf2fa-104">Depois de fechada, não é possível adicionar mais informações de mapeamento.</span><span class="sxs-lookup"><span data-stu-id="cf2fa-104">After it is closed, no more mapping information can be added.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf2fa-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cf2fa-105">Syntax</span></span>  
  
```idl  
HRESULT CloseMapTokensToSourceSpans();  
```  
  
## <a name="return-value"></a><span data-ttu-id="cf2fa-106">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="cf2fa-106">Return Value</span></span>  
 <span data-ttu-id="cf2fa-107">Retorna `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="cf2fa-107">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf2fa-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cf2fa-108">Requirements</span></span>  
 <span data-ttu-id="cf2fa-109">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="cf2fa-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf2fa-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cf2fa-110">See also</span></span>

- [<span data-ttu-id="cf2fa-111">Interface ISymUnmanagedWriter5</span><span class="sxs-lookup"><span data-stu-id="cf2fa-111">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)
