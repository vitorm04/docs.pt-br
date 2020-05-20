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
ms.openlocfilehash: 71b9d59621efb547713cb4a6c9df7a7142f4a677
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615183"
---
# <a name="icordebugregisterset2getregisters-method"></a><span data-ttu-id="e1164-102">Método ICorDebugRegisterSet2:: GetRegisters</span><span class="sxs-lookup"><span data-stu-id="e1164-102">ICorDebugRegisterSet2::GetRegisters method</span></span>

<span data-ttu-id="e1164-103">Obtém o valor de cada registro (para a plataforma em que o código está em execução no momento) que é especificado pela máscara de bits fornecida.</span><span class="sxs-lookup"><span data-stu-id="e1164-103">Gets the value of each register (for the platform on which code is currently executing) that is specified by the given bit mask.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1164-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e1164-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegisters (  
    [in] ULONG32 maskCount,  
    [in, size_is(maskCount)] BYTE mask[],  
    [in] ULONG32 regCount,  
    [out, size_is(regCount)] CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e1164-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e1164-105">Parameters</span></span>

 `maskCount`  
 <span data-ttu-id="e1164-106">no O tamanho, em bytes, da `mask` matriz.</span><span class="sxs-lookup"><span data-stu-id="e1164-106">[in] The size, in bytes, of the `mask` array.</span></span>  
  
 `mask`  
 <span data-ttu-id="e1164-107">no Uma matriz de bytes, cada bit corresponde a um registro.</span><span class="sxs-lookup"><span data-stu-id="e1164-107">[in] An array of bytes, each bit of which corresponds to a register.</span></span> <span data-ttu-id="e1164-108">Se o bit for 1, o valor do registro correspondente será recuperado.</span><span class="sxs-lookup"><span data-stu-id="e1164-108">If the bit is 1, the corresponding register's value will be retrieved.</span></span>  
  
 `regCount`  
 <span data-ttu-id="e1164-109">no O número de valores de registro a serem recuperados.</span><span class="sxs-lookup"><span data-stu-id="e1164-109">[in] The number of register values to be retrieved.</span></span>  
  
 `regBuffer`  
 <span data-ttu-id="e1164-110">fora Uma matriz de `CORDB_REGISTER` objetos, cada um deles recebe o valor de um registro.</span><span class="sxs-lookup"><span data-stu-id="e1164-110">[out] An array of `CORDB_REGISTER` objects, each of which receives the value of a register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e1164-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="e1164-111">Remarks</span></span>

 <span data-ttu-id="e1164-112">O `GetRegisters` método retorna uma matriz de valores dos registros que são especificados pela máscara.</span><span class="sxs-lookup"><span data-stu-id="e1164-112">The `GetRegisters` method returns an array of values from the registers that are specified by the mask.</span></span> <span data-ttu-id="e1164-113">A matriz não contém valores de registros cujo bit de máscara não esteja definido.</span><span class="sxs-lookup"><span data-stu-id="e1164-113">The array does not contain values of registers whose mask bit is not set.</span></span> <span data-ttu-id="e1164-114">Portanto, o tamanho da `regBuffer` matriz deve ser igual ao número de 1 na máscara.</span><span class="sxs-lookup"><span data-stu-id="e1164-114">Thus, the size of the `regBuffer` array must be equal to the number of 1's in the mask.</span></span> <span data-ttu-id="e1164-115">Se o valor de `regCount` for muito pequeno para o número de registros indicado pela máscara, os valores dos registros numerados mais altos serão truncados do conjunto.</span><span class="sxs-lookup"><span data-stu-id="e1164-115">If the value of `regCount` is too small for the number of registers indicated by the mask, the values of the higher numbered registers will be truncated from the set.</span></span> <span data-ttu-id="e1164-116">Se `regCount` for muito grande, os elementos não utilizados não `regBuffer` serão modificados.</span><span class="sxs-lookup"><span data-stu-id="e1164-116">If `regCount` is too large, the unused `regBuffer` elements will be unmodified.</span></span>  
  
 <span data-ttu-id="e1164-117">Se um registro indisponível for indicado pela máscara, um valor indeterminado será retornado para esse registro.</span><span class="sxs-lookup"><span data-stu-id="e1164-117">If an unavailable register is indicated by the mask, an indeterminate value will be returned for that register.</span></span>  
  
 <span data-ttu-id="e1164-118">O `ICorDebugRegisterSet2::GetRegisters` método é necessário para plataformas que têm mais de 64 registros.</span><span class="sxs-lookup"><span data-stu-id="e1164-118">The `ICorDebugRegisterSet2::GetRegisters` method is necessary for platforms that have more than 64 registers.</span></span> <span data-ttu-id="e1164-119">Por exemplo, IA64 tem 128 registros de uso geral e 128 registros de ponto flutuante, portanto, você precisa de mais de 64 bits na máscara de bits.</span><span class="sxs-lookup"><span data-stu-id="e1164-119">For example, IA64 has 128 general purpose registers and 128 floating-point registers, so you need more than 64 bits in the bit mask.</span></span>  
  
 <span data-ttu-id="e1164-120">Se você não tiver mais de 64 registros, como é o caso em plataformas como x86, o `GetRegisters` método apenas converterá os bytes na `mask` matriz de bytes em um `ULONG64` e, em seguida, chamará o método [ICorDebugRegisterSet:: GetRegisters](icordebugregisterset-getregisters-method.md) , que usa a `ULONG64` máscara.</span><span class="sxs-lookup"><span data-stu-id="e1164-120">If you don't have more than 64 registers, as is the case on platforms such as x86, the `GetRegisters` method just translates the bytes in the `mask` byte array into a `ULONG64` and then calls the [ICorDebugRegisterSet::GetRegisters](icordebugregisterset-getregisters-method.md) method, which takes the `ULONG64` mask.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1164-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e1164-121">Requirements</span></span>

 <span data-ttu-id="e1164-122">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1164-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1164-123">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e1164-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e1164-124">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e1164-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e1164-125">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1164-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1164-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="e1164-126">See also</span></span>

- [<span data-ttu-id="e1164-127">Interface ICorDebugRegisterSet2</span><span class="sxs-lookup"><span data-stu-id="e1164-127">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
- [<span data-ttu-id="e1164-128">Interface ICorDebugRegisterSet</span><span class="sxs-lookup"><span data-stu-id="e1164-128">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
