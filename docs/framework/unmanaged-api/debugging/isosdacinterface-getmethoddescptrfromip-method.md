---
title: Método ISOSDacInterface::GetMethodDescPtrFromIP
ms.date: 02/01/2019
api.name:
- ISOSDacInterface::GetMethodDescPtrFromIP Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- ISOSDacInterface::GetMethodDescPtrFromIP Method
helpviewer.keywords:
- ISOSDacInterface::GetMethodDescPtrFromIP Method [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: 74853733b1fb7f023d9f192d3e862dbf6875ecda
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55828580"
---
# <a name="isosdacinterfacegetmethoddescptrfromip-method"></a><span data-ttu-id="a3362-102">Método ISOSDacInterface::GetMethodDescPtrFromIP</span><span class="sxs-lookup"><span data-stu-id="a3362-102">ISOSDacInterface::GetMethodDescPtrFromIP Method</span></span>

<span data-ttu-id="a3362-103">Recupera o ponteiro do MethodDesc correspondente o método que contém o endereço de determinada instrução nativos.</span><span class="sxs-lookup"><span data-stu-id="a3362-103">Retrieves the pointer of the MethodDesc corresponding the method containing the given native instruction address.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="a3362-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a3362-104">Syntax</span></span>

```
HRESULT GetMethodDescPtrFromIP(
    CLRDATA_ADDRESS ip,
    CLRDATA_ADDRESS * ppMD
);
```

### <a name="parameters"></a><span data-ttu-id="a3362-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a3362-105">Parameters</span></span>

<span data-ttu-id="a3362-106">`ip` [in] Um endereço dentro do método em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="a3362-106">`ip` [in] An address within the method at runtime.</span></span>

<span data-ttu-id="a3362-107">`ppMD` [out] O endereço do `MethodDesc` para o método específico.</span><span class="sxs-lookup"><span data-stu-id="a3362-107">`ppMD` [out] The address of the `MethodDesc` for the particular method.</span></span>

## <a name="remarks"></a><span data-ttu-id="a3362-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="a3362-108">Remarks</span></span>

<span data-ttu-id="a3362-109">O método fornecido faz parte dos [ `ISOSDacInterface` interface](isosdacinterface-interface.md) e corresponde ao slot de 21 da tabela de método virtual.</span><span class="sxs-lookup"><span data-stu-id="a3362-109">The provided method is part of the [`ISOSDacInterface` interface](isosdacinterface-interface.md) and corresponds to the 21st slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="a3362-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a3362-110">Requirements</span></span>

<span data-ttu-id="a3362-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a3362-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="a3362-112">**Cabeçalho:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="a3362-112">**Header:** None</span></span>  
<span data-ttu-id="a3362-113">**Biblioteca:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="a3362-113">**Library:** None</span></span>  
<span data-ttu-id="a3362-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a3362-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="a3362-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a3362-115">See also</span></span>

- [<span data-ttu-id="a3362-116">Depuração</span><span class="sxs-lookup"><span data-stu-id="a3362-116">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="a3362-117">ISOSDacInterface Interface</span><span class="sxs-lookup"><span data-stu-id="a3362-117">ISOSDacInterface Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/isosdacinterface-interface.md)
