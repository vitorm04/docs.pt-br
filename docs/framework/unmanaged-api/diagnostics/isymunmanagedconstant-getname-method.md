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
ms.openlocfilehash: 2dd70693528904459a34689dbad944c65c971254
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441637"
---
# <a name="isymunmanagedconstantgetname-method"></a><span data-ttu-id="cdcdd-102">Método ISymUnmanagedConstant::GetName</span><span class="sxs-lookup"><span data-stu-id="cdcdd-102">ISymUnmanagedConstant::GetName Method</span></span>
<span data-ttu-id="cdcdd-103">Obtém o nome da constante.</span><span class="sxs-lookup"><span data-stu-id="cdcdd-103">Gets the name of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cdcdd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cdcdd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cdcdd-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cdcdd-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="cdcdd-106">no O comprimento do buffer para o qual o `szName` parâmetro aponta.</span><span class="sxs-lookup"><span data-stu-id="cdcdd-106">[in] The length of the buffer that the `szName` parameter points to.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="cdcdd-107">fora Um ponteiro para um `ULONG32` que recebe o tamanho, em caracteres, do buffer necessário para conter o nome, incluindo a terminação nula.</span><span class="sxs-lookup"><span data-stu-id="cdcdd-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="cdcdd-108">fora O buffer que armazena o nome.</span><span class="sxs-lookup"><span data-stu-id="cdcdd-108">[out] The buffer that stores the name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cdcdd-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="cdcdd-109">Return Value</span></span>  
 <span data-ttu-id="cdcdd-110">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="cdcdd-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cdcdd-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cdcdd-111">Requirements</span></span>  
 <span data-ttu-id="cdcdd-112">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="cdcdd-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdcdd-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="cdcdd-113">See also</span></span>

- [<span data-ttu-id="cdcdd-114">Interface ISymUnmanagedConstant</span><span class="sxs-lookup"><span data-stu-id="cdcdd-114">ISymUnmanagedConstant Interface</span></span>](isymunmanagedconstant-interface.md)
- [<span data-ttu-id="cdcdd-115">Método GetSignature</span><span class="sxs-lookup"><span data-stu-id="cdcdd-115">GetSignature Method</span></span>](isymunmanagedconstant-getsignature-method.md)
- [<span data-ttu-id="cdcdd-116">Método GetValue</span><span class="sxs-lookup"><span data-stu-id="cdcdd-116">GetValue Method</span></span>](isymunmanagedconstant-getvalue-method.md)
