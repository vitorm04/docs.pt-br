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
ms.openlocfilehash: acbd49de7362d9c05a609a2d870af100637e10ab
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427909"
---
# <a name="isymunmanagedwriteropennamespace-method"></a><span data-ttu-id="cfc9f-102">Método ISymUnmanagedWriter::OpenNamespace</span><span class="sxs-lookup"><span data-stu-id="cfc9f-102">ISymUnmanagedWriter::OpenNamespace Method</span></span>
<span data-ttu-id="cfc9f-103">Abre um novo namespace.</span><span class="sxs-lookup"><span data-stu-id="cfc9f-103">Opens a new namespace.</span></span> <span data-ttu-id="cfc9f-104">Chame esse método antes de definir métodos ou variáveis que ocupem um namespace.</span><span class="sxs-lookup"><span data-stu-id="cfc9f-104">Call this method before defining methods or variables that occupy a namespace.</span></span> <span data-ttu-id="cfc9f-105">Os namespaces podem ser aninhados.</span><span class="sxs-lookup"><span data-stu-id="cfc9f-105">Namespaces can be nested.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cfc9f-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cfc9f-106">Syntax</span></span>  
  
```cpp  
HRESULT OpenNamespace(  
    [in] const WCHAR *name);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cfc9f-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cfc9f-107">Parameters</span></span>  
 `name`  
 <span data-ttu-id="cfc9f-108">no Um ponteiro para o nome do novo namespace.</span><span class="sxs-lookup"><span data-stu-id="cfc9f-108">[in] A pointer to the name of the new namespace.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cfc9f-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="cfc9f-109">Return Value</span></span>  
 <span data-ttu-id="cfc9f-110">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="cfc9f-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cfc9f-111">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="cfc9f-111">Requirements</span></span>  
 <span data-ttu-id="cfc9f-112">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="cfc9f-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfc9f-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cfc9f-113">See also</span></span>

- [<span data-ttu-id="cfc9f-114">Interface ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="cfc9f-114">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="cfc9f-115">Método CloseNamespace</span><span class="sxs-lookup"><span data-stu-id="cfc9f-115">CloseNamespace Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closenamespace-method.md)
