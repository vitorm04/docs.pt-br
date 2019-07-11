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
ms.openlocfilehash: 3d9e3ca31eddff9d08607c4d6d37ca76139bf5d2
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67756310"
---
# <a name="ixclrdatamethoddefinitionendenuminstances-method"></a><span data-ttu-id="7ab83-102">Método IXCLRDataMethodDefinition::EndEnumInstances</span><span class="sxs-lookup"><span data-stu-id="7ab83-102">IXCLRDataMethodDefinition::EndEnumInstances Method</span></span>

<span data-ttu-id="7ab83-103">Libera os recursos usados pelos iteradores internos usados durante a enumeração de instância.</span><span class="sxs-lookup"><span data-stu-id="7ab83-103">Releases the resources used by internal iterators used during instance enumeration.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="7ab83-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7ab83-104">Syntax</span></span>

```cpp
HRESULT EndEnumInstances(
    [in] CLRDATA_ENUM handle
);
```

## <a name="parameters"></a><span data-ttu-id="7ab83-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7ab83-105">Parameters</span></span>

`handle`\
<span data-ttu-id="7ab83-106">[out] Um identificador para enumerar as instâncias.</span><span class="sxs-lookup"><span data-stu-id="7ab83-106">[out] A handle for enumerating the instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="7ab83-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="7ab83-107">Remarks</span></span>

<span data-ttu-id="7ab83-108">O método fornecido é parte do `IXCLRDataMethodDefinition` de interface e corresponde ao slot quinto da tabela de método virtual.</span><span class="sxs-lookup"><span data-stu-id="7ab83-108">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the fifth slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="7ab83-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7ab83-109">Requirements</span></span>

<span data-ttu-id="7ab83-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ab83-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="7ab83-111">**Cabeçalho:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="7ab83-111">**Header:** None</span></span>  
<span data-ttu-id="7ab83-112">**Biblioteca:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="7ab83-112">**Library:** None</span></span>  
<span data-ttu-id="7ab83-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="7ab83-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="7ab83-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7ab83-114">See also</span></span>

- [<span data-ttu-id="7ab83-115">Depuração</span><span class="sxs-lookup"><span data-stu-id="7ab83-115">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="7ab83-116">Interface IXCLRDataMethodDefinition</span><span class="sxs-lookup"><span data-stu-id="7ab83-116">IXCLRDataMethodDefinition Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethoddefinition-interface.md)
