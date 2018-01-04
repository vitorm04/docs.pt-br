---
title: "Método ISymUnmanagedWriter3::OpenMethod2"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter3.OpenMethod2
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter3::OpenMethod2
helpviewer_keywords:
- ISymUnmanagedWriter3::OpenMethod2 method [.NET Framework debugging]
- OpenMethod2 method [.NET Framework debugging]
ms.assetid: 025e358c-448f-4423-a2f2-57acf437c8a5
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8da6de0271ddce5b956e667420a206c09cc291d8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriter3openmethod2-method"></a><span data-ttu-id="79956-102">Método ISymUnmanagedWriter3::OpenMethod2</span><span class="sxs-lookup"><span data-stu-id="79956-102">ISymUnmanagedWriter3::OpenMethod2 Method</span></span>
<span data-ttu-id="79956-103">Abre um método e fornece seu deslocamento real de seção na imagem.</span><span class="sxs-lookup"><span data-stu-id="79956-103">Opens a method and provides its real section offset in the image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79956-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="79956-104">Syntax</span></span>  
  
```  
HRESULT OpenMethod2(   
    [in] mdMethodDef method,  
    [in] ULONG32 isect,  
    [in] ULONG32 offset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="79956-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="79956-105">Parameters</span></span>  
 `method`  
 <span data-ttu-id="79956-106">[in] O token de metadados para o método a ser aberto.</span><span class="sxs-lookup"><span data-stu-id="79956-106">[in] The metadata token for the method to be opened.</span></span>  
  
 `isect`  
 <span data-ttu-id="79956-107">[in] O deslocamento de seção na imagem.</span><span class="sxs-lookup"><span data-stu-id="79956-107">[in] The section offset in the image.</span></span>  
  
 `offset`  
 <span data-ttu-id="79956-108">[in] O deslocamento da imagem.</span><span class="sxs-lookup"><span data-stu-id="79956-108">[in] The offset in the image.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="79956-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="79956-109">Return Value</span></span>  
 <span data-ttu-id="79956-110">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="79956-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79956-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="79956-111">Requirements</span></span>  
 <span data-ttu-id="79956-112">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="79956-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79956-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="79956-113">See Also</span></span>  
 [<span data-ttu-id="79956-114">Interface ISymUnmanagedWriter3</span><span class="sxs-lookup"><span data-stu-id="79956-114">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)  
 [<span data-ttu-id="79956-115">Método OpenMethod</span><span class="sxs-lookup"><span data-stu-id="79956-115">OpenMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)
