---
title: Método IXCLRDataProcess::EnumMethodInstanceByAddress
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::EnumMethodInstanceByAddress Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::EnumMethodInstanceByAddress Method
helpviewer.keywords:
- IXCLRDataProcess::EnumMethodInstanceByAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: a51c709b0b331127b74d98c4dc42e2772fd7f2db
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59166433"
---
# <a name="ixclrdataprocessenummethodinstancebyaddress-method"></a><span data-ttu-id="e03c2-102">Método IXCLRDataProcess::EnumMethodInstanceByAddress</span><span class="sxs-lookup"><span data-stu-id="e03c2-102">IXCLRDataProcess::EnumMethodInstanceByAddress Method</span></span>

<span data-ttu-id="e03c2-103">Enumera as instâncias do método desse processo, começando em um deslocamento do endereço.</span><span class="sxs-lookup"><span data-stu-id="e03c2-103">Enumerates the method instances of this process starting at an address offset.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="e03c2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e03c2-104">Syntax</span></span>

```
HRESULT EnumMethodInstanceByAddress(
    [in] CLRDATA_ENUM              *handle,
    [out] IXCLRDataMethodInstance **method
);
```

## <a name="parameters"></a><span data-ttu-id="e03c2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e03c2-105">Parameters</span></span>

`handle`\
<span data-ttu-id="e03c2-106">[in] Um identificador para enumerar as instâncias de método.</span><span class="sxs-lookup"><span data-stu-id="e03c2-106">[in] A handle for enumerating the method instances.</span></span>

`mod`\
<span data-ttu-id="e03c2-107">[out] A instância de método enumerado.</span><span class="sxs-lookup"><span data-stu-id="e03c2-107">[out] The enumerated method instance.</span></span>

## <a name="remarks"></a><span data-ttu-id="e03c2-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="e03c2-108">Remarks</span></span>

<span data-ttu-id="e03c2-109">O método fornecido é parte do `IXCLRDataProcess` de interface e corresponde ao slot de 28, da tabela de método virtual.</span><span class="sxs-lookup"><span data-stu-id="e03c2-109">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 28th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="e03c2-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e03c2-110">Requirements</span></span>

<span data-ttu-id="e03c2-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e03c2-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>   
<span data-ttu-id="e03c2-112">**Cabeçalho:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="e03c2-112">**Header:** None</span></span>   
<span data-ttu-id="e03c2-113">**Biblioteca:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="e03c2-113">**Library:** None</span></span>   
<span data-ttu-id="e03c2-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e03c2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>   
 
## <a name="see-also"></a><span data-ttu-id="e03c2-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e03c2-115">See also</span></span>

- [<span data-ttu-id="e03c2-116">Enumeração CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="e03c2-116">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="e03c2-117">Depuração</span><span class="sxs-lookup"><span data-stu-id="e03c2-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="e03c2-118">Interface IXCLRDataProcess</span><span class="sxs-lookup"><span data-stu-id="e03c2-118">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
