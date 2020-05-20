---
title: Método ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReaderSymbolSearchInfo.GetSymbolSearchInfoCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount
helpviewer_keywords:
- GetSymbolSearchInfoCount method [.NET Framework debugging]
- ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount method [.NET Framework debugging]
ms.assetid: 4068b6ec-525f-4446-8818-0296178cbd19
topic_type:
- apiref
ms.openlocfilehash: a81a5afeec8f97864e1772347c6575b9d09cb176
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614884"
---
# <a name="isymunmanagedreadersymbolsearchinfogetsymbolsearchinfocount-method"></a><span data-ttu-id="2f2d4-102">Método ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount</span><span class="sxs-lookup"><span data-stu-id="2f2d4-102">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount Method</span></span>
<span data-ttu-id="2f2d4-103">Obtém uma contagem de informações de pesquisa de símbolo.</span><span class="sxs-lookup"><span data-stu-id="2f2d4-103">Gets a count of symbol search information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f2d4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2f2d4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSymbolSearchInfoCount(  
    [out] ULONG32 *pcSearchInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2f2d4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2f2d4-105">Parameters</span></span>  
 `pcSearchInfo`  
 <span data-ttu-id="2f2d4-106">] out] um ponteiro para um `ULONG32` que recebe o tamanho do buffer necessário para conter as informações de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="2f2d4-106">]out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the search information.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2f2d4-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="2f2d4-107">Return Value</span></span>  
 <span data-ttu-id="2f2d4-108">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="2f2d4-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f2d4-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2f2d4-109">Requirements</span></span>  
 <span data-ttu-id="2f2d4-110">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="2f2d4-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f2d4-111">Confira também</span><span class="sxs-lookup"><span data-stu-id="2f2d4-111">See also</span></span>

- [<span data-ttu-id="2f2d4-112">Interface ISymUnmanagedReaderSymbolSearchInfo</span><span class="sxs-lookup"><span data-stu-id="2f2d4-112">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>](isymunmanagedreadersymbolsearchinfo-interface.md)
