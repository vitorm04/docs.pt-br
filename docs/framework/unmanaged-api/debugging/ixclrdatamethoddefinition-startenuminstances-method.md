---
title: 'Método IXCLRDataMethodDefinition:: StartEnumInstances'
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
ms.openlocfilehash: b0c37c666f23f04239ed827246b87c43ee8d5ad9
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420923"
---
# <a name="ixclrdatamethoddefinitionstartenuminstances-method"></a><span data-ttu-id="92f06-102">Método IXCLRDataMethodDefinition:: StartEnumInstances</span><span class="sxs-lookup"><span data-stu-id="92f06-102">IXCLRDataMethodDefinition::StartEnumInstances Method</span></span>

<span data-ttu-id="92f06-103">Fornece um identificador para a enumeração de instâncias de método para um determinado `IXCLRDataAppDomain` .</span><span class="sxs-lookup"><span data-stu-id="92f06-103">Provides a handle for the enumeration of method instances for a given `IXCLRDataAppDomain`.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="92f06-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="92f06-104">Syntax</span></span>

```cpp
HRESULT StartEnumInstances(
    [in] IXCLRDataAppDomain* appDomain,
    [out] CLRDATA_ENUM *handle
);
```

## <a name="parameters"></a><span data-ttu-id="92f06-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="92f06-105">Parameters</span></span>

`appDomain`\
<span data-ttu-id="92f06-106">no Um AppDomain para a enumeração.</span><span class="sxs-lookup"><span data-stu-id="92f06-106">[in] An AppDomain for the enumeration.</span></span>

`handle`\
<span data-ttu-id="92f06-107">fora Um identificador para enumerar as instâncias.</span><span class="sxs-lookup"><span data-stu-id="92f06-107">[out] A handle for enumerating the instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="92f06-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="92f06-108">Remarks</span></span>

<span data-ttu-id="92f06-109">O método fornecido faz parte da `IXCLRDataMethodDefinition` interface e corresponde ao quarto slot da tabela de métodos virtuais.</span><span class="sxs-lookup"><span data-stu-id="92f06-109">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the 5th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="92f06-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="92f06-110">Requirements</span></span>

<span data-ttu-id="92f06-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92f06-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="92f06-112">**Cabeçalho:** None</span><span class="sxs-lookup"><span data-stu-id="92f06-112">**Header:** None</span></span>  
<span data-ttu-id="92f06-113">**Biblioteca:** None</span><span class="sxs-lookup"><span data-stu-id="92f06-113">**Library:** None</span></span>  
<span data-ttu-id="92f06-114">**.NET Framework versões:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="92f06-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="92f06-115">Veja também</span><span class="sxs-lookup"><span data-stu-id="92f06-115">See also</span></span>

- [<span data-ttu-id="92f06-116">Enumeração CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="92f06-116">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="92f06-117">Depuração</span><span class="sxs-lookup"><span data-stu-id="92f06-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="92f06-118">Interface IXCLRDataMethodDefinition</span><span class="sxs-lookup"><span data-stu-id="92f06-118">IXCLRDataMethodDefinition Interface</span></span>](ixclrdatamethoddefinition-interface.md)
