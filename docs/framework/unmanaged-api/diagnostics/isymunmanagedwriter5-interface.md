---
title: Interface ISymUnmanagedWriter5
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 15b8526e-4f5d-475c-a1e3-d8b2d145c879
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 701b8de977d49a7d93f393b320bcb9d0d780c7bb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriter5-interface"></a><span data-ttu-id="9fee4-102">Interface ISymUnmanagedWriter5</span><span class="sxs-lookup"><span data-stu-id="9fee4-102">ISymUnmanagedWriter5 Interface</span></span>
<span data-ttu-id="9fee4-103">Interface ISymUnmanagedWriter5.</span><span class="sxs-lookup"><span data-stu-id="9fee4-103">ISymUnmanagedWriter5 interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9fee4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9fee4-104">Syntax</span></span>  
  
```idl  
[object,uuid(DCF7780D-BDE9-45DF-ACFE-21731A32000C),pointer_default(unique)]interface ISymUnmanagedWriter5 : ISymUnmanagedWriter4  
```  
  
## <a name="methods"></a><span data-ttu-id="9fee4-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="9fee4-105">Methods</span></span>  
 <span data-ttu-id="9fee4-106">Essa interface contém os seguintes métodos:</span><span class="sxs-lookup"><span data-stu-id="9fee4-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="9fee4-107">Método</span><span class="sxs-lookup"><span data-stu-id="9fee4-107">Method</span></span>|<span data-ttu-id="9fee4-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="9fee4-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9fee4-109">Método CloseMapTokensToSourceSpans</span><span class="sxs-lookup"><span data-stu-id="9fee4-109">CloseMapTokensToSourceSpans Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md)|<span data-ttu-id="9fee4-110">Feche a seção de dados personalizada especial para informações de mapeamento de extensão de token para a fonte.</span><span class="sxs-lookup"><span data-stu-id="9fee4-110">Close the special custom data section for token-to- source span mapping information.</span></span> <span data-ttu-id="9fee4-111">Depois de fechado, não há mais informações de mapeamento podem ser adicionadas.</span><span class="sxs-lookup"><span data-stu-id="9fee4-111">After it is closed, no more mapping information can be added.</span></span>|  
|[<span data-ttu-id="9fee4-112">Método MapTokenToSourceSpan</span><span class="sxs-lookup"><span data-stu-id="9fee4-112">MapTokenToSourceSpan Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-maptokentosourcespan-method.md)|<span data-ttu-id="9fee4-113">Mapeia o token de metadados fornecidos para a linha de origem span no arquivo de origem especificado.</span><span class="sxs-lookup"><span data-stu-id="9fee4-113">Maps the given metadata token to the given source line span in the specified source file.</span></span><br /><br /> <span data-ttu-id="9fee4-114">Deve ser chamado entre as chamadas para [método OpenMapTokensToSourceSpans](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) e [método CloseMapTokensToSourceSpans](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span><span class="sxs-lookup"><span data-stu-id="9fee4-114">Must be called between calls to [OpenMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) and [CloseMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span></span>|  
|[<span data-ttu-id="9fee4-115">Método OpenMapTokensToSourceSpans</span><span class="sxs-lookup"><span data-stu-id="9fee4-115">OpenMapTokensToSourceSpans Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md)|<span data-ttu-id="9fee4-116">Abra uma seção de dados personalizada especial para emitir informações de mapeamento de span da fonte de token em.</span><span class="sxs-lookup"><span data-stu-id="9fee4-116">Open a special custom data section to emit token-to- source span mapping information into.</span></span> <span data-ttu-id="9fee4-117">Abrir esta seção quando um método já estiver aberto, ou vice-versa, é um erro.</span><span class="sxs-lookup"><span data-stu-id="9fee4-117">Opening this section when a method is already open, or vice versa, is an error.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9fee4-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9fee4-118">Requirements</span></span>  
 <span data-ttu-id="9fee4-119">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="9fee4-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fee4-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9fee4-120">See Also</span></span>  
 [<span data-ttu-id="9fee4-121">Interfaces do repositório de símbolos de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="9fee4-121">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="9fee4-122">Interface ISymUnmanagedWriter4</span><span class="sxs-lookup"><span data-stu-id="9fee4-122">ISymUnmanagedWriter4 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)
