---
title: Método ICorDebug::CreateProcess
ms.date: 03/30/2017
api_name:
- ICorDebug.CreateProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::CreateProcess
helpviewer_keywords:
- ICorDebug::CreateProcess method [.NET Framework debugging]
- CreateProcess method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: b6128694-11ed-46e7-bd4e-49ea1914c46a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 795392bc50d4b7c5eeb82b98230a52156f273f15
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59187363"
---
# <a name="icordebugcreateprocess-method"></a>Método ICorDebug::CreateProcess
Inicia um processo e thread primário, sob o controle do depurador.  
  
## <a name="syntax"></a>Sintaxe  
  
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
  
## <a name="parameters"></a>Parâmetros  
 `lpApplicationName`  
 [in] Ponteiro para uma cadeia de caracteres terminada em nulo que especifica o módulo a ser executado, o processo iniciado. O módulo é executado no contexto de segurança do processo de chamada.  
  
 `lpCommandLine`  
 [in] Ponteiro para uma cadeia de caracteres terminada em nulo que especifica a linha de comando a ser executado, o processo iniciado. O nome do aplicativo (por exemplo, "SomeApp.exe") deve ser o primeiro argumento.  
  
 `lpProcessAttributes`  
 [in] Ponteiro para um Win32 `SECURITY_ATTRIBUTES` estrutura que especifica o descritor de segurança para o processo. Se `lpProcessAttributes` é nulo, o processo obtém um descritor de segurança padrão.  
  
 `lpThreadAttributes`  
 [in] Ponteiro para um Win32 `SECURITY_ATTRIBUTES` estrutura que especifica o descritor de segurança para o thread principal do processo. Se `lpThreadAttributes` é null, o thread obtém um descritor de segurança padrão.  
  
 `bInheritHandles`  
 [in] Definido como `true` para indicar que cada identificador herdável no processo de chamada é herdada pelo processo iniciado, ou `false` para indicar que os identificadores não são herdados. Os identificadores de herdados têm os mesmos direitos de acesso e o valor que as alças originais.  
  
 `dwCreationFlags`  
 [in] Uma combinação bit a bit do [sinalizadores de criação do processo Win32](https://go.microsoft.com/fwlink/?linkid=69981) que controlam a classe de prioridade e o comportamento do processo iniciado.  
  
 `lpEnvironment`  
 [in] Ponteiro para um bloco de ambiente para o novo processo.  
  
 `lpCurrentDirectory`  
 [in] Ponteiro para uma cadeia de caracteres terminada em nulo que especifica o caminho completo para o diretório atual para o processo. Se esse parâmetro for nulo, o novo processo terá a mesma unidade atual e o diretório como o processo de chamada.  
  
 `lpStartupInfo`  
 [in] Ponteiro para um Win32 `STARTUPINFOW` estrutura que especifica a estação de janela, área de trabalho, os identificadores padrão e aparência da janela principal para o processo iniciado.  
  
 `lpProcessInformation`  
 [in] Ponteiro para um Win32 `PROCESS_INFORMATION` estrutura que especifica as informações de identificação sobre o processo a ser iniciado.  
  
 `debuggingFlags`  
 [in] Um valor de enumeração CorDebugCreateProcessFlags que especifica as opções de depuração.  
  
 `ppProcess`  
 [out] Um ponteiro para o endereço de um objeto ICorDebugProcess que representa o processo.  
  
## <a name="remarks"></a>Comentários  
 Os parâmetros desse método são iguais do Win32 `CreateProcess` método.  
  
 Para habilitar a depuração não gerenciada de modo misto, defina `dwCreationFlags` para DEBUG_PROCESS &#124; DEBUG_ONLY_THIS_PROCESS. Se você quiser usar a depuração somente gerenciado, não defina esses sinalizadores.  
  
 Se o depurador e o processo a ser depurado (o processo anexado) compartilham um único console, e se depuração interop for usado, é possível que o processo anexado manter bloqueios de console e parar em um evento de depuração. O depurador, em seguida, irá bloquear qualquer tentativa de usar o console. Para evitar esse problema, defina o sinalizador CREATE_NEW_CONSOLE `dwCreationFlags` parâmetro.  
  
 Não há suporte para depuração Interop em plataformas Win9x e não x86 como plataformas baseadas em IA-64 e com base em AMD64.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
