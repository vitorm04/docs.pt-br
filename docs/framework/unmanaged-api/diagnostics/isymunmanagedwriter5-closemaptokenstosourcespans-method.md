---
title: "Método ISymUnmanagedWriter5::CloseMapTokensToSourceSpans"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: f8a0c0a2-a11d-436c-aa85-bc110215cfd6
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f5f23c3fe39adcebcfdfadb9e9c2b639f16330d1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedwriter5closemaptokenstosourcespans-method"></a><span data-ttu-id="2a7b8-102">Método ISymUnmanagedWriter5::CloseMapTokensToSourceSpans</span><span class="sxs-lookup"><span data-stu-id="2a7b8-102">ISymUnmanagedWriter5::CloseMapTokensToSourceSpans Method</span></span>
<span data-ttu-id="2a7b8-103">Feche a seção de dados personalizada especial para informações de mapeamento de extensão de token para a fonte.</span><span class="sxs-lookup"><span data-stu-id="2a7b8-103">Close the special custom data section for token-to-source span mapping information.</span></span> <span data-ttu-id="2a7b8-104">Depois de fechado, não há mais informações de mapeamento podem ser adicionadas.</span><span class="sxs-lookup"><span data-stu-id="2a7b8-104">After it is closed, no more mapping information can be added.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a7b8-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2a7b8-105">Syntax</span></span>  
  
```idl  
HRESULT CloseMapTokensToSourceSpans();  
```  
  
## <a name="return-value"></a><span data-ttu-id="2a7b8-106">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="2a7b8-106">Return Value</span></span>  
 <span data-ttu-id="2a7b8-107">Retorna `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="2a7b8-107">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a7b8-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2a7b8-108">Requirements</span></span>  
 <span data-ttu-id="2a7b8-109">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="2a7b8-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a7b8-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2a7b8-110">See Also</span></span>  
 [<span data-ttu-id="2a7b8-111">Interface ISymUnmanagedWriter5</span><span class="sxs-lookup"><span data-stu-id="2a7b8-111">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)
