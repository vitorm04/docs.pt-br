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
ms.openlocfilehash: 73ece48a21ac40320379f5bf4ea309a3ec36b40f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67736771"
---
# <a name="isymunmanagedconstantgetname-method"></a><span data-ttu-id="b05a5-102">Método ISymUnmanagedConstant::GetName</span><span class="sxs-lookup"><span data-stu-id="b05a5-102">ISymUnmanagedConstant::GetName Method</span></span>
<span data-ttu-id="b05a5-103">Obtém o nome da constante.</span><span class="sxs-lookup"><span data-stu-id="b05a5-103">Gets the name of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b05a5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b05a5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b05a5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b05a5-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="b05a5-106">[in] O comprimento do buffer que o `szName` parâmetro aponta.</span><span class="sxs-lookup"><span data-stu-id="b05a5-106">[in] The length of the buffer that the `szName` parameter points to.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="b05a5-107">[out] Um ponteiro para um `ULONG32` que recebe o tamanho, em caracteres, do buffer necessário para conter o nome, incluindo a terminação nula.</span><span class="sxs-lookup"><span data-stu-id="b05a5-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="b05a5-108">[out] O buffer que armazena o nome.</span><span class="sxs-lookup"><span data-stu-id="b05a5-108">[out] The buffer that stores the name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b05a5-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="b05a5-109">Return Value</span></span>  
 <span data-ttu-id="b05a5-110">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="b05a5-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b05a5-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b05a5-111">Requirements</span></span>  
 <span data-ttu-id="b05a5-112">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b05a5-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b05a5-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b05a5-113">See also</span></span>

- [<span data-ttu-id="b05a5-114">Interface ISymUnmanagedConstant</span><span class="sxs-lookup"><span data-stu-id="b05a5-114">ISymUnmanagedConstant Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)
- [<span data-ttu-id="b05a5-115">Método GetSignature</span><span class="sxs-lookup"><span data-stu-id="b05a5-115">GetSignature Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getsignature-method.md)
- [<span data-ttu-id="b05a5-116">Método GetValue</span><span class="sxs-lookup"><span data-stu-id="b05a5-116">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getvalue-method.md)
