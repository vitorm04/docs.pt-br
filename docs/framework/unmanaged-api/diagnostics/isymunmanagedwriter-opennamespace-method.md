---
title: Método ISymUnmanagedWriter::OpenNamespace
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.OpenNamespace
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::OpenNamespace
helpviewer_keywords:
- ISymUnmanagedWriter::OpenNamespace method [.NET Framework debugging]
- OpenNamespace method [.NET Framework debugging]
ms.assetid: 426f4e4f-e60d-4ad1-b546-a10e3c55c283
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1585acce8bba0dff327c961f5e32ef6b46794401
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59126328"
---
# <a name="isymunmanagedwriteropennamespace-method"></a><span data-ttu-id="08efa-102">Método ISymUnmanagedWriter::OpenNamespace</span><span class="sxs-lookup"><span data-stu-id="08efa-102">ISymUnmanagedWriter::OpenNamespace Method</span></span>
<span data-ttu-id="08efa-103">Abre um novo namespace.</span><span class="sxs-lookup"><span data-stu-id="08efa-103">Opens a new namespace.</span></span> <span data-ttu-id="08efa-104">Chame esse método antes de definir os métodos ou variáveis que ocupam um namespace.</span><span class="sxs-lookup"><span data-stu-id="08efa-104">Call this method before defining methods or variables that occupy a namespace.</span></span> <span data-ttu-id="08efa-105">Namespaces podem ser aninhados.</span><span class="sxs-lookup"><span data-stu-id="08efa-105">Namespaces can be nested.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08efa-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="08efa-106">Syntax</span></span>  
  
```  
HRESULT OpenNamespace(  
    [in] const WCHAR *name);  
```  
  
## <a name="parameters"></a><span data-ttu-id="08efa-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="08efa-107">Parameters</span></span>  
 `name`  
 <span data-ttu-id="08efa-108">[in] Um ponteiro para o nome do novo namespace.</span><span class="sxs-lookup"><span data-stu-id="08efa-108">[in] A pointer to the name of the new namespace.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="08efa-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="08efa-109">Return Value</span></span>  
 <span data-ttu-id="08efa-110">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="08efa-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08efa-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="08efa-111">Requirements</span></span>  
 <span data-ttu-id="08efa-112">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="08efa-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08efa-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="08efa-113">See also</span></span>

- [<span data-ttu-id="08efa-114">Interface ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="08efa-114">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="08efa-115">Método CloseNamespace</span><span class="sxs-lookup"><span data-stu-id="08efa-115">CloseNamespace Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closenamespace-method.md)
