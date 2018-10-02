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
ms.openlocfilehash: 6da4c282c7f969a406a657d1e30dd6120a32b4e3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420902"
---
# <a name="icordebugprocesswritememory-method"></a><span data-ttu-id="b65a2-102">Método ICorDebugProcess::WriteMemory</span><span class="sxs-lookup"><span data-stu-id="b65a2-102">ICorDebugProcess::WriteMemory Method</span></span>
<span data-ttu-id="b65a2-103">Grava dados em uma área da memória do processo.</span><span class="sxs-lookup"><span data-stu-id="b65a2-103">Writes data to an area of memory in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b65a2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b65a2-104">Syntax</span></span>  
  
```  
HRESULT WriteMemory(  
    [in]  CORDB_ADDRESS address,  
    [in]  DWORD size,  
    [in, size_is(size)] BYTE buffer[],  
    [out] SIZE_T *written);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b65a2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b65a2-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="b65a2-106">[in] Um `CORDB_ADDRESS` valor que é o endereço base da área de memória no qual os dados é gravado.</span><span class="sxs-lookup"><span data-stu-id="b65a2-106">[in] A `CORDB_ADDRESS` value that is the base address of the memory area to which data is written.</span></span> <span data-ttu-id="b65a2-107">Antes que ocorra a transferência de dados, o sistema verifica se a área da memória do tamanho especificado, começando no endereço base, está acessível para gravação.</span><span class="sxs-lookup"><span data-stu-id="b65a2-107">Before data transfer occurs, the system verifies that the memory area of the specified size, beginning at the base address, is accessible for writing.</span></span> <span data-ttu-id="b65a2-108">Se não estiver acessível, o método falhará.</span><span class="sxs-lookup"><span data-stu-id="b65a2-108">If it is not accessible, the method fails.</span></span>  
  
 `size`  
 <span data-ttu-id="b65a2-109">[in] O número de bytes a serem gravados para a área de memória.</span><span class="sxs-lookup"><span data-stu-id="b65a2-109">[in] The number of bytes to be written to the memory area.</span></span>  
  
 `buffer`  
 <span data-ttu-id="b65a2-110">[in] Um buffer que contém os dados a serem gravados.</span><span class="sxs-lookup"><span data-stu-id="b65a2-110">[in] A buffer that contains data to be written.</span></span>  
  
 `written`  
 <span data-ttu-id="b65a2-111">[out] Um ponteiro para uma variável que recebe o número de bytes gravados para a área de memória nesse processo.</span><span class="sxs-lookup"><span data-stu-id="b65a2-111">[out] A pointer to a variable that receives the number of bytes written to the memory area in this process.</span></span> <span data-ttu-id="b65a2-112">Se `written` for NULL, esse parâmetro é ignorado.</span><span class="sxs-lookup"><span data-stu-id="b65a2-112">If `written` is NULL, this parameter is ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b65a2-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="b65a2-113">Remarks</span></span>  
 <span data-ttu-id="b65a2-114">Automaticamente, os dados são gravados por trás de qualquer ponto de interrupção.</span><span class="sxs-lookup"><span data-stu-id="b65a2-114">Data is automatically written behind any breakpoints.</span></span> <span data-ttu-id="b65a2-115">O .NET Framework versão 2.0, depuradores nativo não devem usar esse método para inserir pontos de interrupção no fluxo de instrução.</span><span class="sxs-lookup"><span data-stu-id="b65a2-115">In the .NET Framework version 2.0, native debuggers should not use this method to inject breakpoints into the instruction stream.</span></span> <span data-ttu-id="b65a2-116">Use [Icordebugprocess2](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md) em vez disso.</span><span class="sxs-lookup"><span data-stu-id="b65a2-116">Use [ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md) instead.</span></span>  
  
 <span data-ttu-id="b65a2-117">O `WriteMemory` método deve ser usado somente fora do código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="b65a2-117">The `WriteMemory` method should be used only outside of managed code.</span></span> <span data-ttu-id="b65a2-118">Esse método pode corromper o tempo de execução se usada incorretamente.</span><span class="sxs-lookup"><span data-stu-id="b65a2-118">This method can corrupt the runtime if used improperly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b65a2-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b65a2-119">Requirements</span></span>  
 <span data-ttu-id="b65a2-120">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b65a2-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b65a2-121">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b65a2-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b65a2-122">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b65a2-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b65a2-123">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b65a2-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
