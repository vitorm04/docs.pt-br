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
ms.openlocfilehash: e33d69e319d7817a54dca76526b6c3ee9bb6384f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54729964"
---
# <a name="isymunmanagedwriterclosescope-method"></a><span data-ttu-id="82981-102">Método ISymUnmanagedWriter::CloseScope</span><span class="sxs-lookup"><span data-stu-id="82981-102">ISymUnmanagedWriter::CloseScope Method</span></span>
<span data-ttu-id="82981-103">Fecha o escopo léxico atual.</span><span class="sxs-lookup"><span data-stu-id="82981-103">Closes the current lexical scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82981-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="82981-104">Syntax</span></span>  
  
```  
HRESULT CloseScope(  
    [in] ULONG32 endOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="82981-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="82981-105">Parameters</span></span>  
 `endOffset`  
 <span data-ttu-id="82981-106">[in] O deslocamento do início do método do ponto no final da última instrução no escopo léxico, em bytes.</span><span class="sxs-lookup"><span data-stu-id="82981-106">[in] The offset from the beginning of the method of the point at the end of the last instruction in the lexical scope, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="82981-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="82981-107">Return Value</span></span>  
 <span data-ttu-id="82981-108">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="82981-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="82981-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="82981-109">Remarks</span></span>  
 <span data-ttu-id="82981-110">Quando um escopo é fechado, não há mais variáveis podem ser definidas dentro dele.</span><span class="sxs-lookup"><span data-stu-id="82981-110">Once a scope is closed, no more variables can be defined within it.</span></span>  
  
 <span data-ttu-id="82981-111">[Isymunmanagedwriter:: Openscope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) retorna um identificador de escopo opaco que pode ser usado com [isymunmanagedwriter:: Setscoperange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) definir posteriormente um escopo inicial e final deslocamento.</span><span class="sxs-lookup"><span data-stu-id="82981-111">[ISymUnmanagedWriter::OpenScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) returns an opaque scope identifier that can be used with [ISymUnmanagedWriter::SetScopeRange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) to later define a scope's starting and ending offset.</span></span> <span data-ttu-id="82981-112">Nesse caso, os deslocamentos passados para `ISymUnmanagedWriter::OpenScope` e `ISymUnmanagedWriter::CloseScope` são ignorados.</span><span class="sxs-lookup"><span data-stu-id="82981-112">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and `ISymUnmanagedWriter::CloseScope` are ignored.</span></span> <span data-ttu-id="82981-113">Identificadores de escopo são válidos somente no método atual.</span><span class="sxs-lookup"><span data-stu-id="82981-113">Scope identifiers are valid only in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82981-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="82981-114">Requirements</span></span>  
 <span data-ttu-id="82981-115">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="82981-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82981-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="82981-116">See also</span></span>
- [<span data-ttu-id="82981-117">Interface ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="82981-117">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
