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
ms.openlocfilehash: 7901ba3ac95052e265df619d06996b4c9ce8baa6
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416265"
---
# <a name="ixclrdatamethoddefinitionendenuminstances-method"></a><span data-ttu-id="aa8f3-102">Método IXCLRDataMethodDefinition::EndEnumInstances</span><span class="sxs-lookup"><span data-stu-id="aa8f3-102">IXCLRDataMethodDefinition::EndEnumInstances Method</span></span>

<span data-ttu-id="aa8f3-103">Libera os recursos usados pelos iteradores internos usados durante a enumeração de instância.</span><span class="sxs-lookup"><span data-stu-id="aa8f3-103">Releases the resources used by internal iterators used during instance enumeration.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="aa8f3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="aa8f3-104">Syntax</span></span>

```
HRESULT EndEnumInstances(
    [in] CLRDATA_ENUM handle
);
```

### <a name="parameters"></a><span data-ttu-id="aa8f3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="aa8f3-105">Parameters</span></span>

<span data-ttu-id="aa8f3-106">`handle` [out] Um identificador para enumerar as instâncias.</span><span class="sxs-lookup"><span data-stu-id="aa8f3-106">`handle` [out] A handle for enumerating the instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="aa8f3-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="aa8f3-107">Remarks</span></span>

<span data-ttu-id="aa8f3-108">O método fornecido é parte do `IXCLRDataMethodDefinition` de interface e corresponde ao slot quinto da tabela de método virtual.</span><span class="sxs-lookup"><span data-stu-id="aa8f3-108">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the fifth slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="aa8f3-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="aa8f3-109">Requirements</span></span>

<span data-ttu-id="aa8f3-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aa8f3-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="aa8f3-111">**Cabeçalho:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="aa8f3-111">**Header:** None</span></span>  
<span data-ttu-id="aa8f3-112">**Biblioteca:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="aa8f3-112">**Library:** None</span></span>  
<span data-ttu-id="aa8f3-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="aa8f3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="aa8f3-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aa8f3-114">See Also</span></span>

- [<span data-ttu-id="aa8f3-115">Depuração</span><span class="sxs-lookup"><span data-stu-id="aa8f3-115">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="aa8f3-116">Interface IXCLRDataMethodDefinition</span><span class="sxs-lookup"><span data-stu-id="aa8f3-116">IXCLRDataMethodDefinition Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethoddefinition-interface.md)
