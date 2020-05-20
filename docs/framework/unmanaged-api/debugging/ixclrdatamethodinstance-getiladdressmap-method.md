---
title: 'Método IXCLRDataMethodInstance:: GetILAddressMap'
ms.date: 01/16/2019
api.name:
- IXCLRDataMethodInstance::GetILAddressMap Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodInstance::GetILAddressMap Method
helpviewer.keywords:
- IXCLRDataMethodInstance::GetILAddressMap Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 0acfa9ffd6f4bc3be567855008dccd08c9c74153
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420910"
---
# <a name="ixclrdatamethodinstancegetiladdressmap-method"></a><span data-ttu-id="04c9d-102">Método IXCLRDataMethodInstance:: GetILAddressMap</span><span class="sxs-lookup"><span data-stu-id="04c9d-102">IXCLRDataMethodInstance::GetILAddressMap Method</span></span>

<span data-ttu-id="04c9d-103">Obtém o IL para endereçar informações de mapeamento.</span><span class="sxs-lookup"><span data-stu-id="04c9d-103">Gets the IL to address mapping information.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="04c9d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="04c9d-104">Syntax</span></span>

```cpp
HRESULT GetILAddressMap(
    [in] ULONG32                                   mapLen,
    [out] ULONG32                                 *mapNeeded,
    [out, size_is(mapLen)] CLRDATA_IL_ADDRESS_MAP  maps[]
);
```

## <a name="parameters"></a><span data-ttu-id="04c9d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="04c9d-105">Parameters</span></span>

`mapLen`\
<span data-ttu-id="04c9d-106">no O comprimento da matriz de mapas fornecida.</span><span class="sxs-lookup"><span data-stu-id="04c9d-106">[in] The length of the provided maps array.</span></span>

`mapNeeded`\
<span data-ttu-id="04c9d-107">fora O número de entradas de mapa que o método precisa.</span><span class="sxs-lookup"><span data-stu-id="04c9d-107">[out] The number of map entries that the method needs.</span></span>

`maps`\
<span data-ttu-id="04c9d-108">[fora, size_is (Bordon)] A matriz para armazenar as entradas do mapa.</span><span class="sxs-lookup"><span data-stu-id="04c9d-108">[out, size_is(mapLen)] The array for storing the map entries.</span></span>

## <a name="remarks"></a><span data-ttu-id="04c9d-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="04c9d-109">Remarks</span></span>

<span data-ttu-id="04c9d-110">O método fornecido faz parte da `IXCLRDataMethodInstance` interface e corresponde ao décimo quinto slot da tabela de métodos virtuais.</span><span class="sxs-lookup"><span data-stu-id="04c9d-110">The provided method is part of the `IXCLRDataMethodInstance` interface and corresponds to the 15th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="04c9d-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="04c9d-111">Requirements</span></span>

<span data-ttu-id="04c9d-112">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04c9d-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="04c9d-113">**Cabeçalho:** None</span><span class="sxs-lookup"><span data-stu-id="04c9d-113">**Header:** None</span></span>  
<span data-ttu-id="04c9d-114">**Biblioteca:** None</span><span class="sxs-lookup"><span data-stu-id="04c9d-114">**Library:** None</span></span>  
<span data-ttu-id="04c9d-115">**.NET Framework versões:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="04c9d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="04c9d-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="04c9d-116">See also</span></span>

- [<span data-ttu-id="04c9d-117">Depuração</span><span class="sxs-lookup"><span data-stu-id="04c9d-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="04c9d-118">Interface IXCLRDataMethodInstance</span><span class="sxs-lookup"><span data-stu-id="04c9d-118">IXCLRDataMethodInstance Interface</span></span>](ixclrdatamethodinstance-interface.md)
