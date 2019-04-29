---
title: Método ISymUnmanagedConstant::GetName
ms.date: 03/30/2017
api_name:
- ISymUnmanagedConstant.GetName
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedConstant::GetName
helpviewer_keywords:
- ISymUnmanagedConstant::GetName method [.NET Framework debugging]
- GetName method, ISymUnmanagedConstant interface [.NET Framework debugging]
ms.assetid: cbaca4e1-4473-459b-ba34-f1f59ce7c0ba
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1da8d89cf9ae2eed7b846774434d6ea472afbb94
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61939965"
---
# <a name="isymunmanagedconstantgetname-method"></a><span data-ttu-id="5372c-102">Método ISymUnmanagedConstant::GetName</span><span class="sxs-lookup"><span data-stu-id="5372c-102">ISymUnmanagedConstant::GetName Method</span></span>
<span data-ttu-id="5372c-103">Obtém o nome da constante.</span><span class="sxs-lookup"><span data-stu-id="5372c-103">Gets the name of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5372c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5372c-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5372c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5372c-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="5372c-106">[in] O comprimento do buffer que o `szName` parâmetro aponta.</span><span class="sxs-lookup"><span data-stu-id="5372c-106">[in] The length of the buffer that the `szName` parameter points to.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="5372c-107">[out] Um ponteiro para um `ULONG32` que recebe o tamanho, em caracteres, do buffer necessário para conter o nome, incluindo a terminação nula.</span><span class="sxs-lookup"><span data-stu-id="5372c-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="5372c-108">[out] O buffer que armazena o nome.</span><span class="sxs-lookup"><span data-stu-id="5372c-108">[out] The buffer that stores the name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5372c-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="5372c-109">Return Value</span></span>  
 <span data-ttu-id="5372c-110">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="5372c-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5372c-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5372c-111">Requirements</span></span>  
 <span data-ttu-id="5372c-112">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="5372c-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5372c-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5372c-113">See also</span></span>

- [<span data-ttu-id="5372c-114">Interface ISymUnmanagedConstant</span><span class="sxs-lookup"><span data-stu-id="5372c-114">ISymUnmanagedConstant Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)
- [<span data-ttu-id="5372c-115">Método GetSignature</span><span class="sxs-lookup"><span data-stu-id="5372c-115">GetSignature Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getsignature-method.md)
- [<span data-ttu-id="5372c-116">Método GetValue</span><span class="sxs-lookup"><span data-stu-id="5372c-116">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getvalue-method.md)
