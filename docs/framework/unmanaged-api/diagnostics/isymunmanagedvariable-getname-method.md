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
ms.openlocfilehash: 77dec4332aa65f6125685db607169b3398bcab98
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446060"
---
# <a name="isymunmanagedvariablegetname-method"></a><span data-ttu-id="8dd72-102">Método ISymUnmanagedVariable::GetName</span><span class="sxs-lookup"><span data-stu-id="8dd72-102">ISymUnmanagedVariable::GetName Method</span></span>
<span data-ttu-id="8dd72-103">Obtém o nome dessa variável.</span><span class="sxs-lookup"><span data-stu-id="8dd72-103">Gets the name of this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8dd72-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8dd72-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8dd72-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8dd72-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="8dd72-106">no O comprimento do buffer ao qual o parâmetro `pcchName` aponta.</span><span class="sxs-lookup"><span data-stu-id="8dd72-106">[in] The length of the buffer that the `pcchName` parameter points to.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="8dd72-107">fora Um ponteiro para um `ULONG32` que recebe o tamanho, em caracteres, do buffer necessário para conter o nome, incluindo a terminação nula.</span><span class="sxs-lookup"><span data-stu-id="8dd72-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="8dd72-108">fora O buffer que armazena o nome.</span><span class="sxs-lookup"><span data-stu-id="8dd72-108">[out] The buffer that stores the name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8dd72-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="8dd72-109">Return Value</span></span>  
 <span data-ttu-id="8dd72-110">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="8dd72-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8dd72-111">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="8dd72-111">Requirements</span></span>  
 <span data-ttu-id="8dd72-112">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="8dd72-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8dd72-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8dd72-113">See also</span></span>

- [<span data-ttu-id="8dd72-114">Interface ISymUnmanagedVariable</span><span class="sxs-lookup"><span data-stu-id="8dd72-114">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
