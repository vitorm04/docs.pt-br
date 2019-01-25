---
title: Método IXCLRDataProcess::EndEnumModules
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::EndEnumModules Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::EndEnumModules Method
helpviewer.keywords:
- IXCLRDataProcess::EndEnumModules Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 50ad55674360d7b880af3ddf701cf17005f30ce7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54722732"
---
# <a name="ixclrdataprocessendenummodules-method"></a><span data-ttu-id="7abcb-102">Método IXCLRDataProcess::EndEnumModules</span><span class="sxs-lookup"><span data-stu-id="7abcb-102">IXCLRDataProcess::EndEnumModules Method</span></span>

<span data-ttu-id="7abcb-103">Libera os recursos usados pelos iteradores internos usados durante a enumeração de módulo.</span><span class="sxs-lookup"><span data-stu-id="7abcb-103">Releases the resources used by internal iterators used during module enumeration.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="7abcb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7abcb-104">Syntax</span></span>
```
HRESULT EndEnumModules(
    [in] CLRDATA_ENUM handle
);
```

### <a name="parameters"></a><span data-ttu-id="7abcb-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7abcb-105">Parameters</span></span>
<span data-ttu-id="7abcb-106">`handle` [out] Um identificador para enumerar os módulos.</span><span class="sxs-lookup"><span data-stu-id="7abcb-106">`handle` [out] A handle for enumerating the modules.</span></span>

## <a name="remarks"></a><span data-ttu-id="7abcb-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="7abcb-107">Remarks</span></span>

<span data-ttu-id="7abcb-108">O método fornecido é parte do `IXCLRDataProcess` de interface e corresponde ao slot de 26 da tabela de método virtual.</span><span class="sxs-lookup"><span data-stu-id="7abcb-108">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 26th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="7abcb-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7abcb-109">Requirements</span></span>

<span data-ttu-id="7abcb-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7abcb-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>   
<span data-ttu-id="7abcb-111">**Cabeçalho:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="7abcb-111">**Header:** None</span></span>   
<span data-ttu-id="7abcb-112">**Biblioteca:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="7abcb-112">**Library:** None</span></span>   
<span data-ttu-id="7abcb-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="7abcb-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>   

## <a name="see-also"></a><span data-ttu-id="7abcb-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7abcb-114">See also</span></span>

- [<span data-ttu-id="7abcb-115">Depuração</span><span class="sxs-lookup"><span data-stu-id="7abcb-115">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="7abcb-116">Interface IXCLRDataProcess</span><span class="sxs-lookup"><span data-stu-id="7abcb-116">IXCLRDataProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-interface.md)
