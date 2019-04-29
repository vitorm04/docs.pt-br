---
title: Método IXCLRDataMethodDefinition::EnumInstance
ms.date: 01/16/2019
api.name:
- IXCLRDataMethodDefinition::EnumInstance Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodDefinition::EnumInstance Method
helpviewer.keywords:
- IXCLRDataMethodDefinition::EnumInstance Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: dacf76582916ad50f51ae7c8818b496f31f9553e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61771924"
---
# <a name="ixclrdatamethoddefinitionenuminstance-method"></a><span data-ttu-id="b27ab-102">Método IXCLRDataMethodDefinition::EnumInstance</span><span class="sxs-lookup"><span data-stu-id="b27ab-102">IXCLRDataMethodDefinition::EnumInstance Method</span></span>

<span data-ttu-id="b27ab-103">Enumera as instâncias desta definição de método.</span><span class="sxs-lookup"><span data-stu-id="b27ab-103">Enumerates the instances of this method definition.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="b27ab-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b27ab-104">Syntax</span></span>

```
HRESULT EnumInstance(
    [in, out] CLRDATA_ENUM         *handle,
    [out] IXCLRDataMethodInstance **instance
);
```

## <a name="parameters"></a><span data-ttu-id="b27ab-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b27ab-105">Parameters</span></span>

`handle`\
<span data-ttu-id="b27ab-106">[no, out] Um identificador para enumerar as instâncias.</span><span class="sxs-lookup"><span data-stu-id="b27ab-106">[in, out] A handle for enumerating the instances.</span></span>

`instance`\
<span data-ttu-id="b27ab-107">[out] A instância enumerada.</span><span class="sxs-lookup"><span data-stu-id="b27ab-107">[out] The enumerated instance.</span></span>

## <a name="remarks"></a><span data-ttu-id="b27ab-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="b27ab-108">Remarks</span></span>

<span data-ttu-id="b27ab-109">O método fornecido é parte do `IXCLRDataMethodDefinition` de interface e corresponde ao slot de quarto da tabela de método virtual.</span><span class="sxs-lookup"><span data-stu-id="b27ab-109">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the fourth slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="b27ab-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b27ab-110">Requirements</span></span>

<span data-ttu-id="b27ab-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b27ab-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="b27ab-112">**Cabeçalho:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="b27ab-112">**Header:** None</span></span>  
<span data-ttu-id="b27ab-113">**Biblioteca:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="b27ab-113">**Library:** None</span></span>  
<span data-ttu-id="b27ab-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b27ab-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="b27ab-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b27ab-115">See also</span></span>

- [<span data-ttu-id="b27ab-116">Enumeração CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="b27ab-116">CLRDataSourceType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="b27ab-117">Depuração</span><span class="sxs-lookup"><span data-stu-id="b27ab-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="b27ab-118">Interface IXCLRDataMethodDefinition</span><span class="sxs-lookup"><span data-stu-id="b27ab-118">IXCLRDataMethodDefinition Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethoddefinition-interface.md)
- [<span data-ttu-id="b27ab-119">Interface IXCLRDataMethodInstance</span><span class="sxs-lookup"><span data-stu-id="b27ab-119">IXCLRDataMethodInstance Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethodinstance-interface.md)
