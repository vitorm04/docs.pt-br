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
ms.openlocfilehash: e28fa73300e147ac07a2d325fbf517480bb73797
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83394944"
---
# <a name="ixclrdataprocessstartenummethodinstancesbyaddress-method"></a><span data-ttu-id="17ac4-102">Método IXCLRDataProcess:: StartEnumMethodInstancesByAddress</span><span class="sxs-lookup"><span data-stu-id="17ac4-102">IXCLRDataProcess::StartEnumMethodInstancesByAddress Method</span></span>

<span data-ttu-id="17ac4-103">Fornece um identificador para enumerar as instâncias de método de `AppDomain` Iniciar em um determinado endereço.</span><span class="sxs-lookup"><span data-stu-id="17ac4-103">Provides a handle to enumerate the method instances of `AppDomain` starting at a given address.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="17ac4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="17ac4-104">Syntax</span></span>

```cpp
HRESULT StartEnumMethodInstancesByAddress(
    [in] CLRDATA_ADDRESS     address,
    [in] IXCLRDataAppDomain *appDomain,
    [out] CLRDATA_ENUM      *handle
);
```

## <a name="parameters"></a><span data-ttu-id="17ac4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="17ac4-105">Parameters</span></span>

`address`\
<span data-ttu-id="17ac4-106">no O endereço da primeira instância do método.</span><span class="sxs-lookup"><span data-stu-id="17ac4-106">[in] The address of the first method instance.</span></span>

`appDomain`\
<span data-ttu-id="17ac4-107">no O AppDomain das instâncias de método.</span><span class="sxs-lookup"><span data-stu-id="17ac4-107">[in] The AppDomain of the method instances.</span></span>

`handle`\
<span data-ttu-id="17ac4-108">fora Um identificador para enumerar as instâncias de método.</span><span class="sxs-lookup"><span data-stu-id="17ac4-108">[out] A handle for enumerating the method instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="17ac4-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="17ac4-109">Remarks</span></span>

<span data-ttu-id="17ac4-110">O método fornecido faz parte da `IXCLRDataProcess` interface e corresponde ao slot 28 da tabela de métodos virtuais.</span><span class="sxs-lookup"><span data-stu-id="17ac4-110">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 28th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="17ac4-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="17ac4-111">Requirements</span></span>

<span data-ttu-id="17ac4-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17ac4-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="17ac4-113">**Cabeçalho:** None</span><span class="sxs-lookup"><span data-stu-id="17ac4-113">**Header:** None</span></span>  
<span data-ttu-id="17ac4-114">**Biblioteca:** None</span><span class="sxs-lookup"><span data-stu-id="17ac4-114">**Library:** None</span></span>  
<span data-ttu-id="17ac4-115">**.NET Framework versões:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="17ac4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="17ac4-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="17ac4-116">See also</span></span>

- [<span data-ttu-id="17ac4-117">Enumeração CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="17ac4-117">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="17ac4-118">Depuração</span><span class="sxs-lookup"><span data-stu-id="17ac4-118">Debugging</span></span>](index.md)
- [<span data-ttu-id="17ac4-119">Interface IXCLRDataProcess</span><span class="sxs-lookup"><span data-stu-id="17ac4-119">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
