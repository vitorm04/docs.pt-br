---
title: Método ICorDebugRegisterSet2::GetRegisters
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet2.GetRegisters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet2::GetRegisters
helpviewer_keywords:
- GetRegisters method, ICorDebugRegisterSet2 interface [.NET Framework debugging]
- ICorDebugRegisterSet2::GetRegisters method [.NET Framework debugging]
ms.assetid: dbc498a8-ba3f-42f2-bdd9-b623c77a1019
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e2dc1064656f3493db78d858cf1e86db0cb83d6c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59136689"
---
# <a name="icordebugregisterset2getregisters-method"></a><span data-ttu-id="41e9a-102">Método ICorDebugRegisterSet2::GetRegisters</span><span class="sxs-lookup"><span data-stu-id="41e9a-102">ICorDebugRegisterSet2::GetRegisters Method</span></span>
<span data-ttu-id="41e9a-103">Obtém o valor de cada registro (para a plataforma na qual o código está sendo executado) que é especificado pela máscara de bits especificado.</span><span class="sxs-lookup"><span data-stu-id="41e9a-103">Gets the value of each register (for the platform on which code is currently executing) that is specified by the given bit mask.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41e9a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="41e9a-104">Syntax</span></span>  
  
```  
HRESULT GetRegisters (  
    [in] ULONG32 maskCount,  
    [in, size_is(maskCount)] BYTE mask[],  
    [in] ULONG32 regCount,  
    [out, size_is(regCount)] CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="41e9a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="41e9a-105">Parameters</span></span>  
 `maskCount`  
 <span data-ttu-id="41e9a-106">[in] O tamanho, em bytes, da `mask` matriz.</span><span class="sxs-lookup"><span data-stu-id="41e9a-106">[in] The size, in bytes, of the `mask` array.</span></span>  
  
 `mask`  
 <span data-ttu-id="41e9a-107">[in] Uma matriz de bytes, cada bit que corresponde a um registro.</span><span class="sxs-lookup"><span data-stu-id="41e9a-107">[in] An array of bytes, each bit of which corresponds to a register.</span></span> <span data-ttu-id="41e9a-108">Se o bit for 1, o valor do registro correspondentes será recuperado.</span><span class="sxs-lookup"><span data-stu-id="41e9a-108">If the bit is 1, the corresponding register's value will be retrieved.</span></span>  
  
 `regCount`  
 <span data-ttu-id="41e9a-109">[in] O número de valores do registro a ser recuperado.</span><span class="sxs-lookup"><span data-stu-id="41e9a-109">[in] The number of register values to be retrieved.</span></span>  
  
 `regBuffer`  
 <span data-ttu-id="41e9a-110">[out] Uma matriz de `CORDB_REGISTER` objetos, cada um dos quais recebe o valor de um registro.</span><span class="sxs-lookup"><span data-stu-id="41e9a-110">[out] An array of `CORDB_REGISTER` objects, each of which receives the value of a register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="41e9a-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="41e9a-111">Remarks</span></span>  
 <span data-ttu-id="41e9a-112">O `GetRegisters` método retorna uma matriz de valores dos registros que são especificados pela máscara.</span><span class="sxs-lookup"><span data-stu-id="41e9a-112">The `GetRegisters` method returns an array of values from the registers that are specified by the mask.</span></span> <span data-ttu-id="41e9a-113">A matriz não contém valores de registradores cujo bit da máscara não está definida.</span><span class="sxs-lookup"><span data-stu-id="41e9a-113">The array does not contain values of registers whose mask bit is not set.</span></span> <span data-ttu-id="41e9a-114">Portanto, o tamanho do `regBuffer` matriz deve ser igual ao número de 1 na máscara.</span><span class="sxs-lookup"><span data-stu-id="41e9a-114">Thus, the size of the `regBuffer` array must be equal to the number of 1's in the mask.</span></span> <span data-ttu-id="41e9a-115">Se o valor de `regCount` é muito pequeno para o número de registros indicados pela máscara, os valores dos registros numerados mais alta será truncado do conjunto.</span><span class="sxs-lookup"><span data-stu-id="41e9a-115">If the value of `regCount` is too small for the number of registers indicated by the mask, the values of the higher numbered registers will be truncated from the set.</span></span> <span data-ttu-id="41e9a-116">Se `regCount` é muito grande, não usada `regBuffer` elementos serão não modificados.</span><span class="sxs-lookup"><span data-stu-id="41e9a-116">If `regCount` is too large, the unused `regBuffer` elements will be unmodified.</span></span>  
  
 <span data-ttu-id="41e9a-117">Se um registro não está disponível é indicado pela máscara, um valor indeterminado será retornado para que se registram.</span><span class="sxs-lookup"><span data-stu-id="41e9a-117">If an unavailable register is indicated by the mask, an indeterminate value will be returned for that register.</span></span>  
  
 <span data-ttu-id="41e9a-118">O `ICorDebugRegisterSet2::GetRegisters` método é necessário para plataformas que têm mais de 64 registros.</span><span class="sxs-lookup"><span data-stu-id="41e9a-118">The `ICorDebugRegisterSet2::GetRegisters` method is necessary for platforms which have more than 64 registers.</span></span> <span data-ttu-id="41e9a-119">Por exemplo, IA64 tem 128 registros de uso geral e 128 registros de ponto flutuante, portanto, você precisará de mais de 64 bits na máscara de bits.</span><span class="sxs-lookup"><span data-stu-id="41e9a-119">For example, IA64 has 128 general purpose registers and 128 floating-point registers, so you need more than 64-bits in the bit mask.</span></span>  
  
 <span data-ttu-id="41e9a-120">Se você não tiver mais de 64 registros, como é o caso em plataformas como x86, o `GetRegisters` método traduz, na verdade, apenas os bytes na `mask` matriz de bytes em uma `ULONG64` e, em seguida, chama o [ICorDebugRegisterSet:: GetRegisters](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregisters-method.md) método, que usa o `ULONG64` máscara.</span><span class="sxs-lookup"><span data-stu-id="41e9a-120">If you do not have more than 64 registers, as is the case on platforms such as x86, the `GetRegisters` method actually just translates the bytes in the `mask` byte array into a `ULONG64` and then calls the [ICorDebugRegisterSet::GetRegisters](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregisters-method.md) method, which takes the `ULONG64` mask.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41e9a-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="41e9a-121">Requirements</span></span>  
 <span data-ttu-id="41e9a-122">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41e9a-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41e9a-123">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="41e9a-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="41e9a-124">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="41e9a-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="41e9a-125">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41e9a-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41e9a-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="41e9a-126">See also</span></span>

- [<span data-ttu-id="41e9a-127">Interface ICorDebugRegisterSet2</span><span class="sxs-lookup"><span data-stu-id="41e9a-127">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
- [<span data-ttu-id="41e9a-128">Interface ICorDebugRegisterSet</span><span class="sxs-lookup"><span data-stu-id="41e9a-128">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
