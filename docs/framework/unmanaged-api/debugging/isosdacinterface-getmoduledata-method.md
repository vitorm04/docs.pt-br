---
title: 'Método ISOSDacInterface:: GetModuleData'
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
ms.openlocfilehash: 14e0eb812c84a0042150345d039451adf178caf1
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396918"
---
# <a name="isosdacinterfacegetmoduledata-method"></a><span data-ttu-id="88c0e-102">Método ISOSDacInterface:: GetModuleData</span><span class="sxs-lookup"><span data-stu-id="88c0e-102">ISOSDacInterface::GetModuleData Method</span></span>

<span data-ttu-id="88c0e-103">Busca os dados correspondentes ao módulo carregado em um determinado endereço.</span><span class="sxs-lookup"><span data-stu-id="88c0e-103">Fetches the data corresponding to the module loaded at a given address.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="88c0e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="88c0e-104">Syntax</span></span>

```cpp
HRESULT GetModuleData(
    CLRDATA_ADDRESS moduleAddr,
    DacpModuleData *data
);
```

## <a name="parameters"></a><span data-ttu-id="88c0e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="88c0e-105">Parameters</span></span>

`moduleAddr`\
<span data-ttu-id="88c0e-106">no O endereço do módulo para o qual recuperar informações.</span><span class="sxs-lookup"><span data-stu-id="88c0e-106">[in] The address of the module to retrieve information for.</span></span>

`data`\
<span data-ttu-id="88c0e-107">fora A [estrutura DacpModuleData](dacpmoduledata-structure.md) para armazenar as informações do módulo carregado.</span><span class="sxs-lookup"><span data-stu-id="88c0e-107">[out] The [DacpModuleData structure](dacpmoduledata-structure.md) to hold the information of the loaded module.</span></span>

## <a name="remarks"></a><span data-ttu-id="88c0e-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="88c0e-108">Remarks</span></span>

<span data-ttu-id="88c0e-109">O método fornecido faz parte da `ISOSDacInterface` interface e corresponde ao slot 14 da tabela de métodos virtuais.</span><span class="sxs-lookup"><span data-stu-id="88c0e-109">The provided method is part of the `ISOSDacInterface` interface and corresponds to the 14th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="88c0e-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="88c0e-110">Requirements</span></span>

<span data-ttu-id="88c0e-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="88c0e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="88c0e-112">**Cabeçalho:** None</span><span class="sxs-lookup"><span data-stu-id="88c0e-112">**Header:** None</span></span>  
<span data-ttu-id="88c0e-113">**Biblioteca:** None</span><span class="sxs-lookup"><span data-stu-id="88c0e-113">**Library:** None</span></span>  
<span data-ttu-id="88c0e-114">**.NET Framework versões:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="88c0e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="88c0e-115">Veja também</span><span class="sxs-lookup"><span data-stu-id="88c0e-115">See also</span></span>

- [<span data-ttu-id="88c0e-116">Depuração</span><span class="sxs-lookup"><span data-stu-id="88c0e-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="88c0e-117">Interface ISOSDacInterface</span><span class="sxs-lookup"><span data-stu-id="88c0e-117">ISOSDacInterface Interface</span></span>](isosdacinterface-interface.md)
