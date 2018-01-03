---
title: "Método ICorDebug::CreateProcess"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebug.CreateProcess
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebug::CreateProcess
helpviewer_keywords:
- ICorDebug::CreateProcess method [.NET Framework debugging]
- CreateProcess method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: b6128694-11ed-46e7-bd4e-49ea1914c46a
topic_type: apiref
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 16e45f3bad92914ce8c7fb0044534789a7a28b2e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcreateprocess-method"></a><span data-ttu-id="dfd6e-102">Método ICorDebug::CreateProcess</span><span class="sxs-lookup"><span data-stu-id="dfd6e-102">ICorDebug::CreateProcess Method</span></span>
<span data-ttu-id="dfd6e-103">Inicia um processo e o thread principal sob o controle do depurador.</span><span class="sxs-lookup"><span data-stu-id="dfd6e-103">Launches a process and its primary thread under the control of the debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfd6e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dfd6e-104">Syntax</span></span>  
  
```  
HRESULT CreateProcess (  
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
    [out] ICorDebugProcess            **ppProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dfd6e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="dfd6e-105">Parameters</span></span>  
 `lpApplicationName`  
 <span data-ttu-id="dfd6e-106">[in] Ponteiro para uma cadeia de caracteres terminada em nulo que especifica o módulo a ser executado pelo processo iniciado.</span><span class="sxs-lookup"><span data-stu-id="dfd6e-106">[in] Pointer to a null-terminated string that specifies the module to be executed by the launched process.</span></span> <span data-ttu-id="dfd6e-107">O módulo é executado no contexto de segurança do processo de chamada.</span><span class="sxs-lookup"><span data-stu-id="dfd6e-107">The module is executed in the security context of the calling process.</span></span>  
  
 `lpCommandLine`  
 <span data-ttu-id="dfd6e-108">[in] Ponteiro para uma cadeia de caracteres terminada em nulo que especifica a linha de comando a ser executado pelo processo iniciado.</span><span class="sxs-lookup"><span data-stu-id="dfd6e-108">[in] Pointer to a null-terminated string that specifies the command line to be executed by the launched process.</span></span> <span data-ttu-id="dfd6e-109">O nome do aplicativo (por exemplo, "SomeApp.exe") deve ser o primeiro argumento.</span><span class="sxs-lookup"><span data-stu-id="dfd6e-109">The application name (for example, "SomeApp.exe") must be the first argument.</span></span>  
  
 `lpProcessAttributes`  
 <span data-ttu-id="dfd6e-110">[in] Ponteiro para um Win32 `SECURITY_ATTRIBUTES` estrutura que especifica o descritor de segurança para o processo.</span><span class="sxs-lookup"><span data-stu-id="dfd6e-110">[in] Pointer to a Win32 `SECURITY_ATTRIBUTES` structure that specifies the security descriptor for the process.</span></span> <span data-ttu-id="dfd6e-111">Se `lpProcessAttributes` é null, o processo obtém um descritor de segurança padrão.</span><span class="sxs-lookup"><span data-stu-id="dfd6e-111">If `lpProcessAttributes` is null, the process gets a default security descriptor.</span></span>  
  
 `lpThreadAttributes`  
 <span data-ttu-id="dfd6e-112">[in] Ponteiro para um Win32 `SECURITY_ATTRIBUTES` estrutura que especifica o descritor de segurança para o thread principal do processo.</span><span class="sxs-lookup"><span data-stu-id="dfd6e-112">[in] Pointer to a Win32 `SECURITY_ATTRIBUTES` structure that specifies the security descriptor for the primary thread of the process.</span></span> <span data-ttu-id="dfd6e-113">Se `lpThreadAttributes` é null, o thread obtém um descritor de segurança padrão.</span><span class="sxs-lookup"><span data-stu-id="dfd6e-113">If `lpThreadAttributes` is null, the thread gets a default security descriptor.</span></span>  
  
 `bInheritHandles`  
 <span data-ttu-id="dfd6e-114">[in] Definido como `true` para indicar que cada alça herdável no processo de chamada é herdada pelo processo iniciado, ou `false` para indicar que os identificadores não são herdados.</span><span class="sxs-lookup"><span data-stu-id="dfd6e-114">[in] Set to `true` to indicate that each inheritable handle in the calling process is inherited by the launched process, or `false` to indicate that the handles are not inherited.</span></span> <span data-ttu-id="dfd6e-115">Os identificadores de herdadas têm os mesmos direitos de acesso e o valor como os identificadores originais.</span><span class="sxs-lookup"><span data-stu-id="dfd6e-115">The inherited handles have the same value and access rights as the original handles.</span></span>  
  
 `dwCreationFlags`  
 <span data-ttu-id="dfd6e-116">[in] Uma combinação bit a bit do [sinalizadores de criação de processo Win32](http://go.microsoft.com/fwlink/?linkid=69981) que controlam o comportamento do processo iniciado e a classe de prioridade.</span><span class="sxs-lookup"><span data-stu-id="dfd6e-116">[in] A bitwise combination of the [Win32 Process Creation Flags](http://go.microsoft.com/fwlink/?linkid=69981) that control the priority class and the behavior of the launched process.</span></span>  
  
 `lpEnvironment`  
 <span data-ttu-id="dfd6e-117">[in] Ponteiro para um bloco de ambiente para o novo processo.</span><span class="sxs-lookup"><span data-stu-id="dfd6e-117">[in] Pointer to an environment block for the new process.</span></span>  
  
 `lpCurrentDirectory`  
 <span data-ttu-id="dfd6e-118">[in] Ponteiro para uma cadeia de caracteres terminada em nulo que especifica o caminho completo para o diretório atual para o processo.</span><span class="sxs-lookup"><span data-stu-id="dfd6e-118">[in] Pointer to a null-terminated string that specifies the full path to the current directory for the process.</span></span> <span data-ttu-id="dfd6e-119">Se esse parâmetro for null, o novo processo terá a mesma unidade atual e o diretório como o processo de chamada.</span><span class="sxs-lookup"><span data-stu-id="dfd6e-119">If this parameter is null, the new process will have the same current drive and directory as the calling process.</span></span>  
  
 `lpStartupInfo`  
 <span data-ttu-id="dfd6e-120">[in] Ponteiro para um Win32 `STARTUPINFOW` estrutura que especifica a estação de trabalho, a área de trabalho, a identificadores padrão e a aparência da janela principal para o processo iniciado.</span><span class="sxs-lookup"><span data-stu-id="dfd6e-120">[in] Pointer to a Win32 `STARTUPINFOW` structure that specifies the window station, desktop, standard handles, and appearance of the main window for the launched process.</span></span>  
  
 `lpProcessInformation`  
 <span data-ttu-id="dfd6e-121">[in] Ponteiro para um Win32 `PROCESS_INFORMATION` estrutura que especifica as informações de identificação sobre o processo a ser iniciado.</span><span class="sxs-lookup"><span data-stu-id="dfd6e-121">[in] Pointer to a Win32 `PROCESS_INFORMATION` structure that specifies the identification information about the process to be launched.</span></span>  
  
 `debuggingFlags`  
 <span data-ttu-id="dfd6e-122">[in] Um valor da enumeração CorDebugCreateProcessFlags que especifica as opções de depuração.</span><span class="sxs-lookup"><span data-stu-id="dfd6e-122">[in] A value of the CorDebugCreateProcessFlags enumeration that specifies the debugging options.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="dfd6e-123">[out] Um ponteiro para o endereço de um objeto ICorDebugProcess que representa o processo.</span><span class="sxs-lookup"><span data-stu-id="dfd6e-123">[out] A pointer to the address of a ICorDebugProcess object that represents the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dfd6e-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="dfd6e-124">Remarks</span></span>  
 <span data-ttu-id="dfd6e-125">Os parâmetros desse método são iguais do Win32 `CreateProcess` método.</span><span class="sxs-lookup"><span data-stu-id="dfd6e-125">The parameters of this method are the same as those of the Win32 `CreateProcess` method.</span></span>  
  
 <span data-ttu-id="dfd6e-126">Para habilitar a depuração de modo misto não gerenciado, defina `dwCreationFlags` DEBUG_PROCESS &#124; DEBUG_ONLY_THIS_PROCESS.</span><span class="sxs-lookup"><span data-stu-id="dfd6e-126">To enable unmanaged mixed-mode debugging, set `dwCreationFlags` to DEBUG_PROCESS &#124; DEBUG_ONLY_THIS_PROCESS.</span></span> <span data-ttu-id="dfd6e-127">Se você quiser usar a depuração somente gerenciado, não defina esses sinalizadores.</span><span class="sxs-lookup"><span data-stu-id="dfd6e-127">If you want to use only managed debugging, do not set these flags.</span></span>  
  
 <span data-ttu-id="dfd6e-128">Se o depurador e o processo a ser depurado (o processo anexado) compartilham um único console e se a depuração interop for usado, é possível que o processo anexado manter bloqueios de console e parar em um evento de depuração.</span><span class="sxs-lookup"><span data-stu-id="dfd6e-128">If the debugger and the process to be debugged (the attached process) share a single console, and if interop debugging is used, it is possible for the attached process to hold console locks and stop at a debug event.</span></span> <span data-ttu-id="dfd6e-129">O depurador, em seguida, irá bloquear qualquer tentativa de usar o console.</span><span class="sxs-lookup"><span data-stu-id="dfd6e-129">The debugger will then block any attempt to use the console.</span></span> <span data-ttu-id="dfd6e-130">Para evitar esse problema, defina o sinalizador CREATE_NEW_CONSOLE `dwCreationFlags` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="dfd6e-130">To avoid this problem, set the CREATE_NEW_CONSOLE flag in the `dwCreationFlags` parameter.</span></span>  
  
 <span data-ttu-id="dfd6e-131">Não há suporte para depuração Interop em plataformas Win9x e não-x86 como plataformas com base em IA-64 e AMD64.</span><span class="sxs-lookup"><span data-stu-id="dfd6e-131">Interop debugging is not supported on Win9x and non-x86 platforms such as IA-64-based and AMD64-based platforms.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dfd6e-132">Requisitos</span><span class="sxs-lookup"><span data-stu-id="dfd6e-132">Requirements</span></span>  
 <span data-ttu-id="dfd6e-133">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dfd6e-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dfd6e-134">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dfd6e-134">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dfd6e-135">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dfd6e-135">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dfd6e-136">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dfd6e-136">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfd6e-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dfd6e-137">See Also</span></span>  
 [<span data-ttu-id="dfd6e-138">Interface ICorDebug</span><span class="sxs-lookup"><span data-stu-id="dfd6e-138">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
