---
title: Método ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReaderSymbolSearchInfo.GetSymbolSearchInfo
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo
helpviewer_keywords:
- GetSymbolSearchInfo method [.NET Framework debugging]
- ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo method [.NET Framework debugging]
ms.assetid: 40fcdbc5-3bb2-41e9-b995-40984c209a7f
topic_type:
- apiref
ms.openlocfilehash: 2b5a42c89e0e3efed61b1b471c227e0df85a51aa
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614897"
---
# <a name="isymunmanagedreadersymbolsearchinfogetsymbolsearchinfo-method"></a><span data-ttu-id="fee1f-102">Método ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo</span><span class="sxs-lookup"><span data-stu-id="fee1f-102">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo Method</span></span>
<span data-ttu-id="fee1f-103">Obtém informações de pesquisa de símbolo.</span><span class="sxs-lookup"><span data-stu-id="fee1f-103">Gets symbol search information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fee1f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fee1f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSymbolSearchInfo(  
    [in]  ULONG32  cSearchInfo,  
    [out] ULONG32  *pcSearchInfo,  
    [out, size_is(cSearchInfo), length_is(*pcSearchInfo)]  
        ISymUnmanagedSymbolSearchInfo **rgpSearchInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fee1f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fee1f-105">Parameters</span></span>  
 `cSearchInfo`  
 <span data-ttu-id="fee1f-106">no Um `ULONG32` que indica o tamanho de `rgpSearchInfo` .</span><span class="sxs-lookup"><span data-stu-id="fee1f-106">[in] A `ULONG32` that indicates the size of `rgpSearchInfo`.</span></span>  
  
 `pcSearchInfo`  
 <span data-ttu-id="fee1f-107">fora Um ponteiro para um `ULONG32` que recebe o tamanho do buffer necessário para conter as informações de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="fee1f-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the search information.</span></span>  
  
 `rgpSearchInfo`  
 <span data-ttu-id="fee1f-108">fora Um ponteiro que é definido para a interface [ISymUnmanagedSymbolSearchInfo](isymunmanagedsymbolsearchinfo-interface.md) retornada.</span><span class="sxs-lookup"><span data-stu-id="fee1f-108">[out] A pointer that is set to the returned [ISymUnmanagedSymbolSearchInfo](isymunmanagedsymbolsearchinfo-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fee1f-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="fee1f-109">Return Value</span></span>  
 <span data-ttu-id="fee1f-110">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="fee1f-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fee1f-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fee1f-111">Requirements</span></span>  
 <span data-ttu-id="fee1f-112">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="fee1f-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fee1f-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="fee1f-113">See also</span></span>

- [<span data-ttu-id="fee1f-114">Interface ISymUnmanagedReaderSymbolSearchInfo</span><span class="sxs-lookup"><span data-stu-id="fee1f-114">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>](isymunmanagedreadersymbolsearchinfo-interface.md)
