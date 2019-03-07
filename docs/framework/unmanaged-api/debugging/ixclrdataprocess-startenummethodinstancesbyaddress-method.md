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
ms.openlocfilehash: 41b6ff0a3c44d3ad997c54b1c82590cc3583fe52
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57474599"
---
# <a name="ixclrdataprocessstartenummethodinstancesbyaddress-method"></a><span data-ttu-id="4eb88-102">Método IXCLRDataProcess::StartEnumMethodInstancesByAddress</span><span class="sxs-lookup"><span data-stu-id="4eb88-102">IXCLRDataProcess::StartEnumMethodInstancesByAddress Method</span></span>

<span data-ttu-id="4eb88-103">Fornece um identificador para enumerar as instâncias do método de `AppDomain` começando em um determinado endereço.</span><span class="sxs-lookup"><span data-stu-id="4eb88-103">Provides a handle to enumerate the method instances of `AppDomain` starting at a given address.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="4eb88-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4eb88-104">Syntax</span></span>

```
HRESULT StartEnumMethodInstancesByAddress(
    [in] CLRDATA_ADDRESS     address,
    [in] IXCLRDataAppDomain *appDomain,
    [out] CLRDATA_ENUM      *handle
);
```

## <a name="parameters"></a><span data-ttu-id="4eb88-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4eb88-105">Parameters</span></span>

`address`\
<span data-ttu-id="4eb88-106">[in] O endereço da primeira instância de método.</span><span class="sxs-lookup"><span data-stu-id="4eb88-106">[in] The address of the first method instance.</span></span>

`appDomain`\
<span data-ttu-id="4eb88-107">[in] O AppDomain das instâncias do método.</span><span class="sxs-lookup"><span data-stu-id="4eb88-107">[in] The AppDomain of the method instances.</span></span>

`handle`\
<span data-ttu-id="4eb88-108">[out] Um identificador para enumerar as instâncias de método.</span><span class="sxs-lookup"><span data-stu-id="4eb88-108">[out] A handle for enumerating the method instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="4eb88-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="4eb88-109">Remarks</span></span>

<span data-ttu-id="4eb88-110">O método fornecido é parte do `IXCLRDataProcess` de interface e corresponde ao slot de 27 da tabela de método virtual.</span><span class="sxs-lookup"><span data-stu-id="4eb88-110">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 27th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="4eb88-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4eb88-111">Requirements</span></span>

<span data-ttu-id="4eb88-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4eb88-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="4eb88-113">**Cabeçalho:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="4eb88-113">**Header:** None</span></span>  
<span data-ttu-id="4eb88-114">**Biblioteca:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="4eb88-114">**Library:** None</span></span>  
<span data-ttu-id="4eb88-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="4eb88-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="4eb88-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4eb88-116">See also</span></span>

- [<span data-ttu-id="4eb88-117">Enumeração CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="4eb88-117">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="4eb88-118">Depuração</span><span class="sxs-lookup"><span data-stu-id="4eb88-118">Debugging</span></span>](index.md)
- [<span data-ttu-id="4eb88-119">Interface IXCLRDataProcess</span><span class="sxs-lookup"><span data-stu-id="4eb88-119">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
