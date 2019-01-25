---
title: Método IXCLRDataProcess::StartEnumMethodInstancesByAddress
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::StartEnumMethodInstancesByAddress Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::StartEnumMethodInstancesByAddress Method
helpviewer.keywords:
- IXCLRDataProcess::StartEnumMethodInstancesByAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 9afbf0665b114169661a74b60c744203d160fed3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54662615"
---
# <a name="ixclrdataprocessstartenummethodinstancesbyaddress-method"></a><span data-ttu-id="45e82-102">Método IXCLRDataProcess::StartEnumMethodInstancesByAddress</span><span class="sxs-lookup"><span data-stu-id="45e82-102">IXCLRDataProcess::StartEnumMethodInstancesByAddress Method</span></span>

<span data-ttu-id="45e82-103">Fornece um identificador para enumerar as instâncias do método de `AppDomain` começando em um determinado endereço.</span><span class="sxs-lookup"><span data-stu-id="45e82-103">Provides a handle to enumerate the method instances of `AppDomain` starting at a given address.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="45e82-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="45e82-104">Syntax</span></span>

```
HRESULT StartEnumMethodInstancesByAddress(
    [in] CLRDATA_ADDRESS     address,
    [in] IXCLRDataAppDomain *appDomain,
    [out] CLRDATA_ENUM      *handle
);
```

### <a name="parameters"></a><span data-ttu-id="45e82-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="45e82-105">Parameters</span></span>

<span data-ttu-id="45e82-106">`address` [in] O endereço da primeira instância de método.</span><span class="sxs-lookup"><span data-stu-id="45e82-106">`address` [in] The address of the first method instance.</span></span>

<span data-ttu-id="45e82-107">`appDomain` [in] O AppDomain das instâncias do método.</span><span class="sxs-lookup"><span data-stu-id="45e82-107">`appDomain` [in] The AppDomain of the method instances.</span></span>

<span data-ttu-id="45e82-108">`handle` [out] Um identificador para enumerar as instâncias de método.</span><span class="sxs-lookup"><span data-stu-id="45e82-108">`handle` [out] A handle for enumerating the method instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="45e82-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="45e82-109">Remarks</span></span>

<span data-ttu-id="45e82-110">O método fornecido é parte do `IXCLRDataProcess` de interface e corresponde ao slot de 27 da tabela de método virtual.</span><span class="sxs-lookup"><span data-stu-id="45e82-110">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 27th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="45e82-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="45e82-111">Requirements</span></span>

<span data-ttu-id="45e82-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45e82-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="45e82-113">**Cabeçalho:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="45e82-113">**Header:** None</span></span>  
<span data-ttu-id="45e82-114">**Biblioteca:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="45e82-114">**Library:** None</span></span>  
<span data-ttu-id="45e82-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="45e82-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="45e82-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="45e82-116">See also</span></span>

- [<span data-ttu-id="45e82-117">Enumeração CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="45e82-117">CLRDataSourceType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="45e82-118">Depuração</span><span class="sxs-lookup"><span data-stu-id="45e82-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="45e82-119">Interface IXCLRDataProcess</span><span class="sxs-lookup"><span data-stu-id="45e82-119">IXCLRDataProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-interface.md)
