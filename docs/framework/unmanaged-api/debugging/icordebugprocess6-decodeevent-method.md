---
title: Método ICorDebugProcess6::DecodeEvent
ms.date: 03/30/2017
ms.assetid: 1453bc0c-6e0d-4d5a-b176-22607f8a3e6c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dc5c90cf5006763a84ddc891b9a011dc6cfbe754
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54738281"
---
# <a name="icordebugprocess6decodeevent-method"></a><span data-ttu-id="9bdab-102">Método ICorDebugProcess6::DecodeEvent</span><span class="sxs-lookup"><span data-stu-id="9bdab-102">ICorDebugProcess6::DecodeEvent Method</span></span>
<span data-ttu-id="9bdab-103">Decodifica eventos de depuração gerenciados que foram encapsulados na carga de eventos de depuração de exceção nativo especialmente criado.</span><span class="sxs-lookup"><span data-stu-id="9bdab-103">Decodes managed debug events that have been encapsulated in the payload of specially crafted native exception debug events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9bdab-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9bdab-104">Syntax</span></span>  
  
```  
HRESULT DecodeEvent(  
        [in, length_is(countBytes), size_is(countBytes)]  const BYTE pRecord[],  
        [in] DWORD countBytes,  
        [in] CorDebugRecordFormat format,  
        [in] DWORD dwFlags,   
        [in] DWORD dwThreadId,   
        [out] ICorDebugDebugEvent **ppEvent  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9bdab-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9bdab-105">Parameters</span></span>  
 `pRecord`  
 <span data-ttu-id="9bdab-106">[in] Um ponteiro para uma matriz de bytes de um evento de depuração de exceção nativo que inclui informações sobre um evento de depuração gerenciado.</span><span class="sxs-lookup"><span data-stu-id="9bdab-106">[in] A pointer to a byte array from a native exception debug event that includes information about a managed debug event.</span></span>  
  
 `countBytes`  
 <span data-ttu-id="9bdab-107">[in] O número de elementos nas matrizes de byte `pRecord`.</span><span class="sxs-lookup"><span data-stu-id="9bdab-107">[in] The number of elements in the `pRecord` byte array.</span></span>  
  
 `format`  
 <span data-ttu-id="9bdab-108">[in] Um [CorDebugRecordFormat](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md) membro de enumeração que especifica o formato do evento depuração não gerenciada.</span><span class="sxs-lookup"><span data-stu-id="9bdab-108">[in] A [CorDebugRecordFormat](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md) enumeration member that specifies the format of the unmanaged debug event.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="9bdab-109">[in] Um campo de bits que depende da arquitetura de destino e que especifica informações adicionais sobre o evento de depuração.</span><span class="sxs-lookup"><span data-stu-id="9bdab-109">[in] A bit field that depends on the target architecture and that specifies additional information about the debug event.</span></span> <span data-ttu-id="9bdab-110">Para sistemas Windows, ele pode ser um membro do [CorDebugDecodeEventFlagsWindows](../../../../docs/framework/unmanaged-api/debugging/cordebugdecodeeventflagswindows-enumeration.md) enumeração.</span><span class="sxs-lookup"><span data-stu-id="9bdab-110">For Windows systems, it can be a member of the [CorDebugDecodeEventFlagsWindows](../../../../docs/framework/unmanaged-api/debugging/cordebugdecodeeventflagswindows-enumeration.md) enumeration.</span></span>  
  
 `dwThreadId`  
 <span data-ttu-id="9bdab-111">[in] O identificador de sistema operacional do thread em que a exceção foi gerada.</span><span class="sxs-lookup"><span data-stu-id="9bdab-111">[in] The operating system identifier of the thread on which the exception was thrown.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="9bdab-112">[out] Um ponteiro para o endereço de um [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) objeto que representa um evento de depuração gerenciado decodificado.</span><span class="sxs-lookup"><span data-stu-id="9bdab-112">[out] A pointer to the address of an [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) object that represents a decoded managed debug event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9bdab-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="9bdab-113">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9bdab-114">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="9bdab-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9bdab-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9bdab-115">Requirements</span></span>  
 <span data-ttu-id="9bdab-116">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9bdab-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9bdab-117">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9bdab-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9bdab-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9bdab-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9bdab-119">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9bdab-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bdab-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9bdab-120">See also</span></span>
- [<span data-ttu-id="9bdab-121">Interface ICorDebugProcess6</span><span class="sxs-lookup"><span data-stu-id="9bdab-121">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [<span data-ttu-id="9bdab-122">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="9bdab-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
