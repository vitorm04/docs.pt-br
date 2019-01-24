---
title: Método ISymUnmanagedWriter5::OpenMapTokensToSourceSpans
ms.date: 03/30/2017
ms.assetid: 93ad2517-b0dc-464c-8688-a58a30eda18d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 60c1984e6193481efdaaeb82a2bc025aef67a33f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54534428"
---
# <a name="isymunmanagedwriter5openmaptokenstosourcespans-method"></a><span data-ttu-id="87eaf-102">Método ISymUnmanagedWriter5::OpenMapTokensToSourceSpans</span><span class="sxs-lookup"><span data-stu-id="87eaf-102">ISymUnmanagedWriter5::OpenMapTokensToSourceSpans Method</span></span>
<span data-ttu-id="87eaf-103">Abra uma seção especial de dados personalizados para emitir informações de mapeamento de span da fonte de token em.</span><span class="sxs-lookup"><span data-stu-id="87eaf-103">Open a special custom data section to emit token-to-source span mapping information into.</span></span> <span data-ttu-id="87eaf-104">Abrir esta seção quando um método já está aberto, ou vice-versa, é um erro.</span><span class="sxs-lookup"><span data-stu-id="87eaf-104">Opening this section when a method is already open, or vice versa, is an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87eaf-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="87eaf-105">Syntax</span></span>  
  
```idl  
HRESULT OpenMapTokensToSourceSpans();  
```  
  
## <a name="return-value"></a><span data-ttu-id="87eaf-106">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="87eaf-106">Return Value</span></span>  
 <span data-ttu-id="87eaf-107">Retorna `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="87eaf-107">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87eaf-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="87eaf-108">Requirements</span></span>  
 <span data-ttu-id="87eaf-109">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="87eaf-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87eaf-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="87eaf-110">See also</span></span>
- [<span data-ttu-id="87eaf-111">Interface ISymUnmanagedWriter5</span><span class="sxs-lookup"><span data-stu-id="87eaf-111">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)
