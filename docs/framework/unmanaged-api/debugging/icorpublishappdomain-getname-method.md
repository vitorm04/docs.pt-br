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
ms.openlocfilehash: 2f91891164f1f80617cab10347eb4a7a08762c10
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140345"
---
# <a name="icorpublishappdomaingetname-method"></a><span data-ttu-id="d04d4-102">Método ICorPublishAppDomain::GetName</span><span class="sxs-lookup"><span data-stu-id="d04d4-102">ICorPublishAppDomain::GetName Method</span></span>
<span data-ttu-id="d04d4-103">Obtém o nome do domínio do aplicativo que é representado por este [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md).</span><span class="sxs-lookup"><span data-stu-id="d04d4-103">Gets the name of the application domain that is represented by this [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d04d4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d04d4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in]  ULONG32   cchName,   
    [out] ULONG32   *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]   
        WCHAR       *szName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d04d4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d04d4-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="d04d4-106">no O tamanho da matriz de `szName`.</span><span class="sxs-lookup"><span data-stu-id="d04d4-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="d04d4-107">fora Um ponteiro para o número de caracteres largos, incluindo o caractere nulo, retornado na matriz de `szName`.</span><span class="sxs-lookup"><span data-stu-id="d04d4-107">[out] A pointer to the number of wide characters, including the null character, returned in the `szName` array.</span></span>  
  
 `szName`  
 <span data-ttu-id="d04d4-108">fora Uma matriz na qual armazenar o nome.</span><span class="sxs-lookup"><span data-stu-id="d04d4-108">[out] An array in which to store the name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d04d4-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="d04d4-109">Remarks</span></span>  
 <span data-ttu-id="d04d4-110">Se `szName` não for NULL, o método `GetName` copiará até `cchName` caracteres (incluindo o terminador nulo) em `szName`.</span><span class="sxs-lookup"><span data-stu-id="d04d4-110">If `szName` is non-null, the `GetName` method copies up to `cchName` characters (including the null terminator) into `szName`.</span></span> <span data-ttu-id="d04d4-111">Se um não nulo for retornado em `pcchName`, o número real de caracteres no nome (incluindo o terminador nulo) será armazenado na matriz de `szName`.</span><span class="sxs-lookup"><span data-stu-id="d04d4-111">If a non-null is returned in `pcchName`, the actual number of characters in the name (including the null terminator) is stored in the `szName` array.</span></span>  
  
 <span data-ttu-id="d04d4-112">O método `GetName` retorna um caractere S_OK HRESULT, independentemente de quantos caracteres foram copiados.</span><span class="sxs-lookup"><span data-stu-id="d04d4-112">The `GetName` method returns an S_OK HRESULT regardless of how many characters were copied.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d04d4-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d04d4-113">Requirements</span></span>  
 <span data-ttu-id="d04d4-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d04d4-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d04d4-115">**Cabeçalho:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="d04d4-115">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="d04d4-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d04d4-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d04d4-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d04d4-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d04d4-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d04d4-118">See also</span></span>

- [<span data-ttu-id="d04d4-119">Interface ICorPublishAppDomain</span><span class="sxs-lookup"><span data-stu-id="d04d4-119">ICorPublishAppDomain Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)
