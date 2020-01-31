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
ms.openlocfilehash: fb3e0ccb57cf3b056bd25e643706e49b8bc75531
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792550"
---
# <a name="icordebugprocesswritememory-method"></a><span data-ttu-id="b3504-102">Método ICorDebugProcess::WriteMemory</span><span class="sxs-lookup"><span data-stu-id="b3504-102">ICorDebugProcess::WriteMemory Method</span></span>
<span data-ttu-id="b3504-103">Grava dados em uma área de memória nesse processo.</span><span class="sxs-lookup"><span data-stu-id="b3504-103">Writes data to an area of memory in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3504-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b3504-104">Syntax</span></span>  
  
```cpp  
HRESULT WriteMemory(  
    [in]  CORDB_ADDRESS address,  
    [in]  DWORD size,  
    [in, size_is(size)] BYTE buffer[],  
    [out] SIZE_T *written);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b3504-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b3504-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="b3504-106">no Um valor `CORDB_ADDRESS` que é o endereço base da área de memória na qual os dados são gravados.</span><span class="sxs-lookup"><span data-stu-id="b3504-106">[in] A `CORDB_ADDRESS` value that is the base address of the memory area to which data is written.</span></span> <span data-ttu-id="b3504-107">Antes que a transferência de dados ocorra, o sistema verifica se a área de memória do tamanho especificado, começando no endereço base, está acessível para gravação.</span><span class="sxs-lookup"><span data-stu-id="b3504-107">Before data transfer occurs, the system verifies that the memory area of the specified size, beginning at the base address, is accessible for writing.</span></span> <span data-ttu-id="b3504-108">Se não estiver acessível, o método falhará.</span><span class="sxs-lookup"><span data-stu-id="b3504-108">If it is not accessible, the method fails.</span></span>  
  
 `size`  
 <span data-ttu-id="b3504-109">no O número de bytes a serem gravados na área de memória.</span><span class="sxs-lookup"><span data-stu-id="b3504-109">[in] The number of bytes to be written to the memory area.</span></span>  
  
 `buffer`  
 <span data-ttu-id="b3504-110">no Um buffer que contém dados a serem gravados.</span><span class="sxs-lookup"><span data-stu-id="b3504-110">[in] A buffer that contains data to be written.</span></span>  
  
 `written`  
 <span data-ttu-id="b3504-111">fora Um ponteiro para uma variável que recebe o número de bytes gravados na área de memória nesse processo.</span><span class="sxs-lookup"><span data-stu-id="b3504-111">[out] A pointer to a variable that receives the number of bytes written to the memory area in this process.</span></span> <span data-ttu-id="b3504-112">Se `written` for NULL, esse parâmetro será ignorado.</span><span class="sxs-lookup"><span data-stu-id="b3504-112">If `written` is NULL, this parameter is ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b3504-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="b3504-113">Remarks</span></span>  
 <span data-ttu-id="b3504-114">Os dados são gravados automaticamente por trás de qualquer ponto de interrupção.</span><span class="sxs-lookup"><span data-stu-id="b3504-114">Data is automatically written behind any breakpoints.</span></span> <span data-ttu-id="b3504-115">No .NET Framework versão 2,0, os depuradores nativos não devem usar esse método para injetar pontos de interrupção no fluxo de instrução.</span><span class="sxs-lookup"><span data-stu-id="b3504-115">In the .NET Framework version 2.0, native debuggers should not use this method to inject breakpoints into the instruction stream.</span></span> <span data-ttu-id="b3504-116">Use [ICorDebugProcess2:: SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md) em vez disso.</span><span class="sxs-lookup"><span data-stu-id="b3504-116">Use [ICorDebugProcess2::SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md) instead.</span></span>  
  
 <span data-ttu-id="b3504-117">O método `WriteMemory` deve ser usado somente fora do código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="b3504-117">The `WriteMemory` method should be used only outside of managed code.</span></span> <span data-ttu-id="b3504-118">Esse método pode corromper o tempo de execução se for usado de forma inadequada.</span><span class="sxs-lookup"><span data-stu-id="b3504-118">This method can corrupt the runtime if used improperly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3504-119">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="b3504-119">Requirements</span></span>  
 <span data-ttu-id="b3504-120">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b3504-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3504-121">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b3504-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b3504-122">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b3504-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b3504-123">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3504-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
