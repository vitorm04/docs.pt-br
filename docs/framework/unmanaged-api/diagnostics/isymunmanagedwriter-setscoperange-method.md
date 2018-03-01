---
title: "Método ISymUnmanagedWriter::SetScopeRange"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ISymUnmanagedWriter.SetScopeRange
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::SetScopeRange
helpviewer_keywords:
- SetScopeRange method [.NET Framework debugging]
- ISymUnmanagedWriter::SetScopeRange method [.NET Framework debugging]
ms.assetid: d4d98676-444b-46ca-bfe6-0d827385cd22
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9afb0038adc4273033fb9f1db1ebc57f43eae779
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwritersetscoperange-method"></a><span data-ttu-id="96dde-102">Método ISymUnmanagedWriter::SetScopeRange</span><span class="sxs-lookup"><span data-stu-id="96dde-102">ISymUnmanagedWriter::SetScopeRange Method</span></span>
<span data-ttu-id="96dde-103">Define o intervalo de deslocamento do escopo léxico especificado.</span><span class="sxs-lookup"><span data-stu-id="96dde-103">Defines the offset range for the specified lexical scope.</span></span> <span data-ttu-id="96dde-104">O escopo se torna o novo escopo atual e é enviada por push para uma pilha de escopos.</span><span class="sxs-lookup"><span data-stu-id="96dde-104">The scope becomes the new current scope and is pushed onto a stack of scopes.</span></span> <span data-ttu-id="96dde-105">Escopos devem formar uma hierarquia.</span><span class="sxs-lookup"><span data-stu-id="96dde-105">Scopes must form a hierarchy.</span></span> <span data-ttu-id="96dde-106">Irmãos não podem se sobrepor.</span><span class="sxs-lookup"><span data-stu-id="96dde-106">Siblings are not allowed to overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96dde-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="96dde-107">Syntax</span></span>  
  
```  
HRESULT OpenScope(  
    [in] ULONG32  scopeID,  
    [in] ULONG32  startOffset,  
    [in] ULONG32  endOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="96dde-108">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="96dde-108">Parameters</span></span>  
 `scopeId`  
 <span data-ttu-id="96dde-109">[in] O identificador de escopo para o escopo.</span><span class="sxs-lookup"><span data-stu-id="96dde-109">[in] The scope identifier for the scope.</span></span>  
  
 `startOffset`  
 <span data-ttu-id="96dde-110">[in] O deslocamento, em bytes, da primeira instrução no escopo léxico desde o início do método.</span><span class="sxs-lookup"><span data-stu-id="96dde-110">[in] The offset, in bytes, of the first instruction in the lexical scope from the beginning of the method.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="96dde-111">[in] O deslocamento, em bytes, da última instrução no escopo léxico desde o início do método.</span><span class="sxs-lookup"><span data-stu-id="96dde-111">[in] The offset, in bytes, of the last instruction in the lexical scope from the beginning of the method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="96dde-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="96dde-112">Return Value</span></span>  
 <span data-ttu-id="96dde-113">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="96dde-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="96dde-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="96dde-114">Remarks</span></span>  
 <span data-ttu-id="96dde-115">[Isymunmanagedwriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) retorna um identificador de escopo opaco que pode ser usado com `ISymUnmanagedWriter::SetScopeRange` definir um escopo inicial e final deslocamento mais tarde.</span><span class="sxs-lookup"><span data-stu-id="96dde-115">[ISymUnmanagedWriter::OpenScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) returns an opaque scope identifier that can be used with `ISymUnmanagedWriter::SetScopeRange` to define a scope's starting and ending offset at a later time.</span></span> <span data-ttu-id="96dde-116">Nesse caso, os deslocamentos passado para `ISymUnmanagedWriter::OpenScope` e [: Closescope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md) são ignorados.</span><span class="sxs-lookup"><span data-stu-id="96dde-116">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and [ISymUnmanagedWriter::CloseScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md) are ignored.</span></span> <span data-ttu-id="96dde-117">Identificadores de escopo só são válidos no método atual.</span><span class="sxs-lookup"><span data-stu-id="96dde-117">Scope identifiers are only valid in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96dde-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="96dde-118">Requirements</span></span>  
 <span data-ttu-id="96dde-119">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="96dde-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96dde-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="96dde-120">See Also</span></span>  
 [<span data-ttu-id="96dde-121">Interface ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="96dde-121">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
