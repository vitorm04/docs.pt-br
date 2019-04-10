---
title: Método ISymUnmanagedWriter5::OpenMapTokensToSourceSpans
ms.date: 03/30/2017
ms.assetid: 93ad2517-b0dc-464c-8688-a58a30eda18d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 82dc2ced988f7277c994eb9449e7c26efa5450b7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59222673"
---
# <a name="isymunmanagedwriter5openmaptokenstosourcespans-method"></a><span data-ttu-id="bf5f8-102">Método ISymUnmanagedWriter5::OpenMapTokensToSourceSpans</span><span class="sxs-lookup"><span data-stu-id="bf5f8-102">ISymUnmanagedWriter5::OpenMapTokensToSourceSpans Method</span></span>
<span data-ttu-id="bf5f8-103">Abra uma seção especial de dados personalizados para emitir informações de mapeamento de span da fonte de token em.</span><span class="sxs-lookup"><span data-stu-id="bf5f8-103">Open a special custom data section to emit token-to-source span mapping information into.</span></span> <span data-ttu-id="bf5f8-104">Abrir esta seção quando um método já está aberto, ou vice-versa, é um erro.</span><span class="sxs-lookup"><span data-stu-id="bf5f8-104">Opening this section when a method is already open, or vice versa, is an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf5f8-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bf5f8-105">Syntax</span></span>  
  
```idl  
HRESULT OpenMapTokensToSourceSpans();  
```  
  
## <a name="return-value"></a><span data-ttu-id="bf5f8-106">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="bf5f8-106">Return Value</span></span>  
 <span data-ttu-id="bf5f8-107">Retorna `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="bf5f8-107">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf5f8-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bf5f8-108">Requirements</span></span>  
 <span data-ttu-id="bf5f8-109">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="bf5f8-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf5f8-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bf5f8-110">See also</span></span>

- [<span data-ttu-id="bf5f8-111">Interface ISymUnmanagedWriter5</span><span class="sxs-lookup"><span data-stu-id="bf5f8-111">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)
