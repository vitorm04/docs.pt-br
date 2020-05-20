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
ms.openlocfilehash: 6a6def8fc10f04b89aa8d8c735025b01f9b6ddfb
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420754"
---
# <a name="ixclrdataprocess-interface"></a><span data-ttu-id="037ad-102">Interface IXCLRDataProcess</span><span class="sxs-lookup"><span data-stu-id="037ad-102">IXCLRDataProcess Interface</span></span>

<span data-ttu-id="037ad-103">Fornece métodos para consultar informações sobre um processo.</span><span class="sxs-lookup"><span data-stu-id="037ad-103">Provides methods for querying information about a process.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="037ad-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="037ad-104">Methods</span></span>

| <span data-ttu-id="037ad-105">Método</span><span class="sxs-lookup"><span data-stu-id="037ad-105">Method</span></span>                                                                                                                                               | <span data-ttu-id="037ad-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="037ad-106">Description</span></span>                                                                                     |
| ---------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="037ad-107">GetAppDomainByUniqueId</span><span class="sxs-lookup"><span data-stu-id="037ad-107">GetAppDomainByUniqueId</span></span>](ixclrdataprocess-getappdomainbyuniqueid-method.md)                       | <span data-ttu-id="037ad-108">Obtém um `AppDomain` em um processo por sua ID exclusiva.</span><span class="sxs-lookup"><span data-stu-id="037ad-108">Gets an `AppDomain` in a process by its unique id.</span></span>                                              |
| [<span data-ttu-id="037ad-109">StartEnumModules</span><span class="sxs-lookup"><span data-stu-id="037ad-109">StartEnumModules</span></span>](ixclrdataprocess-startenummodules-method.md)                                   | <span data-ttu-id="037ad-110">Fornece um identificador para enumerar os módulos de um processo.</span><span class="sxs-lookup"><span data-stu-id="037ad-110">Provides a handle to enumerate the modules of a process.</span></span>                                        |
| [<span data-ttu-id="037ad-111">EnumModule</span><span class="sxs-lookup"><span data-stu-id="037ad-111">EnumModule</span></span>](ixclrdataprocess-enummodule-method.md)                                               | <span data-ttu-id="037ad-112">Enumera os módulos desse processo.</span><span class="sxs-lookup"><span data-stu-id="037ad-112">Enumerates the modules of this process.</span></span>                                                         |
| [<span data-ttu-id="037ad-113">EndEnumModules</span><span class="sxs-lookup"><span data-stu-id="037ad-113">EndEnumModules</span></span>](ixclrdataprocess-endenummodules-method.md)                                       | <span data-ttu-id="037ad-114">Libera os recursos usados por iteradores internos usados durante a enumeração do módulo.</span><span class="sxs-lookup"><span data-stu-id="037ad-114">Releases the resources used by internal iterators used during module enumeration.</span></span>               |
| [<span data-ttu-id="037ad-115">StartEnumMethodInstancesByAddress</span><span class="sxs-lookup"><span data-stu-id="037ad-115">StartEnumMethodInstancesByAddress</span></span>](ixclrdataprocess-startenummethodinstancesbyaddress-method.md) | <span data-ttu-id="037ad-116">Fornece um identificador para enumerar as instâncias de método de `AppDomain` Iniciar em um determinado endereço.</span><span class="sxs-lookup"><span data-stu-id="037ad-116">Provides a handle to enumerate the method instances of `AppDomain` starting at a given address.</span></span> |
| [<span data-ttu-id="037ad-117">EnumMethodInstanceByAddress</span><span class="sxs-lookup"><span data-stu-id="037ad-117">EnumMethodInstanceByAddress</span></span>](ixclrdataprocess-enummethodinstancebyaddress-method.md)             | <span data-ttu-id="037ad-118">Enumera as instâncias de método deste processo Iniciando em um deslocamento de endereço.</span><span class="sxs-lookup"><span data-stu-id="037ad-118">Enumerates the method instances of this process starting at an address offset.</span></span>                  |
| [<span data-ttu-id="037ad-119">EndEnumMethodInstancesByAddress</span><span class="sxs-lookup"><span data-stu-id="037ad-119">EndEnumMethodInstancesByAddress</span></span>](ixclrdataprocess-endenummethodinstancesbyaddress-method.md)     | <span data-ttu-id="037ad-120">Libera os recursos usados por iteradores internos usados durante a enumeração da instância.</span><span class="sxs-lookup"><span data-stu-id="037ad-120">Releases the resources used by internal iterators used during instance enumeration.</span></span>             |

## <a name="remarks"></a><span data-ttu-id="037ad-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="037ad-121">Remarks</span></span>

<span data-ttu-id="037ad-122">Essa interface reside dentro do tempo de execução e não é exposta por nenhum cabeçalho ou arquivo de biblioteca.</span><span class="sxs-lookup"><span data-stu-id="037ad-122">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="037ad-123">No entanto, é uma interface COM que deriva de `IUnknown` com GUID `5c552ab6-fc09-4cb3-8e36-22fa03c798b7` que pode ser obtido por meio dos mecanismos com usuais.</span><span class="sxs-lookup"><span data-stu-id="037ad-123">However, it's a COM interface that derives from `IUnknown` with GUID `5c552ab6-fc09-4cb3-8e36-22fa03c798b7` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="037ad-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="037ad-124">Requirements</span></span>

<span data-ttu-id="037ad-125">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="037ad-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>
<span data-ttu-id="037ad-126">**Cabeçalho:** None</span><span class="sxs-lookup"><span data-stu-id="037ad-126">**Header:** None</span></span>  
<span data-ttu-id="037ad-127">**Biblioteca:** None</span><span class="sxs-lookup"><span data-stu-id="037ad-127">**Library:** None</span></span>  
<span data-ttu-id="037ad-128">**.NET Framework versões:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="037ad-128">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="037ad-129">Veja também</span><span class="sxs-lookup"><span data-stu-id="037ad-129">See also</span></span>

- [<span data-ttu-id="037ad-130">Depuração</span><span class="sxs-lookup"><span data-stu-id="037ad-130">Debugging</span></span>](index.md)
- [<span data-ttu-id="037ad-131">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="037ad-131">Debugging Interfaces</span></span>](debugging-interfaces.md)
