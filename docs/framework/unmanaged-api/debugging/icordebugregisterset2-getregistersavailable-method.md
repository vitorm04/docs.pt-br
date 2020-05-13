---
title: Método ICorDebugRegisterSet2::GetRegistersAvailable
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet2.GetRegistersAvailable
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet2::GetRegistersAvailable
helpviewer_keywords:
- GetRegistersAvailable method, ICorDebugRegisterSet2 interface [.NET Framework debugging]
- ICorDebugRegisterSet2::GetRegistersAvailable method [.NET Framework debugging]
ms.assetid: f3ed344b-0d3a-44e8-8000-2a97e0805a2c
topic_type:
- apiref
ms.openlocfilehash: 2149c985519b95f89af2c50d05753ae7259babe4
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378214"
---
# <a name="icordebugregisterset2getregistersavailable-method"></a><span data-ttu-id="76dd6-102">Método ICorDebugRegisterSet2::GetRegistersAvailable</span><span class="sxs-lookup"><span data-stu-id="76dd6-102">ICorDebugRegisterSet2::GetRegistersAvailable Method</span></span>
<span data-ttu-id="76dd6-103">Obtém uma matriz de bytes que fornece um bitmap dos registros disponíveis.</span><span class="sxs-lookup"><span data-stu-id="76dd6-103">Gets an array of bytes that provides a bitmap of the available registers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76dd6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="76dd6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegistersAvailable (  
    [in] ULONG32 numChunks,  
    [out, size_is(numChunks)] BYTE availableRegChunks[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="76dd6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="76dd6-105">Parameters</span></span>  
 `numChunks`  
 <span data-ttu-id="76dd6-106">no O tamanho da `availableRegChunks` matriz.</span><span class="sxs-lookup"><span data-stu-id="76dd6-106">[in] The size of the `availableRegChunks` array.</span></span>  
  
 `availableRegChunks`  
 <span data-ttu-id="76dd6-107">fora Uma matriz de bytes, cada bit corresponde a um registro.</span><span class="sxs-lookup"><span data-stu-id="76dd6-107">[out] An array of bytes, each bit of which corresponds to a register.</span></span> <span data-ttu-id="76dd6-108">Se um registro estiver disponível, o bit correspondente do registro será definido.</span><span class="sxs-lookup"><span data-stu-id="76dd6-108">If a register is available, the register's corresponding bit is set.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="76dd6-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="76dd6-109">Remarks</span></span>  
 <span data-ttu-id="76dd6-110">Os valores da enumeração CorDebugRegister especificam os registros de diferentes microprocessadores.</span><span class="sxs-lookup"><span data-stu-id="76dd6-110">The values of the CorDebugRegister enumeration specify the registers of different microprocessors.</span></span> <span data-ttu-id="76dd6-111">Os cinco bits superiores de cada valor são o índice na `availableRegChunks` matriz de bytes.</span><span class="sxs-lookup"><span data-stu-id="76dd6-111">The upper five bits of each value are the index into the `availableRegChunks` array of bytes.</span></span> <span data-ttu-id="76dd6-112">Os três bits inferiores de cada valor identificam a posição do bit dentro do byte indexado.</span><span class="sxs-lookup"><span data-stu-id="76dd6-112">The lower three bits of each value identify the bit position within the indexed byte.</span></span> <span data-ttu-id="76dd6-113">Dado um `CorDebugRegister` valor que especifica um registro específico, a posição do registro na máscara é determinada da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="76dd6-113">Given a `CorDebugRegister` value that specifies a particular register, the register's position in the mask is determined as follows:</span></span>  
  
1. <span data-ttu-id="76dd6-114">Extraia o índice necessário para acessar o byte correto na `availableRegChunks` matriz:</span><span class="sxs-lookup"><span data-stu-id="76dd6-114">Extract the index needed to access the correct byte in the `availableRegChunks` array:</span></span>  
  
     <span data-ttu-id="76dd6-115">`CorDebugRegister`valor >> 3</span><span class="sxs-lookup"><span data-stu-id="76dd6-115">`CorDebugRegister` value >> 3</span></span>  
  
2. <span data-ttu-id="76dd6-116">Extraia a posição do bit dentro do byte indexado, em que bit zero é o bit menos significativo:</span><span class="sxs-lookup"><span data-stu-id="76dd6-116">Extract the bit position within the indexed byte, where bit zero is the least significant bit:</span></span>  
  
     <span data-ttu-id="76dd6-117">`CorDebugRegister`valor & 7</span><span class="sxs-lookup"><span data-stu-id="76dd6-117">`CorDebugRegister` value & 7</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76dd6-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="76dd6-118">Requirements</span></span>  
 <span data-ttu-id="76dd6-119">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="76dd6-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76dd6-120">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="76dd6-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="76dd6-121">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="76dd6-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="76dd6-122">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76dd6-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76dd6-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="76dd6-123">See also</span></span>

- [<span data-ttu-id="76dd6-124">Interface ICorDebugRegisterSet2</span><span class="sxs-lookup"><span data-stu-id="76dd6-124">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
- [<span data-ttu-id="76dd6-125">Interface ICorDebugRegisterSet</span><span class="sxs-lookup"><span data-stu-id="76dd6-125">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
