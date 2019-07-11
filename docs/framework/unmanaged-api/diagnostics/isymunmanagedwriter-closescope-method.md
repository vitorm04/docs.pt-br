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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8a9edfa2f8888480c72f290ee237972f3a0ed912
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778127"
---
# <a name="isymunmanagedwriterclosescope-method"></a><span data-ttu-id="013ec-102">Método ISymUnmanagedWriter::CloseScope</span><span class="sxs-lookup"><span data-stu-id="013ec-102">ISymUnmanagedWriter::CloseScope Method</span></span>
<span data-ttu-id="013ec-103">Fecha o escopo léxico atual.</span><span class="sxs-lookup"><span data-stu-id="013ec-103">Closes the current lexical scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="013ec-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="013ec-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseScope(  
    [in] ULONG32 endOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="013ec-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="013ec-105">Parameters</span></span>  
 `endOffset`  
 <span data-ttu-id="013ec-106">[in] O deslocamento do início do método do ponto no final da última instrução no escopo léxico, em bytes.</span><span class="sxs-lookup"><span data-stu-id="013ec-106">[in] The offset from the beginning of the method of the point at the end of the last instruction in the lexical scope, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="013ec-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="013ec-107">Return Value</span></span>  
 <span data-ttu-id="013ec-108">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="013ec-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="013ec-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="013ec-109">Remarks</span></span>  
 <span data-ttu-id="013ec-110">Quando um escopo é fechado, não há mais variáveis podem ser definidas dentro dele.</span><span class="sxs-lookup"><span data-stu-id="013ec-110">Once a scope is closed, no more variables can be defined within it.</span></span>  
  
 <span data-ttu-id="013ec-111">[Isymunmanagedwriter:: Openscope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) retorna um identificador de escopo opaco que pode ser usado com [isymunmanagedwriter:: Setscoperange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) definir posteriormente um escopo inicial e final deslocamento.</span><span class="sxs-lookup"><span data-stu-id="013ec-111">[ISymUnmanagedWriter::OpenScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) returns an opaque scope identifier that can be used with [ISymUnmanagedWriter::SetScopeRange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) to later define a scope's starting and ending offset.</span></span> <span data-ttu-id="013ec-112">Nesse caso, os deslocamentos passados para `ISymUnmanagedWriter::OpenScope` e `ISymUnmanagedWriter::CloseScope` são ignorados.</span><span class="sxs-lookup"><span data-stu-id="013ec-112">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and `ISymUnmanagedWriter::CloseScope` are ignored.</span></span> <span data-ttu-id="013ec-113">Identificadores de escopo são válidos somente no método atual.</span><span class="sxs-lookup"><span data-stu-id="013ec-113">Scope identifiers are valid only in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="013ec-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="013ec-114">Requirements</span></span>  
 <span data-ttu-id="013ec-115">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="013ec-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="013ec-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="013ec-116">See also</span></span>

- [<span data-ttu-id="013ec-117">Interface ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="013ec-117">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
