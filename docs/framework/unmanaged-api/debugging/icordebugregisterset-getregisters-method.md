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
ms.openlocfilehash: 112d530c765fc74ab4ea767cb3168977d1b45f47
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138361"
---
# <a name="icordebugregistersetgetregisters-method"></a><span data-ttu-id="fccd5-102">Método ICorDebugRegisterSet::GetRegisters</span><span class="sxs-lookup"><span data-stu-id="fccd5-102">ICorDebugRegisterSet::GetRegisters Method</span></span>
<span data-ttu-id="fccd5-103">Obtém o valor de cada registro (no computador que está executando o código) que é especificado pela máscara de bits.</span><span class="sxs-lookup"><span data-stu-id="fccd5-103">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fccd5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fccd5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegisters (  
    [in] ULONG64       mask,   
    [in] ULONG32       regCount,  
    [out, size_is(regCount), length_is(regCount)]  
        CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fccd5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fccd5-105">Parameters</span></span>  
 `mask`  
 <span data-ttu-id="fccd5-106">no Uma máscara de bits que especifica quais valores de registro devem ser recuperados.</span><span class="sxs-lookup"><span data-stu-id="fccd5-106">[in] A bit mask that specifies which register values are to be retrieved.</span></span> <span data-ttu-id="fccd5-107">Cada bit corresponde a um registro.</span><span class="sxs-lookup"><span data-stu-id="fccd5-107">Each bit corresponds to a register.</span></span> <span data-ttu-id="fccd5-108">Se um bit for definido como um, o valor do registro será recuperado; caso contrário, o valor do registro não será recuperado.</span><span class="sxs-lookup"><span data-stu-id="fccd5-108">If a bit is set to one, the register's value is retrieved; otherwise, the register's value is not retrieved.</span></span>  
  
 `regCount`  
 <span data-ttu-id="fccd5-109">no O número de valores de registro a serem recuperados.</span><span class="sxs-lookup"><span data-stu-id="fccd5-109">[in] The number of register values to be retrieved.</span></span>  
  
 `regBuffer`  
 <span data-ttu-id="fccd5-110">fora Uma matriz de objetos `CORDB_REGISTER`, cada um dos quais recebe um valor de um registro.</span><span class="sxs-lookup"><span data-stu-id="fccd5-110">[out] An array of `CORDB_REGISTER` objects, each of which receives a value of a register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fccd5-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="fccd5-111">Remarks</span></span>  
 <span data-ttu-id="fccd5-112">O tamanho da matriz deve ser igual ao número de bits definido como um na máscara de bits.</span><span class="sxs-lookup"><span data-stu-id="fccd5-112">The size of the array should be equal to the number of bits set to one in the bit mask.</span></span> <span data-ttu-id="fccd5-113">O parâmetro `regCount` especifica o número de elementos no buffer que receberão os valores de registro.</span><span class="sxs-lookup"><span data-stu-id="fccd5-113">The `regCount` parameter specifies the number of elements in the buffer that will receive the register values.</span></span> <span data-ttu-id="fccd5-114">Se o valor de `regCount` for muito pequeno para o número de registros indicado pela máscara, os registros numerados mais altos serão truncados do conjunto.</span><span class="sxs-lookup"><span data-stu-id="fccd5-114">If the `regCount` value is too small for the number of registers indicated by the mask, the higher numbered registers will be truncated from the set.</span></span> <span data-ttu-id="fccd5-115">Se o valor de `regCount` for muito grande, os elementos de `regBuffer` não utilizados não serão modificados.</span><span class="sxs-lookup"><span data-stu-id="fccd5-115">If the `regCount` value is too large, the unused `regBuffer` elements will be unmodified.</span></span>  
  
 <span data-ttu-id="fccd5-116">Se a máscara de bits especificar um registro que não está disponível, `GetRegisters` retornará um valor indeterminado para esse registro.</span><span class="sxs-lookup"><span data-stu-id="fccd5-116">If the bit mask specifies a register that is unavailable, `GetRegisters` returns an indeterminate value for that register.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fccd5-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fccd5-117">Requirements</span></span>  
 <span data-ttu-id="fccd5-118">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fccd5-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fccd5-119">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fccd5-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fccd5-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fccd5-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fccd5-121">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fccd5-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fccd5-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fccd5-122">See also</span></span>

- [<span data-ttu-id="fccd5-123">Interface ICorDebugRegisterSet</span><span class="sxs-lookup"><span data-stu-id="fccd5-123">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
- [<span data-ttu-id="fccd5-124">Interface ICorDebugRegisterSet2</span><span class="sxs-lookup"><span data-stu-id="fccd5-124">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
