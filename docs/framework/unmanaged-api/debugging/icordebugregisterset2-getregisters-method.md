---
title: "Método ICorDebugRegisterSet2::GetRegisters"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugRegisterSet2.GetRegisters
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugRegisterSet2::GetRegisters
helpviewer_keywords:
- GetRegisters method, ICorDebugRegisterSet2 interface [.NET Framework debugging]
- ICorDebugRegisterSet2::GetRegisters method [.NET Framework debugging]
ms.assetid: dbc498a8-ba3f-42f2-bdd9-b623c77a1019
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 830fd9b4c04d536f64ca5b15e513c9f5f049f059
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugregisterset2getregisters-method"></a><span data-ttu-id="3d8e9-102">Método ICorDebugRegisterSet2::GetRegisters</span><span class="sxs-lookup"><span data-stu-id="3d8e9-102">ICorDebugRegisterSet2::GetRegisters Method</span></span>
<span data-ttu-id="3d8e9-103">Obtém o valor de cada registro (para a plataforma na qual o código está sendo executado) que é especificado, a máscara de bits especificado.</span><span class="sxs-lookup"><span data-stu-id="3d8e9-103">Gets the value of each register (for the platform on which code is currently executing) that is specified by the given bit mask.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d8e9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3d8e9-104">Syntax</span></span>  
  
```  
HRESULT GetRegisters (  
    [in] ULONG32 maskCount,  
    [in, size_is(maskCount)] BYTE mask[],  
    [in] ULONG32 regCount,  
    [out, size_is(regCount)] CORDB_REGISTER regBuffer[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3d8e9-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3d8e9-105">Parameters</span></span>  
 `maskCount`  
 <span data-ttu-id="3d8e9-106">[in] O tamanho, em bytes, do `mask` matriz.</span><span class="sxs-lookup"><span data-stu-id="3d8e9-106">[in] The size, in bytes, of the `mask` array.</span></span>  
  
 `mask`  
 <span data-ttu-id="3d8e9-107">[in] Uma matriz de bytes, cada bit que corresponde a um registro.</span><span class="sxs-lookup"><span data-stu-id="3d8e9-107">[in] An array of bytes, each bit of which corresponds to a register.</span></span> <span data-ttu-id="3d8e9-108">Se o bit for 1, o valor do registro correspondente será recuperada.</span><span class="sxs-lookup"><span data-stu-id="3d8e9-108">If the bit is 1, the corresponding register's value will be retrieved.</span></span>  
  
 `regCount`  
 <span data-ttu-id="3d8e9-109">[in] O número de valores do registro a ser recuperado.</span><span class="sxs-lookup"><span data-stu-id="3d8e9-109">[in] The number of register values to be retrieved.</span></span>  
  
 `regBuffer`  
 <span data-ttu-id="3d8e9-110">[out] Uma matriz de `CORDB_REGISTER` objetos, cada um dos quais recebe o valor de um registro.</span><span class="sxs-lookup"><span data-stu-id="3d8e9-110">[out] An array of `CORDB_REGISTER` objects, each of which receives the value of a register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3d8e9-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="3d8e9-111">Remarks</span></span>  
 <span data-ttu-id="3d8e9-112">O `GetRegisters` método retorna uma matriz de valores de registros que são especificados pela máscara.</span><span class="sxs-lookup"><span data-stu-id="3d8e9-112">The `GetRegisters` method returns an array of values from the registers that are specified by the mask.</span></span> <span data-ttu-id="3d8e9-113">A matriz não contém valores de registros cujo bit da máscara não está definido.</span><span class="sxs-lookup"><span data-stu-id="3d8e9-113">The array does not contain values of registers whose mask bit is not set.</span></span> <span data-ttu-id="3d8e9-114">Portanto, o tamanho do `regBuffer` matriz deve ser igual ao número de 1 a máscara.</span><span class="sxs-lookup"><span data-stu-id="3d8e9-114">Thus, the size of the `regBuffer` array must be equal to the number of 1's in the mask.</span></span> <span data-ttu-id="3d8e9-115">Se o valor de `regCount` é muito pequeno para o número de registros indicado pela máscara, os valores dos registros numerados mais altos será truncado do conjunto.</span><span class="sxs-lookup"><span data-stu-id="3d8e9-115">If the value of `regCount` is too small for the number of registers indicated by the mask, the values of the higher numbered registers will be truncated from the set.</span></span> <span data-ttu-id="3d8e9-116">Se `regCount` é muito grande, não usada `regBuffer` elementos serão modificados.</span><span class="sxs-lookup"><span data-stu-id="3d8e9-116">If `regCount` is too large, the unused `regBuffer` elements will be unmodified.</span></span>  
  
 <span data-ttu-id="3d8e9-117">Se um registro não disponível é indicado pela máscara, um valor indeterminado será retornado para o registrador.</span><span class="sxs-lookup"><span data-stu-id="3d8e9-117">If an unavailable register is indicated by the mask, an indeterminate value will be returned for that register.</span></span>  
  
 <span data-ttu-id="3d8e9-118">O `ICorDebugRegisterSet2::GetRegisters` método é necessário para as plataformas que têm mais de 64 registros.</span><span class="sxs-lookup"><span data-stu-id="3d8e9-118">The `ICorDebugRegisterSet2::GetRegisters` method is necessary for platforms which have more than 64 registers.</span></span> <span data-ttu-id="3d8e9-119">Por exemplo, IA64 tem 128 registros de uso geral e 128 registros de ponto flutuantes, portanto, você precisa de mais de 64 bits na máscara de bits.</span><span class="sxs-lookup"><span data-stu-id="3d8e9-119">For example, IA64 has 128 general purpose registers and 128 floating-point registers, so you need more than 64-bits in the bit mask.</span></span>  
  
 <span data-ttu-id="3d8e9-120">Se você não tem mais de 64 registros, como é o caso em plataformas, como x86, o `GetRegisters` método converte apenas os bytes no `mask` matriz de bytes em uma `ULONG64` e, em seguida, chama o [ICorDebugRegisterSet:: GetRegisters](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregisters-method.md) método, que usa o `ULONG64` máscara.</span><span class="sxs-lookup"><span data-stu-id="3d8e9-120">If you do not have more than 64 registers, as is the case on platforms such as x86, the `GetRegisters` method actually just translates the bytes in the `mask` byte array into a `ULONG64` and then calls the [ICorDebugRegisterSet::GetRegisters](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregisters-method.md) method, which takes the `ULONG64` mask.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d8e9-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3d8e9-121">Requirements</span></span>  
 <span data-ttu-id="3d8e9-122">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3d8e9-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d8e9-123">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3d8e9-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3d8e9-124">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3d8e9-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3d8e9-125">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d8e9-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d8e9-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3d8e9-126">See Also</span></span>  
 [<span data-ttu-id="3d8e9-127">Interface ICorDebugRegisterSet2</span><span class="sxs-lookup"><span data-stu-id="3d8e9-127">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)  
 [<span data-ttu-id="3d8e9-128">Interface ICorDebugRegisterSet</span><span class="sxs-lookup"><span data-stu-id="3d8e9-128">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
