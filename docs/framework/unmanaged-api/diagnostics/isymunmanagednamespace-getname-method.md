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
ms.openlocfilehash: 43f32ac85bebc12d0a9253205aae3f1de0dc9e5b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433968"
---
# <a name="isymunmanagednamespacegetname-method"></a><span data-ttu-id="4666e-102">Método ISymUnmanagedNamespace::GetName</span><span class="sxs-lookup"><span data-stu-id="4666e-102">ISymUnmanagedNamespace::GetName Method</span></span>
<span data-ttu-id="4666e-103">Obtém o nome deste namespace.</span><span class="sxs-lookup"><span data-stu-id="4666e-103">Gets the name of this namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4666e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4666e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4666e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4666e-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="4666e-106">no Um `ULONG32` que indica o tamanho do buffer de `szName`.</span><span class="sxs-lookup"><span data-stu-id="4666e-106">[in] A `ULONG32` that indicates the size of the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="4666e-107">fora Um ponteiro para um `ULONG32` que recebe o tamanho, em caracteres, do buffer necessário para conter o nome do namespace, incluindo a terminação nula.</span><span class="sxs-lookup"><span data-stu-id="4666e-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the namespace name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="4666e-108">fora Um ponteiro para um buffer que contém o nome do namespace.</span><span class="sxs-lookup"><span data-stu-id="4666e-108">[out] A pointer to a buffer that contains the namespace name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4666e-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="4666e-109">Return Value</span></span>  
 <span data-ttu-id="4666e-110">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="4666e-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4666e-111">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="4666e-111">Requirements</span></span>  
 <span data-ttu-id="4666e-112">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="4666e-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4666e-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4666e-113">See also</span></span>

- [<span data-ttu-id="4666e-114">Interface ISymUnmanagedNamespace</span><span class="sxs-lookup"><span data-stu-id="4666e-114">ISymUnmanagedNamespace Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)
