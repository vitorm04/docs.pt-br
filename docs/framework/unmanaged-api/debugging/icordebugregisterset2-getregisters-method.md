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
ms.openlocfilehash: b7a356d80d63fae65191bbf4fc0a23d7e02004c9
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378226"
---
# <a name="icordebugregisterset2getregisters-method"></a><span data-ttu-id="c9dfe-102">Método ICorDebugRegisterSet2::GetRegisters</span><span class="sxs-lookup"><span data-stu-id="c9dfe-102">ICorDebugRegisterSet2::GetRegisters Method</span></span>
<span data-ttu-id="c9dfe-103">Obtém o valor de cada registro (para a plataforma em que o código está em execução no momento) que é especificado pela máscara de bits fornecida.</span><span class="sxs-lookup"><span data-stu-id="c9dfe-103">Gets the value of each register (for the platform on which code is currently executing) that is specified by the given bit mask.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9dfe-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c9dfe-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegisters (  
    [in] ULONG32 maskCount,  
    [in, size_is(maskCount)] BYTE mask[],  
    [in] ULONG32 regCount,  
    [out, size_is(regCount)] CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c9dfe-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c9dfe-105">Parameters</span></span>  
 `maskCount`  
 <span data-ttu-id="c9dfe-106">no O tamanho, em bytes, da `mask` matriz.</span><span class="sxs-lookup"><span data-stu-id="c9dfe-106">[in] The size, in bytes, of the `mask` array.</span></span>  
  
 `mask`  
 <span data-ttu-id="c9dfe-107">no Uma matriz de bytes, cada bit corresponde a um registro.</span><span class="sxs-lookup"><span data-stu-id="c9dfe-107">[in] An array of bytes, each bit of which corresponds to a register.</span></span> <span data-ttu-id="c9dfe-108">Se o bit for 1, o valor do registro correspondente será recuperado.</span><span class="sxs-lookup"><span data-stu-id="c9dfe-108">If the bit is 1, the corresponding register's value will be retrieved.</span></span>  
  
 `regCount`  
 <span data-ttu-id="c9dfe-109">no O número de valores de registro a serem recuperados.</span><span class="sxs-lookup"><span data-stu-id="c9dfe-109">[in] The number of register values to be retrieved.</span></span>  
  
 `regBuffer`  
 <span data-ttu-id="c9dfe-110">fora Uma matriz de `CORDB_REGISTER` objetos, cada um deles recebe o valor de um registro.</span><span class="sxs-lookup"><span data-stu-id="c9dfe-110">[out] An array of `CORDB_REGISTER` objects, each of which receives the value of a register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c9dfe-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="c9dfe-111">Remarks</span></span>  
 <span data-ttu-id="c9dfe-112">O `GetRegisters` método retorna uma matriz de valores dos registros que são especificados pela máscara.</span><span class="sxs-lookup"><span data-stu-id="c9dfe-112">The `GetRegisters` method returns an array of values from the registers that are specified by the mask.</span></span> <span data-ttu-id="c9dfe-113">A matriz não contém valores de registros cujo bit de máscara não esteja definido.</span><span class="sxs-lookup"><span data-stu-id="c9dfe-113">The array does not contain values of registers whose mask bit is not set.</span></span> <span data-ttu-id="c9dfe-114">Portanto, o tamanho da `regBuffer` matriz deve ser igual ao número de 1 na máscara.</span><span class="sxs-lookup"><span data-stu-id="c9dfe-114">Thus, the size of the `regBuffer` array must be equal to the number of 1's in the mask.</span></span> <span data-ttu-id="c9dfe-115">Se o valor de `regCount` for muito pequeno para o número de registros indicado pela máscara, os valores dos registros numerados mais altos serão truncados do conjunto.</span><span class="sxs-lookup"><span data-stu-id="c9dfe-115">If the value of `regCount` is too small for the number of registers indicated by the mask, the values of the higher numbered registers will be truncated from the set.</span></span> <span data-ttu-id="c9dfe-116">Se `regCount` for muito grande, os elementos não utilizados não `regBuffer` serão modificados.</span><span class="sxs-lookup"><span data-stu-id="c9dfe-116">If `regCount` is too large, the unused `regBuffer` elements will be unmodified.</span></span>  
  
 <span data-ttu-id="c9dfe-117">Se um registro indisponível for indicado pela máscara, um valor indeterminado será retornado para esse registro.</span><span class="sxs-lookup"><span data-stu-id="c9dfe-117">If an unavailable register is indicated by the mask, an indeterminate value will be returned for that register.</span></span>  
  
 <span data-ttu-id="c9dfe-118">O `ICorDebugRegisterSet2::GetRegisters` método é necessário para plataformas que têm mais de 64 registros.</span><span class="sxs-lookup"><span data-stu-id="c9dfe-118">The `ICorDebugRegisterSet2::GetRegisters` method is necessary for platforms which have more than 64 registers.</span></span> <span data-ttu-id="c9dfe-119">Por exemplo, IA64 tem 128 registros de uso geral e 128 registros de ponto flutuante, portanto, você precisa de mais de 64 bits na máscara de bits.</span><span class="sxs-lookup"><span data-stu-id="c9dfe-119">For example, IA64 has 128 general purpose registers and 128 floating-point registers, so you need more than 64-bits in the bit mask.</span></span>  
  
 <span data-ttu-id="c9dfe-120">Se você não tiver mais de 64 registros, como é o caso em plataformas como o x86, o `GetRegisters` método, na verdade, converte os bytes na matriz de `mask` bytes em um `ULONG64` e, em seguida, chama o método [ICorDebugRegisterSet:: GetRegisters](icordebugregisterset-getregisters-method.md) , que usa a `ULONG64` máscara.</span><span class="sxs-lookup"><span data-stu-id="c9dfe-120">If you do not have more than 64 registers, as is the case on platforms such as x86, the `GetRegisters` method actually just translates the bytes in the `mask` byte array into a `ULONG64` and then calls the [ICorDebugRegisterSet::GetRegisters](icordebugregisterset-getregisters-method.md) method, which takes the `ULONG64` mask.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9dfe-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c9dfe-121">Requirements</span></span>  
 <span data-ttu-id="c9dfe-122">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9dfe-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9dfe-123">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c9dfe-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c9dfe-124">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c9dfe-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c9dfe-125">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9dfe-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9dfe-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="c9dfe-126">See also</span></span>

- [<span data-ttu-id="c9dfe-127">Interface ICorDebugRegisterSet2</span><span class="sxs-lookup"><span data-stu-id="c9dfe-127">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
- [<span data-ttu-id="c9dfe-128">Interface ICorDebugRegisterSet</span><span class="sxs-lookup"><span data-stu-id="c9dfe-128">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
