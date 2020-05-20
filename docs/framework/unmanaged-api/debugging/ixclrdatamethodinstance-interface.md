---
title: Interface IXCLRDataMethodInstance
ms.date: 02/01/2019
api.name:
- IXCLRDataMethodInstance Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodInstance Interface
helpviewer.keywords:
- IXCLRDataMethodInstance Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 0b1c982b25af9edea76a038b4314b4bd608f07df
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420884"
---
# <a name="ixclrdatamethodinstance-interface"></a><span data-ttu-id="cb82d-102">Interface IXCLRDataMethodInstance</span><span class="sxs-lookup"><span data-stu-id="cb82d-102">IXCLRDataMethodInstance Interface</span></span>

<span data-ttu-id="cb82d-103">Fornece métodos para consultar informações sobre uma instância de método.</span><span class="sxs-lookup"><span data-stu-id="cb82d-103">Provides methods for querying information about a method instance.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="cb82d-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="cb82d-104">Methods</span></span>

| <span data-ttu-id="cb82d-105">Método</span><span class="sxs-lookup"><span data-stu-id="cb82d-105">Method</span></span>                                                                                                                  | <span data-ttu-id="cb82d-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="cb82d-106">Description</span></span>                                 |
| ----------------------------------------------------------------------------------------------------------------------- | ------------------------------------------- |
| [<span data-ttu-id="cb82d-107">GetILAddressMap</span><span class="sxs-lookup"><span data-stu-id="cb82d-107">GetILAddressMap</span></span>](ixclrdatamethodinstance-getiladdressmap-method.md) | <span data-ttu-id="cb82d-108">Obtém o IL para endereçar informações de mapeamento.</span><span class="sxs-lookup"><span data-stu-id="cb82d-108">Gets the IL to address mapping information.</span></span> |
| [<span data-ttu-id="cb82d-109">GetRepresentativeEntryAddress</span><span class="sxs-lookup"><span data-stu-id="cb82d-109">GetRepresentativeEntryAddress</span></span>](ixclrdatamethodinstance-getrepresentativeentryaddress-method.md) | <span data-ttu-id="cb82d-110">Obtém o endereço de ponto de entrada mais representativo para a compilação nativa de todos os pontos de entrada possíveis para um método.</span><span class="sxs-lookup"><span data-stu-id="cb82d-110">Gets the most representative entry point address for the native compilation of all the possible entry points for a method.</span></span> |

## <a name="remarks"></a><span data-ttu-id="cb82d-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="cb82d-111">Remarks</span></span>

<span data-ttu-id="cb82d-112">Essa interface reside dentro do tempo de execução e não é exposta por nenhum cabeçalho ou arquivo de biblioteca.</span><span class="sxs-lookup"><span data-stu-id="cb82d-112">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="cb82d-113">No entanto, é uma interface COM que deriva de `IUnknown` com GUID `ECD73800-22CA-4b0d-AB55-E9BA7E6318A5` que pode ser obtido por meio dos mecanismos com usuais.</span><span class="sxs-lookup"><span data-stu-id="cb82d-113">However, it's a COM interface that derives from `IUnknown` with GUID `ECD73800-22CA-4b0d-AB55-E9BA7E6318A5` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="cb82d-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cb82d-114">Requirements</span></span>

<span data-ttu-id="cb82d-115">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb82d-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="cb82d-116">**Cabeçalho:** None</span><span class="sxs-lookup"><span data-stu-id="cb82d-116">**Header:** None</span></span>  
<span data-ttu-id="cb82d-117">**Biblioteca:** None</span><span class="sxs-lookup"><span data-stu-id="cb82d-117">**Library:** None</span></span>  
<span data-ttu-id="cb82d-118">**.NET Framework versões:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="cb82d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="cb82d-119">Veja também</span><span class="sxs-lookup"><span data-stu-id="cb82d-119">See also</span></span>

- [<span data-ttu-id="cb82d-120">Depuração</span><span class="sxs-lookup"><span data-stu-id="cb82d-120">Debugging</span></span>](index.md)
- [<span data-ttu-id="cb82d-121">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="cb82d-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
