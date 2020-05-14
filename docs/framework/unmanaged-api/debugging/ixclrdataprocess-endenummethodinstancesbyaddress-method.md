---
title: 'Método IXCLRDataProcess:: EndEnumMethodInstancesByAddress'
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::EndEnumMethodInstancesByAddress Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::EndEnumMethodInstancesByAddress Method
helpviewer.keywords:
- IXCLRDataProcess::EndEnumMethodInstancesByAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 04ce8f44b0c9f532951666de7bfb9de475c14746
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83395253"
---
# <a name="ixclrdataprocessendenummethodinstancesbyaddress-method"></a><span data-ttu-id="17e48-102">Método IXCLRDataProcess:: EndEnumMethodInstancesByAddress</span><span class="sxs-lookup"><span data-stu-id="17e48-102">IXCLRDataProcess::EndEnumMethodInstancesByAddress Method</span></span>

<span data-ttu-id="17e48-103">Libera os recursos usados por iteradores internos usados durante a enumeração da instância.</span><span class="sxs-lookup"><span data-stu-id="17e48-103">Releases the resources used by internal iterators used during instance enumeration.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="17e48-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="17e48-104">Syntax</span></span>

```cpp
HRESULT EndEnumMethodInstancesByAddress(
    [in] CLRDATA_ENUM handle
);
```

## <a name="parameters"></a><span data-ttu-id="17e48-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="17e48-105">Parameters</span></span>

`handle`\
<span data-ttu-id="17e48-106">fora Um identificador para enumerar as instâncias de método.</span><span class="sxs-lookup"><span data-stu-id="17e48-106">[out] A handle for enumerating the method instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="17e48-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="17e48-107">Remarks</span></span>

<span data-ttu-id="17e48-108">O método fornecido faz parte da `IXCLRDataProcess` interface e corresponde ao slot 30 da tabela de métodos virtuais.</span><span class="sxs-lookup"><span data-stu-id="17e48-108">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 30th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="17e48-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="17e48-109">Requirements</span></span>

<span data-ttu-id="17e48-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17e48-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="17e48-111">**Cabeçalho:** None</span><span class="sxs-lookup"><span data-stu-id="17e48-111">**Header:** None</span></span>  
<span data-ttu-id="17e48-112">**Biblioteca:** None</span><span class="sxs-lookup"><span data-stu-id="17e48-112">**Library:** None</span></span>  
<span data-ttu-id="17e48-113">**.NET Framework versões:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="17e48-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="17e48-114">Veja também</span><span class="sxs-lookup"><span data-stu-id="17e48-114">See also</span></span>

- [<span data-ttu-id="17e48-115">Enumeração CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="17e48-115">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="17e48-116">Depuração</span><span class="sxs-lookup"><span data-stu-id="17e48-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="17e48-117">Interface IXCLRDataProcess</span><span class="sxs-lookup"><span data-stu-id="17e48-117">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
