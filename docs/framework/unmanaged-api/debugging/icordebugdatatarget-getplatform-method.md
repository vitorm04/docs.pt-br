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
ms.openlocfilehash: 3654c94975d16e35d5c3d8e762730d17509a2c6d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788874"
---
# <a name="icordebugdatatargetgetplatform-method"></a><span data-ttu-id="cf195-102">Método ICorDebugDataTarget::GetPlatform</span><span class="sxs-lookup"><span data-stu-id="cf195-102">ICorDebugDataTarget::GetPlatform Method</span></span>
<span data-ttu-id="cf195-103">Fornece informações sobre a plataforma, incluindo arquitetura do processador e sistema operacional, em que o processo de destino está em execução.</span><span class="sxs-lookup"><span data-stu-id="cf195-103">Provides information about the platform, including processor architecture and operating system, on which the target process is running.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf195-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cf195-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPlatform([out] CorDebugPlatform * pTargetPlatform);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cf195-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cf195-105">Parameters</span></span>  
 `pTargetPlatform`  
 <span data-ttu-id="cf195-106">fora Um ponteiro para uma enumeração [CorDebugPlatformEnum](cordebugplatform-enumeration.md) que descreve a plataforma de destino.</span><span class="sxs-lookup"><span data-stu-id="cf195-106">[out] A pointer to a [CorDebugPlatformEnum](cordebugplatform-enumeration.md) enumeration that describes the target platform.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cf195-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="cf195-107">Remarks</span></span>  
 <span data-ttu-id="cf195-108">O valor de retorno de enumeração de `CorDebugPlatformEnum` é usado pela interface [ICorDebug](icordebug-interface.md) para determinar os detalhes do processo de destino, como o tamanho do ponteiro, o layout do espaço de endereço, o conjunto de registros, o formato de instrução, o layout do contexto e as convenções de chamada.</span><span class="sxs-lookup"><span data-stu-id="cf195-108">The `CorDebugPlatformEnum` enumeration return value is used by the [ICorDebug](icordebug-interface.md) interface to determine details of the target process such as its pointer size, address space layout, register set, instruction format, context layout, and calling conventions.</span></span>  
  
 <span data-ttu-id="cf195-109">O valor `pTargetPlatform` pode se referir a uma plataforma que está sendo emulada para o destino em vez de especificar o hardware real em uso.</span><span class="sxs-lookup"><span data-stu-id="cf195-109">The `pTargetPlatform` value may refer to a platform that is being emulated for the target instead of specifying the actual hardware in use.</span></span> <span data-ttu-id="cf195-110">Por exemplo, um processo em execução no ambiente do Windows no Windows (WOW) em uma edição de 64 bits do sistema operacional Windows deve usar o valor `CORDB_PLATFORM_WINDOWS_X86` da enumeração [CorDebugPlatformEnum](cordebugplatform-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="cf195-110">For example, a process that is running in the Windows on Windows (WOW) environment on a 64-bit edition of the Windows operating system should use the `CORDB_PLATFORM_WINDOWS_X86` value of the [CorDebugPlatformEnum](cordebugplatform-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="cf195-111">Esse método deve ter sucesso.</span><span class="sxs-lookup"><span data-stu-id="cf195-111">This method must succeed.</span></span> <span data-ttu-id="cf195-112">Se falhar, a plataforma de destino será inutilizável.</span><span class="sxs-lookup"><span data-stu-id="cf195-112">If it fails, the target platform is unusable.</span></span> <span data-ttu-id="cf195-113">O método pode falhar pelos seguintes motivos:</span><span class="sxs-lookup"><span data-stu-id="cf195-113">The method may fail for the following reasons:</span></span>  
  
- <span data-ttu-id="cf195-114">A plataforma que está sendo emulada para o destino é inutilizável.</span><span class="sxs-lookup"><span data-stu-id="cf195-114">The platform that is being emulated for the target is unusable.</span></span>  
  
- <span data-ttu-id="cf195-115">O hardware real na plataforma de destino é inutilizável.</span><span class="sxs-lookup"><span data-stu-id="cf195-115">The actual hardware on the target platform is unusable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf195-116">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="cf195-116">Requirements</span></span>  
 <span data-ttu-id="cf195-117">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf195-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf195-118">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cf195-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cf195-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cf195-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cf195-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf195-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf195-121">Veja também</span><span class="sxs-lookup"><span data-stu-id="cf195-121">See also</span></span>

- [<span data-ttu-id="cf195-122">Interface ICorDebugDataTarget</span><span class="sxs-lookup"><span data-stu-id="cf195-122">ICorDebugDataTarget Interface</span></span>](icordebugdatatarget-interface.md)
- [<span data-ttu-id="cf195-123">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="cf195-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="cf195-124">Depuração</span><span class="sxs-lookup"><span data-stu-id="cf195-124">Debugging</span></span>](index.md)
