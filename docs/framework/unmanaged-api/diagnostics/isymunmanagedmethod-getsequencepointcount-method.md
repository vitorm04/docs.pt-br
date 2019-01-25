---
title: Método ISymUnmanagedMethod::GetSequencePointCount
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetSequencePointCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetSequencePointCount
helpviewer_keywords:
- ISymUnmanagedMethod::GetSequencePointCount method [.NET Framework debugging]
- GetSequencePointCount method [.NET Framework debugging]
ms.assetid: 836133e8-6108-4b9b-b0a9-bce4e08dccda
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e8e919c546df93a2023858c31ebc4d2dec507513
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54730133"
---
# <a name="isymunmanagedmethodgetsequencepointcount-method"></a><span data-ttu-id="2c28f-102">Método ISymUnmanagedMethod::GetSequencePointCount</span><span class="sxs-lookup"><span data-stu-id="2c28f-102">ISymUnmanagedMethod::GetSequencePointCount Method</span></span>
<span data-ttu-id="2c28f-103">Obtém a contagem de pontos de sequência dentro desse método.</span><span class="sxs-lookup"><span data-stu-id="2c28f-103">Gets the count of sequence points within this method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c28f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2c28f-104">Syntax</span></span>  
  
```  
HRESULT GetSequencePointCount(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2c28f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2c28f-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="2c28f-106">[out] Um ponteiro para um `ULONG32` que recebe o tamanho do buffer necessário para conter os pontos de sequência.</span><span class="sxs-lookup"><span data-stu-id="2c28f-106">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the sequence points.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2c28f-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="2c28f-107">Return Value</span></span>  
 <span data-ttu-id="2c28f-108">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="2c28f-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c28f-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2c28f-109">Requirements</span></span>  
 <span data-ttu-id="2c28f-110">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="2c28f-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c28f-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2c28f-111">See also</span></span>
- [<span data-ttu-id="2c28f-112">Interface ISymUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="2c28f-112">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
