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
ms.openlocfilehash: 82c4531ac16e8b4bf7ac45bc01eb7128b9507ab5
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57358529"
---
# <a name="isosdacinterfacegetmethoddescptrfromip-method"></a><span data-ttu-id="b8baa-102">Método ISOSDacInterface::GetMethodDescPtrFromIP</span><span class="sxs-lookup"><span data-stu-id="b8baa-102">ISOSDacInterface::GetMethodDescPtrFromIP Method</span></span>

<span data-ttu-id="b8baa-103">Recupera o ponteiro do MethodDesc correspondente o método que contém o endereço de determinada instrução nativos.</span><span class="sxs-lookup"><span data-stu-id="b8baa-103">Retrieves the pointer of the MethodDesc corresponding the method containing the given native instruction address.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="b8baa-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b8baa-104">Syntax</span></span>

```
HRESULT GetMethodDescPtrFromIP(
    CLRDATA_ADDRESS ip,
    CLRDATA_ADDRESS * ppMD
);
```

## <a name="parameters"></a><span data-ttu-id="b8baa-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b8baa-105">Parameters</span></span>

`ip`\
<span data-ttu-id="b8baa-106">[in] Um endereço dentro do método em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="b8baa-106">[in] An address within the method at runtime.</span></span>

`ppMD`\
<span data-ttu-id="b8baa-107">[out] O endereço do `MethodDesc` para o método específico.</span><span class="sxs-lookup"><span data-stu-id="b8baa-107">[out] The address of the `MethodDesc` for the particular method.</span></span>

## <a name="remarks"></a><span data-ttu-id="b8baa-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="b8baa-108">Remarks</span></span>

<span data-ttu-id="b8baa-109">O método fornecido faz parte dos [ `ISOSDacInterface` interface](isosdacinterface-interface.md) e corresponde ao slot de 21 da tabela de método virtual.</span><span class="sxs-lookup"><span data-stu-id="b8baa-109">The provided method is part of the [`ISOSDacInterface` interface](isosdacinterface-interface.md) and corresponds to the 21st slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="b8baa-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b8baa-110">Requirements</span></span>

<span data-ttu-id="b8baa-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8baa-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="b8baa-112">**Cabeçalho:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="b8baa-112">**Header:** None</span></span>  
<span data-ttu-id="b8baa-113">**Biblioteca:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="b8baa-113">**Library:** None</span></span>  
<span data-ttu-id="b8baa-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b8baa-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="b8baa-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b8baa-115">See also</span></span>

- [<span data-ttu-id="b8baa-116">Depuração</span><span class="sxs-lookup"><span data-stu-id="b8baa-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="b8baa-117">ISOSDacInterface Interface</span><span class="sxs-lookup"><span data-stu-id="b8baa-117">ISOSDacInterface Interface</span></span>](isosdacinterface-interface.md)