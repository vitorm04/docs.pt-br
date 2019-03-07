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
ms.openlocfilehash: 23b567e4119578fba2f8cd4ba47f66dcf56a3878
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57496840"
---
# <a name="ixclrdataprocessenummethodinstancebyaddress-method"></a><span data-ttu-id="f3cbb-102">Método IXCLRDataProcess::EnumMethodInstanceByAddress</span><span class="sxs-lookup"><span data-stu-id="f3cbb-102">IXCLRDataProcess::EnumMethodInstanceByAddress Method</span></span>

<span data-ttu-id="f3cbb-103">Enumera as instâncias do método desse processo, começando em um deslocamento do endereço.</span><span class="sxs-lookup"><span data-stu-id="f3cbb-103">Enumerates the method instances of this process starting at an address offset.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="f3cbb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f3cbb-104">Syntax</span></span>

```
HRESULT EnumMethodInstanceByAddress(
    [in] CLRDATA_ENUM              *handle,
    [out] IXCLRDataMethodInstance **method
);
```

## <a name="parameters"></a><span data-ttu-id="f3cbb-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f3cbb-105">Parameters</span></span>

`handle`\
<span data-ttu-id="f3cbb-106">[in] Um identificador para enumerar as instâncias de método.</span><span class="sxs-lookup"><span data-stu-id="f3cbb-106">[in] A handle for enumerating the method instances.</span></span>

`mod`\
<span data-ttu-id="f3cbb-107">[out] A instância de método enumerado.</span><span class="sxs-lookup"><span data-stu-id="f3cbb-107">[out] The enumerated method instance.</span></span>

## <a name="remarks"></a><span data-ttu-id="f3cbb-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="f3cbb-108">Remarks</span></span>

<span data-ttu-id="f3cbb-109">O método fornecido é parte do `IXCLRDataProcess` de interface e corresponde ao slot de 28, da tabela de método virtual.</span><span class="sxs-lookup"><span data-stu-id="f3cbb-109">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 28th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="f3cbb-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f3cbb-110">Requirements</span></span>

<span data-ttu-id="f3cbb-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3cbb-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>   
<span data-ttu-id="f3cbb-112">**Cabeçalho:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="f3cbb-112">**Header:** None</span></span>   
<span data-ttu-id="f3cbb-113">**Biblioteca:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="f3cbb-113">**Library:** None</span></span>   
<span data-ttu-id="f3cbb-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f3cbb-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>   
 
## <a name="see-also"></a><span data-ttu-id="f3cbb-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f3cbb-115">See also</span></span>
- [<span data-ttu-id="f3cbb-116">Enumeração CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="f3cbb-116">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="f3cbb-117">Depuração</span><span class="sxs-lookup"><span data-stu-id="f3cbb-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="f3cbb-118">Interface IXCLRDataProcess</span><span class="sxs-lookup"><span data-stu-id="f3cbb-118">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
