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
ms.openlocfilehash: 4d3497d3167715d3e8a04f10a6687260949e4a36
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59104696"
---
# <a name="isymunmanagedwriterclose-method"></a><span data-ttu-id="d59d3-102">Método ISymUnmanagedWriter::Close</span><span class="sxs-lookup"><span data-stu-id="d59d3-102">ISymUnmanagedWriter::Close Method</span></span>
<span data-ttu-id="d59d3-103">Fecha o gravador de símbolo depois de confirmar os símbolos para o repositório de símbolos.</span><span class="sxs-lookup"><span data-stu-id="d59d3-103">Closes the symbol writer after committing the symbols to the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d59d3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d59d3-104">Syntax</span></span>  
  
```  
HRESULT Close();  
```  
  
## <a name="return-value"></a><span data-ttu-id="d59d3-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="d59d3-105">Return Value</span></span>  
 <span data-ttu-id="d59d3-106">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="d59d3-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d59d3-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="d59d3-107">Remarks</span></span>  
 <span data-ttu-id="d59d3-108">Após essa chamada, o gravador de símbolo se torna inválido para obter informações mais atualizadas.</span><span class="sxs-lookup"><span data-stu-id="d59d3-108">After this call, the symbol writer becomes invalid for further updates.</span></span> <span data-ttu-id="d59d3-109">Para fechar o gravador de símbolo sem confirmar os símbolos, use o [isymunmanagedwriter:: Abort](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-abort-method.md) método em vez disso.</span><span class="sxs-lookup"><span data-stu-id="d59d3-109">To close the symbol writer without committing the symbols, use the [ISymUnmanagedWriter::Abort](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-abort-method.md) method instead.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d59d3-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d59d3-110">Requirements</span></span>  
 <span data-ttu-id="d59d3-111">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d59d3-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d59d3-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d59d3-112">See also</span></span>

- [<span data-ttu-id="d59d3-113">Interface ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="d59d3-113">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
