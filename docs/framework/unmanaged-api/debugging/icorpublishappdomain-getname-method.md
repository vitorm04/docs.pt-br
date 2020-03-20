---
title: Método ICorPublishAppDomain::GetName
ms.date: 03/30/2017
api_name:
- ICorPublishAppDomain.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishAppDomain::GetName
helpviewer_keywords:
- GetName method, ICorPublishAppDomain interface [.NET Framework debugging]
- ICorPublishAppDomain::GetName method [.NET Framework debugging]
ms.assetid: 6ef8ac9b-9803-4b65-8b13-25f3e0b1bc6b
topic_type:
- apiref
ms.openlocfilehash: 762c637696fdf79ccab6702918b5bf962ea55903
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178412"
---
# <a name="icorpublishappdomaingetname-method"></a><span data-ttu-id="d7c25-102">Método ICorPublishAppDomain::GetName</span><span class="sxs-lookup"><span data-stu-id="d7c25-102">ICorPublishAppDomain::GetName Method</span></span>
<span data-ttu-id="d7c25-103">Obtém o nome do domínio do aplicativo representado por este [ICorPublishAppDomain](icorpublishappdomain-interface.md).</span><span class="sxs-lookup"><span data-stu-id="d7c25-103">Gets the name of the application domain that is represented by this [ICorPublishAppDomain](icorpublishappdomain-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7c25-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d7c25-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in]  ULONG32   cchName,
    [out] ULONG32   *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]
        WCHAR       *szName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d7c25-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="d7c25-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="d7c25-106">[em] O tamanho `szName` da matriz.</span><span class="sxs-lookup"><span data-stu-id="d7c25-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="d7c25-107">[fora] Um ponteiro para o número de caracteres amplos, `szName` incluindo o caractere nulo, retornou na matriz.</span><span class="sxs-lookup"><span data-stu-id="d7c25-107">[out] A pointer to the number of wide characters, including the null character, returned in the `szName` array.</span></span>  
  
 `szName`  
 <span data-ttu-id="d7c25-108">[fora] Uma matriz na qual armazenar o nome.</span><span class="sxs-lookup"><span data-stu-id="d7c25-108">[out] An array in which to store the name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d7c25-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="d7c25-109">Remarks</span></span>  
 <span data-ttu-id="d7c25-110">Se `szName` não for nulo, `GetName` o `cchName` método copia até caracteres (incluindo o exterminador nulo) em `szName`.</span><span class="sxs-lookup"><span data-stu-id="d7c25-110">If `szName` is non-null, the `GetName` method copies up to `cchName` characters (including the null terminator) into `szName`.</span></span> <span data-ttu-id="d7c25-111">Se um não-nulo `pcchName`for devolvido, o número real de caracteres no nome `szName` (incluindo o exterminador nulo) será armazenado na matriz.</span><span class="sxs-lookup"><span data-stu-id="d7c25-111">If a non-null is returned in `pcchName`, the actual number of characters in the name (including the null terminator) is stored in the `szName` array.</span></span>  
  
 <span data-ttu-id="d7c25-112">O `GetName` método retorna um S_OK HRESULT, independentemente de quantos caracteres foram copiados.</span><span class="sxs-lookup"><span data-stu-id="d7c25-112">The `GetName` method returns an S_OK HRESULT regardless of how many characters were copied.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7c25-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d7c25-113">Requirements</span></span>  
 <span data-ttu-id="d7c25-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7c25-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7c25-115">**Cabeçalho:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="d7c25-115">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="d7c25-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d7c25-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d7c25-117">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7c25-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7c25-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="d7c25-118">See also</span></span>

- [<span data-ttu-id="d7c25-119">Interface ICorPublishAppDomain</span><span class="sxs-lookup"><span data-stu-id="d7c25-119">ICorPublishAppDomain Interface</span></span>](icorpublishappdomain-interface.md)
