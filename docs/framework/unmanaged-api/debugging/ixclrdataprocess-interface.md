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
ms.openlocfilehash: 8c98dd42b4ac5593d96478c2286f49ad216a4bc1
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416281"
---
# <a name="ixclrdataprocess-interface"></a><span data-ttu-id="eaf17-102">Interface IXCLRDataProcess</span><span class="sxs-lookup"><span data-stu-id="eaf17-102">IXCLRDataProcess Interface</span></span>

<span data-ttu-id="eaf17-103">Fornece métodos para consultar informações sobre um processo.</span><span class="sxs-lookup"><span data-stu-id="eaf17-103">Provides methods for querying information about a process.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="eaf17-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="eaf17-104">Methods</span></span>

| <span data-ttu-id="eaf17-105">Método</span><span class="sxs-lookup"><span data-stu-id="eaf17-105">Method</span></span>                                                                                                                                               | <span data-ttu-id="eaf17-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="eaf17-106">Description</span></span>                                                                                     |
| ---------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="eaf17-107">GetAppDomainByUniqueId</span><span class="sxs-lookup"><span data-stu-id="eaf17-107">GetAppDomainByUniqueId</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-getappdomainbyuniqueid-method.md)                       | <span data-ttu-id="eaf17-108">Obtém um `AppDomain` em um processo por sua id exclusiva.</span><span class="sxs-lookup"><span data-stu-id="eaf17-108">Gets an `AppDomain` in a process by its unique id.</span></span>                                              |
| [<span data-ttu-id="eaf17-109">StartEnumModules</span><span class="sxs-lookup"><span data-stu-id="eaf17-109">StartEnumModules</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-startenummodules-method.md)                                   | <span data-ttu-id="eaf17-110">Fornece um identificador para enumerar os módulos de um processo.</span><span class="sxs-lookup"><span data-stu-id="eaf17-110">Provides a handle to enumerate the modules of a process.</span></span>                                        |
| [<span data-ttu-id="eaf17-111">EnumModule</span><span class="sxs-lookup"><span data-stu-id="eaf17-111">EnumModule</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-enummodule-method.md)                                               | <span data-ttu-id="eaf17-112">Enumera os módulos deste processo.</span><span class="sxs-lookup"><span data-stu-id="eaf17-112">Enumerates the modules of this process.</span></span>                                                         |
| [<span data-ttu-id="eaf17-113">EndEnumModules</span><span class="sxs-lookup"><span data-stu-id="eaf17-113">EndEnumModules</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-endenummodules-method.md)                                       | <span data-ttu-id="eaf17-114">Libera os recursos usados pelos iteradores internos usados durante a enumeração de módulo.</span><span class="sxs-lookup"><span data-stu-id="eaf17-114">Releases the resources used by internal iterators used during module enumeration.</span></span>               |
| [<span data-ttu-id="eaf17-115">StartEnumMethodInstancesByAddress</span><span class="sxs-lookup"><span data-stu-id="eaf17-115">StartEnumMethodInstancesByAddress</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-startenummethodinstancesbyaddress-method.md) | <span data-ttu-id="eaf17-116">Fornece um identificador para enumerar as instâncias do método de `AppDomain` começando em um determinado endereço.</span><span class="sxs-lookup"><span data-stu-id="eaf17-116">Provides a handle to enumerate the method instances of `AppDomain` starting at a given address.</span></span> |
| [<span data-ttu-id="eaf17-117">EnumMethodInstanceByAddress</span><span class="sxs-lookup"><span data-stu-id="eaf17-117">EnumMethodInstanceByAddress</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-enummethodinstancebyaddress-method.md)             | <span data-ttu-id="eaf17-118">Enumera as instâncias do método desse processo, começando em um deslocamento do endereço.</span><span class="sxs-lookup"><span data-stu-id="eaf17-118">Enumerates the method instances of this process starting at an address offset.</span></span>                  |
| [<span data-ttu-id="eaf17-119">EndEnumMethodInstancesByAddress</span><span class="sxs-lookup"><span data-stu-id="eaf17-119">EndEnumMethodInstancesByAddress</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-endenummethodinstancesbyaddress-method.md)     | <span data-ttu-id="eaf17-120">Libera os recursos usados pelos iteradores internos usados durante a enumeração de instância.</span><span class="sxs-lookup"><span data-stu-id="eaf17-120">Releases the resources used by internal iterators used during instance enumeration.</span></span>             |

## <a name="remarks"></a><span data-ttu-id="eaf17-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="eaf17-121">Remarks</span></span>

<span data-ttu-id="eaf17-122">Essa interface reside dentro do tempo de execução e não é exposta por meio de todos os cabeçalhos ou arquivos de biblioteca.</span><span class="sxs-lookup"><span data-stu-id="eaf17-122">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="eaf17-123">No entanto, é uma interface COM que deriva de `IUnknown` com o GUID `5c552ab6-fc09-4cb3-8e36-22fa03c798b7` que pode ser obtido por meio de mecanismos COM usual.</span><span class="sxs-lookup"><span data-stu-id="eaf17-123">However, it's a COM interface that derives from `IUnknown` with GUID `5c552ab6-fc09-4cb3-8e36-22fa03c798b7` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="eaf17-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="eaf17-124">Requirements</span></span>

<span data-ttu-id="eaf17-125">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eaf17-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>   
<span data-ttu-id="eaf17-126">**Cabeçalho:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="eaf17-126">**Header:** None</span></span>  
<span data-ttu-id="eaf17-127">**Biblioteca:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="eaf17-127">**Library:** None</span></span>  
<span data-ttu-id="eaf17-128">**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="eaf17-128">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="eaf17-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="eaf17-129">See Also</span></span>

- [<span data-ttu-id="eaf17-130">Depuração</span><span class="sxs-lookup"><span data-stu-id="eaf17-130">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="eaf17-131">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="eaf17-131">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
