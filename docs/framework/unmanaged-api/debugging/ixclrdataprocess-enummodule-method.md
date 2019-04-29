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
ms.openlocfilehash: a0398d18f9568754231082d63b4c6a2c865d8c6f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775257"
---
# <a name="ixclrdataprocessenummodule-method"></a><span data-ttu-id="26f74-102">Método IXCLRDataProcess::EnumModule</span><span class="sxs-lookup"><span data-stu-id="26f74-102">IXCLRDataProcess::EnumModule Method</span></span>

<span data-ttu-id="26f74-103">Enumera os módulos deste processo.</span><span class="sxs-lookup"><span data-stu-id="26f74-103">Enumerates the modules of this process.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="26f74-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="26f74-104">Syntax</span></span>

```
HRESULT EnumModule(
    [in, out] CLRDATA_ENUM  *handle,
    [out] IXCLRDataModule  **mod
);
```

## <a name="parameters"></a><span data-ttu-id="26f74-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="26f74-105">Parameters</span></span>

`handle`\
<span data-ttu-id="26f74-106">[no, out] Um identificador para enumerar os módulos.</span><span class="sxs-lookup"><span data-stu-id="26f74-106">[in, out] A handle for enumerating the modules.</span></span>

`mod`\
<span data-ttu-id="26f74-107">[out] O módulo enumerado.</span><span class="sxs-lookup"><span data-stu-id="26f74-107">[out] The enumerated module.</span></span>

## <a name="remarks"></a><span data-ttu-id="26f74-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="26f74-108">Remarks</span></span>

<span data-ttu-id="26f74-109">O método fornecido é parte do `IXCLRDataProcess` de interface e corresponde a 25 de slot da tabela de método virtual.</span><span class="sxs-lookup"><span data-stu-id="26f74-109">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 25th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="26f74-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="26f74-110">Requirements</span></span>

<span data-ttu-id="26f74-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26f74-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="26f74-112">**Cabeçalho:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="26f74-112">**Header:** None</span></span>  
<span data-ttu-id="26f74-113">**Biblioteca:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="26f74-113">**Library:** None</span></span>  
<span data-ttu-id="26f74-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="26f74-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="26f74-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="26f74-115">See also</span></span>

- [<span data-ttu-id="26f74-116">Enumeração CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="26f74-116">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="26f74-117">Depuração</span><span class="sxs-lookup"><span data-stu-id="26f74-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="26f74-118">Interface IXCLRDataModule</span><span class="sxs-lookup"><span data-stu-id="26f74-118">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)
- [<span data-ttu-id="26f74-119">Interface IXCLRDataProcess</span><span class="sxs-lookup"><span data-stu-id="26f74-119">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
