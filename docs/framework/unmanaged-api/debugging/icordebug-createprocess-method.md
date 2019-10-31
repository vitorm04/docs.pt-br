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
ms.openlocfilehash: 8812a98b0f28dd1336903dc34682f638a291f53b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73111004"
---
# <a name="icordebugcreateprocess-method"></a>Método ICorDebug::CreateProcess
Inicia um processo e seu thread principal sob o controle do depurador.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
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
 no Ponteiro para uma cadeia de caracteres terminada em nulo que especifica o módulo a ser executado pelo processo iniciado. O módulo é executado no contexto de segurança do processo de chamada.  
  
 `lpCommandLine`  
 no Ponteiro para uma cadeia de caracteres terminada em nulo que especifica a linha de comando a ser executada pelo processo iniciado. O nome do aplicativo (por exemplo, "SomeApp. exe") deve ser o primeiro argumento.  
  
 `lpProcessAttributes`  
 no Ponteiro para uma estrutura de `SECURITY_ATTRIBUTES` Win32 que especifica o descritor de segurança para o processo. Se `lpProcessAttributes` for NULL, o processo obterá um descritor de segurança padrão.  
  
 `lpThreadAttributes`  
 no Ponteiro para uma estrutura de `SECURITY_ATTRIBUTES` Win32 que especifica o descritor de segurança para o thread principal do processo. Se `lpThreadAttributes` for NULL, o thread obterá um descritor de segurança padrão.  
  
 `bInheritHandles`  
 no Defina como `true` para indicar que cada identificador herdável no processo de chamada é herdado pelo processo iniciado ou `false` para indicar que os identificadores não são herdados. Os identificadores herdados têm o mesmo valor e direitos de acesso que os identificadores originais.  
  
 `dwCreationFlags`  
 no Uma combinação de bits de bit que indica os [sinalizadores de criação de processos do Win32](https://go.microsoft.com/fwlink/?linkid=69981) que controlam a classe de prioridade e o comportamento do processo iniciado.  
  
 `lpEnvironment`  
 no Ponteiro para um bloco de ambiente para o novo processo.  
  
 `lpCurrentDirectory`  
 no Ponteiro para uma cadeia de caracteres terminada em nulo que especifica o caminho completo para o diretório atual para o processo. Se esse parâmetro for nulo, o novo processo terá a mesma unidade e diretório atuais que o processo de chamada.  
  
 `lpStartupInfo`  
 no Ponteiro para uma estrutura de `STARTUPINFOW` Win32 que especifica a estação de janela, a área de trabalho, os identificadores padrão e a aparência da janela principal para o processo iniciado.  
  
 `lpProcessInformation`  
 no Ponteiro para uma estrutura de `PROCESS_INFORMATION` Win32 que especifica as informações de identificação sobre o processo a ser iniciado.  
  
 `debuggingFlags`  
 no Um valor da Enumeração CorDebugCreateProcessFlags que especifica as opções de depuração.  
  
 `ppProcess`  
 fora Um ponteiro para o endereço de um objeto ICorDebugProcess que representa o processo.  
  
## <a name="remarks"></a>Comentários  
 Os parâmetros desse método são os mesmos do método de `CreateProcess` do Win32.  
  
 Para habilitar a depuração de modo misto não gerenciado, defina `dwCreationFlags` como DEBUG_PROCESS &#124; DEBUG_ONLY_THIS_PROCESS. Se você quiser usar apenas a depuração gerenciada, não defina esses sinalizadores.  
  
 Se o depurador e o processo a serem depurados (o processo anexado) compartilharem um único console e se a depuração de interoperabilidade for usada, é possível que o processo anexado Mantenha os bloqueios do console e pare em um evento de depuração. O depurador bloqueará qualquer tentativa de usar o console. Para evitar esse problema, defina o sinalizador CREATE_NEW_CONSOLE no parâmetro `dwCreationFlags`.  
  
 Não há suporte para depuração de interoperabilidade em plataformas Win9x e não x86, como plataformas baseadas em IA-64 e AMD64.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
