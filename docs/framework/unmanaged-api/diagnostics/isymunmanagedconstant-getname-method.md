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
ms.openlocfilehash: 924feaeb91b42404461ad5d276c0cb77279d4dc4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449285"
---
# <a name="isymunmanagedconstantgetname-method"></a><span data-ttu-id="51331-102">Método ISymUnmanagedConstant::GetName</span><span class="sxs-lookup"><span data-stu-id="51331-102">ISymUnmanagedConstant::GetName Method</span></span>
<span data-ttu-id="51331-103">Obtém o nome da constante.</span><span class="sxs-lookup"><span data-stu-id="51331-103">Gets the name of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51331-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="51331-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="51331-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="51331-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="51331-106">no O comprimento do buffer ao qual o parâmetro `szName` aponta.</span><span class="sxs-lookup"><span data-stu-id="51331-106">[in] The length of the buffer that the `szName` parameter points to.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="51331-107">fora Um ponteiro para um `ULONG32` que recebe o tamanho, em caracteres, do buffer necessário para conter o nome, incluindo a terminação nula.</span><span class="sxs-lookup"><span data-stu-id="51331-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="51331-108">fora O buffer que armazena o nome.</span><span class="sxs-lookup"><span data-stu-id="51331-108">[out] The buffer that stores the name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="51331-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="51331-109">Return Value</span></span>  
 <span data-ttu-id="51331-110">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="51331-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51331-111">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="51331-111">Requirements</span></span>  
 <span data-ttu-id="51331-112">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="51331-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51331-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="51331-113">See also</span></span>

- [<span data-ttu-id="51331-114">Interface ISymUnmanagedConstant</span><span class="sxs-lookup"><span data-stu-id="51331-114">ISymUnmanagedConstant Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)
- [<span data-ttu-id="51331-115">Método GetSignature</span><span class="sxs-lookup"><span data-stu-id="51331-115">GetSignature Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getsignature-method.md)
- [<span data-ttu-id="51331-116">Método GetValue</span><span class="sxs-lookup"><span data-stu-id="51331-116">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getvalue-method.md)
