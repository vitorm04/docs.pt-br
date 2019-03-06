---
title: Método ISOSDacInterface::GetModuleData
ms.date: 02/01/2019
api.name:
- ISOSDacInterface::GetModuleData Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- ISOSDacInterface::GetModuleData Method
helpviewer.keywords:
- ISOSDacInterface::GetModuleData Method [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: b0edd459deaf68040e05209c6ecf2cb7cae12e8d
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57369945"
---
# <a name="isosdacinterfacegetmoduledata-method"></a><span data-ttu-id="2b163-102">Método ISOSDacInterface::GetModuleData</span><span class="sxs-lookup"><span data-stu-id="2b163-102">ISOSDacInterface::GetModuleData Method</span></span>

<span data-ttu-id="2b163-103">Busca os dados correspondentes para o módulo carregado em um determinado endereço.</span><span class="sxs-lookup"><span data-stu-id="2b163-103">Fetches the data corresponding to the module loaded at a given address.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="2b163-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2b163-104">Syntax</span></span>

```
HRESULT GetModuleData(
    CLRDATA_ADDRESS moduleAddr,
    DacpModuleData *data
);
```

### <a name="parameters"></a><span data-ttu-id="2b163-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2b163-105">Parameters</span></span>

`moduleAddr`\
<span data-ttu-id="2b163-106">[in] O endereço do módulo para recuperar informações para.</span><span class="sxs-lookup"><span data-stu-id="2b163-106">[in] The address of the module to retrieve information for.</span></span>

`data`\
<span data-ttu-id="2b163-107">[out] O [DacpModuleData estrutura](dacpmoduledata-structure.md) para conter as informações do módulo carregado.</span><span class="sxs-lookup"><span data-stu-id="2b163-107">[out] The [DacpModuleData structure](dacpmoduledata-structure.md) to hold the information of the loaded module.</span></span>


## <a name="remarks"></a><span data-ttu-id="2b163-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="2b163-108">Remarks</span></span>

<span data-ttu-id="2b163-109">O método fornecido é parte do `ISOSDacInterface` de interface e corresponde ao slot de 13 da tabela de método virtual.</span><span class="sxs-lookup"><span data-stu-id="2b163-109">The provided method is part of the `ISOSDacInterface` interface and corresponds to the 13th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="2b163-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2b163-110">Requirements</span></span>

<span data-ttu-id="2b163-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b163-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="2b163-112">**Cabeçalho:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="2b163-112">**Header:** None</span></span>  
<span data-ttu-id="2b163-113">**Biblioteca:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="2b163-113">**Library:** None</span></span>  
<span data-ttu-id="2b163-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="2b163-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="2b163-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2b163-115">See also</span></span>

- [<span data-ttu-id="2b163-116">Depuração</span><span class="sxs-lookup"><span data-stu-id="2b163-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="2b163-117">ISOSDacInterface Interface</span><span class="sxs-lookup"><span data-stu-id="2b163-117">ISOSDacInterface Interface</span></span>](isosdacinterface-interface.md)