---
title: Método ISymUnmanagedENCUpdate::GetLocalVariables
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate.GetLocalVariables
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariables
helpviewer_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariables method [.NET Framework debugging]
- GetLocalVariables method [.NET Framework debugging]
ms.assetid: 5c8840be-ffea-447f-9c8d-178f1eaf8d06
topic_type:
- apiref
ms.openlocfilehash: 5e5bf097a4b1e366fff807595b22c4696a91cf43
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614546"
---
# <a name="isymunmanagedencupdategetlocalvariables-method"></a><span data-ttu-id="3a729-102">Método ISymUnmanagedENCUpdate::GetLocalVariables</span><span class="sxs-lookup"><span data-stu-id="3a729-102">ISymUnmanagedENCUpdate::GetLocalVariables Method</span></span>
<span data-ttu-id="3a729-103">Obtém as variáveis locais.</span><span class="sxs-lookup"><span data-stu-id="3a729-103">Gets the local variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a729-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3a729-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalVariables(  
    [in]  mdMethodDef  mdMethodToken,  
    [in]  ULONG        cLocals,  
    [out, size_is(cLocals), length_is(*pceltFetched)]  
        ISymUnmanagedVariable *rgLocals[],  
    [out] ULONG        *pceltFetched);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3a729-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3a729-105">Parameters</span></span>  
 `mdMethodToken`  
 <span data-ttu-id="3a729-106">no O token de metadados do método.</span><span class="sxs-lookup"><span data-stu-id="3a729-106">[in] The metadata token of the method.</span></span>  
  
 `cLocals`  
 <span data-ttu-id="3a729-107">no Um `ULONG` que indica o tamanho do `rgLocals` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="3a729-107">[in] A `ULONG` that indicates the size of the `rgLocals` parameter.</span></span>  
  
 `rgLocals`  
 <span data-ttu-id="3a729-108">fora A matriz retornada de instâncias de [ISymUnmanagedVariable](isymunmanagedvariable-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="3a729-108">[out] The returned array of [ISymUnmanagedVariable](isymunmanagedvariable-interface.md) instances.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="3a729-109">fora Um ponteiro para um `ULONG` que recebe o tamanho do `rgLocals` buffer necessário para conter os locais.</span><span class="sxs-lookup"><span data-stu-id="3a729-109">[out] A pointer to a `ULONG` that receives the size of the `rgLocals` buffer required to contain the locals.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3a729-110">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="3a729-110">Return Value</span></span>  
 <span data-ttu-id="3a729-111">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="3a729-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a729-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3a729-112">Requirements</span></span>  
 <span data-ttu-id="3a729-113">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="3a729-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a729-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="3a729-114">See also</span></span>

- [<span data-ttu-id="3a729-115">Interface ISymUnmanagedENCUpdate</span><span class="sxs-lookup"><span data-stu-id="3a729-115">ISymUnmanagedENCUpdate Interface</span></span>](isymunmanagedencupdate-interface.md)
