---
title: Método ISymUnmanagedWriter::Abort
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.Abort
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Abort
helpviewer_keywords:
- ISymUnmanagedWriter::Abort method [.NET Framework debugging]
- Abort method, ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: 416b220f-38d4-48e0-bb49-d2faa7366702
topic_type:
- apiref
ms.openlocfilehash: 6074ec5248d27b1405d2367349904f6630df951b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445986"
---
# <a name="isymunmanagedwriterabort-method"></a><span data-ttu-id="e8afb-102">Método ISymUnmanagedWriter::Abort</span><span class="sxs-lookup"><span data-stu-id="e8afb-102">ISymUnmanagedWriter::Abort Method</span></span>
<span data-ttu-id="e8afb-103">Fecha o gravador de símbolo sem confirmar os símbolos para o repositório de símbolos.</span><span class="sxs-lookup"><span data-stu-id="e8afb-103">Closes the symbol writer without committing the symbols to the symbol store.</span></span> <span data-ttu-id="e8afb-104">Após essa chamada, o gravador de símbolo se torna inválido para atualizações adicionais.</span><span class="sxs-lookup"><span data-stu-id="e8afb-104">After this call, the symbol writer becomes invalid for further updates.</span></span> <span data-ttu-id="e8afb-105">Para confirmar os símbolos e fechar o gravador de símbolo, use o método [ISymUnmanagedWriter:: Close](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-close-method.md) em vez disso.</span><span class="sxs-lookup"><span data-stu-id="e8afb-105">To commit the symbols and close the symbol writer, use the [ISymUnmanagedWriter::Close](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-close-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8afb-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e8afb-106">Syntax</span></span>  
  
```cpp  
HRESULT Abort();  
```  
  
## <a name="return-value"></a><span data-ttu-id="e8afb-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="e8afb-107">Return Value</span></span>  
 <span data-ttu-id="e8afb-108">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="e8afb-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8afb-109">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="e8afb-109">Requirements</span></span>  
 <span data-ttu-id="e8afb-110">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="e8afb-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8afb-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e8afb-111">See also</span></span>

- [<span data-ttu-id="e8afb-112">Interface ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="e8afb-112">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
