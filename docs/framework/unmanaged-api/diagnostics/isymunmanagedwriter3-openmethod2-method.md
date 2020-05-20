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
ms.openlocfilehash: e88a844a7f79f14c717a5966b345588b3b3b9f81
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83609411"
---
# <a name="isymunmanagedwriter3openmethod2-method"></a><span data-ttu-id="2fb77-102">Método ISymUnmanagedWriter3::OpenMethod2</span><span class="sxs-lookup"><span data-stu-id="2fb77-102">ISymUnmanagedWriter3::OpenMethod2 Method</span></span>
<span data-ttu-id="2fb77-103">Abre um método e fornece seu deslocamento de seção real na imagem.</span><span class="sxs-lookup"><span data-stu-id="2fb77-103">Opens a method and provides its real section offset in the image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2fb77-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2fb77-104">Syntax</span></span>  
  
```cpp  
HRESULT OpenMethod2(
    [in] mdMethodDef method,  
    [in] ULONG32 isect,  
    [in] ULONG32 offset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2fb77-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2fb77-105">Parameters</span></span>  
 `method`  
 <span data-ttu-id="2fb77-106">no O token de metadados para o método a ser aberto.</span><span class="sxs-lookup"><span data-stu-id="2fb77-106">[in] The metadata token for the method to be opened.</span></span>  
  
 `isect`  
 <span data-ttu-id="2fb77-107">no O deslocamento da seção na imagem.</span><span class="sxs-lookup"><span data-stu-id="2fb77-107">[in] The section offset in the image.</span></span>  
  
 `offset`  
 <span data-ttu-id="2fb77-108">no O deslocamento na imagem.</span><span class="sxs-lookup"><span data-stu-id="2fb77-108">[in] The offset in the image.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2fb77-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="2fb77-109">Return Value</span></span>  
 <span data-ttu-id="2fb77-110">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="2fb77-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2fb77-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2fb77-111">Requirements</span></span>  
 <span data-ttu-id="2fb77-112">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="2fb77-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2fb77-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="2fb77-113">See also</span></span>

- [<span data-ttu-id="2fb77-114">Interface ISymUnmanagedWriter3</span><span class="sxs-lookup"><span data-stu-id="2fb77-114">ISymUnmanagedWriter3 Interface</span></span>](isymunmanagedwriter3-interface.md)
- [<span data-ttu-id="2fb77-115">Método OpenMethod</span><span class="sxs-lookup"><span data-stu-id="2fb77-115">OpenMethod Method</span></span>](isymunmanagedwriter-openmethod-method.md)
