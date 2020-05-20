---
title: Método ISymUnmanagedWriter5::CloseMapTokensToSourceSpans
ms.date: 03/30/2017
ms.assetid: f8a0c0a2-a11d-436c-aa85-bc110215cfd6
ms.openlocfilehash: 053727604c795bf43a9b1658d5841fe85f53090a
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614624"
---
# <a name="isymunmanagedwriter5closemaptokenstosourcespans-method"></a><span data-ttu-id="d07f3-102">Método ISymUnmanagedWriter5::CloseMapTokensToSourceSpans</span><span class="sxs-lookup"><span data-stu-id="d07f3-102">ISymUnmanagedWriter5::CloseMapTokensToSourceSpans Method</span></span>
<span data-ttu-id="d07f3-103">Feche a seção de dados personalizados especiais para obter informações de mapeamento de token para origem.</span><span class="sxs-lookup"><span data-stu-id="d07f3-103">Close the special custom data section for token-to-source span mapping information.</span></span> <span data-ttu-id="d07f3-104">Depois de fechada, não é possível adicionar mais informações de mapeamento.</span><span class="sxs-lookup"><span data-stu-id="d07f3-104">After it is closed, no more mapping information can be added.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d07f3-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d07f3-105">Syntax</span></span>  
  
```idl  
HRESULT CloseMapTokensToSourceSpans();  
```  
  
## <a name="return-value"></a><span data-ttu-id="d07f3-106">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="d07f3-106">Return Value</span></span>  
 <span data-ttu-id="d07f3-107">Retorna `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="d07f3-107">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d07f3-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d07f3-108">Requirements</span></span>  
 <span data-ttu-id="d07f3-109">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="d07f3-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d07f3-110">Confira também</span><span class="sxs-lookup"><span data-stu-id="d07f3-110">See also</span></span>

- [<span data-ttu-id="d07f3-111">Interface ISymUnmanagedWriter5</span><span class="sxs-lookup"><span data-stu-id="d07f3-111">ISymUnmanagedWriter5 Interface</span></span>](isymunmanagedwriter5-interface.md)
