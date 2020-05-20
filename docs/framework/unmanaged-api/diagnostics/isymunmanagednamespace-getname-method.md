---
title: Método ISymUnmanagedNamespace::GetName
ms.date: 03/30/2017
api_name:
- ISymUnmanagedNamespace.GetName
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedNamespace::GetName
helpviewer_keywords:
- ISymUnmanagedNamespace::GetName method [.NET Framework debugging]
- GetName method, ISymUnmanagedNamespace interface [.NET Framework debugging]
ms.assetid: 657bf91d-005a-4ea4-9298-04d1291c0bc3
topic_type:
- apiref
ms.openlocfilehash: 84b2f1226c84713483499c7ff777838058cb0f95
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615105"
---
# <a name="isymunmanagednamespacegetname-method"></a><span data-ttu-id="36c88-102">Método ISymUnmanagedNamespace::GetName</span><span class="sxs-lookup"><span data-stu-id="36c88-102">ISymUnmanagedNamespace::GetName Method</span></span>
<span data-ttu-id="36c88-103">Obtém o nome deste namespace.</span><span class="sxs-lookup"><span data-stu-id="36c88-103">Gets the name of this namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36c88-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="36c88-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="36c88-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="36c88-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="36c88-106">no Um `ULONG32` que indica o tamanho do `szName` buffer.</span><span class="sxs-lookup"><span data-stu-id="36c88-106">[in] A `ULONG32` that indicates the size of the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="36c88-107">fora Um ponteiro para um `ULONG32` que recebe o tamanho, em caracteres, do buffer necessário para conter o nome do namespace, incluindo a terminação nula.</span><span class="sxs-lookup"><span data-stu-id="36c88-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the namespace name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="36c88-108">fora Um ponteiro para um buffer que contém o nome do namespace.</span><span class="sxs-lookup"><span data-stu-id="36c88-108">[out] A pointer to a buffer that contains the namespace name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="36c88-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="36c88-109">Return Value</span></span>  
 <span data-ttu-id="36c88-110">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="36c88-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36c88-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="36c88-111">Requirements</span></span>  
 <span data-ttu-id="36c88-112">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="36c88-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36c88-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="36c88-113">See also</span></span>

- [<span data-ttu-id="36c88-114">Interface ISymUnmanagedNamespace</span><span class="sxs-lookup"><span data-stu-id="36c88-114">ISymUnmanagedNamespace Interface</span></span>](isymunmanagednamespace-interface.md)
