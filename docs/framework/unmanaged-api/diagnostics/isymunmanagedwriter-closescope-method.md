---
title: Método ISymUnmanagedWriter::CloseScope
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.CloseScope
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::CloseScope
helpviewer_keywords:
- CloseScope method [.NET Framework debugging]
- ISymUnmanagedWriter::CloseScope method [.NET Framework debugging]
ms.assetid: 6dade525-7770-4cb4-bafd-4bb995ad0d87
topic_type:
- apiref
ms.openlocfilehash: 4d8790dc68bc063deed4c58ba0df8e9ea258b9d7
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610074"
---
# <a name="isymunmanagedwriterclosescope-method"></a><span data-ttu-id="861e5-102">Método ISymUnmanagedWriter::CloseScope</span><span class="sxs-lookup"><span data-stu-id="861e5-102">ISymUnmanagedWriter::CloseScope Method</span></span>
<span data-ttu-id="861e5-103">Fecha o escopo léxico atual.</span><span class="sxs-lookup"><span data-stu-id="861e5-103">Closes the current lexical scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="861e5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="861e5-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseScope(  
    [in] ULONG32 endOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="861e5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="861e5-105">Parameters</span></span>  
 `endOffset`  
 <span data-ttu-id="861e5-106">no O deslocamento do início do método do ponto no final da última instrução no escopo léxico, em bytes.</span><span class="sxs-lookup"><span data-stu-id="861e5-106">[in] The offset from the beginning of the method of the point at the end of the last instruction in the lexical scope, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="861e5-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="861e5-107">Return Value</span></span>  
 <span data-ttu-id="861e5-108">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="861e5-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="861e5-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="861e5-109">Remarks</span></span>  
 <span data-ttu-id="861e5-110">Depois que um escopo é fechado, nenhuma outra variável pode ser definida dentro dele.</span><span class="sxs-lookup"><span data-stu-id="861e5-110">Once a scope is closed, no more variables can be defined within it.</span></span>  
  
 <span data-ttu-id="861e5-111">[ISymUnmanagedWriter:: OpenScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) retorna um identificador de escopo opaco que pode ser usado com [ISymUnmanagedWriter:: SetScopeRange](isymunmanagedwriter-setscoperange-method.md) para definir posteriormente o deslocamento de início e de término do escopo.</span><span class="sxs-lookup"><span data-stu-id="861e5-111">[ISymUnmanagedWriter::OpenScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) returns an opaque scope identifier that can be used with [ISymUnmanagedWriter::SetScopeRange](isymunmanagedwriter-setscoperange-method.md) to later define a scope's starting and ending offset.</span></span> <span data-ttu-id="861e5-112">Nesse caso, os deslocamentos passados para `ISymUnmanagedWriter::OpenScope` e `ISymUnmanagedWriter::CloseScope` são ignorados.</span><span class="sxs-lookup"><span data-stu-id="861e5-112">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and `ISymUnmanagedWriter::CloseScope` are ignored.</span></span> <span data-ttu-id="861e5-113">Os identificadores de escopo são válidos somente no método atual.</span><span class="sxs-lookup"><span data-stu-id="861e5-113">Scope identifiers are valid only in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="861e5-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="861e5-114">Requirements</span></span>  
 <span data-ttu-id="861e5-115">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="861e5-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="861e5-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="861e5-116">See also</span></span>

- [<span data-ttu-id="861e5-117">Interface ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="861e5-117">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
