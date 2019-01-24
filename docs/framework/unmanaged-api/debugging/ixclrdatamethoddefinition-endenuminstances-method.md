---
title: Método IXCLRDataMethodDefinition::EndEnumInstances
ms.date: 01/16/2019
api.name:
- IXCLRDataMethodDefinition::EndEnumInstances Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodDefinition::EndEnumInstances Method
helpviewer.keywords:
- IXCLRDataMethodDefinition::EndEnumInstances Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 4a7cd8850778e9bbbc7d8d67f464c7787e40bc13
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54566083"
---
# <a name="ixclrdatamethoddefinitionendenuminstances-method"></a><span data-ttu-id="1aa84-102">Método IXCLRDataMethodDefinition::EndEnumInstances</span><span class="sxs-lookup"><span data-stu-id="1aa84-102">IXCLRDataMethodDefinition::EndEnumInstances Method</span></span>

<span data-ttu-id="1aa84-103">Libera os recursos usados pelos iteradores internos usados durante a enumeração de instância.</span><span class="sxs-lookup"><span data-stu-id="1aa84-103">Releases the resources used by internal iterators used during instance enumeration.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="1aa84-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1aa84-104">Syntax</span></span>

```
HRESULT EndEnumInstances(
    [in] CLRDATA_ENUM handle
);
```

### <a name="parameters"></a><span data-ttu-id="1aa84-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1aa84-105">Parameters</span></span>

<span data-ttu-id="1aa84-106">`handle` [out] Um identificador para enumerar as instâncias.</span><span class="sxs-lookup"><span data-stu-id="1aa84-106">`handle` [out] A handle for enumerating the instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="1aa84-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="1aa84-107">Remarks</span></span>

<span data-ttu-id="1aa84-108">O método fornecido é parte do `IXCLRDataMethodDefinition` de interface e corresponde ao slot quinto da tabela de método virtual.</span><span class="sxs-lookup"><span data-stu-id="1aa84-108">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the fifth slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="1aa84-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1aa84-109">Requirements</span></span>

<span data-ttu-id="1aa84-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1aa84-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="1aa84-111">**Cabeçalho:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="1aa84-111">**Header:** None</span></span>  
<span data-ttu-id="1aa84-112">**Biblioteca:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="1aa84-112">**Library:** None</span></span>  
<span data-ttu-id="1aa84-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="1aa84-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="1aa84-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1aa84-114">See also</span></span>

- [<span data-ttu-id="1aa84-115">Depuração</span><span class="sxs-lookup"><span data-stu-id="1aa84-115">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="1aa84-116">Interface IXCLRDataMethodDefinition</span><span class="sxs-lookup"><span data-stu-id="1aa84-116">IXCLRDataMethodDefinition Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethoddefinition-interface.md)
