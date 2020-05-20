---
title: Interface ISymUnmanagedWriter5
ms.date: 03/30/2017
ms.assetid: 15b8526e-4f5d-475c-a1e3-d8b2d145c879
ms.openlocfilehash: bdc630c3c94c7d03b736efa0a95665f10aac7c6e
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83609424"
---
# <a name="isymunmanagedwriter5-interface"></a><span data-ttu-id="d3c9b-102">Interface ISymUnmanagedWriter5</span><span class="sxs-lookup"><span data-stu-id="d3c9b-102">ISymUnmanagedWriter5 Interface</span></span>
<span data-ttu-id="d3c9b-103">Interface ISymUnmanagedWriter5.</span><span class="sxs-lookup"><span data-stu-id="d3c9b-103">ISymUnmanagedWriter5 interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3c9b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d3c9b-104">Syntax</span></span>  
  
```idl  
[object,uuid(DCF7780D-BDE9-45DF-ACFE-21731A32000C),pointer_default(unique)]interface ISymUnmanagedWriter5 : ISymUnmanagedWriter4  
```  
  
## <a name="methods"></a><span data-ttu-id="d3c9b-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="d3c9b-105">Methods</span></span>  
 <span data-ttu-id="d3c9b-106">Essa interface contém os seguintes métodos:</span><span class="sxs-lookup"><span data-stu-id="d3c9b-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="d3c9b-107">Método</span><span class="sxs-lookup"><span data-stu-id="d3c9b-107">Method</span></span>|<span data-ttu-id="d3c9b-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="d3c9b-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d3c9b-109">Método CloseMapTokensToSourceSpans</span><span class="sxs-lookup"><span data-stu-id="d3c9b-109">CloseMapTokensToSourceSpans Method</span></span>](isymunmanagedwriter5-closemaptokenstosourcespans-method.md)|<span data-ttu-id="d3c9b-110">Feche a seção de dados personalizados especiais para obter informações de mapeamento de token para origem.</span><span class="sxs-lookup"><span data-stu-id="d3c9b-110">Close the special custom data section for token-to- source span mapping information.</span></span> <span data-ttu-id="d3c9b-111">Depois de fechada, não é possível adicionar mais informações de mapeamento.</span><span class="sxs-lookup"><span data-stu-id="d3c9b-111">After it is closed, no more mapping information can be added.</span></span>|  
|[<span data-ttu-id="d3c9b-112">Método MapTokenToSourceSpan</span><span class="sxs-lookup"><span data-stu-id="d3c9b-112">MapTokenToSourceSpan Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-maptokentosourcespan-method.md)|<span data-ttu-id="d3c9b-113">Mapeia o token de metadados fornecido para o span de linha de origem fornecido no arquivo de origem especificado.</span><span class="sxs-lookup"><span data-stu-id="d3c9b-113">Maps the given metadata token to the given source line span in the specified source file.</span></span><br /><br /> <span data-ttu-id="d3c9b-114">Deve ser chamado entre as chamadas para o [método OpenMapTokensToSourceSpans](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) e o [método CloseMapTokensToSourceSpans](isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span><span class="sxs-lookup"><span data-stu-id="d3c9b-114">Must be called between calls to [OpenMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) and [CloseMapTokensToSourceSpans Method](isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span></span>|  
|[<span data-ttu-id="d3c9b-115">Método OpenMapTokensToSourceSpans</span><span class="sxs-lookup"><span data-stu-id="d3c9b-115">OpenMapTokensToSourceSpans Method</span></span>](isymunmanagedwriter5-openmaptokenstosourcespans-method.md)|<span data-ttu-id="d3c9b-116">Abra uma seção especial de dados personalizados para emitir informações de mapeamento de extensão de token para origem no.</span><span class="sxs-lookup"><span data-stu-id="d3c9b-116">Open a special custom data section to emit token-to- source span mapping information into.</span></span> <span data-ttu-id="d3c9b-117">Abrir esta seção quando um método já estiver aberto, ou vice-versa, é um erro.</span><span class="sxs-lookup"><span data-stu-id="d3c9b-117">Opening this section when a method is already open, or vice versa, is an error.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d3c9b-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d3c9b-118">Requirements</span></span>  
 <span data-ttu-id="d3c9b-119">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="d3c9b-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3c9b-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="d3c9b-120">See also</span></span>

- [<span data-ttu-id="d3c9b-121">Interfaces de armazenamento de símbolo de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="d3c9b-121">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="d3c9b-122">Interface ISymUnmanagedWriter4</span><span class="sxs-lookup"><span data-stu-id="d3c9b-122">ISymUnmanagedWriter4 Interface</span></span>](isymunmanagedwriter4-interface.md)
