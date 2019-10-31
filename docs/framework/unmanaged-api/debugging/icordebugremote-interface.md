---
title: Interface ICorDebugRemote
ms.date: 03/30/2017
api_name:
- ICorDebugRemote
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemote
helpviewer_keywords:
- ICorDebugRemote interface [.NET Framework debugging]
ms.assetid: 53d073c6-fa02-40d2-82e1-b9452bb6abaa
topic_type:
- apiref
ms.openlocfilehash: a7eb2796de060b3a5dc8e8c08d07e6aeeb3daecb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131260"
---
# <a name="icordebugremote-interface"></a><span data-ttu-id="74327-102">Interface ICorDebugRemote</span><span class="sxs-lookup"><span data-stu-id="74327-102">ICorDebugRemote Interface</span></span>
<span data-ttu-id="74327-103">Fornece a capacidade de iniciar ou anexar um depurador gerenciado a um processo remoto de destino.</span><span class="sxs-lookup"><span data-stu-id="74327-103">Provides the ability to launch or attach a managed debugger to a remote target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74327-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="74327-104">Syntax</span></span>  
  
```cpp  
interface ICorDebugRemote : IUnknown  
{  
    HRESULT CreateProcessEx  
      (  
      [in] ICorDebugRemoteTarget *     pRemoteTarget,  
      [in] LPCWSTR                     lpApplicationName,  
      [in] LPWSTR                      lpCommandLine,  
      [in] LPSECURITY_ATTRIBUTES       lpProcessAttributes,  
      [in] LPSECURITY_ATTRIBUTES       lpThreadAttributes,  
      [in] BOOL                        bInheritHandles,  
      [in] DWORD                       dwCreationFlags,  
      [in] PVOID                       lpEnvironment,  
      [in] LPCWSTR                     lpCurrentDirectory,  
      [in] LPSTARTUPINFOW              lpStartupInfo,  
      [in] LPPROCESS_INFORMATION       lpProcessInformation,  
      [in] CorDebugCreateProcessFlags  debuggingFlags,  
      [out] ICorDebugProcess **        ppProcess  
      );  
  
    HRESULT DebugActiveProcessEx  
      (  
      [in] ICorDebugRemoteTarget *   pRemoteTarget,  
      [in] DWORD                     dwProcessId,  
      [in] BOOL                      fWin32Attach,  
      [out] ICorDebugProcess **      ppProcess  
      );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="74327-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="74327-105">Methods</span></span>  
  
|<span data-ttu-id="74327-106">Método</span><span class="sxs-lookup"><span data-stu-id="74327-106">Method</span></span>|<span data-ttu-id="74327-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="74327-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="74327-108">Método ICorDebugRemote::CreateProcessEx</span><span class="sxs-lookup"><span data-stu-id="74327-108">ICorDebugRemote::CreateProcessEx Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-createprocessex-method.md)|<span data-ttu-id="74327-109">Cria um processo em um computador remoto para depuração gerenciada.</span><span class="sxs-lookup"><span data-stu-id="74327-109">Creates a process on a remote machine for managed debugging.</span></span>|  
|[<span data-ttu-id="74327-110">Método ICorDebugRemote::DebugActiveProcessEx</span><span class="sxs-lookup"><span data-stu-id="74327-110">ICorDebugRemote::DebugActiveProcessEx Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-debugactiveprocessex-method.md)|<span data-ttu-id="74327-111">Inicia um processo em um computador remoto sob o depurador.</span><span class="sxs-lookup"><span data-stu-id="74327-111">Launches a process on a remote machine under the debugger.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="74327-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="74327-112">Remarks</span></span>  
 <span data-ttu-id="74327-113">Atualmente, essa funcionalidade tem suporte apenas para a depuração de um destino de aplicativo baseado no Silverlight que está sendo executado em um computador Macintosh remoto.</span><span class="sxs-lookup"><span data-stu-id="74327-113">Currently, this functionality is supported only for debugging a Silverlight-based application target that is running on a remote Macintosh machine.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74327-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="74327-114">Requirements</span></span>  
 <span data-ttu-id="74327-115">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74327-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74327-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="74327-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="74327-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="74327-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="74327-118">**Versões do .NET Framework:** 4,5, 4, 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="74327-118">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74327-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="74327-119">See also</span></span>

- [<span data-ttu-id="74327-120">Interface ICorDebugRemoteTarget</span><span class="sxs-lookup"><span data-stu-id="74327-120">ICorDebugRemoteTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)
- [<span data-ttu-id="74327-121">Interface ICorDebug</span><span class="sxs-lookup"><span data-stu-id="74327-121">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

- [<span data-ttu-id="74327-122">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="74327-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
