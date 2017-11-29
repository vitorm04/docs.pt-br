---
title: "Método ISymUnmanagedWriter::CloseScope"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.CloseScope
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::CloseScope
helpviewer_keywords:
- CloseScope method [.NET Framework debugging]
- ISymUnmanagedWriter::CloseScope method [.NET Framework debugging]
ms.assetid: 6dade525-7770-4cb4-bafd-4bb995ad0d87
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a8df22e5f9ea2ca294f502fcebf4b2ed5cd7900d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedwriterclosescope-method"></a><span data-ttu-id="35027-102">Método ISymUnmanagedWriter::CloseScope</span><span class="sxs-lookup"><span data-stu-id="35027-102">ISymUnmanagedWriter::CloseScope Method</span></span>
<span data-ttu-id="35027-103">Fecha o escopo léxico atual.</span><span class="sxs-lookup"><span data-stu-id="35027-103">Closes the current lexical scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35027-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="35027-104">Syntax</span></span>  
  
```  
HRESULT CloseScope(  
    [in] ULONG32 endOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="35027-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="35027-105">Parameters</span></span>  
 `endOffset`  
 <span data-ttu-id="35027-106">[in] O deslocamento do início do método do ponto no final da última instrução no escopo léxico, em bytes.</span><span class="sxs-lookup"><span data-stu-id="35027-106">[in] The offset from the beginning of the method of the point at the end of the last instruction in the lexical scope, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="35027-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="35027-107">Return Value</span></span>  
 <span data-ttu-id="35027-108">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="35027-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="35027-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="35027-109">Remarks</span></span>  
 <span data-ttu-id="35027-110">Quando um escopo é fechado, não mais variáveis podem ser definidos dentro dela.</span><span class="sxs-lookup"><span data-stu-id="35027-110">Once a scope is closed, no more variables can be defined within it.</span></span>  
  
 <span data-ttu-id="35027-111">[Isymunmanagedwriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) retorna um identificador de escopo opaco que pode ser usado com [: Setscoperange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) definir posteriormente um escopo inicial e final deslocamento.</span><span class="sxs-lookup"><span data-stu-id="35027-111">[ISymUnmanagedWriter::OpenScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) returns an opaque scope identifier that can be used with [ISymUnmanagedWriter::SetScopeRange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) to later define a scope's starting and ending offset.</span></span> <span data-ttu-id="35027-112">Nesse caso, os deslocamentos passado para `ISymUnmanagedWriter::OpenScope` e `ISymUnmanagedWriter::CloseScope` são ignorados.</span><span class="sxs-lookup"><span data-stu-id="35027-112">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and `ISymUnmanagedWriter::CloseScope` are ignored.</span></span> <span data-ttu-id="35027-113">Identificadores de escopo são válidos somente no método atual.</span><span class="sxs-lookup"><span data-stu-id="35027-113">Scope identifiers are valid only in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35027-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="35027-114">Requirements</span></span>  
 <span data-ttu-id="35027-115">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="35027-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35027-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="35027-116">See Also</span></span>  
 [<span data-ttu-id="35027-117">Interface ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="35027-117">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
