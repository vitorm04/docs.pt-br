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
ms.openlocfilehash: d0b6960a24e246c7a538e8ffc59fa380a4b8e2a7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131364"
---
# <a name="icordebugregisterset2getregistersavailable-method"></a><span data-ttu-id="a9667-102">Método ICorDebugRegisterSet2::GetRegistersAvailable</span><span class="sxs-lookup"><span data-stu-id="a9667-102">ICorDebugRegisterSet2::GetRegistersAvailable Method</span></span>
<span data-ttu-id="a9667-103">Obtém uma matriz de bytes que fornece um bitmap dos registros disponíveis.</span><span class="sxs-lookup"><span data-stu-id="a9667-103">Gets an array of bytes that provides a bitmap of the available registers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9667-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a9667-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegistersAvailable (  
    [in] ULONG32 numChunks,  
    [out, size_is(numChunks)] BYTE availableRegChunks[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a9667-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a9667-105">Parameters</span></span>  
 `numChunks`  
 <span data-ttu-id="a9667-106">no O tamanho da matriz de `availableRegChunks`.</span><span class="sxs-lookup"><span data-stu-id="a9667-106">[in] The size of the `availableRegChunks` array.</span></span>  
  
 `availableRegChunks`  
 <span data-ttu-id="a9667-107">fora Uma matriz de bytes, cada bit corresponde a um registro.</span><span class="sxs-lookup"><span data-stu-id="a9667-107">[out] An array of bytes, each bit of which corresponds to a register.</span></span> <span data-ttu-id="a9667-108">Se um registro estiver disponível, o bit correspondente do registro será definido.</span><span class="sxs-lookup"><span data-stu-id="a9667-108">If a register is available, the register's corresponding bit is set.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a9667-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="a9667-109">Remarks</span></span>  
 <span data-ttu-id="a9667-110">Os valores da enumeração CorDebugRegister especificam os registros de diferentes microprocessadores.</span><span class="sxs-lookup"><span data-stu-id="a9667-110">The values of the CorDebugRegister enumeration specify the registers of different microprocessors.</span></span> <span data-ttu-id="a9667-111">Os cinco bits superiores de cada valor são o índice na matriz de `availableRegChunks` de bytes.</span><span class="sxs-lookup"><span data-stu-id="a9667-111">The upper five bits of each value are the index into the `availableRegChunks` array of bytes.</span></span> <span data-ttu-id="a9667-112">Os três bits inferiores de cada valor identificam a posição do bit dentro do byte indexado.</span><span class="sxs-lookup"><span data-stu-id="a9667-112">The lower three bits of each value identify the bit position within the indexed byte.</span></span> <span data-ttu-id="a9667-113">Dado um valor `CorDebugRegister` que especifica um registro específico, a posição do registro na máscara é determinada da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="a9667-113">Given a `CorDebugRegister` value that specifies a particular register, the register's position in the mask is determined as follows:</span></span>  
  
1. <span data-ttu-id="a9667-114">Extraia o índice necessário para acessar o byte correto na matriz de `availableRegChunks`:</span><span class="sxs-lookup"><span data-stu-id="a9667-114">Extract the index needed to access the correct byte in the `availableRegChunks` array:</span></span>  
  
     <span data-ttu-id="a9667-115">`CorDebugRegister` valor > > 3</span><span class="sxs-lookup"><span data-stu-id="a9667-115">`CorDebugRegister` value >> 3</span></span>  
  
2. <span data-ttu-id="a9667-116">Extraia a posição do bit dentro do byte indexado, em que bit zero é o bit menos significativo:</span><span class="sxs-lookup"><span data-stu-id="a9667-116">Extract the bit position within the indexed byte, where bit zero is the least significant bit:</span></span>  
  
     <span data-ttu-id="a9667-117">valor `CorDebugRegister` & 7</span><span class="sxs-lookup"><span data-stu-id="a9667-117">`CorDebugRegister` value & 7</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9667-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a9667-118">Requirements</span></span>  
 <span data-ttu-id="a9667-119">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9667-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9667-120">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a9667-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a9667-121">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a9667-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a9667-122">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9667-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9667-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a9667-123">See also</span></span>

- [<span data-ttu-id="a9667-124">Interface ICorDebugRegisterSet2</span><span class="sxs-lookup"><span data-stu-id="a9667-124">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
- [<span data-ttu-id="a9667-125">Interface ICorDebugRegisterSet</span><span class="sxs-lookup"><span data-stu-id="a9667-125">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
