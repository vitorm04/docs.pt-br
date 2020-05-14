---
title: 'Método ISOSDacInterface:: GetMethodDescPtrFromIP'
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
ms.openlocfilehash: 0c8d91c11205e06857b4a6e7edfedcd087270d00
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396935"
---
# <a name="isosdacinterfacegetmethoddescptrfromip-method"></a><span data-ttu-id="f4c7f-102">Método ISOSDacInterface:: GetMethodDescPtrFromIP</span><span class="sxs-lookup"><span data-stu-id="f4c7f-102">ISOSDacInterface::GetMethodDescPtrFromIP Method</span></span>

<span data-ttu-id="f4c7f-103">Recupera o ponteiro do MethodDesc correspondente ao método que contém o endereço de instrução nativo fornecido.</span><span class="sxs-lookup"><span data-stu-id="f4c7f-103">Retrieves the pointer of the MethodDesc corresponding the method containing the given native instruction address.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="f4c7f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f4c7f-104">Syntax</span></span>

```cpp
HRESULT GetMethodDescPtrFromIP(
    CLRDATA_ADDRESS ip,
    CLRDATA_ADDRESS * ppMD
);
```

## <a name="parameters"></a><span data-ttu-id="f4c7f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f4c7f-105">Parameters</span></span>

`ip`\
<span data-ttu-id="f4c7f-106">no Um endereço dentro do método em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="f4c7f-106">[in] An address within the method at runtime.</span></span>

`ppMD`\
<span data-ttu-id="f4c7f-107">fora O endereço do `MethodDesc` para o método específico.</span><span class="sxs-lookup"><span data-stu-id="f4c7f-107">[out] The address of the `MethodDesc` for the particular method.</span></span>

## <a name="remarks"></a><span data-ttu-id="f4c7f-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="f4c7f-108">Remarks</span></span>

<span data-ttu-id="f4c7f-109">O método fornecido faz parte da [ `ISOSDacInterface` interface](isosdacinterface-interface.md) e corresponde ao slot 22 da tabela de métodos virtuais.</span><span class="sxs-lookup"><span data-stu-id="f4c7f-109">The provided method is part of the [`ISOSDacInterface` interface](isosdacinterface-interface.md) and corresponds to the 22nd slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="f4c7f-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f4c7f-110">Requirements</span></span>

<span data-ttu-id="f4c7f-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f4c7f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="f4c7f-112">**Cabeçalho:** None</span><span class="sxs-lookup"><span data-stu-id="f4c7f-112">**Header:** None</span></span>  
<span data-ttu-id="f4c7f-113">**Biblioteca:** None</span><span class="sxs-lookup"><span data-stu-id="f4c7f-113">**Library:** None</span></span>  
<span data-ttu-id="f4c7f-114">**.NET Framework versões:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f4c7f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="f4c7f-115">Veja também</span><span class="sxs-lookup"><span data-stu-id="f4c7f-115">See also</span></span>

- [<span data-ttu-id="f4c7f-116">Depuração</span><span class="sxs-lookup"><span data-stu-id="f4c7f-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="f4c7f-117">Interface ISOSDacInterface</span><span class="sxs-lookup"><span data-stu-id="f4c7f-117">ISOSDacInterface Interface</span></span>](isosdacinterface-interface.md)
