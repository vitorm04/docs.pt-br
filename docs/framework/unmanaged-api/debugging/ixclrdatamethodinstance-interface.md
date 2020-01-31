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
ms.openlocfilehash: c51825433bbc86c897c097475d5c15c855f6ec8b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790416"
---
# <a name="ixclrdatamethodinstance-interface"></a><span data-ttu-id="940af-102">Interface IXCLRDataMethodInstance</span><span class="sxs-lookup"><span data-stu-id="940af-102">IXCLRDataMethodInstance Interface</span></span>

<span data-ttu-id="940af-103">Fornece métodos para consultar informações sobre uma instância de método.</span><span class="sxs-lookup"><span data-stu-id="940af-103">Provides methods for querying information about a method instance.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="940af-104">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="940af-104">Methods</span></span>

| <span data-ttu-id="940af-105">Método</span><span class="sxs-lookup"><span data-stu-id="940af-105">Method</span></span>                                                                                                                  | <span data-ttu-id="940af-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="940af-106">Description</span></span>                                 |
| ----------------------------------------------------------------------------------------------------------------------- | ------------------------------------------- |
| [<span data-ttu-id="940af-107">GetILAddressMap</span><span class="sxs-lookup"><span data-stu-id="940af-107">GetILAddressMap</span></span>](ixclrdatamethodinstance-getiladdressmap-method.md) | <span data-ttu-id="940af-108">Obtém o IL para endereçar informações de mapeamento.</span><span class="sxs-lookup"><span data-stu-id="940af-108">Gets the IL to address mapping information.</span></span> |
| [<span data-ttu-id="940af-109">GetRepresentativeEntryAddress</span><span class="sxs-lookup"><span data-stu-id="940af-109">GetRepresentativeEntryAddress</span></span>](ixclrdatamethodinstance-getrepresentativeentryaddress-method.md) | <span data-ttu-id="940af-110">Obtém o endereço de ponto de entrada mais representativo para a compilação nativa de todos os pontos de entrada possíveis para um método.</span><span class="sxs-lookup"><span data-stu-id="940af-110">Gets the most representative entry point address for the native compilation of all the possible entry points for a method.</span></span> |

## <a name="remarks"></a><span data-ttu-id="940af-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="940af-111">Remarks</span></span>

<span data-ttu-id="940af-112">Essa interface reside dentro do tempo de execução e não é exposta por nenhum cabeçalho ou arquivo de biblioteca.</span><span class="sxs-lookup"><span data-stu-id="940af-112">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="940af-113">No entanto, é uma interface COM que deriva de `IUnknown` com `ECD73800-22CA-4b0d-AB55-E9BA7E6318A5` de GUID que pode ser obtida por meio dos mecanismos COM usuais.</span><span class="sxs-lookup"><span data-stu-id="940af-113">However, it's a COM interface that derives from `IUnknown` with GUID `ECD73800-22CA-4b0d-AB55-E9BA7E6318A5` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="940af-114">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="940af-114">Requirements</span></span>

<span data-ttu-id="940af-115">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="940af-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="940af-116">**Cabeçalho:** None</span><span class="sxs-lookup"><span data-stu-id="940af-116">**Header:** None</span></span>  
<span data-ttu-id="940af-117">**Biblioteca:** None</span><span class="sxs-lookup"><span data-stu-id="940af-117">**Library:** None</span></span>  
<span data-ttu-id="940af-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="940af-118">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="940af-119">Veja também</span><span class="sxs-lookup"><span data-stu-id="940af-119">See also</span></span>

- [<span data-ttu-id="940af-120">Depuração</span><span class="sxs-lookup"><span data-stu-id="940af-120">Debugging</span></span>](index.md)
- [<span data-ttu-id="940af-121">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="940af-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
