---
title: Método IXCLRDataProcess::EnumModule
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::EnumModule Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::EnumModule Method
helpviewer.keywords:
- IXCLRDataProcess::EnumModule Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: fa1e41985444324627c6b66a109b4619d85fc57f
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416301"
---
# <a name="ixclrdataprocessenummodule-method"></a><span data-ttu-id="1c56d-102">Método IXCLRDataProcess::EnumModule</span><span class="sxs-lookup"><span data-stu-id="1c56d-102">IXCLRDataProcess::EnumModule Method</span></span>

<span data-ttu-id="1c56d-103">Enumera os módulos deste processo.</span><span class="sxs-lookup"><span data-stu-id="1c56d-103">Enumerates the modules of this process.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="1c56d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1c56d-104">Syntax</span></span>

```
HRESULT EnumModule(
    [in, out] CLRDATA_ENUM  *handle,
    [out] IXCLRDataModule  **mod
);
```

### <a name="parameters"></a><span data-ttu-id="1c56d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1c56d-105">Parameters</span></span>

<span data-ttu-id="1c56d-106">`handle` [no, out] Um identificador para enumerar os módulos.</span><span class="sxs-lookup"><span data-stu-id="1c56d-106">`handle` [in, out] A handle for enumerating the modules.</span></span>

<span data-ttu-id="1c56d-107">`mod` [out] O módulo enumerado.</span><span class="sxs-lookup"><span data-stu-id="1c56d-107">`mod` [out] The enumerated module.</span></span>

## <a name="remarks"></a><span data-ttu-id="1c56d-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="1c56d-108">Remarks</span></span>

<span data-ttu-id="1c56d-109">O método fornecido é parte do `IXCLRDataProcess` de interface e corresponde a 25 de slot da tabela de método virtual.</span><span class="sxs-lookup"><span data-stu-id="1c56d-109">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 25th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="1c56d-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1c56d-110">Requirements</span></span>

<span data-ttu-id="1c56d-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c56d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="1c56d-112">**Cabeçalho:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="1c56d-112">**Header:** None</span></span>  
<span data-ttu-id="1c56d-113">**Biblioteca:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="1c56d-113">**Library:** None</span></span>  
<span data-ttu-id="1c56d-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="1c56d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="1c56d-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1c56d-115">See Also</span></span>

- [<span data-ttu-id="1c56d-116">Enumeração CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="1c56d-116">CLRDataSourceType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="1c56d-117">Depuração</span><span class="sxs-lookup"><span data-stu-id="1c56d-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="1c56d-118">Interface IXCLRDataModule</span><span class="sxs-lookup"><span data-stu-id="1c56d-118">IXCLRDataModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamodule-interface.md)
- [<span data-ttu-id="1c56d-119">Interface IXCLRDataProcess</span><span class="sxs-lookup"><span data-stu-id="1c56d-119">IXCLRDataProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-interface.md)
