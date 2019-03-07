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
ms.openlocfilehash: dd24289f7e670684effa553f930af9aec92e5730
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57469594"
---
# <a name="isymunmanagedsymbolsearchinfogethresult-method"></a><span data-ttu-id="0599c-102">Método ISymUnmanagedSymbolSearchInfo::GetHRESULT</span><span class="sxs-lookup"><span data-stu-id="0599c-102">ISymUnmanagedSymbolSearchInfo::GetHRESULT Method</span></span>
<span data-ttu-id="0599c-103">Obtém o HRESULT.</span><span class="sxs-lookup"><span data-stu-id="0599c-103">Gets the HRESULT.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0599c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0599c-104">Syntax</span></span>  
  
```  
HRESULT GetHRESULT(  
    [out] HRESULT *phr);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0599c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0599c-105">Parameters</span></span>  
 `phr`  
 <span data-ttu-id="0599c-106">[out] Um ponteiro para o HRESULT.</span><span class="sxs-lookup"><span data-stu-id="0599c-106">[out] A pointer to the HRESULT.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0599c-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="0599c-107">Return Value</span></span>  
 <span data-ttu-id="0599c-108">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="0599c-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0599c-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0599c-109">Requirements</span></span>  
 <span data-ttu-id="0599c-110">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="0599c-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0599c-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0599c-111">See also</span></span>
- [<span data-ttu-id="0599c-112">Interface ISymUnmanagedSymbolSearchInfo</span><span class="sxs-lookup"><span data-stu-id="0599c-112">ISymUnmanagedSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)
