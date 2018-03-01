---
title: "Método ICorDebugRemote::CreateProcessEx"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 25c6e8455bf5154a841d302a7f97db8f5ce0c381
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugremotecreateprocessex-method"></a>Método ICorDebugRemote::CreateProcessEx
Inicia um processo em um computador remoto sob o depurador.  
  
## <a name="syntax"></a>Sintaxe  
  
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
  
#### <a name="parameters"></a>Parâmetros  
 `pRemoteTarget`  
 [in] Ponteiro para um [Interface ICorDebugRemoteTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md). Usado para determinar o computador remoto no qual o processo será iniciado.  
  
 `lpApplicationName`  
 [in] Ponteiro para uma cadeia de caracteres terminada em nulo que especifica o módulo a ser executado pelo processo iniciado. O módulo é executado no contexto de segurança do processo de chamada.  
  
 `lpCommandLine`  
 [in] Ponteiro para uma cadeia de caracteres terminada em nulo que especifica a linha de comando a ser executado pelo processo iniciado.  
  
 `lpProcessAttributes`  
 [in] Não usado para depuração remota.  
  
 `lpThreadAttributes`  
 [in] Não usado para depuração remota.  
  
 `bInheritHandles`  
 [in] Não usado para depuração remota.  
  
 `dwCreationFlags`  
 [in] Não usado para depuração remota.  
  
 `lpEnvironment`  
 [in] Ponteiro para um bloco de ambiente para o novo processo.  
  
 `lpCurrentDirectory`  
 [in] Ponteiro para uma cadeia de caracteres terminada em nulo que especifica o caminho completo para o diretório atual para o processo. Se esse parâmetro for null, o novo processo terá a mesma unidade atual e o diretório como o processo de chamada.  
  
 `lpStartupInfo`  
 [in] Não usado para depuração remota.  
  
 `lpProcessInformation`  
 [in] Não usado para depuração remota.  
  
 `debuggingFlags`  
 [in] Não usado para depuração remota.  
  
 `ppProcess`  
 [out] Um ponteiro para o endereço de um objeto de "ICorDebugProcess Interface" que representa o processo.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK  
 O processo no computador remoto e retornado um "Interface ICorDebugProcess" foi iniciada com êxito para a depuração.  
  
 E_FAIL (ou outros códigos de retorno E_)  
 Não é possível iniciar o processo no computador remoto e retornar "ICorDebugProcess Interface" para depuração.  
  
## <a name="remarks"></a>Comentários  
 Não há suporte para a depuração de modo misto no Silverlight.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** 4.5, 4, 3.5 SP1  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorDebugRemote](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)  
 [Interface ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
    
 [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
