---
title: Método IXCLRDataProcess::StartEnumModules
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::StartEnumModules Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::StartEnumModules Method
helpviewer.keywords:
- IXCLRDataProcess::StartEnumModules Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: a81da147c1483e7649612050f4aba29a2cc63b49
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416308"
---
# <a name="ixclrdataprocessstartenummodules-method"></a><span data-ttu-id="e5c8a-102">Método IXCLRDataProcess::StartEnumModules</span><span class="sxs-lookup"><span data-stu-id="e5c8a-102">IXCLRDataProcess::StartEnumModules Method</span></span>

<span data-ttu-id="e5c8a-103">Fornece um identificador para enumerar os módulos de um processo.</span><span class="sxs-lookup"><span data-stu-id="e5c8a-103">Provides a handle to enumerate the modules of a process.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="e5c8a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e5c8a-104">Syntax</span></span>

```
HRESULT StartEnumModules(
    [out] CLRDATA_ENUM *handle
);
```

### <a name="parameters"></a><span data-ttu-id="e5c8a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e5c8a-105">Parameters</span></span>

<span data-ttu-id="e5c8a-106">`handle` [out] Um identificador para enumerar os módulos.</span><span class="sxs-lookup"><span data-stu-id="e5c8a-106">`handle` [out] A handle for enumerating the modules.</span></span>

## <a name="remarks"></a><span data-ttu-id="e5c8a-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="e5c8a-107">Remarks</span></span>

<span data-ttu-id="e5c8a-108">O método fornecido é parte do `IXCLRDataProcess` de interface e corresponde a 24 de slot da tabela de método virtual.</span><span class="sxs-lookup"><span data-stu-id="e5c8a-108">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 24th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="e5c8a-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e5c8a-109">Requirements</span></span>

<span data-ttu-id="e5c8a-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5c8a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="e5c8a-111">**Cabeçalho:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="e5c8a-111">**Header:** None</span></span>  
<span data-ttu-id="e5c8a-112">**Biblioteca:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="e5c8a-112">**Library:** None</span></span>  
<span data-ttu-id="e5c8a-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e5c8a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="e5c8a-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e5c8a-114">See Also</span></span>

- [<span data-ttu-id="e5c8a-115">Enumeração CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="e5c8a-115">CLRDataSourceType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="e5c8a-116">Depuração</span><span class="sxs-lookup"><span data-stu-id="e5c8a-116">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="e5c8a-117">Interface IXCLRDataProcess</span><span class="sxs-lookup"><span data-stu-id="e5c8a-117">IXCLRDataProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-interface.md)
