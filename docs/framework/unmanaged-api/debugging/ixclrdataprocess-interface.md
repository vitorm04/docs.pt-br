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
ms.openlocfilehash: e7e53615e38d0ab76f9e7c0a753be3c13780057d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178369"
---
# <a name="ixclrdataprocess-interface"></a><span data-ttu-id="4d169-102">Interface IXCLRDataProcess</span><span class="sxs-lookup"><span data-stu-id="4d169-102">IXCLRDataProcess Interface</span></span>

<span data-ttu-id="4d169-103">Fornece métodos para consultar informações sobre um processo.</span><span class="sxs-lookup"><span data-stu-id="4d169-103">Provides methods for querying information about a process.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="4d169-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="4d169-104">Methods</span></span>

| <span data-ttu-id="4d169-105">Método</span><span class="sxs-lookup"><span data-stu-id="4d169-105">Method</span></span>                                                                                                                                               | <span data-ttu-id="4d169-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="4d169-106">Description</span></span>                                                                                     |
| ---------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="4d169-107">GetAppDomainByUniqueId</span><span class="sxs-lookup"><span data-stu-id="4d169-107">GetAppDomainByUniqueId</span></span>](ixclrdataprocess-getappdomainbyuniqueid-method.md)                       | <span data-ttu-id="4d169-108">Recebe `AppDomain` um em um processo por sua identificação única.</span><span class="sxs-lookup"><span data-stu-id="4d169-108">Gets an `AppDomain` in a process by its unique id.</span></span>                                              |
| [<span data-ttu-id="4d169-109">StartEnumModules</span><span class="sxs-lookup"><span data-stu-id="4d169-109">StartEnumModules</span></span>](ixclrdataprocess-startenummodules-method.md)                                   | <span data-ttu-id="4d169-110">Fornece uma alça para enumerar os módulos de um processo.</span><span class="sxs-lookup"><span data-stu-id="4d169-110">Provides a handle to enumerate the modules of a process.</span></span>                                        |
| [<span data-ttu-id="4d169-111">EnumModule</span><span class="sxs-lookup"><span data-stu-id="4d169-111">EnumModule</span></span>](ixclrdataprocess-enummodule-method.md)                                               | <span data-ttu-id="4d169-112">Enumera os módulos desse processo.</span><span class="sxs-lookup"><span data-stu-id="4d169-112">Enumerates the modules of this process.</span></span>                                                         |
| [<span data-ttu-id="4d169-113">EndEnumModules</span><span class="sxs-lookup"><span data-stu-id="4d169-113">EndEnumModules</span></span>](ixclrdataprocess-endenummodules-method.md)                                       | <span data-ttu-id="4d169-114">Libera os recursos utilizados pelos ativadores internos utilizados durante a enumeração do módulo.</span><span class="sxs-lookup"><span data-stu-id="4d169-114">Releases the resources used by internal iterators used during module enumeration.</span></span>               |
| [<span data-ttu-id="4d169-115">StartEnumMethodInstancesByAddress</span><span class="sxs-lookup"><span data-stu-id="4d169-115">StartEnumMethodInstancesByAddress</span></span>](ixclrdataprocess-startenummethodinstancesbyaddress-method.md) | <span data-ttu-id="4d169-116">Fornece uma alça para enumerar `AppDomain` as instâncias do método de começar em um determinado endereço.</span><span class="sxs-lookup"><span data-stu-id="4d169-116">Provides a handle to enumerate the method instances of `AppDomain` starting at a given address.</span></span> |
| [<span data-ttu-id="4d169-117">EnumMethodInstanceByAddress</span><span class="sxs-lookup"><span data-stu-id="4d169-117">EnumMethodInstanceByAddress</span></span>](ixclrdataprocess-enummethodinstancebyaddress-method.md)             | <span data-ttu-id="4d169-118">Enumera as instâncias de método deste processo a partir de uma compensação de endereço.</span><span class="sxs-lookup"><span data-stu-id="4d169-118">Enumerates the method instances of this process starting at an address offset.</span></span>                  |
| [<span data-ttu-id="4d169-119">EndEnumMethodInstancesByAddress</span><span class="sxs-lookup"><span data-stu-id="4d169-119">EndEnumMethodInstancesByAddress</span></span>](ixclrdataprocess-endenummethodinstancesbyaddress-method.md)     | <span data-ttu-id="4d169-120">Libera os recursos utilizados pelos ativadores internos usados durante a enumeração da instância.</span><span class="sxs-lookup"><span data-stu-id="4d169-120">Releases the resources used by internal iterators used during instance enumeration.</span></span>             |

## <a name="remarks"></a><span data-ttu-id="4d169-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="4d169-121">Remarks</span></span>

<span data-ttu-id="4d169-122">Esta interface vive dentro do tempo de execução e não é exposta através de nenhum cabeçalho ou arquivos de biblioteca.</span><span class="sxs-lookup"><span data-stu-id="4d169-122">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="4d169-123">No entanto, é uma interface `IUnknown` COM `5c552ab6-fc09-4cb3-8e36-22fa03c798b7` que deriva de com GUID que pode ser obtida através dos mecanismos COM usuais.</span><span class="sxs-lookup"><span data-stu-id="4d169-123">However, it's a COM interface that derives from `IUnknown` with GUID `5c552ab6-fc09-4cb3-8e36-22fa03c798b7` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="4d169-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4d169-124">Requirements</span></span>

<span data-ttu-id="4d169-125">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4d169-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>
<span data-ttu-id="4d169-126">**Cabeçalho:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="4d169-126">**Header:** None</span></span>  
<span data-ttu-id="4d169-127">**Biblioteca:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="4d169-127">**Library:** None</span></span>  
<span data-ttu-id="4d169-128">**.NET Framework Versions:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="4d169-128">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="4d169-129">Confira também</span><span class="sxs-lookup"><span data-stu-id="4d169-129">See also</span></span>

- [<span data-ttu-id="4d169-130">Depuração</span><span class="sxs-lookup"><span data-stu-id="4d169-130">Debugging</span></span>](index.md)
- [<span data-ttu-id="4d169-131">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="4d169-131">Debugging Interfaces</span></span>](debugging-interfaces.md)
