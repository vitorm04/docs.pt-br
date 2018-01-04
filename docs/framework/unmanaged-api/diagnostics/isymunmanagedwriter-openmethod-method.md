---
title: "Método ISymUnmanagedWriter::OpenMethod"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.OpenMethod
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::OpenMethod
helpviewer_keywords:
- ISymUnmanagedWriter::OpenMethod method [.NET Framework debugging]
- OpenMethod method [.NET Framework debugging]
ms.assetid: fb90cb7f-af88-45e8-a99f-80a0bbddb08b
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e6cfb41748861150b28493c835e80135abe90826
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriteropenmethod-method"></a><span data-ttu-id="b744c-102">Método ISymUnmanagedWriter::OpenMethod</span><span class="sxs-lookup"><span data-stu-id="b744c-102">ISymUnmanagedWriter::OpenMethod Method</span></span>
<span data-ttu-id="b744c-103">Abre um método para o símbolo que informações são emitidas.</span><span class="sxs-lookup"><span data-stu-id="b744c-103">Opens a method into which symbol information is emitted.</span></span> <span data-ttu-id="b744c-104">O método dado torna-se o método atual para chamadas para definir pontos de sequência, parâmetros e escopos léxicos.</span><span class="sxs-lookup"><span data-stu-id="b744c-104">The given method becomes the current method for calls to define sequence points, parameters, and lexical scopes.</span></span> <span data-ttu-id="b744c-105">Há um escopo léxico implícita ao redor de todo o método.</span><span class="sxs-lookup"><span data-stu-id="b744c-105">There is an implicit lexical scope around the entire method.</span></span> <span data-ttu-id="b744c-106">Reabrir um método que foi fechado anteriormente apaga qualquer símbolos definidos anteriormente para esse método.</span><span class="sxs-lookup"><span data-stu-id="b744c-106">Reopening a method that was previously closed erases any previously defined symbols for that method.</span></span> <span data-ttu-id="b744c-107">Pode haver apenas um método aberto por vez.</span><span class="sxs-lookup"><span data-stu-id="b744c-107">There can be only one open method at a time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b744c-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b744c-108">Syntax</span></span>  
  
```  
HRESULT OpenMethod(  
    [in] mdMethodDef method);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b744c-109">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b744c-109">Parameters</span></span>  
 `method`  
 <span data-ttu-id="b744c-110">[in] O token de metadados para o método a ser aberto.</span><span class="sxs-lookup"><span data-stu-id="b744c-110">[in] The metadata token for the method to be opened.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b744c-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="b744c-111">Return Value</span></span>  
 <span data-ttu-id="b744c-112">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="b744c-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b744c-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b744c-113">Requirements</span></span>  
 <span data-ttu-id="b744c-114">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b744c-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b744c-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b744c-115">See Also</span></span>  
 [<span data-ttu-id="b744c-116">Interface ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="b744c-116">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="b744c-117">Método CloseMethod</span><span class="sxs-lookup"><span data-stu-id="b744c-117">CloseMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)  
 [<span data-ttu-id="b744c-118">Método OpenMethod2</span><span class="sxs-lookup"><span data-stu-id="b744c-118">OpenMethod2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-openmethod2-method.md)
