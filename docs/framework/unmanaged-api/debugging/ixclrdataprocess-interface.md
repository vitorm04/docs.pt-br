---
title: Interface IXCLRDataProcess
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess Interface
helpviewer.keywords:
- IXCLRDataProcess Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: a5d707d61513b030e5968af28db3c2a606e4419b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790368"
---
# <a name="ixclrdataprocess-interface"></a><span data-ttu-id="d10f6-102">Interface IXCLRDataProcess</span><span class="sxs-lookup"><span data-stu-id="d10f6-102">IXCLRDataProcess Interface</span></span>

<span data-ttu-id="d10f6-103">Fornece métodos para consultar informações sobre um processo.</span><span class="sxs-lookup"><span data-stu-id="d10f6-103">Provides methods for querying information about a process.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="d10f6-104">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d10f6-104">Methods</span></span>

| <span data-ttu-id="d10f6-105">Método</span><span class="sxs-lookup"><span data-stu-id="d10f6-105">Method</span></span>                                                                                                                                               | <span data-ttu-id="d10f6-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="d10f6-106">Description</span></span>                                                                                     |
| ---------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="d10f6-107">GetAppDomainByUniqueId</span><span class="sxs-lookup"><span data-stu-id="d10f6-107">GetAppDomainByUniqueId</span></span>](ixclrdataprocess-getappdomainbyuniqueid-method.md)                       | <span data-ttu-id="d10f6-108">Obtém um `AppDomain` em um processo por sua ID exclusiva.</span><span class="sxs-lookup"><span data-stu-id="d10f6-108">Gets an `AppDomain` in a process by its unique id.</span></span>                                              |
| [<span data-ttu-id="d10f6-109">StartEnumModules</span><span class="sxs-lookup"><span data-stu-id="d10f6-109">StartEnumModules</span></span>](ixclrdataprocess-startenummodules-method.md)                                   | <span data-ttu-id="d10f6-110">Fornece um identificador para enumerar os módulos de um processo.</span><span class="sxs-lookup"><span data-stu-id="d10f6-110">Provides a handle to enumerate the modules of a process.</span></span>                                        |
| [<span data-ttu-id="d10f6-111">EnumModule</span><span class="sxs-lookup"><span data-stu-id="d10f6-111">EnumModule</span></span>](ixclrdataprocess-enummodule-method.md)                                               | <span data-ttu-id="d10f6-112">Enumera os módulos desse processo.</span><span class="sxs-lookup"><span data-stu-id="d10f6-112">Enumerates the modules of this process.</span></span>                                                         |
| [<span data-ttu-id="d10f6-113">EndEnumModules</span><span class="sxs-lookup"><span data-stu-id="d10f6-113">EndEnumModules</span></span>](ixclrdataprocess-endenummodules-method.md)                                       | <span data-ttu-id="d10f6-114">Libera os recursos usados por iteradores internos usados durante a enumeração do módulo.</span><span class="sxs-lookup"><span data-stu-id="d10f6-114">Releases the resources used by internal iterators used during module enumeration.</span></span>               |
| [<span data-ttu-id="d10f6-115">StartEnumMethodInstancesByAddress</span><span class="sxs-lookup"><span data-stu-id="d10f6-115">StartEnumMethodInstancesByAddress</span></span>](ixclrdataprocess-startenummethodinstancesbyaddress-method.md) | <span data-ttu-id="d10f6-116">Fornece um identificador para enumerar as instâncias de método de `AppDomain` a partir de um determinado endereço.</span><span class="sxs-lookup"><span data-stu-id="d10f6-116">Provides a handle to enumerate the method instances of `AppDomain` starting at a given address.</span></span> |
| [<span data-ttu-id="d10f6-117">EnumMethodInstanceByAddress</span><span class="sxs-lookup"><span data-stu-id="d10f6-117">EnumMethodInstanceByAddress</span></span>](ixclrdataprocess-enummethodinstancebyaddress-method.md)             | <span data-ttu-id="d10f6-118">Enumera as instâncias de método deste processo Iniciando em um deslocamento de endereço.</span><span class="sxs-lookup"><span data-stu-id="d10f6-118">Enumerates the method instances of this process starting at an address offset.</span></span>                  |
| [<span data-ttu-id="d10f6-119">EndEnumMethodInstancesByAddress</span><span class="sxs-lookup"><span data-stu-id="d10f6-119">EndEnumMethodInstancesByAddress</span></span>](ixclrdataprocess-endenummethodinstancesbyaddress-method.md)     | <span data-ttu-id="d10f6-120">Libera os recursos usados por iteradores internos usados durante a enumeração da instância.</span><span class="sxs-lookup"><span data-stu-id="d10f6-120">Releases the resources used by internal iterators used during instance enumeration.</span></span>             |

## <a name="remarks"></a><span data-ttu-id="d10f6-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="d10f6-121">Remarks</span></span>

<span data-ttu-id="d10f6-122">Essa interface reside dentro do tempo de execução e não é exposta por nenhum cabeçalho ou arquivo de biblioteca.</span><span class="sxs-lookup"><span data-stu-id="d10f6-122">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="d10f6-123">No entanto, é uma interface COM que deriva de `IUnknown` com `5c552ab6-fc09-4cb3-8e36-22fa03c798b7` de GUID que pode ser obtida por meio dos mecanismos COM usuais.</span><span class="sxs-lookup"><span data-stu-id="d10f6-123">However, it's a COM interface that derives from `IUnknown` with GUID `5c552ab6-fc09-4cb3-8e36-22fa03c798b7` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="d10f6-124">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="d10f6-124">Requirements</span></span>

<span data-ttu-id="d10f6-125">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d10f6-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>   
<span data-ttu-id="d10f6-126">**Cabeçalho:** None</span><span class="sxs-lookup"><span data-stu-id="d10f6-126">**Header:** None</span></span>  
<span data-ttu-id="d10f6-127">**Biblioteca:** None</span><span class="sxs-lookup"><span data-stu-id="d10f6-127">**Library:** None</span></span>  
<span data-ttu-id="d10f6-128">**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="d10f6-128">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="d10f6-129">Veja também</span><span class="sxs-lookup"><span data-stu-id="d10f6-129">See also</span></span>

- [<span data-ttu-id="d10f6-130">Depuração</span><span class="sxs-lookup"><span data-stu-id="d10f6-130">Debugging</span></span>](index.md)
- [<span data-ttu-id="d10f6-131">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="d10f6-131">Debugging Interfaces</span></span>](debugging-interfaces.md)
