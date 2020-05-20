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
ms.openlocfilehash: 9dcd8282adf200932e86c950bee0b073780ce02d
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615300"
---
# <a name="isymunmanagedsymbolsearchinfogethresult-method"></a><span data-ttu-id="15a08-102">Método ISymUnmanagedSymbolSearchInfo::GetHRESULT</span><span class="sxs-lookup"><span data-stu-id="15a08-102">ISymUnmanagedSymbolSearchInfo::GetHRESULT Method</span></span>
<span data-ttu-id="15a08-103">Obtém o HRESULT.</span><span class="sxs-lookup"><span data-stu-id="15a08-103">Gets the HRESULT.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15a08-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="15a08-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHRESULT(  
    [out] HRESULT *phr);  
```  
  
## <a name="parameters"></a><span data-ttu-id="15a08-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="15a08-105">Parameters</span></span>  
 `phr`  
 <span data-ttu-id="15a08-106">fora Um ponteiro para o HRESULT.</span><span class="sxs-lookup"><span data-stu-id="15a08-106">[out] A pointer to the HRESULT.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="15a08-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="15a08-107">Return Value</span></span>  
 <span data-ttu-id="15a08-108">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="15a08-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15a08-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="15a08-109">Requirements</span></span>  
 <span data-ttu-id="15a08-110">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="15a08-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15a08-111">Confira também</span><span class="sxs-lookup"><span data-stu-id="15a08-111">See also</span></span>

- [<span data-ttu-id="15a08-112">Interface ISymUnmanagedSymbolSearchInfo</span><span class="sxs-lookup"><span data-stu-id="15a08-112">ISymUnmanagedSymbolSearchInfo Interface</span></span>](isymunmanagedsymbolsearchinfo-interface.md)
