---
title: Método ISymUnmanagedVariable::GetName
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetName
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetName
helpviewer_keywords:
- GetName method, ISymUnmanagedVariable interface [.NET Framework debugging]
- ISymUnmanagedVariable::GetName method [.NET Framework debugging]
ms.assetid: eedf1ef0-9d4a-4847-a201-4e99572dfe5e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5aa6f01f161ce7c497cc103493e3bf4506fa3394
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57475015"
---
# <a name="isymunmanagedvariablegetname-method"></a><span data-ttu-id="8600c-102">Método ISymUnmanagedVariable::GetName</span><span class="sxs-lookup"><span data-stu-id="8600c-102">ISymUnmanagedVariable::GetName Method</span></span>
<span data-ttu-id="8600c-103">Obtém o nome dessa variável.</span><span class="sxs-lookup"><span data-stu-id="8600c-103">Gets the name of this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8600c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8600c-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8600c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8600c-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="8600c-106">[in] O comprimento do buffer que o `pcchName` parâmetro aponta.</span><span class="sxs-lookup"><span data-stu-id="8600c-106">[in] The length of the buffer that the `pcchName` parameter points to.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="8600c-107">[out] Um ponteiro para um `ULONG32` que recebe o tamanho, em caracteres, do buffer necessário para conter o nome, incluindo a terminação nula.</span><span class="sxs-lookup"><span data-stu-id="8600c-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="8600c-108">[out] O buffer que armazena o nome.</span><span class="sxs-lookup"><span data-stu-id="8600c-108">[out] The buffer that stores the name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8600c-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="8600c-109">Return Value</span></span>  
 <span data-ttu-id="8600c-110">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="8600c-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8600c-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8600c-111">Requirements</span></span>  
 <span data-ttu-id="8600c-112">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="8600c-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8600c-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8600c-113">See also</span></span>
- [<span data-ttu-id="8600c-114">Interface ISymUnmanagedVariable</span><span class="sxs-lookup"><span data-stu-id="8600c-114">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
