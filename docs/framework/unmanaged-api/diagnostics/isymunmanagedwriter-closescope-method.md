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
ms.openlocfilehash: 264b4487483ed5439a9809feefcdc1b20af402dc
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428082"
---
# <a name="isymunmanagedwriterclosescope-method"></a><span data-ttu-id="f89e0-102">Método ISymUnmanagedWriter::CloseScope</span><span class="sxs-lookup"><span data-stu-id="f89e0-102">ISymUnmanagedWriter::CloseScope Method</span></span>
<span data-ttu-id="f89e0-103">Fecha o escopo léxico atual.</span><span class="sxs-lookup"><span data-stu-id="f89e0-103">Closes the current lexical scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f89e0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f89e0-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseScope(  
    [in] ULONG32 endOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f89e0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f89e0-105">Parameters</span></span>  
 `endOffset`  
 <span data-ttu-id="f89e0-106">no O deslocamento do início do método do ponto no final da última instrução no escopo léxico, em bytes.</span><span class="sxs-lookup"><span data-stu-id="f89e0-106">[in] The offset from the beginning of the method of the point at the end of the last instruction in the lexical scope, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f89e0-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="f89e0-107">Return Value</span></span>  
 <span data-ttu-id="f89e0-108">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="f89e0-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f89e0-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="f89e0-109">Remarks</span></span>  
 <span data-ttu-id="f89e0-110">Depois que um escopo é fechado, nenhuma outra variável pode ser definida dentro dele.</span><span class="sxs-lookup"><span data-stu-id="f89e0-110">Once a scope is closed, no more variables can be defined within it.</span></span>  
  
 <span data-ttu-id="f89e0-111">[ISymUnmanagedWriter:: OpenScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) retorna um identificador de escopo opaco que pode ser usado com [ISymUnmanagedWriter:: SetScopeRange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) para definir posteriormente o deslocamento de início e de término do escopo.</span><span class="sxs-lookup"><span data-stu-id="f89e0-111">[ISymUnmanagedWriter::OpenScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) returns an opaque scope identifier that can be used with [ISymUnmanagedWriter::SetScopeRange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) to later define a scope's starting and ending offset.</span></span> <span data-ttu-id="f89e0-112">Nesse caso, os deslocamentos passados para `ISymUnmanagedWriter::OpenScope` e `ISymUnmanagedWriter::CloseScope` são ignorados.</span><span class="sxs-lookup"><span data-stu-id="f89e0-112">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and `ISymUnmanagedWriter::CloseScope` are ignored.</span></span> <span data-ttu-id="f89e0-113">Os identificadores de escopo são válidos somente no método atual.</span><span class="sxs-lookup"><span data-stu-id="f89e0-113">Scope identifiers are valid only in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f89e0-114">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="f89e0-114">Requirements</span></span>  
 <span data-ttu-id="f89e0-115">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="f89e0-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f89e0-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f89e0-116">See also</span></span>

- [<span data-ttu-id="f89e0-117">Interface ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="f89e0-117">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
