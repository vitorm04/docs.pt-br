---
title: Método IXCLRDataMethodDefinition::EnumInstance
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
ms.openlocfilehash: 7ad1a9957e9bffd7b28aa241723dedba1d11f4cd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67775873"
---
# <a name="ixclrdatamethoddefinitionenuminstance-method"></a><span data-ttu-id="ca6dc-102">Método IXCLRDataMethodDefinition::EnumInstance</span><span class="sxs-lookup"><span data-stu-id="ca6dc-102">IXCLRDataMethodDefinition::EnumInstance Method</span></span>

<span data-ttu-id="ca6dc-103">Enumera as instâncias desta definição de método.</span><span class="sxs-lookup"><span data-stu-id="ca6dc-103">Enumerates the instances of this method definition.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="ca6dc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ca6dc-104">Syntax</span></span>

```cpp
HRESULT EnumInstance(
    [in, out] CLRDATA_ENUM         *handle,
    [out] IXCLRDataMethodInstance **instance
);
```

## <a name="parameters"></a><span data-ttu-id="ca6dc-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ca6dc-105">Parameters</span></span>

`handle`\
<span data-ttu-id="ca6dc-106">[no, out] Um identificador para enumerar as instâncias.</span><span class="sxs-lookup"><span data-stu-id="ca6dc-106">[in, out] A handle for enumerating the instances.</span></span>

`instance`\
<span data-ttu-id="ca6dc-107">[out] A instância enumerada.</span><span class="sxs-lookup"><span data-stu-id="ca6dc-107">[out] The enumerated instance.</span></span>

## <a name="remarks"></a><span data-ttu-id="ca6dc-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="ca6dc-108">Remarks</span></span>

<span data-ttu-id="ca6dc-109">O método fornecido é parte do `IXCLRDataMethodDefinition` de interface e corresponde ao slot de quarto da tabela de método virtual.</span><span class="sxs-lookup"><span data-stu-id="ca6dc-109">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the fourth slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="ca6dc-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ca6dc-110">Requirements</span></span>

<span data-ttu-id="ca6dc-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca6dc-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="ca6dc-112">**Cabeçalho:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="ca6dc-112">**Header:** None</span></span>  
<span data-ttu-id="ca6dc-113">**Biblioteca:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="ca6dc-113">**Library:** None</span></span>  
<span data-ttu-id="ca6dc-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ca6dc-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="ca6dc-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ca6dc-115">See also</span></span>

- [<span data-ttu-id="ca6dc-116">Enumeração CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="ca6dc-116">CLRDataSourceType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="ca6dc-117">Depuração</span><span class="sxs-lookup"><span data-stu-id="ca6dc-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="ca6dc-118">Interface IXCLRDataMethodDefinition</span><span class="sxs-lookup"><span data-stu-id="ca6dc-118">IXCLRDataMethodDefinition Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethoddefinition-interface.md)
- [<span data-ttu-id="ca6dc-119">Interface IXCLRDataMethodInstance</span><span class="sxs-lookup"><span data-stu-id="ca6dc-119">IXCLRDataMethodInstance Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethodinstance-interface.md)
