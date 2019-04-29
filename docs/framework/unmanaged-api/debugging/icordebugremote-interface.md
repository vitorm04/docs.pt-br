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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a50a799c625c647aa275994bc92738b8a4267eec
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61782714"
---
# <a name="icordebugremote-interface"></a><span data-ttu-id="5b07b-102">Interface ICorDebugRemote</span><span class="sxs-lookup"><span data-stu-id="5b07b-102">ICorDebugRemote Interface</span></span>
<span data-ttu-id="5b07b-103">Fornece a capacidade de iniciar ou anexar um depurador gerenciado a um processo remoto de destino.</span><span class="sxs-lookup"><span data-stu-id="5b07b-103">Provides the ability to launch or attach a managed debugger to a remote target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b07b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5b07b-104">Syntax</span></span>  
  
```  
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
  
## <a name="methods"></a><span data-ttu-id="5b07b-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="5b07b-105">Methods</span></span>  
  
|<span data-ttu-id="5b07b-106">Método</span><span class="sxs-lookup"><span data-stu-id="5b07b-106">Method</span></span>|<span data-ttu-id="5b07b-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="5b07b-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5b07b-108">Método ICorDebugRemote::CreateProcessEx</span><span class="sxs-lookup"><span data-stu-id="5b07b-108">ICorDebugRemote::CreateProcessEx Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-createprocessex-method.md)|<span data-ttu-id="5b07b-109">Cria um processo em um computador remoto para depuração gerenciada.</span><span class="sxs-lookup"><span data-stu-id="5b07b-109">Creates a process on a remote machine for managed debugging.</span></span>|  
|[<span data-ttu-id="5b07b-110">Método ICorDebugRemote::DebugActiveProcessEx</span><span class="sxs-lookup"><span data-stu-id="5b07b-110">ICorDebugRemote::DebugActiveProcessEx Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-debugactiveprocessex-method.md)|<span data-ttu-id="5b07b-111">Inicia um processo em um computador remoto sob o depurador.</span><span class="sxs-lookup"><span data-stu-id="5b07b-111">Launches a process on a remote machine under the debugger.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5b07b-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="5b07b-112">Remarks</span></span>  
 <span data-ttu-id="5b07b-113">Atualmente, essa funcionalidade tem suporte somente para depuração de um destino de aplicativo baseado em Silverlight que está em execução em um computador remoto do Macintosh.</span><span class="sxs-lookup"><span data-stu-id="5b07b-113">Currently, this functionality is supported only for debugging a Silverlight-based application target that is running on a remote Macintosh machine.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b07b-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5b07b-114">Requirements</span></span>  
 <span data-ttu-id="5b07b-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b07b-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b07b-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5b07b-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5b07b-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5b07b-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5b07b-118">**Versões do .NET framework:** 4.5, 4, 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="5b07b-118">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b07b-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5b07b-119">See also</span></span>

- [<span data-ttu-id="5b07b-120">Interface ICorDebugRemoteTarget</span><span class="sxs-lookup"><span data-stu-id="5b07b-120">ICorDebugRemoteTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)
- [<span data-ttu-id="5b07b-121">Interface ICorDebug</span><span class="sxs-lookup"><span data-stu-id="5b07b-121">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

- [<span data-ttu-id="5b07b-122">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="5b07b-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
