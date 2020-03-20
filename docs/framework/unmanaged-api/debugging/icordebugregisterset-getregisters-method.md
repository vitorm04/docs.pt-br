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
ms.openlocfilehash: 32e899622b9c649a08e3bca1b6645f70dcbcbb19
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178539"
---
# <a name="icordebugregistersetgetregisters-method"></a><span data-ttu-id="bdc00-102">Método ICorDebugRegisterSet::GetRegisters</span><span class="sxs-lookup"><span data-stu-id="bdc00-102">ICorDebugRegisterSet::GetRegisters Method</span></span>
<span data-ttu-id="bdc00-103">Obtém o valor de cada registro (no computador que está executando o código) que é especificado pela máscara de bit.</span><span class="sxs-lookup"><span data-stu-id="bdc00-103">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bdc00-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bdc00-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegisters (  
    [in] ULONG64       mask,
    [in] ULONG32       regCount,  
    [out, size_is(regCount), length_is(regCount)]  
        CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bdc00-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="bdc00-105">Parameters</span></span>  
 `mask`  
 <span data-ttu-id="bdc00-106">[em] Uma máscara de bit que especifica quais valores de registro devem ser recuperados.</span><span class="sxs-lookup"><span data-stu-id="bdc00-106">[in] A bit mask that specifies which register values are to be retrieved.</span></span> <span data-ttu-id="bdc00-107">Cada bit corresponde a um registro.</span><span class="sxs-lookup"><span data-stu-id="bdc00-107">Each bit corresponds to a register.</span></span> <span data-ttu-id="bdc00-108">Se um bit for definido como um, o valor do registro será recuperado; caso contrário, o valor do registro não é recuperado.</span><span class="sxs-lookup"><span data-stu-id="bdc00-108">If a bit is set to one, the register's value is retrieved; otherwise, the register's value is not retrieved.</span></span>  
  
 `regCount`  
 <span data-ttu-id="bdc00-109">[em] O número de valores cadastrais a serem recuperados.</span><span class="sxs-lookup"><span data-stu-id="bdc00-109">[in] The number of register values to be retrieved.</span></span>  
  
 `regBuffer`  
 <span data-ttu-id="bdc00-110">[fora] Uma matriz `CORDB_REGISTER` de objetos, cada um dos quais recebe um valor de um registro.</span><span class="sxs-lookup"><span data-stu-id="bdc00-110">[out] An array of `CORDB_REGISTER` objects, each of which receives a value of a register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bdc00-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="bdc00-111">Remarks</span></span>  
 <span data-ttu-id="bdc00-112">O tamanho da matriz deve ser igual ao número de bits definido para um na máscara de bit.</span><span class="sxs-lookup"><span data-stu-id="bdc00-112">The size of the array should be equal to the number of bits set to one in the bit mask.</span></span> <span data-ttu-id="bdc00-113">O `regCount` parâmetro especifica o número de elementos no buffer que receberão os valores do registro.</span><span class="sxs-lookup"><span data-stu-id="bdc00-113">The `regCount` parameter specifies the number of elements in the buffer that will receive the register values.</span></span> <span data-ttu-id="bdc00-114">Se `regCount` o valor for muito pequeno para o número de registros indicados pela máscara, os registros numerados mais altos serão truncados a partir do conjunto.</span><span class="sxs-lookup"><span data-stu-id="bdc00-114">If the `regCount` value is too small for the number of registers indicated by the mask, the higher numbered registers will be truncated from the set.</span></span> <span data-ttu-id="bdc00-115">Se `regCount` o valor for muito grande, os elementos não utilizados `regBuffer` não serão modificados.</span><span class="sxs-lookup"><span data-stu-id="bdc00-115">If the `regCount` value is too large, the unused `regBuffer` elements will be unmodified.</span></span>  
  
 <span data-ttu-id="bdc00-116">Se a máscara de bit especificar `GetRegisters` um registro indisponível, retorne um valor indeterminado para esse registro.</span><span class="sxs-lookup"><span data-stu-id="bdc00-116">If the bit mask specifies a register that is unavailable, `GetRegisters` returns an indeterminate value for that register.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bdc00-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bdc00-117">Requirements</span></span>  
 <span data-ttu-id="bdc00-118">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bdc00-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bdc00-119">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bdc00-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bdc00-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bdc00-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bdc00-121">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bdc00-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdc00-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="bdc00-122">See also</span></span>

- [<span data-ttu-id="bdc00-123">Interface ICorDebugRegisterSet</span><span class="sxs-lookup"><span data-stu-id="bdc00-123">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
- [<span data-ttu-id="bdc00-124">Interface ICorDebugRegisterSet2</span><span class="sxs-lookup"><span data-stu-id="bdc00-124">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
