---
title: Método ISymUnmanagedMethod::GetToken
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetToken
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetToken
helpviewer_keywords:
- ISymUnmanagedMethod::GetToken method [.NET Framework debugging]
- GetToken method, ISymUnmanagedMethod interface [.NET Framework debugging]
ms.assetid: 4effbe95-c36e-4a45-8b2a-ee21339415fb
topic_type:
- apiref
ms.openlocfilehash: 0803f0b55f19b779f5b6608a9f8200d2b085b504
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615147"
---
# <a name="isymunmanagedmethodgettoken-method"></a><span data-ttu-id="02c64-102">Método ISymUnmanagedMethod::GetToken</span><span class="sxs-lookup"><span data-stu-id="02c64-102">ISymUnmanagedMethod::GetToken Method</span></span>
<span data-ttu-id="02c64-103">Retorna o token de metadados para esse método.</span><span class="sxs-lookup"><span data-stu-id="02c64-103">Returns the metadata token for this method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02c64-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="02c64-104">Syntax</span></span>  
  
```cpp  
HRESULT GetToken(  
   [out, retval]  mdMethodDef  *pToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="02c64-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="02c64-105">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="02c64-106">fora Um ponteiro para um `mdMethodDef` que recebe o tamanho, em caracteres, do buffer necessário para conter os metadados.</span><span class="sxs-lookup"><span data-stu-id="02c64-106">[out] A pointer to a `mdMethodDef` that receives the size, in characters, of the buffer required to contain the metadata.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="02c64-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="02c64-107">Return Value</span></span>  
 <span data-ttu-id="02c64-108">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="02c64-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02c64-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="02c64-109">Requirements</span></span>  
 <span data-ttu-id="02c64-110">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="02c64-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02c64-111">Confira também</span><span class="sxs-lookup"><span data-stu-id="02c64-111">See also</span></span>

- [<span data-ttu-id="02c64-112">Interface ISymUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="02c64-112">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
