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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 796f8ea42cc5cbe13729f7b92e15bc214d62734d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icorpublishappdomaingetname-method"></a><span data-ttu-id="2c982-102">Método ICorPublishAppDomain::GetName</span><span class="sxs-lookup"><span data-stu-id="2c982-102">ICorPublishAppDomain::GetName Method</span></span>
<span data-ttu-id="2c982-103">Obtém o nome do domínio do aplicativo que é representado por esse [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md).</span><span class="sxs-lookup"><span data-stu-id="2c982-103">Gets the name of the application domain that is represented by this [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c982-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2c982-104">Syntax</span></span>  
  
```  
HRESULT GetName (  
    [in]  ULONG32   cchName,   
    [out] ULONG32   *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]   
        WCHAR       *szName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2c982-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2c982-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="2c982-106">[in] O tamanho do `szName` matriz.</span><span class="sxs-lookup"><span data-stu-id="2c982-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="2c982-107">[out] Um ponteiro para o número de caracteres largos, incluindo o caractere nulo, retornado na `szName` matriz.</span><span class="sxs-lookup"><span data-stu-id="2c982-107">[out] A pointer to the number of wide characters, including the null character, returned in the `szName` array.</span></span>  
  
 `szName`  
 <span data-ttu-id="2c982-108">[out] Uma matriz na qual deseja armazenar o nome.</span><span class="sxs-lookup"><span data-stu-id="2c982-108">[out] An array in which to store the name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2c982-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="2c982-109">Remarks</span></span>  
 <span data-ttu-id="2c982-110">Se `szName` não for nulo, o `GetName` método copia até `cchName` caracteres (incluindo o terminador nulo) em `szName`.</span><span class="sxs-lookup"><span data-stu-id="2c982-110">If `szName` is non-null, the `GetName` method copies up to `cchName` characters (including the null terminator) into `szName`.</span></span> <span data-ttu-id="2c982-111">Se não null é retornado em `pcchName`, o número real de caracteres no nome (incluindo o terminador nulo) é armazenado na `szName` matriz.</span><span class="sxs-lookup"><span data-stu-id="2c982-111">If a non-null is returned in `pcchName`, the actual number of characters in the name (including the null terminator) is stored in the `szName` array.</span></span>  
  
 <span data-ttu-id="2c982-112">O `GetName` método retorna um HRESULT S_OK, independentemente de quantos caracteres foram copiado.</span><span class="sxs-lookup"><span data-stu-id="2c982-112">The `GetName` method returns an S_OK HRESULT regardless of how many characters were copied.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c982-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2c982-113">Requirements</span></span>  
 <span data-ttu-id="2c982-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c982-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c982-115">**Cabeçalho:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="2c982-115">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="2c982-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2c982-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2c982-117">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c982-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c982-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2c982-118">See Also</span></span>  
 [<span data-ttu-id="2c982-119">Interface ICorPublishAppDomain</span><span class="sxs-lookup"><span data-stu-id="2c982-119">ICorPublishAppDomain Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)
