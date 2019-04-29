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
ms.openlocfilehash: ff74a7acb5cc84c177f083c19402cd78977aeab5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775239"
---
# <a name="ixclrdataprocess-interface"></a><span data-ttu-id="50906-102">Interface IXCLRDataProcess</span><span class="sxs-lookup"><span data-stu-id="50906-102">IXCLRDataProcess Interface</span></span>

<span data-ttu-id="50906-103">Fornece métodos para consultar informações sobre um processo.</span><span class="sxs-lookup"><span data-stu-id="50906-103">Provides methods for querying information about a process.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="50906-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="50906-104">Methods</span></span>

| <span data-ttu-id="50906-105">Método</span><span class="sxs-lookup"><span data-stu-id="50906-105">Method</span></span>                                                                                                                                               | <span data-ttu-id="50906-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="50906-106">Description</span></span>                                                                                     |
| ---------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="50906-107">GetAppDomainByUniqueId</span><span class="sxs-lookup"><span data-stu-id="50906-107">GetAppDomainByUniqueId</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-getappdomainbyuniqueid-method.md)                       | <span data-ttu-id="50906-108">Obtém um `AppDomain` em um processo por sua id exclusiva.</span><span class="sxs-lookup"><span data-stu-id="50906-108">Gets an `AppDomain` in a process by its unique id.</span></span>                                              |
| [<span data-ttu-id="50906-109">StartEnumModules</span><span class="sxs-lookup"><span data-stu-id="50906-109">StartEnumModules</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-startenummodules-method.md)                                   | <span data-ttu-id="50906-110">Fornece um identificador para enumerar os módulos de um processo.</span><span class="sxs-lookup"><span data-stu-id="50906-110">Provides a handle to enumerate the modules of a process.</span></span>                                        |
| [<span data-ttu-id="50906-111">EnumModule</span><span class="sxs-lookup"><span data-stu-id="50906-111">EnumModule</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-enummodule-method.md)                                               | <span data-ttu-id="50906-112">Enumera os módulos deste processo.</span><span class="sxs-lookup"><span data-stu-id="50906-112">Enumerates the modules of this process.</span></span>                                                         |
| [<span data-ttu-id="50906-113">EndEnumModules</span><span class="sxs-lookup"><span data-stu-id="50906-113">EndEnumModules</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-endenummodules-method.md)                                       | <span data-ttu-id="50906-114">Libera os recursos usados pelos iteradores internos usados durante a enumeração de módulo.</span><span class="sxs-lookup"><span data-stu-id="50906-114">Releases the resources used by internal iterators used during module enumeration.</span></span>               |
| [<span data-ttu-id="50906-115">StartEnumMethodInstancesByAddress</span><span class="sxs-lookup"><span data-stu-id="50906-115">StartEnumMethodInstancesByAddress</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-startenummethodinstancesbyaddress-method.md) | <span data-ttu-id="50906-116">Fornece um identificador para enumerar as instâncias do método de `AppDomain` começando em um determinado endereço.</span><span class="sxs-lookup"><span data-stu-id="50906-116">Provides a handle to enumerate the method instances of `AppDomain` starting at a given address.</span></span> |
| [<span data-ttu-id="50906-117">EnumMethodInstanceByAddress</span><span class="sxs-lookup"><span data-stu-id="50906-117">EnumMethodInstanceByAddress</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-enummethodinstancebyaddress-method.md)             | <span data-ttu-id="50906-118">Enumera as instâncias do método desse processo, começando em um deslocamento do endereço.</span><span class="sxs-lookup"><span data-stu-id="50906-118">Enumerates the method instances of this process starting at an address offset.</span></span>                  |
| [<span data-ttu-id="50906-119">EndEnumMethodInstancesByAddress</span><span class="sxs-lookup"><span data-stu-id="50906-119">EndEnumMethodInstancesByAddress</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-endenummethodinstancesbyaddress-method.md)     | <span data-ttu-id="50906-120">Libera os recursos usados pelos iteradores internos usados durante a enumeração de instância.</span><span class="sxs-lookup"><span data-stu-id="50906-120">Releases the resources used by internal iterators used during instance enumeration.</span></span>             |

## <a name="remarks"></a><span data-ttu-id="50906-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="50906-121">Remarks</span></span>

<span data-ttu-id="50906-122">Essa interface reside dentro do tempo de execução e não é exposta por meio de todos os cabeçalhos ou arquivos de biblioteca.</span><span class="sxs-lookup"><span data-stu-id="50906-122">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="50906-123">No entanto, é uma interface COM que deriva de `IUnknown` com o GUID `5c552ab6-fc09-4cb3-8e36-22fa03c798b7` que pode ser obtido por meio de mecanismos COM usual.</span><span class="sxs-lookup"><span data-stu-id="50906-123">However, it's a COM interface that derives from `IUnknown` with GUID `5c552ab6-fc09-4cb3-8e36-22fa03c798b7` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="50906-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="50906-124">Requirements</span></span>

<span data-ttu-id="50906-125">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50906-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>   
<span data-ttu-id="50906-126">**Cabeçalho:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="50906-126">**Header:** None</span></span>  
<span data-ttu-id="50906-127">**Biblioteca:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="50906-127">**Library:** None</span></span>  
<span data-ttu-id="50906-128">**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="50906-128">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="50906-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="50906-129">See also</span></span>

- [<span data-ttu-id="50906-130">Depuração</span><span class="sxs-lookup"><span data-stu-id="50906-130">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="50906-131">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="50906-131">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
