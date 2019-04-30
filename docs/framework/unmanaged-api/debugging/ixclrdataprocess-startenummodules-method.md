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
ms.openlocfilehash: d871ca5dfd62dbca309f4ccc3dcedf959033a41e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61986551"
---
# <a name="ixclrdataprocessstartenummodules-method"></a><span data-ttu-id="ba9f8-102">Método IXCLRDataProcess::StartEnumModules</span><span class="sxs-lookup"><span data-stu-id="ba9f8-102">IXCLRDataProcess::StartEnumModules Method</span></span>

<span data-ttu-id="ba9f8-103">Fornece um identificador para enumerar os módulos de um processo.</span><span class="sxs-lookup"><span data-stu-id="ba9f8-103">Provides a handle to enumerate the modules of a process.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="ba9f8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ba9f8-104">Syntax</span></span>

```
HRESULT StartEnumModules(
    [out] CLRDATA_ENUM *handle
);
```

## <a name="parameters"></a><span data-ttu-id="ba9f8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ba9f8-105">Parameters</span></span>

`handle`\
<span data-ttu-id="ba9f8-106">[out] Um identificador para enumerar os módulos.</span><span class="sxs-lookup"><span data-stu-id="ba9f8-106">[out] A handle for enumerating the modules.</span></span>

## <a name="remarks"></a><span data-ttu-id="ba9f8-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="ba9f8-107">Remarks</span></span>

<span data-ttu-id="ba9f8-108">O método fornecido é parte do `IXCLRDataProcess` de interface e corresponde a 24 de slot da tabela de método virtual.</span><span class="sxs-lookup"><span data-stu-id="ba9f8-108">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 24th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="ba9f8-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ba9f8-109">Requirements</span></span>

<span data-ttu-id="ba9f8-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba9f8-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="ba9f8-111">**Cabeçalho:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="ba9f8-111">**Header:** None</span></span>  
<span data-ttu-id="ba9f8-112">**Biblioteca:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="ba9f8-112">**Library:** None</span></span>  
<span data-ttu-id="ba9f8-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ba9f8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="ba9f8-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ba9f8-114">See also</span></span>

- [<span data-ttu-id="ba9f8-115">Enumeração CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="ba9f8-115">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="ba9f8-116">Depuração</span><span class="sxs-lookup"><span data-stu-id="ba9f8-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="ba9f8-117">Interface IXCLRDataProcess</span><span class="sxs-lookup"><span data-stu-id="ba9f8-117">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
