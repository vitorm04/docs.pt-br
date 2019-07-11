---
title: Método ICorDebugRegisterSet::GetRegisters
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.GetRegisters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::GetRegisters
helpviewer_keywords:
- GetRegisters method, ICorDebugRegisterSet interface [.NET Framework debugging]
- ICorDebugRegisterSet::GetRegisters method [.NET Framework debugging]
ms.assetid: fdf91864-48ea-4aa6-b70c-361b7a3184c7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: daee6c46c247bcd21073f779cada8c843947a949
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67747243"
---
# <a name="icordebugregistersetgetregisters-method"></a><span data-ttu-id="61dc4-102">Método ICorDebugRegisterSet::GetRegisters</span><span class="sxs-lookup"><span data-stu-id="61dc4-102">ICorDebugRegisterSet::GetRegisters Method</span></span>
<span data-ttu-id="61dc4-103">Obtém o valor de cada registro (no computador que está executando código) que é especificado pela máscara de bits.</span><span class="sxs-lookup"><span data-stu-id="61dc4-103">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61dc4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="61dc4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegisters (  
    [in] ULONG64       mask,   
    [in] ULONG32       regCount,  
    [out, size_is(regCount), length_is(regCount)]  
        CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="61dc4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="61dc4-105">Parameters</span></span>  
 `mask`  
 <span data-ttu-id="61dc4-106">[in] Uma máscara de bits que especifica quais valores devem ser recuperadas de registro.</span><span class="sxs-lookup"><span data-stu-id="61dc4-106">[in] A bit mask that specifies which register values are to be retrieved.</span></span> <span data-ttu-id="61dc4-107">Cada bit corresponde a um registro.</span><span class="sxs-lookup"><span data-stu-id="61dc4-107">Each bit corresponds to a register.</span></span> <span data-ttu-id="61dc4-108">Se um bit é definido como um, o valor do registro é recuperado; Caso contrário, o valor do registro não será recuperado.</span><span class="sxs-lookup"><span data-stu-id="61dc4-108">If a bit is set to one, the register's value is retrieved; otherwise, the register's value is not retrieved.</span></span>  
  
 `regCount`  
 <span data-ttu-id="61dc4-109">[in] O número de valores do registro a ser recuperado.</span><span class="sxs-lookup"><span data-stu-id="61dc4-109">[in] The number of register values to be retrieved.</span></span>  
  
 `regBuffer`  
 <span data-ttu-id="61dc4-110">[out] Uma matriz de `CORDB_REGISTER` objetos, cada um dos quais recebe um valor de um registro.</span><span class="sxs-lookup"><span data-stu-id="61dc4-110">[out] An array of `CORDB_REGISTER` objects, each of which receives a value of a register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="61dc4-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="61dc4-111">Remarks</span></span>  
 <span data-ttu-id="61dc4-112">O tamanho da matriz deve ser igual ao número de bits definidos para um em que a máscara de bits.</span><span class="sxs-lookup"><span data-stu-id="61dc4-112">The size of the array should be equal to the number of bits set to one in the bit mask.</span></span> <span data-ttu-id="61dc4-113">O `regCount` parâmetro especifica o número de elementos no buffer que receberá os valores do registro.</span><span class="sxs-lookup"><span data-stu-id="61dc4-113">The `regCount` parameter specifies the number of elements in the buffer that will receive the register values.</span></span> <span data-ttu-id="61dc4-114">Se o `regCount` valor for muito pequeno para o número de registros indicados pela máscara, os registros de numerada mais alta serão truncados do conjunto.</span><span class="sxs-lookup"><span data-stu-id="61dc4-114">If the `regCount` value is too small for the number of registers indicated by the mask, the higher numbered registers will be truncated from the set.</span></span> <span data-ttu-id="61dc4-115">Se o `regCount` valor é muito grande, não usada `regBuffer` elementos serão não modificados.</span><span class="sxs-lookup"><span data-stu-id="61dc4-115">If the `regCount` value is too large, the unused `regBuffer` elements will be unmodified.</span></span>  
  
 <span data-ttu-id="61dc4-116">Se a máscara de bits especifica um registro que não está disponível, `GetRegisters` retorna um valor indeterminado para que se registram.</span><span class="sxs-lookup"><span data-stu-id="61dc4-116">If the bit mask specifies a register that is unavailable, `GetRegisters` returns an indeterminate value for that register.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61dc4-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="61dc4-117">Requirements</span></span>  
 <span data-ttu-id="61dc4-118">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61dc4-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61dc4-119">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="61dc4-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="61dc4-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="61dc4-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="61dc4-121">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61dc4-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61dc4-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="61dc4-122">See also</span></span>

- [<span data-ttu-id="61dc4-123">Interface ICorDebugRegisterSet</span><span class="sxs-lookup"><span data-stu-id="61dc4-123">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
- [<span data-ttu-id="61dc4-124">Interface ICorDebugRegisterSet2</span><span class="sxs-lookup"><span data-stu-id="61dc4-124">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
