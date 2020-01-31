---
title: 'Método IXCLRDataMethodDefinition:: EndEnumInstances'
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
ms.openlocfilehash: 605a4244d20ef6c0b7af3c2b26b65ff2a63fa9dd
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790457"
---
# <a name="ixclrdatamethoddefinitionendenuminstances-method"></a><span data-ttu-id="72978-102">Método IXCLRDataMethodDefinition:: EndEnumInstances</span><span class="sxs-lookup"><span data-stu-id="72978-102">IXCLRDataMethodDefinition::EndEnumInstances Method</span></span>

<span data-ttu-id="72978-103">Libera os recursos usados por iteradores internos usados durante a enumeração da instância.</span><span class="sxs-lookup"><span data-stu-id="72978-103">Releases the resources used by internal iterators used during instance enumeration.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="72978-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="72978-104">Syntax</span></span>

```cpp
HRESULT EndEnumInstances(
    [in] CLRDATA_ENUM handle
);
```

## <a name="parameters"></a><span data-ttu-id="72978-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="72978-105">Parameters</span></span>

`handle`\
<span data-ttu-id="72978-106">fora Um identificador para enumerar as instâncias.</span><span class="sxs-lookup"><span data-stu-id="72978-106">[out] A handle for enumerating the instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="72978-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="72978-107">Remarks</span></span>

<span data-ttu-id="72978-108">O método fornecido faz parte da interface de `IXCLRDataMethodDefinition` e corresponde ao quinto slot da tabela de métodos virtuais.</span><span class="sxs-lookup"><span data-stu-id="72978-108">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the fifth slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="72978-109">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="72978-109">Requirements</span></span>

<span data-ttu-id="72978-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72978-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="72978-111">**Cabeçalho:** None</span><span class="sxs-lookup"><span data-stu-id="72978-111">**Header:** None</span></span>  
<span data-ttu-id="72978-112">**Biblioteca:** None</span><span class="sxs-lookup"><span data-stu-id="72978-112">**Library:** None</span></span>  
<span data-ttu-id="72978-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="72978-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="72978-114">Veja também</span><span class="sxs-lookup"><span data-stu-id="72978-114">See also</span></span>

- [<span data-ttu-id="72978-115">Depuração</span><span class="sxs-lookup"><span data-stu-id="72978-115">Debugging</span></span>](index.md)
- [<span data-ttu-id="72978-116">Interface IXCLRDataMethodDefinition</span><span class="sxs-lookup"><span data-stu-id="72978-116">IXCLRDataMethodDefinition Interface</span></span>](ixclrdatamethoddefinition-interface.md)
