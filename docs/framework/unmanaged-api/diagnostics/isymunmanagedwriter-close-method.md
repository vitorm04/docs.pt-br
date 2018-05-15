---
title: Método ISymUnmanagedWriter::Close
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.Close
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Close
helpviewer_keywords:
- Close method, ISymUnmanagedWriter interface [.NET Framework debugging]
- ISymUnmanagedWriter::Close method [.NET Framework debugging]
ms.assetid: 4cce59e1-80b9-4fc4-b3aa-126f1c5876bc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 30747fa25528f5679264ebfb67addf401b7d01d9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedwriterclose-method"></a><span data-ttu-id="e5bd8-102">Método ISymUnmanagedWriter::Close</span><span class="sxs-lookup"><span data-stu-id="e5bd8-102">ISymUnmanagedWriter::Close Method</span></span>
<span data-ttu-id="e5bd8-103">Fecha o gravador de símbolo depois confirmando os símbolos para o repositório de símbolos.</span><span class="sxs-lookup"><span data-stu-id="e5bd8-103">Closes the symbol writer after committing the symbols to the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5bd8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e5bd8-104">Syntax</span></span>  
  
```  
HRESULT Close();  
```  
  
## <a name="return-value"></a><span data-ttu-id="e5bd8-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="e5bd8-105">Return Value</span></span>  
 <span data-ttu-id="e5bd8-106">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="e5bd8-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e5bd8-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="e5bd8-107">Remarks</span></span>  
 <span data-ttu-id="e5bd8-108">Após essa chamada, o gravador de símbolo se torna inválido para obter informações mais atualizadas.</span><span class="sxs-lookup"><span data-stu-id="e5bd8-108">After this call, the symbol writer becomes invalid for further updates.</span></span> <span data-ttu-id="e5bd8-109">Para fechar o gravador de símbolo sem confirmar os símbolos, use o [Isymunmanagedwriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-abort-method.md) método em vez disso.</span><span class="sxs-lookup"><span data-stu-id="e5bd8-109">To close the symbol writer without committing the symbols, use the [ISymUnmanagedWriter::Abort](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-abort-method.md) method instead.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5bd8-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e5bd8-110">Requirements</span></span>  
 <span data-ttu-id="e5bd8-111">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e5bd8-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5bd8-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e5bd8-112">See Also</span></span>  
 [<span data-ttu-id="e5bd8-113">Interface ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="e5bd8-113">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
