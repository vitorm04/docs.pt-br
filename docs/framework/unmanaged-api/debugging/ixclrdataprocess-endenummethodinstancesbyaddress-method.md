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
ms.openlocfilehash: a48a7fc9a141354666c50b1f6da8f1aaa180ff6c
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416279"
---
# <a name="ixclrdataprocessendenummethodinstancesbyaddress-method"></a><span data-ttu-id="61a75-102">Método IXCLRDataProcess::EndEnumMethodInstancesByAddress</span><span class="sxs-lookup"><span data-stu-id="61a75-102">IXCLRDataProcess::EndEnumMethodInstancesByAddress Method</span></span>

<span data-ttu-id="61a75-103">Libera os recursos usados pelos iteradores internos usados durante a enumeração de instância.</span><span class="sxs-lookup"><span data-stu-id="61a75-103">Releases the resources used by internal iterators used during instance enumeration.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="61a75-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="61a75-104">Syntax</span></span>

```
HRESULT EndEnumMethodInstancesByAddress(
    [in] CLRDATA_ENUM handle
);
```

### <a name="parameters"></a><span data-ttu-id="61a75-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="61a75-105">Parameters</span></span>

<span data-ttu-id="61a75-106">`handle` [out] Um identificador para enumerar as instâncias de método.</span><span class="sxs-lookup"><span data-stu-id="61a75-106">`handle` [out] A handle for enumerating the method instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="61a75-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="61a75-107">Remarks</span></span>

<span data-ttu-id="61a75-108">O método fornecido é parte do `IXCLRDataProcess` de interface e corresponde ao slot da tabela de método virtual de 29.</span><span class="sxs-lookup"><span data-stu-id="61a75-108">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 29th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="61a75-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="61a75-109">Requirements</span></span>

<span data-ttu-id="61a75-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61a75-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="61a75-111">**Cabeçalho:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="61a75-111">**Header:** None</span></span>  
<span data-ttu-id="61a75-112">**Biblioteca:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="61a75-112">**Library:** None</span></span>  
<span data-ttu-id="61a75-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="61a75-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="61a75-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="61a75-114">See Also</span></span>

- [<span data-ttu-id="61a75-115">Enumeração CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="61a75-115">CLRDataSourceType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="61a75-116">Depuração</span><span class="sxs-lookup"><span data-stu-id="61a75-116">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="61a75-117">Interface IXCLRDataProcess</span><span class="sxs-lookup"><span data-stu-id="61a75-117">IXCLRDataProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-interface.md)
