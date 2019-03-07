---
title: Método ICorDebugRemote::CreateProcessEx
ms.date: 03/30/2017
api_name:
- ICorDebugRemote.CreateProcessEx
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemoteTarget::CreateProcessEx
helpviewer_keywords:
- CreateProcessEx method, ICorDebugRemote interface [.NET Framework debugging]
- ICorDebugRemote::CreateProcessEx method [.NET Framework debugging]
ms.assetid: 41af93c7-e448-4251-8d4d-413d38c635f2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7b8c72a2dde70a93b589181b0cc1bd7824b3f52d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57496515"
---
# <a name="icordebugremotecreateprocessex-method"></a><span data-ttu-id="00729-102">Método ICorDebugRemote::CreateProcessEx</span><span class="sxs-lookup"><span data-stu-id="00729-102">ICorDebugRemote::CreateProcessEx Method</span></span>
<span data-ttu-id="00729-103">Inicia um processo em um computador remoto sob o depurador.</span><span class="sxs-lookup"><span data-stu-id="00729-103">Launches a process on a remote machine under the debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00729-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="00729-104">Syntax</span></span>  
  
```  
HRESULT CreateProcessEx (  
    [in]  ICorDebugRemoteTarget*      pRemoteTarget,  
    [in]  LPCWSTR                     lpApplicationName,  
    [in]  LPWSTR                      lpCommandLine,  
    [in]  LPSECURITY_ATTRIBUTES       lpProcessAttributes,  
    [in]  LPSECURITY_ATTRIBUTES       lpThreadAttributes,  
    [in]  BOOL                        bInheritHandles,  
    [in]  DWORD                       dwCreationFlags,  
    [in]  PVOID                       lpEnvironment,  
    [in]  LPCWSTR                     lpCurrentDirectory,  
    [in]  LPSTARTUPINFOW              lpStartupInfo,  
    [in]  LPPROCESS_INFORMATION       lpProcessInformation,  
    [in]  CorDebugCreateProcessFlags  debuggingFlags,  
    [out] ICorDebugProcess**          ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="00729-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="00729-105">Parameters</span></span>  
 `pRemoteTarget`  
 <span data-ttu-id="00729-106">[in] Ponteiro para um [Interface ICorDebugRemoteTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md).</span><span class="sxs-lookup"><span data-stu-id="00729-106">[in] Pointer to an [ICorDebugRemoteTarget Interface](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md).</span></span> <span data-ttu-id="00729-107">Usado para determinar o computador remoto no qual o processo será iniciado.</span><span class="sxs-lookup"><span data-stu-id="00729-107">Used to determine the remote machine on which the process will be launched.</span></span>  
  
 `lpApplicationName`  
 <span data-ttu-id="00729-108">[in] Ponteiro para uma cadeia de caracteres terminada em nulo que especifica o módulo a ser executado, o processo iniciado.</span><span class="sxs-lookup"><span data-stu-id="00729-108">[in] Pointer to a null-terminated string that specifies the module to be executed by the launched process.</span></span> <span data-ttu-id="00729-109">O módulo é executado no contexto de segurança do processo de chamada.</span><span class="sxs-lookup"><span data-stu-id="00729-109">The module is executed in the security context of the calling process.</span></span>  
  
 `lpCommandLine`  
 <span data-ttu-id="00729-110">[in] Ponteiro para uma cadeia de caracteres terminada em nulo que especifica a linha de comando a ser executado, o processo iniciado.</span><span class="sxs-lookup"><span data-stu-id="00729-110">[in] Pointer to a null-terminated string that specifies the command line to be executed by the launched process.</span></span>  
  
 `lpProcessAttributes`  
 <span data-ttu-id="00729-111">[in] Não utilizado para a depuração remota.</span><span class="sxs-lookup"><span data-stu-id="00729-111">[in] Unused for remote debugging.</span></span>  
  
 `lpThreadAttributes`  
 <span data-ttu-id="00729-112">[in] Não utilizado para a depuração remota.</span><span class="sxs-lookup"><span data-stu-id="00729-112">[in] Unused for remote debugging.</span></span>  
  
 `bInheritHandles`  
 <span data-ttu-id="00729-113">[in] Não utilizado para a depuração remota.</span><span class="sxs-lookup"><span data-stu-id="00729-113">[in] Unused for remote debugging.</span></span>  
  
 `dwCreationFlags`  
 <span data-ttu-id="00729-114">[in] Não utilizado para a depuração remota.</span><span class="sxs-lookup"><span data-stu-id="00729-114">[in] Unused for remote debugging.</span></span>  
  
 `lpEnvironment`  
 <span data-ttu-id="00729-115">[in] Ponteiro para um bloco de ambiente para o novo processo.</span><span class="sxs-lookup"><span data-stu-id="00729-115">[in] Pointer to an environment block for the new process.</span></span>  
  
 `lpCurrentDirectory`  
 <span data-ttu-id="00729-116">[in] Ponteiro para uma cadeia de caracteres terminada em nulo que especifica o caminho completo para o diretório atual para o processo.</span><span class="sxs-lookup"><span data-stu-id="00729-116">[in] Pointer to a null-terminated string that specifies the full path to the current directory for the process.</span></span> <span data-ttu-id="00729-117">Se esse parâmetro for nulo, o novo processo terá a mesma unidade atual e o diretório como o processo de chamada.</span><span class="sxs-lookup"><span data-stu-id="00729-117">If this parameter is null, the new process will have the same current drive and directory as the calling process.</span></span>  
  
 `lpStartupInfo`  
 <span data-ttu-id="00729-118">[in] Não utilizado para a depuração remota.</span><span class="sxs-lookup"><span data-stu-id="00729-118">[in] Unused for remote debugging.</span></span>  
  
 `lpProcessInformation`  
 <span data-ttu-id="00729-119">[in] Não utilizado para a depuração remota.</span><span class="sxs-lookup"><span data-stu-id="00729-119">[in] Unused for remote debugging.</span></span>  
  
 `debuggingFlags`  
 <span data-ttu-id="00729-120">[in] Não utilizado para a depuração remota.</span><span class="sxs-lookup"><span data-stu-id="00729-120">[in] Unused for remote debugging.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="00729-121">[out] Um ponteiro para o endereço de um objeto de "ICorDebugProcess Interface" que representa o processo.</span><span class="sxs-lookup"><span data-stu-id="00729-121">[out] A pointer to the address of a"ICorDebugProcess Interface" object that represents the process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="00729-122">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="00729-122">Return Value</span></span>  
 <span data-ttu-id="00729-123">S_OK</span><span class="sxs-lookup"><span data-stu-id="00729-123">S_OK</span></span>  
 <span data-ttu-id="00729-124">Iniciado com êxito o processo no computador remoto e retornado uma "Interface ICorDebugProcess" para depuração.</span><span class="sxs-lookup"><span data-stu-id="00729-124">Successfully launched the process on the remote machine and returned an "ICorDebugProcess Interface" for debugging.</span></span>  
  
 <span data-ttu-id="00729-125">E_FAIL (ou outros códigos de retorno e _)</span><span class="sxs-lookup"><span data-stu-id="00729-125">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="00729-126">Não é possível iniciar o processo no computador remoto e retornar uma "ICorDebugProcess Interface" para depuração.</span><span class="sxs-lookup"><span data-stu-id="00729-126">Unable to launch the process on the remote machine and return an "ICorDebugProcess Interface" for debugging.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="00729-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="00729-127">Remarks</span></span>  
 <span data-ttu-id="00729-128">Não há suporte para a depuração de modo misto no Silverlight.</span><span class="sxs-lookup"><span data-stu-id="00729-128">Mixed-mode debugging is not supported in Silverlight.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00729-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="00729-129">Requirements</span></span>  
 <span data-ttu-id="00729-130">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00729-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00729-131">**Cabeçalho:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="00729-131">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="00729-132">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="00729-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="00729-133">**Versões do .NET framework:** 4.5, 4, 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="00729-133">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00729-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="00729-134">See also</span></span>
- [<span data-ttu-id="00729-135">Interface ICorDebugRemote</span><span class="sxs-lookup"><span data-stu-id="00729-135">ICorDebugRemote Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)
- [<span data-ttu-id="00729-136">Interface ICorDebug</span><span class="sxs-lookup"><span data-stu-id="00729-136">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

- [<span data-ttu-id="00729-137">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="00729-137">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
