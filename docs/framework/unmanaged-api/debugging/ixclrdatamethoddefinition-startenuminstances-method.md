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
ms.openlocfilehash: c78af112e9239143c4854e34e9b6aa8e99344ec3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54623645"
---
# <a name="ixclrdatamethoddefinitionstartenuminstances-method"></a><span data-ttu-id="78c3c-102">Método IXCLRDataMethodDefinition::StartEnumInstances</span><span class="sxs-lookup"><span data-stu-id="78c3c-102">IXCLRDataMethodDefinition::StartEnumInstances Method</span></span>

<span data-ttu-id="78c3c-103">Fornece um identificador para a enumeração de instâncias de método para um determinado `IXCLRDataAppDomain`.</span><span class="sxs-lookup"><span data-stu-id="78c3c-103">Provides a handle for the enumeration of method instances for a given `IXCLRDataAppDomain`.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="78c3c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="78c3c-104">Syntax</span></span>

```
HRESULT StartEnumInstances(
    [in] IXCLRDataAppDomain* appDomain,
    [out] CLRDATA_ENUM *handle
);
```

### <a name="parameters"></a><span data-ttu-id="78c3c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="78c3c-105">Parameters</span></span>

<span data-ttu-id="78c3c-106">`appDomain` [in] Um AppDomain para a enumeração.</span><span class="sxs-lookup"><span data-stu-id="78c3c-106">`appDomain` [in] An AppDomain for the enumeration.</span></span>

<span data-ttu-id="78c3c-107">`handle` [out] Um identificador para enumerar as instâncias.</span><span class="sxs-lookup"><span data-stu-id="78c3c-107">`handle` [out] A handle for enumerating the instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="78c3c-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="78c3c-108">Remarks</span></span>

<span data-ttu-id="78c3c-109">O método fornecido é parte do `IXCLRDataMethodDefinition` de interface e corresponde ao terceiro slot da tabela de método virtual.</span><span class="sxs-lookup"><span data-stu-id="78c3c-109">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the third slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="78c3c-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="78c3c-110">Requirements</span></span>

<span data-ttu-id="78c3c-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78c3c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="78c3c-112">**Cabeçalho:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="78c3c-112">**Header:** None</span></span>  
<span data-ttu-id="78c3c-113">**Biblioteca:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="78c3c-113">**Library:** None</span></span>  
<span data-ttu-id="78c3c-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="78c3c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="78c3c-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="78c3c-115">See also</span></span>

- [<span data-ttu-id="78c3c-116">Enumeração CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="78c3c-116">CLRDataSourceType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="78c3c-117">Depuração</span><span class="sxs-lookup"><span data-stu-id="78c3c-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="78c3c-118">Interface IXCLRDataMethodDefinition</span><span class="sxs-lookup"><span data-stu-id="78c3c-118">IXCLRDataMethodDefinition Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethoddefinition-interface.md)
