---
title: Método ISymUnmanagedReader::GetGlobalVariables
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetGlobalVariables
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetGlobalVariables
helpviewer_keywords:
- GetGlobalVariables method [.NET Framework debugging]
- ISymUnmanagedReader::GetGlobalVariables method [.NET Framework debugging]
ms.assetid: a2dd5098-3e58-4be5-b7a2-e4160b3b505a
topic_type:
- apiref
ms.openlocfilehash: b6cf7293f1d65db1f60301f49ce655c74df3daca
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448323"
---
# <a name="isymunmanagedreadergetglobalvariables-method"></a><span data-ttu-id="de85e-102">Método ISymUnmanagedReader::GetGlobalVariables</span><span class="sxs-lookup"><span data-stu-id="de85e-102">ISymUnmanagedReader::GetGlobalVariables Method</span></span>
<span data-ttu-id="de85e-103">Retorna todas as variáveis globais.</span><span class="sxs-lookup"><span data-stu-id="de85e-103">Returns all global variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de85e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="de85e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGlobalVariables(  
    [in]  ULONG32  cVars,  
    [out] ULONG32  *pcVars,  
    [out, size_is(cVars),  
        length_is(*pcVars)] ISymUnmanagedVariable *pVars[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="de85e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="de85e-105">Parameters</span></span>  
 `cVars`  
 <span data-ttu-id="de85e-106">no O comprimento do buffer apontado por `pcVars`.</span><span class="sxs-lookup"><span data-stu-id="de85e-106">[in] The length of the buffer pointed to by `pcVars`.</span></span>  
  
 `pcVars`  
 <span data-ttu-id="de85e-107">fora Um ponteiro para um `ULONG32` que recebe o tamanho do buffer necessário para conter as variáveis.</span><span class="sxs-lookup"><span data-stu-id="de85e-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the variables.</span></span>  
  
 `pVars`  
 <span data-ttu-id="de85e-108">fora Um buffer que contém as variáveis.</span><span class="sxs-lookup"><span data-stu-id="de85e-108">[out] A buffer that contains the variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="de85e-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="de85e-109">Return Value</span></span>  
 <span data-ttu-id="de85e-110">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="de85e-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de85e-111">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="de85e-111">Requirements</span></span>  
 <span data-ttu-id="de85e-112">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="de85e-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de85e-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="de85e-113">See also</span></span>

- [<span data-ttu-id="de85e-114">Interface ISymUnmanagedReader</span><span class="sxs-lookup"><span data-stu-id="de85e-114">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
