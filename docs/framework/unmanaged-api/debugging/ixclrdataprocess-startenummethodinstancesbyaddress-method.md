---
title: 'Método IXCLRDataProcess:: StartEnumMethodInstancesByAddress'
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::StartEnumMethodInstancesByAddress Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::StartEnumMethodInstancesByAddress Method
helpviewer.keywords:
- IXCLRDataProcess::StartEnumMethodInstancesByAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 52d533f1c86b34b7b9febade8590e7ab58d8221e
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420728"
---
# <a name="ixclrdataprocessstartenummethodinstancesbyaddress-method"></a><span data-ttu-id="74433-102">Método IXCLRDataProcess:: StartEnumMethodInstancesByAddress</span><span class="sxs-lookup"><span data-stu-id="74433-102">IXCLRDataProcess::StartEnumMethodInstancesByAddress Method</span></span>

<span data-ttu-id="74433-103">Fornece um identificador para enumerar as instâncias de método de `AppDomain` Iniciar em um determinado endereço.</span><span class="sxs-lookup"><span data-stu-id="74433-103">Provides a handle to enumerate the method instances of `AppDomain` starting at a given address.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="74433-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="74433-104">Syntax</span></span>

```cpp
HRESULT StartEnumMethodInstancesByAddress(
    [in] CLRDATA_ADDRESS     address,
    [in] IXCLRDataAppDomain *appDomain,
    [out] CLRDATA_ENUM      *handle
);
```

## <a name="parameters"></a><span data-ttu-id="74433-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="74433-105">Parameters</span></span>

`address`\
<span data-ttu-id="74433-106">no O endereço da primeira instância do método.</span><span class="sxs-lookup"><span data-stu-id="74433-106">[in] The address of the first method instance.</span></span>

`appDomain`\
<span data-ttu-id="74433-107">no O AppDomain das instâncias de método.</span><span class="sxs-lookup"><span data-stu-id="74433-107">[in] The AppDomain of the method instances.</span></span>

`handle`\
<span data-ttu-id="74433-108">fora Um identificador para enumerar as instâncias de método.</span><span class="sxs-lookup"><span data-stu-id="74433-108">[out] A handle for enumerating the method instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="74433-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="74433-109">Remarks</span></span>

<span data-ttu-id="74433-110">O método fornecido faz parte da `IXCLRDataProcess` interface e corresponde ao slot 28 da tabela de métodos virtuais.</span><span class="sxs-lookup"><span data-stu-id="74433-110">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 28th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="74433-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="74433-111">Requirements</span></span>

<span data-ttu-id="74433-112">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74433-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="74433-113">**Cabeçalho:** None</span><span class="sxs-lookup"><span data-stu-id="74433-113">**Header:** None</span></span>  
<span data-ttu-id="74433-114">**Biblioteca:** None</span><span class="sxs-lookup"><span data-stu-id="74433-114">**Library:** None</span></span>  
<span data-ttu-id="74433-115">**.NET Framework versões:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="74433-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="74433-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="74433-116">See also</span></span>

- [<span data-ttu-id="74433-117">Enumeração CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="74433-117">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="74433-118">Depuração</span><span class="sxs-lookup"><span data-stu-id="74433-118">Debugging</span></span>](index.md)
- [<span data-ttu-id="74433-119">Interface IXCLRDataProcess</span><span class="sxs-lookup"><span data-stu-id="74433-119">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
