---
title: Método IXCLRDataMethodDefinition::StartEnumInstances
ms.date: 01/16/2019
api.name:
- IXCLRDataMethodDefinition::StartEnumInstances Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodDefinition::StartEnumInstances Method
helpviewer.keywords:
- IXCLRDataMethodDefinition::StartEnumInstances Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 208d6c46f18834b23e642efa82df0a365013a410
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416268"
---
# <a name="ixclrdatamethoddefinitionstartenuminstances-method"></a><span data-ttu-id="362c5-102">Método IXCLRDataMethodDefinition::StartEnumInstances</span><span class="sxs-lookup"><span data-stu-id="362c5-102">IXCLRDataMethodDefinition::StartEnumInstances Method</span></span>

<span data-ttu-id="362c5-103">Fornece um identificador para a enumeração de instâncias de método para um determinado `IXCLRDataAppDomain`.</span><span class="sxs-lookup"><span data-stu-id="362c5-103">Provides a handle for the enumeration of method instances for a given `IXCLRDataAppDomain`.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="362c5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="362c5-104">Syntax</span></span>

```
HRESULT StartEnumInstances(
    [in] IXCLRDataAppDomain* appDomain,
    [out] CLRDATA_ENUM *handle
);
```

### <a name="parameters"></a><span data-ttu-id="362c5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="362c5-105">Parameters</span></span>

<span data-ttu-id="362c5-106">`appDomain` [in] Um AppDomain para a enumeração.</span><span class="sxs-lookup"><span data-stu-id="362c5-106">`appDomain` [in] An AppDomain for the enumeration.</span></span>

<span data-ttu-id="362c5-107">`handle` [out] Um identificador para enumerar as instâncias.</span><span class="sxs-lookup"><span data-stu-id="362c5-107">`handle` [out] A handle for enumerating the instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="362c5-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="362c5-108">Remarks</span></span>

<span data-ttu-id="362c5-109">O método fornecido é parte do `IXCLRDataMethodDefinition` de interface e corresponde ao terceiro slot da tabela de método virtual.</span><span class="sxs-lookup"><span data-stu-id="362c5-109">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the third slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="362c5-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="362c5-110">Requirements</span></span>

<span data-ttu-id="362c5-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="362c5-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="362c5-112">**Cabeçalho:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="362c5-112">**Header:** None</span></span>  
<span data-ttu-id="362c5-113">**Biblioteca:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="362c5-113">**Library:** None</span></span>  
<span data-ttu-id="362c5-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="362c5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="362c5-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="362c5-115">See Also</span></span>

- [<span data-ttu-id="362c5-116">Enumeração CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="362c5-116">CLRDataSourceType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="362c5-117">Depuração</span><span class="sxs-lookup"><span data-stu-id="362c5-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="362c5-118">Interface IXCLRDataMethodDefinition</span><span class="sxs-lookup"><span data-stu-id="362c5-118">IXCLRDataMethodDefinition Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethoddefinition-interface.md)
