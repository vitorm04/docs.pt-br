---
title: Método ISymUnmanagedWriter3::OpenMethod2
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter3.OpenMethod2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter3::OpenMethod2
helpviewer_keywords:
- ISymUnmanagedWriter3::OpenMethod2 method [.NET Framework debugging]
- OpenMethod2 method [.NET Framework debugging]
ms.assetid: 025e358c-448f-4423-a2f2-57acf437c8a5
topic_type:
- apiref
ms.openlocfilehash: 0c112819ef3bc4f9a7146ee80f55202ff89d689a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178325"
---
# <a name="isymunmanagedwriter3openmethod2-method"></a><span data-ttu-id="9ea94-102">Método ISymUnmanagedWriter3::OpenMethod2</span><span class="sxs-lookup"><span data-stu-id="9ea94-102">ISymUnmanagedWriter3::OpenMethod2 Method</span></span>
<span data-ttu-id="9ea94-103">Abre um método e fornece sua real compensação de seção na imagem.</span><span class="sxs-lookup"><span data-stu-id="9ea94-103">Opens a method and provides its real section offset in the image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ea94-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9ea94-104">Syntax</span></span>  
  
```cpp  
HRESULT OpenMethod2(
    [in] mdMethodDef method,  
    [in] ULONG32 isect,  
    [in] ULONG32 offset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9ea94-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="9ea94-105">Parameters</span></span>  
 `method`  
 <span data-ttu-id="9ea94-106">[em] O token de metadados para o método a ser aberto.</span><span class="sxs-lookup"><span data-stu-id="9ea94-106">[in] The metadata token for the method to be opened.</span></span>  
  
 `isect`  
 <span data-ttu-id="9ea94-107">[em] A seção deslocada na imagem.</span><span class="sxs-lookup"><span data-stu-id="9ea94-107">[in] The section offset in the image.</span></span>  
  
 `offset`  
 <span data-ttu-id="9ea94-108">[em] O deslocamento na imagem.</span><span class="sxs-lookup"><span data-stu-id="9ea94-108">[in] The offset in the image.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9ea94-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="9ea94-109">Return Value</span></span>  
 <span data-ttu-id="9ea94-110">S_OK se o método for bem sucedido; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="9ea94-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ea94-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9ea94-111">Requirements</span></span>  
 <span data-ttu-id="9ea94-112">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="9ea94-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ea94-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="9ea94-113">See also</span></span>

- [<span data-ttu-id="9ea94-114">Interface ISymUnmanagedWriter3</span><span class="sxs-lookup"><span data-stu-id="9ea94-114">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
- [<span data-ttu-id="9ea94-115">Método OpenMethod</span><span class="sxs-lookup"><span data-stu-id="9ea94-115">OpenMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)
