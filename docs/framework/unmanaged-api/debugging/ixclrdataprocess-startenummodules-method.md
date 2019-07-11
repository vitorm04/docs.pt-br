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
ms.openlocfilehash: 79c4e0ed99a068d7d806d5c25580dc477aac6475
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67752633"
---
# <a name="ixclrdataprocessstartenummodules-method"></a><span data-ttu-id="4f43e-102">Método IXCLRDataProcess::StartEnumModules</span><span class="sxs-lookup"><span data-stu-id="4f43e-102">IXCLRDataProcess::StartEnumModules Method</span></span>

<span data-ttu-id="4f43e-103">Fornece um identificador para enumerar os módulos de um processo.</span><span class="sxs-lookup"><span data-stu-id="4f43e-103">Provides a handle to enumerate the modules of a process.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="4f43e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4f43e-104">Syntax</span></span>

```cpp
HRESULT StartEnumModules(
    [out] CLRDATA_ENUM *handle
);
```

## <a name="parameters"></a><span data-ttu-id="4f43e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4f43e-105">Parameters</span></span>

`handle`\
<span data-ttu-id="4f43e-106">[out] Um identificador para enumerar os módulos.</span><span class="sxs-lookup"><span data-stu-id="4f43e-106">[out] A handle for enumerating the modules.</span></span>

## <a name="remarks"></a><span data-ttu-id="4f43e-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="4f43e-107">Remarks</span></span>

<span data-ttu-id="4f43e-108">O método fornecido é parte do `IXCLRDataProcess` de interface e corresponde a 24 de slot da tabela de método virtual.</span><span class="sxs-lookup"><span data-stu-id="4f43e-108">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 24th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="4f43e-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4f43e-109">Requirements</span></span>

<span data-ttu-id="4f43e-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4f43e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="4f43e-111">**Cabeçalho:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="4f43e-111">**Header:** None</span></span>  
<span data-ttu-id="4f43e-112">**Biblioteca:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="4f43e-112">**Library:** None</span></span>  
<span data-ttu-id="4f43e-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="4f43e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="4f43e-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4f43e-114">See also</span></span>

- [<span data-ttu-id="4f43e-115">Enumeração CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="4f43e-115">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="4f43e-116">Depuração</span><span class="sxs-lookup"><span data-stu-id="4f43e-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="4f43e-117">Interface IXCLRDataProcess</span><span class="sxs-lookup"><span data-stu-id="4f43e-117">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
