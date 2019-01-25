---
title: Método IXCLRDataProcess::GetAppDomainByUniqueId
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::GetAppDomainByUniqueId Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::GetAppDomainByUniqueId Method
helpviewer.keywords:
- IXCLRDataProcess::GetAppDomainByUniqueId Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: cf610e3af26c60dd9bf738bff8785890394d0f34
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54710268"
---
# <a name="ixclrdataprocessgetappdomainbyuniqueid-method"></a><span data-ttu-id="525bb-102">Método IXCLRDataProcess::GetAppDomainByUniqueId</span><span class="sxs-lookup"><span data-stu-id="525bb-102">IXCLRDataProcess::GetAppDomainByUniqueId Method</span></span>

<span data-ttu-id="525bb-103">Obtém um `AppDomain` em um processo com base em seu identificador exclusivo.</span><span class="sxs-lookup"><span data-stu-id="525bb-103">Gets an `AppDomain` in a process based on its unique identifier.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="525bb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="525bb-104">Syntax</span></span>
```
HRESULT GetAppDomainByUniqueID(
    [in] ULONG64               id,
    [out] IXCLRDataAppDomain **appDomain
);
```

### <a name="parameters"></a><span data-ttu-id="525bb-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="525bb-105">Parameters</span></span>
<span data-ttu-id="525bb-106">`id` [in] O identificador exclusivo do AppDomain</span><span class="sxs-lookup"><span data-stu-id="525bb-106">`id` [in] The unique identifier of the AppDomain</span></span>

<span data-ttu-id="525bb-107">`appDomain` [out] O AppDomain</span><span class="sxs-lookup"><span data-stu-id="525bb-107">`appDomain` [out] The AppDomain</span></span>

## <a name="remarks"></a><span data-ttu-id="525bb-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="525bb-108">Remarks</span></span>

<span data-ttu-id="525bb-109">O método fornecido é parte do `IXCLRDataProcess` de interface e corresponde ao slot de 20 anos da tabela de método virtual.</span><span class="sxs-lookup"><span data-stu-id="525bb-109">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 20th slot of the virtual method table.</span></span> <span data-ttu-id="525bb-110">O `IXCLRDataAppDomain*` retornado é usado para interação com outras APIs.</span><span class="sxs-lookup"><span data-stu-id="525bb-110">The `IXCLRDataAppDomain*` returned is used for interaction with other APIs.</span></span>

## <a name="requirements"></a><span data-ttu-id="525bb-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="525bb-111">Requirements</span></span>
<span data-ttu-id="525bb-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="525bb-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="525bb-113">**Cabeçalho:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="525bb-113">**Header:** None</span></span>  
<span data-ttu-id="525bb-114">**Biblioteca:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="525bb-114">**Library:** None</span></span>  
<span data-ttu-id="525bb-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="525bb-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="525bb-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="525bb-116">See also</span></span>
- [<span data-ttu-id="525bb-117">Depuração</span><span class="sxs-lookup"><span data-stu-id="525bb-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="525bb-118">Interface IXCLRDataProcess</span><span class="sxs-lookup"><span data-stu-id="525bb-118">IXCLRDataProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-interface.md)
