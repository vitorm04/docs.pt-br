---
title: Método ISymUnmanagedConstant::GetSignature
ms.date: 03/30/2017
api_name:
- ISymUnmanagedConstant.GetSignature
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedConstant::GetSignature
helpviewer_keywords:
- GetSignature method, ISymUnmanagedConstant interface [.NET Framework debugging]
- ISymUnmanagedConstant::GetSignature method [.NET Framework debugging]
ms.assetid: 3eb41151-a228-43e3-ba8f-e6dd3ceb8542
topic_type:
- apiref
ms.openlocfilehash: 332d60418c744a9391c7c0afc20248c2239b090c
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441614"
---
# <a name="isymunmanagedconstantgetsignature-method"></a><span data-ttu-id="2ad26-102">Método ISymUnmanagedConstant::GetSignature</span><span class="sxs-lookup"><span data-stu-id="2ad26-102">ISymUnmanagedConstant::GetSignature Method</span></span>
<span data-ttu-id="2ad26-103">Obtém a assinatura da constante.</span><span class="sxs-lookup"><span data-stu-id="2ad26-103">Gets the signature of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ad26-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2ad26-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSignature(  
    [in]  ULONG32  cSig,  
    [out] ULONG32  *pcSig,  
    [out, size_is(cSig),  
        length_is(*pcSig)] BYTE sig[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2ad26-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2ad26-105">Parameters</span></span>  
 `cSig`  
 <span data-ttu-id="2ad26-106">no O comprimento do buffer para o qual o `pcSig` parâmetro aponta.</span><span class="sxs-lookup"><span data-stu-id="2ad26-106">[in] The length of the buffer that the `pcSig` parameter points to.</span></span>  
  
 `pcSig`  
 <span data-ttu-id="2ad26-107">fora Um ponteiro para um `ULONG32` que recebe o tamanho, em caracteres, do buffer necessário para conter a assinatura.</span><span class="sxs-lookup"><span data-stu-id="2ad26-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the signature.</span></span>  
  
 `sig`  
 <span data-ttu-id="2ad26-108">fora O buffer que armazena a assinatura.</span><span class="sxs-lookup"><span data-stu-id="2ad26-108">[out] The buffer that stores the signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2ad26-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="2ad26-109">Return Value</span></span>  
 <span data-ttu-id="2ad26-110">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="2ad26-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ad26-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2ad26-111">Requirements</span></span>  
 <span data-ttu-id="2ad26-112">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="2ad26-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ad26-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="2ad26-113">See also</span></span>

- [<span data-ttu-id="2ad26-114">Interface ISymUnmanagedConstant</span><span class="sxs-lookup"><span data-stu-id="2ad26-114">ISymUnmanagedConstant Interface</span></span>](isymunmanagedconstant-interface.md)
- [<span data-ttu-id="2ad26-115">Método GetName</span><span class="sxs-lookup"><span data-stu-id="2ad26-115">GetName Method</span></span>](isymunmanagedconstant-getname-method.md)
- [<span data-ttu-id="2ad26-116">Método GetValue</span><span class="sxs-lookup"><span data-stu-id="2ad26-116">GetValue Method</span></span>](isymunmanagedconstant-getvalue-method.md)
