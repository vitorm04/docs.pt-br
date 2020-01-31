---
title: 'Método IXCLRDataMethodDefinition:: EnumInstance'
ms.date: 01/16/2019
api.name:
- IXCLRDataMethodDefinition::EnumInstance Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodDefinition::EnumInstance Method
helpviewer.keywords:
- IXCLRDataMethodDefinition::EnumInstance Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: b6393d7fa4853c230203521e665bbe89d7b228e2
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790436"
---
# <a name="ixclrdatamethoddefinitionenuminstance-method"></a><span data-ttu-id="82757-102">Método IXCLRDataMethodDefinition:: EnumInstance</span><span class="sxs-lookup"><span data-stu-id="82757-102">IXCLRDataMethodDefinition::EnumInstance Method</span></span>

<span data-ttu-id="82757-103">Enumera as instâncias desta definição de método.</span><span class="sxs-lookup"><span data-stu-id="82757-103">Enumerates the instances of this method definition.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="82757-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="82757-104">Syntax</span></span>

```cpp
HRESULT EnumInstance(
    [in, out] CLRDATA_ENUM         *handle,
    [out] IXCLRDataMethodInstance **instance
);
```

## <a name="parameters"></a><span data-ttu-id="82757-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="82757-105">Parameters</span></span>

`handle`\
<span data-ttu-id="82757-106">[entrada, saída] Um identificador para enumerar as instâncias.</span><span class="sxs-lookup"><span data-stu-id="82757-106">[in, out] A handle for enumerating the instances.</span></span>

`instance`\
<span data-ttu-id="82757-107">fora A instância enumerada.</span><span class="sxs-lookup"><span data-stu-id="82757-107">[out] The enumerated instance.</span></span>

## <a name="remarks"></a><span data-ttu-id="82757-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="82757-108">Remarks</span></span>

<span data-ttu-id="82757-109">O método fornecido faz parte da interface de `IXCLRDataMethodDefinition` e corresponde ao quarto slot da tabela de métodos virtuais.</span><span class="sxs-lookup"><span data-stu-id="82757-109">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the fourth slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="82757-110">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="82757-110">Requirements</span></span>

<span data-ttu-id="82757-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82757-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="82757-112">**Cabeçalho:** None</span><span class="sxs-lookup"><span data-stu-id="82757-112">**Header:** None</span></span>  
<span data-ttu-id="82757-113">**Biblioteca:** None</span><span class="sxs-lookup"><span data-stu-id="82757-113">**Library:** None</span></span>  
<span data-ttu-id="82757-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="82757-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="82757-115">Veja também</span><span class="sxs-lookup"><span data-stu-id="82757-115">See also</span></span>

- [<span data-ttu-id="82757-116">Enumeração CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="82757-116">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="82757-117">Depuração</span><span class="sxs-lookup"><span data-stu-id="82757-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="82757-118">Interface IXCLRDataMethodDefinition</span><span class="sxs-lookup"><span data-stu-id="82757-118">IXCLRDataMethodDefinition Interface</span></span>](ixclrdatamethoddefinition-interface.md)
- [<span data-ttu-id="82757-119">Interface IXCLRDataMethodInstance</span><span class="sxs-lookup"><span data-stu-id="82757-119">IXCLRDataMethodInstance Interface</span></span>](ixclrdatamethodinstance-interface.md)
