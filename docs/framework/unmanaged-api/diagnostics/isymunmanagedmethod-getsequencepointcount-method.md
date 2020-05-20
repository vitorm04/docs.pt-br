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
ms.openlocfilehash: a44f81deb2d57b49f1fd0650fa52c06383210352
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614429"
---
# <a name="isymunmanagedmethodgetsequencepointcount-method"></a><span data-ttu-id="35d84-102">Método ISymUnmanagedMethod::GetSequencePointCount</span><span class="sxs-lookup"><span data-stu-id="35d84-102">ISymUnmanagedMethod::GetSequencePointCount Method</span></span>
<span data-ttu-id="35d84-103">Obtém a contagem de pontos de sequência dentro deste método.</span><span class="sxs-lookup"><span data-stu-id="35d84-103">Gets the count of sequence points within this method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35d84-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="35d84-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSequencePointCount(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="35d84-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="35d84-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="35d84-106">fora Um ponteiro para um `ULONG32` que recebe o tamanho do buffer necessário para conter os pontos de sequência.</span><span class="sxs-lookup"><span data-stu-id="35d84-106">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the sequence points.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="35d84-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="35d84-107">Return Value</span></span>  
 <span data-ttu-id="35d84-108">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="35d84-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35d84-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="35d84-109">Requirements</span></span>  
 <span data-ttu-id="35d84-110">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="35d84-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35d84-111">Veja também</span><span class="sxs-lookup"><span data-stu-id="35d84-111">See also</span></span>

- [<span data-ttu-id="35d84-112">Interface ISymUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="35d84-112">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
