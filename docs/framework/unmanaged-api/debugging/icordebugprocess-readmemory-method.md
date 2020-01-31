---
title: Método ICorDebugProcess::ReadMemory
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.ReadMemory
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::ReadMemory
helpviewer_keywords:
- ReadMemory method [.NET Framework debugging]
- ICorDebugProcess::ReadMemory method [.NET Framework debugging]
ms.assetid: 28e4b2f6-9589-445c-be24-24a3306795e7
topic_type:
- apiref
ms.openlocfilehash: dca2a4e5ee869346108137a8ba01ab8855756725
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792551"
---
# <a name="icordebugprocessreadmemory-method"></a><span data-ttu-id="0c919-102">Método ICorDebugProcess::ReadMemory</span><span class="sxs-lookup"><span data-stu-id="0c919-102">ICorDebugProcess::ReadMemory Method</span></span>
<span data-ttu-id="0c919-103">Lê uma área especificada de memória para esse processo.</span><span class="sxs-lookup"><span data-stu-id="0c919-103">Reads a specified area of memory for this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c919-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0c919-104">Syntax</span></span>  
  
```cpp  
HRESULT ReadMemory(  
    [in]  CORDB_ADDRESS address,   
    [in]  DWORD size,  
    [out, size_is(size), length_is(size)] BYTE buffer[],  
    [out] SIZE_T *read);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0c919-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0c919-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="0c919-106">no Um valor `CORDB_ADDRESS` que especifica o endereço base da memória a ser lida.</span><span class="sxs-lookup"><span data-stu-id="0c919-106">[in] A `CORDB_ADDRESS` value that specifies the base address of the memory to be read.</span></span>  
  
 `size`  
 <span data-ttu-id="0c919-107">no O número de bytes a serem lidos da memória.</span><span class="sxs-lookup"><span data-stu-id="0c919-107">[in] The number of bytes to be read from memory.</span></span>  
  
 `buffer`  
 <span data-ttu-id="0c919-108">fora Um buffer que recebe o conteúdo da memória.</span><span class="sxs-lookup"><span data-stu-id="0c919-108">[out] A buffer that receives the contents of the memory.</span></span>  
  
 `read`  
 <span data-ttu-id="0c919-109">fora Um ponteiro para o número de bytes transferidos para o buffer especificado.</span><span class="sxs-lookup"><span data-stu-id="0c919-109">[out] A pointer to the number of bytes transferred into the specified buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0c919-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="0c919-110">Remarks</span></span>  
 <span data-ttu-id="0c919-111">O método `ReadMemory` destina-se principalmente a ser usado pela depuração de interoperabilidade para inspecionar regiões de memória que estão sendo usadas pela parte não gerenciada do depurador.</span><span class="sxs-lookup"><span data-stu-id="0c919-111">The `ReadMemory` method is primarily intended to be used by interop debugging to inspect memory regions that are being used by the unmanaged portion of the debuggee.</span></span> <span data-ttu-id="0c919-112">Esse método também pode ser usado para ler o código MSIL (Microsoft Intermediate Language) e o código compilado por JIT nativo.</span><span class="sxs-lookup"><span data-stu-id="0c919-112">This method can also be used to read Microsoft intermediate language (MSIL) code and native JIT-compiled code.</span></span>  
  
 <span data-ttu-id="0c919-113">Todos os pontos de interrupção gerenciados serão removidos dos dados retornados no parâmetro `buffer`.</span><span class="sxs-lookup"><span data-stu-id="0c919-113">Any managed breakpoints will be removed from the data that is returned in the `buffer` parameter.</span></span> <span data-ttu-id="0c919-114">Nenhum ajuste será feito para pontos de interrupção nativos definidos por [ICorDebugProcess2:: SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md).</span><span class="sxs-lookup"><span data-stu-id="0c919-114">No adjustments will be made for native breakpoints set by [ICorDebugProcess2::SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md).</span></span>  
  
 <span data-ttu-id="0c919-115">Nenhum cache de memória de processo é executado.</span><span class="sxs-lookup"><span data-stu-id="0c919-115">No caching of process memory is performed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c919-116">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="0c919-116">Requirements</span></span>  
 <span data-ttu-id="0c919-117">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c919-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c919-118">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0c919-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0c919-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0c919-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0c919-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c919-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
