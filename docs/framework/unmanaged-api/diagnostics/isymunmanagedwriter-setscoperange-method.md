---
title: Método ISymUnmanagedWriter::SetScopeRange
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7d7fe8f36c7a5dbe6e715402fd7253092b64e68e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61650746"
---
# <a name="isymunmanagedwritersetscoperange-method"></a><span data-ttu-id="170ae-102">Método ISymUnmanagedWriter::SetScopeRange</span><span class="sxs-lookup"><span data-stu-id="170ae-102">ISymUnmanagedWriter::SetScopeRange Method</span></span>
<span data-ttu-id="170ae-103">Define o intervalo de deslocamento do escopo léxico especificado.</span><span class="sxs-lookup"><span data-stu-id="170ae-103">Defines the offset range for the specified lexical scope.</span></span> <span data-ttu-id="170ae-104">O escopo se torna o novo escopo atual e é enviada por push para uma pilha de escopos.</span><span class="sxs-lookup"><span data-stu-id="170ae-104">The scope becomes the new current scope and is pushed onto a stack of scopes.</span></span> <span data-ttu-id="170ae-105">Escopos devem formar uma hierarquia.</span><span class="sxs-lookup"><span data-stu-id="170ae-105">Scopes must form a hierarchy.</span></span> <span data-ttu-id="170ae-106">Irmãos não podem se sobrepor.</span><span class="sxs-lookup"><span data-stu-id="170ae-106">Siblings are not allowed to overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="170ae-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="170ae-107">Syntax</span></span>  
  
```  
HRESULT OpenScope(  
    [in] ULONG32  scopeID,  
    [in] ULONG32  startOffset,  
    [in] ULONG32  endOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="170ae-108">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="170ae-108">Parameters</span></span>  
 `scopeId`  
 <span data-ttu-id="170ae-109">[in] O identificador de escopo para o escopo.</span><span class="sxs-lookup"><span data-stu-id="170ae-109">[in] The scope identifier for the scope.</span></span>  
  
 `startOffset`  
 <span data-ttu-id="170ae-110">[in] O deslocamento, em bytes, da primeira instrução no escopo léxico desde o início do método.</span><span class="sxs-lookup"><span data-stu-id="170ae-110">[in] The offset, in bytes, of the first instruction in the lexical scope from the beginning of the method.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="170ae-111">[in] O deslocamento, em bytes, da última instrução no escopo léxico desde o início do método.</span><span class="sxs-lookup"><span data-stu-id="170ae-111">[in] The offset, in bytes, of the last instruction in the lexical scope from the beginning of the method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="170ae-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="170ae-112">Return Value</span></span>  
 <span data-ttu-id="170ae-113">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="170ae-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="170ae-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="170ae-114">Remarks</span></span>  
 <span data-ttu-id="170ae-115">[Isymunmanagedwriter:: Openscope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) retorna um identificador de escopo opaco que pode ser usado com `ISymUnmanagedWriter::SetScopeRange` definir um escopo inicial e final deslocamento em um momento posterior.</span><span class="sxs-lookup"><span data-stu-id="170ae-115">[ISymUnmanagedWriter::OpenScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) returns an opaque scope identifier that can be used with `ISymUnmanagedWriter::SetScopeRange` to define a scope's starting and ending offset at a later time.</span></span> <span data-ttu-id="170ae-116">Nesse caso, os deslocamentos passados para `ISymUnmanagedWriter::OpenScope` e [isymunmanagedwriter:: Closescope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md) são ignorados.</span><span class="sxs-lookup"><span data-stu-id="170ae-116">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and [ISymUnmanagedWriter::CloseScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md) are ignored.</span></span> <span data-ttu-id="170ae-117">Identificadores de escopo só são válidos no método atual.</span><span class="sxs-lookup"><span data-stu-id="170ae-117">Scope identifiers are only valid in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="170ae-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="170ae-118">Requirements</span></span>  
 <span data-ttu-id="170ae-119">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="170ae-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="170ae-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="170ae-120">See also</span></span>

- [<span data-ttu-id="170ae-121">Interface ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="170ae-121">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
