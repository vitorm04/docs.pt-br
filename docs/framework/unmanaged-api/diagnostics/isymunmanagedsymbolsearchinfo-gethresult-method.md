---
title: Método ISymUnmanagedSymbolSearchInfo::GetHRESULT
ms.date: 03/30/2017
api_name:
- ISymUnmanagedSymbolSearchInfo.GetHRESULT
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedSymbolSearchInfo::GetHRESULT
helpviewer_keywords:
- ISymUnmanagedSymbolSearchInfo::GetHRESULT method [.NET Framework debugging]
- GetHRESULT method [.NET Framework debugging]
ms.assetid: 6999dc3d-65d7-4bf6-bb0a-6efc0fc72588
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1534955c1f7cfd37732a08b0b33cda5bff8a8aab
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59113016"
---
# <a name="isymunmanagedsymbolsearchinfogethresult-method"></a><span data-ttu-id="59821-102">Método ISymUnmanagedSymbolSearchInfo::GetHRESULT</span><span class="sxs-lookup"><span data-stu-id="59821-102">ISymUnmanagedSymbolSearchInfo::GetHRESULT Method</span></span>
<span data-ttu-id="59821-103">Obtém o HRESULT.</span><span class="sxs-lookup"><span data-stu-id="59821-103">Gets the HRESULT.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59821-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="59821-104">Syntax</span></span>  
  
```  
HRESULT GetHRESULT(  
    [out] HRESULT *phr);  
```  
  
## <a name="parameters"></a><span data-ttu-id="59821-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="59821-105">Parameters</span></span>  
 `phr`  
 <span data-ttu-id="59821-106">[out] Um ponteiro para o HRESULT.</span><span class="sxs-lookup"><span data-stu-id="59821-106">[out] A pointer to the HRESULT.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="59821-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="59821-107">Return Value</span></span>  
 <span data-ttu-id="59821-108">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="59821-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59821-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="59821-109">Requirements</span></span>  
 <span data-ttu-id="59821-110">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="59821-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59821-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="59821-111">See also</span></span>

- [<span data-ttu-id="59821-112">Interface ISymUnmanagedSymbolSearchInfo</span><span class="sxs-lookup"><span data-stu-id="59821-112">ISymUnmanagedSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)
