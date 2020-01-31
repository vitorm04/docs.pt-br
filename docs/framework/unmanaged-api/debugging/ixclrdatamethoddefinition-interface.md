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
ms.openlocfilehash: 708c681a98113a406249a360c2fc81087e5b97f8
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790422"
---
# <a name="ixclrdatamethoddefinition-interface"></a><span data-ttu-id="dff95-102">Interface IXCLRDataMethodDefinition</span><span class="sxs-lookup"><span data-stu-id="dff95-102">IXCLRDataMethodDefinition Interface</span></span>

<span data-ttu-id="dff95-103">Fornece métodos para consultar informações sobre uma definição de método.</span><span class="sxs-lookup"><span data-stu-id="dff95-103">Provides methods for querying information about a method definition.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="dff95-104">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="dff95-104">Methods</span></span>

<span data-ttu-id="dff95-105">Os métodos a seguir são alguns dos métodos disponíveis na interface.</span><span class="sxs-lookup"><span data-stu-id="dff95-105">The following methods are some of the methods available in the interface.</span></span>

| <span data-ttu-id="dff95-106">Método</span><span class="sxs-lookup"><span data-stu-id="dff95-106">Method</span></span>                                                                                                                          | <span data-ttu-id="dff95-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="dff95-107">Description</span></span>                                                                                 |
| ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="dff95-108">StartEnumInstances</span><span class="sxs-lookup"><span data-stu-id="dff95-108">StartEnumInstances</span></span>](ixclrdatamethoddefinition-startenuminstances-method.md) | <span data-ttu-id="dff95-109">Fornece um identificador para a enumeração de instâncias de método para um determinado `IXCLRDataAppDomain`.</span><span class="sxs-lookup"><span data-stu-id="dff95-109">Provides a handle for the enumeration of method instances for a given `IXCLRDataAppDomain`.</span></span> |
| [<span data-ttu-id="dff95-110">EnumInstance</span><span class="sxs-lookup"><span data-stu-id="dff95-110">EnumInstance</span></span>](ixclrdatamethoddefinition-enuminstance-method.md)             | <span data-ttu-id="dff95-111">Enumera as instâncias desta definição de método.</span><span class="sxs-lookup"><span data-stu-id="dff95-111">Enumerates the instances of this method definition.</span></span>                                         |
| [<span data-ttu-id="dff95-112">EndEnumInstances</span><span class="sxs-lookup"><span data-stu-id="dff95-112">EndEnumInstances</span></span>](ixclrdatamethoddefinition-endenuminstances-method.md)     | <span data-ttu-id="dff95-113">Libera os recursos usados por iteradores internos usados durante a enumeração da instância.</span><span class="sxs-lookup"><span data-stu-id="dff95-113">Releases the resources used by internal iterators used during instance enumeration.</span></span>         |

## <a name="remarks"></a><span data-ttu-id="dff95-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="dff95-114">Remarks</span></span>

<span data-ttu-id="dff95-115">Essa interface reside dentro do tempo de execução e não é exposta por nenhum cabeçalho ou arquivo de biblioteca.</span><span class="sxs-lookup"><span data-stu-id="dff95-115">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="dff95-116">No entanto, é uma interface COM que deriva de `IUnknown` com `AAF60008-FB2C-420b-8FB1-42D244A54A97` de GUID que pode ser obtida por meio dos mecanismos COM usuais.</span><span class="sxs-lookup"><span data-stu-id="dff95-116">However, it's a COM interface that derives from `IUnknown` with GUID `AAF60008-FB2C-420b-8FB1-42D244A54A97` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="dff95-117">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="dff95-117">Requirements</span></span>

<span data-ttu-id="dff95-118">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dff95-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="dff95-119">**Cabeçalho:** None</span><span class="sxs-lookup"><span data-stu-id="dff95-119">**Header:** None</span></span>  
<span data-ttu-id="dff95-120">**Biblioteca:** None</span><span class="sxs-lookup"><span data-stu-id="dff95-120">**Library:** None</span></span>  
<span data-ttu-id="dff95-121">**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="dff95-121">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="dff95-122">Veja também</span><span class="sxs-lookup"><span data-stu-id="dff95-122">See also</span></span>

- [<span data-ttu-id="dff95-123">Depuração</span><span class="sxs-lookup"><span data-stu-id="dff95-123">Debugging</span></span>](index.md)
- [<span data-ttu-id="dff95-124">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="dff95-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
