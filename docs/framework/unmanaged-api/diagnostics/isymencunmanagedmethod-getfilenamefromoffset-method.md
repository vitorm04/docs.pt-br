---
title: "Método ISymENCUnmanagedMethod::GetFileNameFromOffset"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymENCUnmanagedMethod.GetFileNameFromOffset
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymENCUnmanagedMethod::GetFileNameFromOffset
helpviewer_keywords:
- GetFileNameFromOffset method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetFileNameFromOffset method [.NET Framework debugging]
ms.assetid: 00e2e194-12f5-436e-a997-2b9d3e844d4f
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5f4b760f2782cf75cf0ab0879eb77e185a93b8b2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="isymencunmanagedmethodgetfilenamefromoffset-method"></a><span data-ttu-id="ddbf7-102">Método ISymENCUnmanagedMethod::GetFileNameFromOffset</span><span class="sxs-lookup"><span data-stu-id="ddbf7-102">ISymENCUnmanagedMethod::GetFileNameFromOffset Method</span></span>
<span data-ttu-id="ddbf7-103">Obtém o nome do arquivo para a linha associada a um deslocamento.</span><span class="sxs-lookup"><span data-stu-id="ddbf7-103">Gets the file name for the line associated with an offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ddbf7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ddbf7-104">Syntax</span></span>  
  
```  
HRESULT GetFileNameFromOffset(  
    [in]  ULONG32  dwOffset,  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
       length_is(*pcchName)] WCHAR szName[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ddbf7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ddbf7-105">Parameters</span></span>  
 `dwOffset`  
 <span data-ttu-id="ddbf7-106">[in] Um `ULONG32` que contém o deslocamento.</span><span class="sxs-lookup"><span data-stu-id="ddbf7-106">[in] A `ULONG32` that contains the offset.</span></span>  
  
 `cchName`  
 <span data-ttu-id="ddbf7-107">[in] Um `ULONG32` que indica o tamanho do `szName` buffer.</span><span class="sxs-lookup"><span data-stu-id="ddbf7-107">[in] A `ULONG32` that indicates the size of the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="ddbf7-108">[out] Um ponteiro para um `ULONG32` que recebe o tamanho, em caracteres, do buffer necessário para conter os nomes de arquivo.</span><span class="sxs-lookup"><span data-stu-id="ddbf7-108">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the file names.</span></span>  
  
 `szName`  
 <span data-ttu-id="ddbf7-109">[out] O buffer que contém os nomes de arquivo.</span><span class="sxs-lookup"><span data-stu-id="ddbf7-109">[out] The buffer that contains the file names.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ddbf7-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="ddbf7-110">Return Value</span></span>  
 <span data-ttu-id="ddbf7-111">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="ddbf7-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ddbf7-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ddbf7-112">Requirements</span></span>  
 <span data-ttu-id="ddbf7-113">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ddbf7-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddbf7-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ddbf7-114">See Also</span></span>  
 [<span data-ttu-id="ddbf7-115">Interface ISymENCUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="ddbf7-115">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
