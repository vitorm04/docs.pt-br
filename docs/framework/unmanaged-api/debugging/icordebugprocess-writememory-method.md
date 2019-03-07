---
title: Método ICorDebugProcess::WriteMemory
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.WriteMemory
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::WriteMemory
helpviewer_keywords:
- ICorDebugProcess::WriteMemory method [.NET Framework debugging]
- WriteMemory method [.NET Framework debugging]
ms.assetid: d5c07d86-045d-4391-893b-0bcd2959f90e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2e9d640fb1c9dae5bb195baa504e560ba8e45821
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57497087"
---
# <a name="icordebugprocesswritememory-method"></a><span data-ttu-id="89fc4-102">Método ICorDebugProcess::WriteMemory</span><span class="sxs-lookup"><span data-stu-id="89fc4-102">ICorDebugProcess::WriteMemory Method</span></span>
<span data-ttu-id="89fc4-103">Grava dados em uma área de memória nesse processo.</span><span class="sxs-lookup"><span data-stu-id="89fc4-103">Writes data to an area of memory in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89fc4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="89fc4-104">Syntax</span></span>  
  
```  
HRESULT WriteMemory(  
    [in]  CORDB_ADDRESS address,  
    [in]  DWORD size,  
    [in, size_is(size)] BYTE buffer[],  
    [out] SIZE_T *written);  
```  
  
## <a name="parameters"></a><span data-ttu-id="89fc4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="89fc4-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="89fc4-106">[in] Um `CORDB_ADDRESS` valor que é o endereço básico da área de memória no qual os dados é gravado.</span><span class="sxs-lookup"><span data-stu-id="89fc4-106">[in] A `CORDB_ADDRESS` value that is the base address of the memory area to which data is written.</span></span> <span data-ttu-id="89fc4-107">Antes que ocorra a transferência de dados, o sistema verifica que a área de memória do tamanho especificado, começando no endereço base, é acessível para gravação.</span><span class="sxs-lookup"><span data-stu-id="89fc4-107">Before data transfer occurs, the system verifies that the memory area of the specified size, beginning at the base address, is accessible for writing.</span></span> <span data-ttu-id="89fc4-108">Se não estiver acessível, o método falhará.</span><span class="sxs-lookup"><span data-stu-id="89fc4-108">If it is not accessible, the method fails.</span></span>  
  
 `size`  
 <span data-ttu-id="89fc4-109">[in] O número de bytes a serem gravados para a área de memória.</span><span class="sxs-lookup"><span data-stu-id="89fc4-109">[in] The number of bytes to be written to the memory area.</span></span>  
  
 `buffer`  
 <span data-ttu-id="89fc4-110">[in] Um buffer que contém dados a serem gravados.</span><span class="sxs-lookup"><span data-stu-id="89fc4-110">[in] A buffer that contains data to be written.</span></span>  
  
 `written`  
 <span data-ttu-id="89fc4-111">[out] Um ponteiro para uma variável que recebe o número de bytes gravados para a área de memória nesse processo.</span><span class="sxs-lookup"><span data-stu-id="89fc4-111">[out] A pointer to a variable that receives the number of bytes written to the memory area in this process.</span></span> <span data-ttu-id="89fc4-112">Se `written` for NULL, esse parâmetro será ignorado.</span><span class="sxs-lookup"><span data-stu-id="89fc4-112">If `written` is NULL, this parameter is ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="89fc4-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="89fc4-113">Remarks</span></span>  
 <span data-ttu-id="89fc4-114">Automaticamente, os dados são gravados por trás de qualquer ponto de interrupção.</span><span class="sxs-lookup"><span data-stu-id="89fc4-114">Data is automatically written behind any breakpoints.</span></span> <span data-ttu-id="89fc4-115">No .NET Framework versão 2.0, depuradores nativos não devem usar esse método para inserir pontos de interrupção no fluxo de instruções.</span><span class="sxs-lookup"><span data-stu-id="89fc4-115">In the .NET Framework version 2.0, native debuggers should not use this method to inject breakpoints into the instruction stream.</span></span> <span data-ttu-id="89fc4-116">Use [ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md) em vez disso.</span><span class="sxs-lookup"><span data-stu-id="89fc4-116">Use [ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md) instead.</span></span>  
  
 <span data-ttu-id="89fc4-117">O `WriteMemory` método deve ser usado apenas para código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="89fc4-117">The `WriteMemory` method should be used only outside of managed code.</span></span> <span data-ttu-id="89fc4-118">Esse método pode corromper o tempo de execução se usado incorretamente.</span><span class="sxs-lookup"><span data-stu-id="89fc4-118">This method can corrupt the runtime if used improperly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89fc4-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="89fc4-119">Requirements</span></span>  
 <span data-ttu-id="89fc4-120">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89fc4-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89fc4-121">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="89fc4-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="89fc4-122">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="89fc4-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="89fc4-123">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89fc4-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
