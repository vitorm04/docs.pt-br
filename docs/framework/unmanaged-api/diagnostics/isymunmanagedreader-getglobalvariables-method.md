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
ms.openlocfilehash: 20bfb3e48f411524bd4d9798f17dd935595a12bb
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615014"
---
# <a name="isymunmanagedreadergetglobalvariables-method"></a><span data-ttu-id="b3ff6-102">Método ISymUnmanagedReader::GetGlobalVariables</span><span class="sxs-lookup"><span data-stu-id="b3ff6-102">ISymUnmanagedReader::GetGlobalVariables Method</span></span>
<span data-ttu-id="b3ff6-103">Retorna todas as variáveis globais.</span><span class="sxs-lookup"><span data-stu-id="b3ff6-103">Returns all global variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3ff6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b3ff6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGlobalVariables(  
    [in]  ULONG32  cVars,  
    [out] ULONG32  *pcVars,  
    [out, size_is(cVars),  
        length_is(*pcVars)] ISymUnmanagedVariable *pVars[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b3ff6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b3ff6-105">Parameters</span></span>  
 `cVars`  
 <span data-ttu-id="b3ff6-106">no O comprimento do buffer apontado por `pcVars` .</span><span class="sxs-lookup"><span data-stu-id="b3ff6-106">[in] The length of the buffer pointed to by `pcVars`.</span></span>  
  
 `pcVars`  
 <span data-ttu-id="b3ff6-107">fora Um ponteiro para um `ULONG32` que recebe o tamanho do buffer necessário para conter as variáveis.</span><span class="sxs-lookup"><span data-stu-id="b3ff6-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the variables.</span></span>  
  
 `pVars`  
 <span data-ttu-id="b3ff6-108">fora Um buffer que contém as variáveis.</span><span class="sxs-lookup"><span data-stu-id="b3ff6-108">[out] A buffer that contains the variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b3ff6-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="b3ff6-109">Return Value</span></span>  
 <span data-ttu-id="b3ff6-110">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="b3ff6-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3ff6-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b3ff6-111">Requirements</span></span>  
 <span data-ttu-id="b3ff6-112">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="b3ff6-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3ff6-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="b3ff6-113">See also</span></span>

- [<span data-ttu-id="b3ff6-114">Interface ISymUnmanagedReader</span><span class="sxs-lookup"><span data-stu-id="b3ff6-114">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
