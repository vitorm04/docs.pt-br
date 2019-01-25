---
title: Método IXCLRDataProcess::EndEnumMethodInstancesByAddress
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::EndEnumMethodInstancesByAddress Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::EndEnumMethodInstancesByAddress Method
helpviewer.keywords:
- IXCLRDataProcess::EndEnumMethodInstancesByAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 67978e49a8c23c4b25234ecbb3639c696c7232f4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54655641"
---
# <a name="ixclrdataprocessendenummethodinstancesbyaddress-method"></a><span data-ttu-id="83e78-102">Método IXCLRDataProcess::EndEnumMethodInstancesByAddress</span><span class="sxs-lookup"><span data-stu-id="83e78-102">IXCLRDataProcess::EndEnumMethodInstancesByAddress Method</span></span>

<span data-ttu-id="83e78-103">Libera os recursos usados pelos iteradores internos usados durante a enumeração de instância.</span><span class="sxs-lookup"><span data-stu-id="83e78-103">Releases the resources used by internal iterators used during instance enumeration.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="83e78-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="83e78-104">Syntax</span></span>

```
HRESULT EndEnumMethodInstancesByAddress(
    [in] CLRDATA_ENUM handle
);
```

### <a name="parameters"></a><span data-ttu-id="83e78-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="83e78-105">Parameters</span></span>

<span data-ttu-id="83e78-106">`handle` [out] Um identificador para enumerar as instâncias de método.</span><span class="sxs-lookup"><span data-stu-id="83e78-106">`handle` [out] A handle for enumerating the method instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="83e78-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="83e78-107">Remarks</span></span>

<span data-ttu-id="83e78-108">O método fornecido é parte do `IXCLRDataProcess` de interface e corresponde ao slot da tabela de método virtual de 29.</span><span class="sxs-lookup"><span data-stu-id="83e78-108">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 29th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="83e78-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="83e78-109">Requirements</span></span>

<span data-ttu-id="83e78-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83e78-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="83e78-111">**Cabeçalho:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="83e78-111">**Header:** None</span></span>  
<span data-ttu-id="83e78-112">**Biblioteca:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="83e78-112">**Library:** None</span></span>  
<span data-ttu-id="83e78-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="83e78-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="83e78-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="83e78-114">See also</span></span>

- [<span data-ttu-id="83e78-115">Enumeração CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="83e78-115">CLRDataSourceType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="83e78-116">Depuração</span><span class="sxs-lookup"><span data-stu-id="83e78-116">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="83e78-117">Interface IXCLRDataProcess</span><span class="sxs-lookup"><span data-stu-id="83e78-117">IXCLRDataProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-interface.md)
