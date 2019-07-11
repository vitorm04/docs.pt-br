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
ms.openlocfilehash: 5bd07411acd074bf5a25148110dbdf28a004551a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777250"
---
# <a name="isymunmanagedwriteropennamespace-method"></a><span data-ttu-id="28926-102">Método ISymUnmanagedWriter::OpenNamespace</span><span class="sxs-lookup"><span data-stu-id="28926-102">ISymUnmanagedWriter::OpenNamespace Method</span></span>
<span data-ttu-id="28926-103">Abre um novo namespace.</span><span class="sxs-lookup"><span data-stu-id="28926-103">Opens a new namespace.</span></span> <span data-ttu-id="28926-104">Chame esse método antes de definir os métodos ou variáveis que ocupam um namespace.</span><span class="sxs-lookup"><span data-stu-id="28926-104">Call this method before defining methods or variables that occupy a namespace.</span></span> <span data-ttu-id="28926-105">Namespaces podem ser aninhados.</span><span class="sxs-lookup"><span data-stu-id="28926-105">Namespaces can be nested.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28926-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="28926-106">Syntax</span></span>  
  
```cpp  
HRESULT OpenNamespace(  
    [in] const WCHAR *name);  
```  
  
## <a name="parameters"></a><span data-ttu-id="28926-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="28926-107">Parameters</span></span>  
 `name`  
 <span data-ttu-id="28926-108">[in] Um ponteiro para o nome do novo namespace.</span><span class="sxs-lookup"><span data-stu-id="28926-108">[in] A pointer to the name of the new namespace.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="28926-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="28926-109">Return Value</span></span>  
 <span data-ttu-id="28926-110">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="28926-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28926-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="28926-111">Requirements</span></span>  
 <span data-ttu-id="28926-112">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="28926-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28926-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="28926-113">See also</span></span>

- [<span data-ttu-id="28926-114">Interface ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="28926-114">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="28926-115">Método CloseNamespace</span><span class="sxs-lookup"><span data-stu-id="28926-115">CloseNamespace Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closenamespace-method.md)
