---
title: "Método ICorDebugProcess::ReadMemory"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess.ReadMemory
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess::ReadMemory
helpviewer_keywords:
- ReadMemory method [.NET Framework debugging]
- ICorDebugProcess::ReadMemory method [.NET Framework debugging]
ms.assetid: 28e4b2f6-9589-445c-be24-24a3306795e7
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 33345ada6606bc1a43a630340251d3ba1404b2f2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugprocessreadmemory-method"></a><span data-ttu-id="b6ce9-102">Método ICorDebugProcess::ReadMemory</span><span class="sxs-lookup"><span data-stu-id="b6ce9-102">ICorDebugProcess::ReadMemory Method</span></span>
<span data-ttu-id="b6ce9-103">Lê uma área especificada de memória para esse processo.</span><span class="sxs-lookup"><span data-stu-id="b6ce9-103">Reads a specified area of memory for this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6ce9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b6ce9-104">Syntax</span></span>  
  
```  
HRESULT ReadMemory(  
    [in]  CORDB_ADDRESS address,   
    [in]  DWORD size,  
    [out, size_is(size), length_is(size)] BYTE buffer[],  
    [out] SIZE_T *read);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b6ce9-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b6ce9-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="b6ce9-106">[in] Um `CORDB_ADDRESS` valor que especifica o endereço base da memória para ser lido.</span><span class="sxs-lookup"><span data-stu-id="b6ce9-106">[in] A `CORDB_ADDRESS` value that specifies the base address of the memory to be read.</span></span>  
  
 `size`  
 <span data-ttu-id="b6ce9-107">[in] O número de bytes a serem lidos da memória.</span><span class="sxs-lookup"><span data-stu-id="b6ce9-107">[in] The number of bytes to be read from memory.</span></span>  
  
 `buffer`  
 <span data-ttu-id="b6ce9-108">[out] Um buffer que recebe o conteúdo da memória.</span><span class="sxs-lookup"><span data-stu-id="b6ce9-108">[out] A buffer that receives the contents of the memory.</span></span>  
  
 `read`  
 <span data-ttu-id="b6ce9-109">[out] Um ponteiro para o número de bytes transferidos para o buffer especificado.</span><span class="sxs-lookup"><span data-stu-id="b6ce9-109">[out] A pointer to the number of bytes transferred into the specified buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b6ce9-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="b6ce9-110">Remarks</span></span>  
 <span data-ttu-id="b6ce9-111">O `ReadMemory` método destina-se principalmente a ser usado ao depurar interop para inspecionar as regiões de memória que estão sendo usadas pela parte não gerenciada o ser depurado.</span><span class="sxs-lookup"><span data-stu-id="b6ce9-111">The `ReadMemory` method is primarily intended to be used by interop debugging to inspect memory regions that are being used by the unmanaged portion of the debuggee.</span></span> <span data-ttu-id="b6ce9-112">Esse método também pode ser usado para ler o código Microsoft intermediate language (MSIL) e o código nativo de compilação JIT.</span><span class="sxs-lookup"><span data-stu-id="b6ce9-112">This method can also be used to read Microsoft intermediate language (MSIL) code and native JIT-compiled code.</span></span>  
  
 <span data-ttu-id="b6ce9-113">Qualquer ponto de interrupção gerenciado será removido dos dados que são retornados no `buffer` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="b6ce9-113">Any managed breakpoints will be removed from the data that is returned in the `buffer` parameter.</span></span> <span data-ttu-id="b6ce9-114">Nenhum ajuste será feita para pontos de interrupção nativo definido pelo [Icordebugprocess2](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md).</span><span class="sxs-lookup"><span data-stu-id="b6ce9-114">No adjustments will be made for native breakpoints set by [ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md).</span></span>  
  
 <span data-ttu-id="b6ce9-115">Nenhum cache de memória de processo é executada.</span><span class="sxs-lookup"><span data-stu-id="b6ce9-115">No caching of process memory is performed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6ce9-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b6ce9-116">Requirements</span></span>  
 <span data-ttu-id="b6ce9-117">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6ce9-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6ce9-118">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b6ce9-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b6ce9-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b6ce9-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b6ce9-120">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6ce9-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
