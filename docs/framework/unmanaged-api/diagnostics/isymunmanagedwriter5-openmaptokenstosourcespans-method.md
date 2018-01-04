---
title: "Método ISymUnmanagedWriter5::OpenMapTokensToSourceSpans"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 93ad2517-b0dc-464c-8688-a58a30eda18d
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cb283198de5621748b37fe8e22f2fbc408754ad6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriter5openmaptokenstosourcespans-method"></a><span data-ttu-id="577c0-102">Método ISymUnmanagedWriter5::OpenMapTokensToSourceSpans</span><span class="sxs-lookup"><span data-stu-id="577c0-102">ISymUnmanagedWriter5::OpenMapTokensToSourceSpans Method</span></span>
<span data-ttu-id="577c0-103">Abra uma seção de dados personalizada especial para emitir informações de mapeamento de span da fonte de token em.</span><span class="sxs-lookup"><span data-stu-id="577c0-103">Open a special custom data section to emit token-to-source span mapping information into.</span></span> <span data-ttu-id="577c0-104">Abrir esta seção quando um método já estiver aberto, ou vice-versa, é um erro.</span><span class="sxs-lookup"><span data-stu-id="577c0-104">Opening this section when a method is already open, or vice versa, is an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="577c0-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="577c0-105">Syntax</span></span>  
  
```idl  
HRESULT OpenMapTokensToSourceSpans();  
```  
  
## <a name="return-value"></a><span data-ttu-id="577c0-106">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="577c0-106">Return Value</span></span>  
 <span data-ttu-id="577c0-107">Retorna `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="577c0-107">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="577c0-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="577c0-108">Requirements</span></span>  
 <span data-ttu-id="577c0-109">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="577c0-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="577c0-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="577c0-110">See Also</span></span>  
 [<span data-ttu-id="577c0-111">Interface ISymUnmanagedWriter5</span><span class="sxs-lookup"><span data-stu-id="577c0-111">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)
