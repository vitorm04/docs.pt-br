---
title: "Método ISymUnmanagedWriter::OpenScope"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.OpenScope
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::OpenScope
helpviewer_keywords:
- OpenScope method, ISymUnmanagedWriter interface [.NET Framework debugging]
- ISymUnmanagedWriter::OpenScope method [.NET Framework debugging]
ms.assetid: dbea0644-3873-4329-90b8-624163e87467
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 99919a1d932bca1bb8677fd71c447c7098c7d44c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriteropenscope-method"></a><span data-ttu-id="8df6e-102">Método ISymUnmanagedWriter::OpenScope</span><span class="sxs-lookup"><span data-stu-id="8df6e-102">ISymUnmanagedWriter::OpenScope Method</span></span>
<span data-ttu-id="8df6e-103">Abre um novo escopo léxico no método atual.</span><span class="sxs-lookup"><span data-stu-id="8df6e-103">Opens a new lexical scope in the current method.</span></span> <span data-ttu-id="8df6e-104">O escopo se torna o novo escopo atual e é enviada por push para uma pilha de escopos.</span><span class="sxs-lookup"><span data-stu-id="8df6e-104">The scope becomes the new current scope and is pushed onto a stack of scopes.</span></span> <span data-ttu-id="8df6e-105">Escopos devem formar uma hierarquia.</span><span class="sxs-lookup"><span data-stu-id="8df6e-105">Scopes must form a hierarchy.</span></span> <span data-ttu-id="8df6e-106">Irmãos não podem se sobrepor.</span><span class="sxs-lookup"><span data-stu-id="8df6e-106">Siblings are not allowed to overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8df6e-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8df6e-107">Syntax</span></span>  
  
```  
HRESULT OpenScope(  
    [in] ULONG32 startOffset,  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8df6e-108">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8df6e-108">Parameters</span></span>  
 `startOffset`  
 <span data-ttu-id="8df6e-109">[in] O deslocamento da primeira instrução no escopo léxico, em bytes, do início do método.</span><span class="sxs-lookup"><span data-stu-id="8df6e-109">[in] The offset of the first instruction in the lexical scope, in bytes, from the beginning of the method.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="8df6e-110">[out] Um ponteiro para um `ULONG32` que recebe o identificador de escopo.</span><span class="sxs-lookup"><span data-stu-id="8df6e-110">[out] A pointer to a `ULONG32` that receives the scope identifier.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8df6e-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="8df6e-111">Return Value</span></span>  
 <span data-ttu-id="8df6e-112">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="8df6e-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8df6e-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="8df6e-113">Remarks</span></span>  
 <span data-ttu-id="8df6e-114">`ISymUnmanagedWriter::OpenScope`Retorna um identificador de escopo opaco que pode ser usado com [: Setscoperange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) definir um escopo inicial e final deslocamento mais tarde.</span><span class="sxs-lookup"><span data-stu-id="8df6e-114">`ISymUnmanagedWriter::OpenScope` returns an opaque scope identifier that can be used with [ISymUnmanagedWriter::SetScopeRange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) to define a scope's starting and ending offset at a later time.</span></span> <span data-ttu-id="8df6e-115">Nesse caso, os deslocamentos passado para `ISymUnmanagedWriter::OpenScope` e [: Closescope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md) são ignorados.</span><span class="sxs-lookup"><span data-stu-id="8df6e-115">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and [ISymUnmanagedWriter::CloseScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md) are ignored.</span></span> <span data-ttu-id="8df6e-116">Identificadores de escopo são válidos somente no método atual.</span><span class="sxs-lookup"><span data-stu-id="8df6e-116">Scope identifiers are valid only in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8df6e-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8df6e-117">Requirements</span></span>  
 <span data-ttu-id="8df6e-118">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="8df6e-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8df6e-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8df6e-119">See Also</span></span>  
 [<span data-ttu-id="8df6e-120">Interface ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="8df6e-120">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
