---
title: Interface IXCLRDataMethodDefinition
ms.date: 01/16/2019
api.name:
- IXCLRDataMethodDefinition Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodDefinition Interface
helpviewer.keywords:
- IXCLRDataMethodDefinition Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: ebb689eee4a89a70e81d8f9d958e7826c3b3421b
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420949"
---
# <a name="ixclrdatamethoddefinition-interface"></a><span data-ttu-id="47c75-102">Interface IXCLRDataMethodDefinition</span><span class="sxs-lookup"><span data-stu-id="47c75-102">IXCLRDataMethodDefinition Interface</span></span>

<span data-ttu-id="47c75-103">Fornece métodos para consultar informações sobre uma definição de método.</span><span class="sxs-lookup"><span data-stu-id="47c75-103">Provides methods for querying information about a method definition.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="47c75-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="47c75-104">Methods</span></span>

<span data-ttu-id="47c75-105">Os métodos a seguir são alguns dos métodos disponíveis na interface.</span><span class="sxs-lookup"><span data-stu-id="47c75-105">The following methods are some of the methods available in the interface.</span></span>

| <span data-ttu-id="47c75-106">Método</span><span class="sxs-lookup"><span data-stu-id="47c75-106">Method</span></span>                                                                                                                          | <span data-ttu-id="47c75-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="47c75-107">Description</span></span>                                                                                 |
| ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="47c75-108">StartEnumInstances</span><span class="sxs-lookup"><span data-stu-id="47c75-108">StartEnumInstances</span></span>](ixclrdatamethoddefinition-startenuminstances-method.md) | <span data-ttu-id="47c75-109">Fornece um identificador para a enumeração de instâncias de método para um determinado `IXCLRDataAppDomain` .</span><span class="sxs-lookup"><span data-stu-id="47c75-109">Provides a handle for the enumeration of method instances for a given `IXCLRDataAppDomain`.</span></span> |
| [<span data-ttu-id="47c75-110">EnumInstance</span><span class="sxs-lookup"><span data-stu-id="47c75-110">EnumInstance</span></span>](ixclrdatamethoddefinition-enuminstance-method.md)             | <span data-ttu-id="47c75-111">Enumera as instâncias desta definição de método.</span><span class="sxs-lookup"><span data-stu-id="47c75-111">Enumerates the instances of this method definition.</span></span>                                         |
| [<span data-ttu-id="47c75-112">EndEnumInstances</span><span class="sxs-lookup"><span data-stu-id="47c75-112">EndEnumInstances</span></span>](ixclrdatamethoddefinition-endenuminstances-method.md)     | <span data-ttu-id="47c75-113">Libera os recursos usados por iteradores internos usados durante a enumeração da instância.</span><span class="sxs-lookup"><span data-stu-id="47c75-113">Releases the resources used by internal iterators used during instance enumeration.</span></span>         |

## <a name="remarks"></a><span data-ttu-id="47c75-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="47c75-114">Remarks</span></span>

<span data-ttu-id="47c75-115">Essa interface reside dentro do tempo de execução e não é exposta por nenhum cabeçalho ou arquivo de biblioteca.</span><span class="sxs-lookup"><span data-stu-id="47c75-115">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="47c75-116">No entanto, é uma interface COM que deriva de `IUnknown` com GUID `AAF60008-FB2C-420b-8FB1-42D244A54A97` que pode ser obtido por meio dos mecanismos com usuais.</span><span class="sxs-lookup"><span data-stu-id="47c75-116">However, it's a COM interface that derives from `IUnknown` with GUID `AAF60008-FB2C-420b-8FB1-42D244A54A97` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="47c75-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="47c75-117">Requirements</span></span>

<span data-ttu-id="47c75-118">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="47c75-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="47c75-119">**Cabeçalho:** None</span><span class="sxs-lookup"><span data-stu-id="47c75-119">**Header:** None</span></span>  
<span data-ttu-id="47c75-120">**Biblioteca:** None</span><span class="sxs-lookup"><span data-stu-id="47c75-120">**Library:** None</span></span>  
<span data-ttu-id="47c75-121">**.NET Framework versões:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="47c75-121">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="47c75-122">Veja também</span><span class="sxs-lookup"><span data-stu-id="47c75-122">See also</span></span>

- [<span data-ttu-id="47c75-123">Depuração</span><span class="sxs-lookup"><span data-stu-id="47c75-123">Debugging</span></span>](index.md)
- [<span data-ttu-id="47c75-124">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="47c75-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
