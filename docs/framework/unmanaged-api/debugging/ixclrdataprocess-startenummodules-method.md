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
ms.openlocfilehash: 0de622e96b9138b86cfc77c51d1a215c1868accf
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57375916"
---
# <a name="ixclrdataprocessstartenummodules-method"></a><span data-ttu-id="150cd-102">Método IXCLRDataProcess::StartEnumModules</span><span class="sxs-lookup"><span data-stu-id="150cd-102">IXCLRDataProcess::StartEnumModules Method</span></span>

<span data-ttu-id="150cd-103">Fornece um identificador para enumerar os módulos de um processo.</span><span class="sxs-lookup"><span data-stu-id="150cd-103">Provides a handle to enumerate the modules of a process.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="150cd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="150cd-104">Syntax</span></span>

```
HRESULT StartEnumModules(
    [out] CLRDATA_ENUM *handle
);
```

### <a name="parameters"></a><span data-ttu-id="150cd-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="150cd-105">Parameters</span></span>

`handle`\
<span data-ttu-id="150cd-106">[out] Um identificador para enumerar os módulos.</span><span class="sxs-lookup"><span data-stu-id="150cd-106">[out] A handle for enumerating the modules.</span></span>

## <a name="remarks"></a><span data-ttu-id="150cd-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="150cd-107">Remarks</span></span>

<span data-ttu-id="150cd-108">O método fornecido é parte do `IXCLRDataProcess` de interface e corresponde a 24 de slot da tabela de método virtual.</span><span class="sxs-lookup"><span data-stu-id="150cd-108">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 24th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="150cd-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="150cd-109">Requirements</span></span>

<span data-ttu-id="150cd-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="150cd-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="150cd-111">**Cabeçalho:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="150cd-111">**Header:** None</span></span>  
<span data-ttu-id="150cd-112">**Biblioteca:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="150cd-112">**Library:** None</span></span>  
<span data-ttu-id="150cd-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="150cd-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="150cd-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="150cd-114">See also</span></span>

- [<span data-ttu-id="150cd-115">Enumeração CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="150cd-115">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="150cd-116">Depuração</span><span class="sxs-lookup"><span data-stu-id="150cd-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="150cd-117">Interface IXCLRDataProcess</span><span class="sxs-lookup"><span data-stu-id="150cd-117">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
