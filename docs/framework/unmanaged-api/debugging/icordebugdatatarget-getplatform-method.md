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
ms.openlocfilehash: 309c31dacd801f1c46a2d37932124638bc157cd6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61749040"
---
# <a name="icordebugdatatargetgetplatform-method"></a><span data-ttu-id="c579c-102">Método ICorDebugDataTarget::GetPlatform</span><span class="sxs-lookup"><span data-stu-id="c579c-102">ICorDebugDataTarget::GetPlatform Method</span></span>
<span data-ttu-id="c579c-103">Fornece informações sobre a plataforma, incluindo a arquitetura do processador e sistema operacional, que está executando o processo de destino.</span><span class="sxs-lookup"><span data-stu-id="c579c-103">Provides information about the platform, including processor architecture and operating system, on which the target process is running.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c579c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c579c-104">Syntax</span></span>  
  
```  
HRESULT GetPlatform([out] CorDebugPlatform * pTargetPlatform);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c579c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c579c-105">Parameters</span></span>  
 `pTargetPlatform`  
 <span data-ttu-id="c579c-106">[out] Um ponteiro para um [CorDebugPlatformEnum](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md) enumeração que descreve a plataforma de destino.</span><span class="sxs-lookup"><span data-stu-id="c579c-106">[out] A pointer to a [CorDebugPlatformEnum](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md) enumeration that describes the target platform.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c579c-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="c579c-107">Remarks</span></span>  
 <span data-ttu-id="c579c-108">O `CorDebugPlatformEnum` valor de retorno de enumeração é usado pelas [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interface para determinar os detalhes do processo de destino, como seu tamanho do ponteiro, layout do espaço de endereço, o conjunto de registro, o formato de instrução, layout de contexto, e convenções de chamada.</span><span class="sxs-lookup"><span data-stu-id="c579c-108">The `CorDebugPlatformEnum` enumeration return value is used by the [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interface to determine details of the target process such as its pointer size, address space layout, register set, instruction format, context layout, and calling conventions.</span></span>  
  
 <span data-ttu-id="c579c-109">O `pTargetPlatform` valor pode se referir a uma plataforma que está sendo emulada para o destino em vez de especificar o hardware real em uso.</span><span class="sxs-lookup"><span data-stu-id="c579c-109">The `pTargetPlatform` value may refer to a platform that is being emulated for the target instead of specifying the actual hardware in use.</span></span> <span data-ttu-id="c579c-110">Por exemplo, um processo que esteja executando o Windows no ambiente do Windows (WOW) em uma edição de 64 bits do sistema operacional Windows deve usar o `CORDB_PLATFORM_WINDOWS_X86` valor de [CorDebugPlatformEnum](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md) enumeração.</span><span class="sxs-lookup"><span data-stu-id="c579c-110">For example, a process that is running in the Windows on Windows (WOW) environment on a 64-bit edition of the Windows operating system should use the `CORDB_PLATFORM_WINDOWS_X86` value of the [CorDebugPlatformEnum](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="c579c-111">Esse método deve ter êxito.</span><span class="sxs-lookup"><span data-stu-id="c579c-111">This method must succeed.</span></span> <span data-ttu-id="c579c-112">Se ele falhar, a plataforma de destino é inutilizável.</span><span class="sxs-lookup"><span data-stu-id="c579c-112">If it fails, the target platform is unusable.</span></span> <span data-ttu-id="c579c-113">O método pode falhar pelos seguintes motivos:</span><span class="sxs-lookup"><span data-stu-id="c579c-113">The method may fail for the following reasons:</span></span>  
  
- <span data-ttu-id="c579c-114">A plataforma que está sendo emulada para o destino é inutilizável.</span><span class="sxs-lookup"><span data-stu-id="c579c-114">The platform that is being emulated for the target is unusable.</span></span>  
  
- <span data-ttu-id="c579c-115">O hardware real na plataforma de destino pode ser usado.</span><span class="sxs-lookup"><span data-stu-id="c579c-115">The actual hardware on the target platform is unusable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c579c-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c579c-116">Requirements</span></span>  
 <span data-ttu-id="c579c-117">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c579c-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c579c-118">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c579c-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c579c-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c579c-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c579c-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c579c-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c579c-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c579c-121">See also</span></span>

- [<span data-ttu-id="c579c-122">Interface ICorDebugDataTarget</span><span class="sxs-lookup"><span data-stu-id="c579c-122">ICorDebugDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)
- [<span data-ttu-id="c579c-123">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="c579c-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="c579c-124">Depuração</span><span class="sxs-lookup"><span data-stu-id="c579c-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
