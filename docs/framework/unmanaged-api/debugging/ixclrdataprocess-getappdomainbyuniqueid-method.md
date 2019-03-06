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
ms.openlocfilehash: d4226bd73c7ae0c1faf510ed63b644116b064fb2
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57375071"
---
# <a name="ixclrdataprocessgetappdomainbyuniqueid-method"></a><span data-ttu-id="898d4-102">Método IXCLRDataProcess::GetAppDomainByUniqueId</span><span class="sxs-lookup"><span data-stu-id="898d4-102">IXCLRDataProcess::GetAppDomainByUniqueId Method</span></span>

<span data-ttu-id="898d4-103">Obtém um `AppDomain` em um processo com base em seu identificador exclusivo.</span><span class="sxs-lookup"><span data-stu-id="898d4-103">Gets an `AppDomain` in a process based on its unique identifier.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="898d4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="898d4-104">Syntax</span></span>
```
HRESULT GetAppDomainByUniqueID(
    [in] ULONG64               id,
    [out] IXCLRDataAppDomain **appDomain
);
```

## <a name="parameters"></a><span data-ttu-id="898d4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="898d4-105">Parameters</span></span>

`id`\
<span data-ttu-id="898d4-106">[in] O identificador exclusivo do AppDomain</span><span class="sxs-lookup"><span data-stu-id="898d4-106">[in] The unique identifier of the AppDomain</span></span>

`appDomain`\
<span data-ttu-id="898d4-107">[out] O AppDomain</span><span class="sxs-lookup"><span data-stu-id="898d4-107">[out] The AppDomain</span></span>

## <a name="remarks"></a><span data-ttu-id="898d4-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="898d4-108">Remarks</span></span>

<span data-ttu-id="898d4-109">O método fornecido é parte do `IXCLRDataProcess` de interface e corresponde ao slot de 20 anos da tabela de método virtual.</span><span class="sxs-lookup"><span data-stu-id="898d4-109">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 20th slot of the virtual method table.</span></span> <span data-ttu-id="898d4-110">O `IXCLRDataAppDomain*` retornado é usado para interação com outras APIs.</span><span class="sxs-lookup"><span data-stu-id="898d4-110">The `IXCLRDataAppDomain*` returned is used for interaction with other APIs.</span></span>

## <a name="requirements"></a><span data-ttu-id="898d4-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="898d4-111">Requirements</span></span>
<span data-ttu-id="898d4-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="898d4-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="898d4-113">**Cabeçalho:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="898d4-113">**Header:** None</span></span>  
<span data-ttu-id="898d4-114">**Biblioteca:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="898d4-114">**Library:** None</span></span>  
<span data-ttu-id="898d4-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="898d4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="898d4-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="898d4-116">See also</span></span>
- [<span data-ttu-id="898d4-117">Depuração</span><span class="sxs-lookup"><span data-stu-id="898d4-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="898d4-118">Interface IXCLRDataProcess</span><span class="sxs-lookup"><span data-stu-id="898d4-118">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
