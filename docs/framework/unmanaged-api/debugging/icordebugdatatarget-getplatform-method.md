---
title: Método ICorDebugDataTarget::GetPlatform
ms.date: 03/30/2017
api_name:
- ICorDebugDataTarget.GetPlatform Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget::GetPlatform
helpviewer_keywords:
- GetPlatform method [.NET Framework debugging]
- ICorDebugDataTarget::GetPlatform method [.NET Framework debugging]
ms.assetid: 9ee96c9d-7a3d-4129-a6cc-7675c7f2dda4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 17ae761b2d48552aded8191ddbea26552d8da277
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33411012"
---
# <a name="icordebugdatatargetgetplatform-method"></a><span data-ttu-id="24027-102">Método ICorDebugDataTarget::GetPlatform</span><span class="sxs-lookup"><span data-stu-id="24027-102">ICorDebugDataTarget::GetPlatform Method</span></span>
<span data-ttu-id="24027-103">Fornece informações sobre a plataforma, incluindo arquitetura de processador e sistema operacional, que está executando o processo de destino.</span><span class="sxs-lookup"><span data-stu-id="24027-103">Provides information about the platform, including processor architecture and operating system, on which the target process is running.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24027-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="24027-104">Syntax</span></span>  
  
```  
HRESULT GetPlatform([out] CorDebugPlatform * pTargetPlatform);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="24027-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="24027-105">Parameters</span></span>  
 `pTargetPlatform`  
 <span data-ttu-id="24027-106">[out] Um ponteiro para um [CorDebugPlatformEnum](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md) enumeração que descreve a plataforma de destino.</span><span class="sxs-lookup"><span data-stu-id="24027-106">[out] A pointer to a [CorDebugPlatformEnum](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md) enumeration that describes the target platform.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="24027-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="24027-107">Remarks</span></span>  
 <span data-ttu-id="24027-108">O `CorDebugPlatformEnum` valor de retorno de enumeração é usado pelo [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interface para determinar os detalhes do processo de destino como o tamanho do ponteiro, layout do espaço de endereço, conjunto de registro, formato de instrução, layout de contexto, e convenções de chamada.</span><span class="sxs-lookup"><span data-stu-id="24027-108">The `CorDebugPlatformEnum` enumeration return value is used by the [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interface to determine details of the target process such as its pointer size, address space layout, register set, instruction format, context layout, and calling conventions.</span></span>  
  
 <span data-ttu-id="24027-109">O `pTargetPlatform` valor pode se referir a uma plataforma que está sendo emulada para o destino em vez de especificar o hardware atual em uso.</span><span class="sxs-lookup"><span data-stu-id="24027-109">The `pTargetPlatform` value may refer to a platform that is being emulated for the target instead of specifying the actual hardware in use.</span></span> <span data-ttu-id="24027-110">Por exemplo, um processo que esteja executando o Windows no ambiente do Windows (WOW) em uma edição de 64 bits do sistema operacional Windows deve usar o `CORDB_PLATFORM_WINDOWS_X86` valor o [CorDebugPlatformEnum](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md) enumeração.</span><span class="sxs-lookup"><span data-stu-id="24027-110">For example, a process that is running in the Windows on Windows (WOW) environment on a 64-bit edition of the Windows operating system should use the `CORDB_PLATFORM_WINDOWS_X86` value of the [CorDebugPlatformEnum](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="24027-111">Esse método deve ter êxito.</span><span class="sxs-lookup"><span data-stu-id="24027-111">This method must succeed.</span></span> <span data-ttu-id="24027-112">Se ele falhar, a plataforma de destino é inutilizável.</span><span class="sxs-lookup"><span data-stu-id="24027-112">If it fails, the target platform is unusable.</span></span> <span data-ttu-id="24027-113">O método pode falhar pelos seguintes motivos:</span><span class="sxs-lookup"><span data-stu-id="24027-113">The method may fail for the following reasons:</span></span>  
  
-   <span data-ttu-id="24027-114">A plataforma que está sendo emulada para o destino não é utilizável.</span><span class="sxs-lookup"><span data-stu-id="24027-114">The platform that is being emulated for the target is unusable.</span></span>  
  
-   <span data-ttu-id="24027-115">O hardware real na plataforma de destino não é utilizável.</span><span class="sxs-lookup"><span data-stu-id="24027-115">The actual hardware on the target platform is unusable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24027-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="24027-116">Requirements</span></span>  
 <span data-ttu-id="24027-117">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="24027-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24027-118">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="24027-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="24027-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="24027-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="24027-120">**Versões do .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24027-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24027-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="24027-121">See Also</span></span>  
 [<span data-ttu-id="24027-122">Interface ICorDebugDataTarget</span><span class="sxs-lookup"><span data-stu-id="24027-122">ICorDebugDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)  
 [<span data-ttu-id="24027-123">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="24027-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="24027-124">Depuração</span><span class="sxs-lookup"><span data-stu-id="24027-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
