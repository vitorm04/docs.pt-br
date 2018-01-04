---
title: "Método ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReaderSymbolSearchInfo.GetSymbolSearchInfoCount
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount
helpviewer_keywords:
- GetSymbolSearchInfoCount method [.NET Framework debugging]
- ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount method [.NET Framework debugging]
ms.assetid: 4068b6ec-525f-4446-8818-0296178cbd19
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c87ef1b3ce185c2a92813f231abe6a9ef14ac055
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedreadersymbolsearchinfogetsymbolsearchinfocount-method"></a><span data-ttu-id="39cb2-102">Método ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount</span><span class="sxs-lookup"><span data-stu-id="39cb2-102">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount Method</span></span>
<span data-ttu-id="39cb2-103">Obtém uma contagem de informações de pesquisa do símbolo.</span><span class="sxs-lookup"><span data-stu-id="39cb2-103">Gets a count of symbol search information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39cb2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="39cb2-104">Syntax</span></span>  
  
```  
HRESULT GetSymbolSearchInfoCount(  
    [out] ULONG32 *pcSearchInfo);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="39cb2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="39cb2-105">Parameters</span></span>  
 `pcSearchInfo`  
 <span data-ttu-id="39cb2-106">] out] um ponteiro para um `ULONG32` que recebe o tamanho do buffer necessário para conter as informações de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="39cb2-106">]out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the search information.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="39cb2-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="39cb2-107">Return Value</span></span>  
 <span data-ttu-id="39cb2-108">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="39cb2-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39cb2-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="39cb2-109">Requirements</span></span>  
 <span data-ttu-id="39cb2-110">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="39cb2-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39cb2-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="39cb2-111">See Also</span></span>  
 [<span data-ttu-id="39cb2-112">Interface ISymUnmanagedReaderSymbolSearchInfo</span><span class="sxs-lookup"><span data-stu-id="39cb2-112">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreadersymbolsearchinfo-interface.md)
