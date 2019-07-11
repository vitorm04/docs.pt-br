---
title: Método IXCLRDataModule::GetVersionId
ms.date: 01/16/2019
api.name:
- IXCLRDataModule::GetVersionId Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataModule::GetVersionId Method
helpviewer.keywords:
- IXCLRDataModule::GetVersionId Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 5bd84f784ea92e7b2ce2465e64972dc84e16a16c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744696"
---
# <a name="ixclrdatamodulegetversionid-method"></a><span data-ttu-id="fff29-102">Método IXCLRDataModule::GetVersionId</span><span class="sxs-lookup"><span data-stu-id="fff29-102">IXCLRDataModule::GetVersionId Method</span></span>

<span data-ttu-id="fff29-103">Obtém o identificador de versão do módulo.</span><span class="sxs-lookup"><span data-stu-id="fff29-103">Gets the module's version identifier.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="fff29-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fff29-104">Syntax</span></span>

```cpp
HRESULT GetVersionId(
    [out] GUID* vid
);
```

## <a name="parameters"></a><span data-ttu-id="fff29-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fff29-105">Parameters</span></span>

`vid`\
<span data-ttu-id="fff29-106">[out] Identificador de versão do módulo.</span><span class="sxs-lookup"><span data-stu-id="fff29-106">[out] The module's version identifier.</span></span>

## <a name="remarks"></a><span data-ttu-id="fff29-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="fff29-107">Remarks</span></span>

<span data-ttu-id="fff29-108">O método fornecido é parte do `IXCLRDataModule` de interface e corresponde ao slot 40th da tabela de método virtual.</span><span class="sxs-lookup"><span data-stu-id="fff29-108">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 40th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="fff29-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fff29-109">Requirements</span></span>

<span data-ttu-id="fff29-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fff29-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="fff29-111">**Cabeçalho:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="fff29-111">**Header:** None</span></span>  
<span data-ttu-id="fff29-112">**Biblioteca:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="fff29-112">**Library:** None</span></span>  
<span data-ttu-id="fff29-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="fff29-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="fff29-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fff29-114">See also</span></span>

- [<span data-ttu-id="fff29-115">Depuração</span><span class="sxs-lookup"><span data-stu-id="fff29-115">Debugging</span></span>](index.md)
- [<span data-ttu-id="fff29-116">Interface IXCLRDataModule</span><span class="sxs-lookup"><span data-stu-id="fff29-116">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)
