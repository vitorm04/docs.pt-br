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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9017eeaf8e80c3dc0b546c1f3c2fb54634b3e949
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59186427"
---
# <a name="isymunmanagednamespacegetname-method"></a><span data-ttu-id="db7e3-102">Método ISymUnmanagedNamespace::GetName</span><span class="sxs-lookup"><span data-stu-id="db7e3-102">ISymUnmanagedNamespace::GetName Method</span></span>
<span data-ttu-id="db7e3-103">Obtém o nome desse namespace.</span><span class="sxs-lookup"><span data-stu-id="db7e3-103">Gets the name of this namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db7e3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="db7e3-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="db7e3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="db7e3-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="db7e3-106">[in] Um `ULONG32` que indica o tamanho do `szName` buffer.</span><span class="sxs-lookup"><span data-stu-id="db7e3-106">[in] A `ULONG32` that indicates the size of the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="db7e3-107">[out] Um ponteiro para um `ULONG32` que recebe o tamanho, em caracteres, do buffer necessário para conter o nome do namespace, incluindo a terminação nula.</span><span class="sxs-lookup"><span data-stu-id="db7e3-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the namespace name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="db7e3-108">[out] Um ponteiro para um buffer que contém o nome do namespace.</span><span class="sxs-lookup"><span data-stu-id="db7e3-108">[out] A pointer to a buffer that contains the namespace name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="db7e3-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="db7e3-109">Return Value</span></span>  
 <span data-ttu-id="db7e3-110">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="db7e3-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db7e3-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="db7e3-111">Requirements</span></span>  
 <span data-ttu-id="db7e3-112">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="db7e3-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db7e3-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="db7e3-113">See also</span></span>

- [<span data-ttu-id="db7e3-114">Interface ISymUnmanagedNamespace</span><span class="sxs-lookup"><span data-stu-id="db7e3-114">ISymUnmanagedNamespace Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)
