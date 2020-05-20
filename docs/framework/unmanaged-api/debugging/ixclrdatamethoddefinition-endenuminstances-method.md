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
ms.openlocfilehash: 7271c9594a679af205c404f59ff6731821aa0acf
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420988"
---
# <a name="ixclrdatamethoddefinitionendenuminstances-method"></a><span data-ttu-id="ac2cf-102">Método IXCLRDataMethodDefinition:: EndEnumInstances</span><span class="sxs-lookup"><span data-stu-id="ac2cf-102">IXCLRDataMethodDefinition::EndEnumInstances Method</span></span>

<span data-ttu-id="ac2cf-103">Libera os recursos usados por iteradores internos usados durante a enumeração da instância.</span><span class="sxs-lookup"><span data-stu-id="ac2cf-103">Releases the resources used by internal iterators used during instance enumeration.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="ac2cf-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ac2cf-104">Syntax</span></span>

```cpp
HRESULT EndEnumInstances(
    [in] CLRDATA_ENUM handle
);
```

## <a name="parameters"></a><span data-ttu-id="ac2cf-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ac2cf-105">Parameters</span></span>

`handle`\
<span data-ttu-id="ac2cf-106">fora Um identificador para enumerar as instâncias.</span><span class="sxs-lookup"><span data-stu-id="ac2cf-106">[out] A handle for enumerating the instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="ac2cf-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="ac2cf-107">Remarks</span></span>

<span data-ttu-id="ac2cf-108">O método fornecido faz parte da `IXCLRDataMethodDefinition` interface e corresponde ao sétimo slot da tabela de métodos virtuais.</span><span class="sxs-lookup"><span data-stu-id="ac2cf-108">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the 7th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="ac2cf-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ac2cf-109">Requirements</span></span>

<span data-ttu-id="ac2cf-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac2cf-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="ac2cf-111">**Cabeçalho:** None</span><span class="sxs-lookup"><span data-stu-id="ac2cf-111">**Header:** None</span></span>  
<span data-ttu-id="ac2cf-112">**Biblioteca:** None</span><span class="sxs-lookup"><span data-stu-id="ac2cf-112">**Library:** None</span></span>  
<span data-ttu-id="ac2cf-113">**.NET Framework versões:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ac2cf-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="ac2cf-114">Veja também</span><span class="sxs-lookup"><span data-stu-id="ac2cf-114">See also</span></span>

- [<span data-ttu-id="ac2cf-115">Depuração</span><span class="sxs-lookup"><span data-stu-id="ac2cf-115">Debugging</span></span>](index.md)
- [<span data-ttu-id="ac2cf-116">Interface IXCLRDataMethodDefinition</span><span class="sxs-lookup"><span data-stu-id="ac2cf-116">IXCLRDataMethodDefinition Interface</span></span>](ixclrdatamethoddefinition-interface.md)
