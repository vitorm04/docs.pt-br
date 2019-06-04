---
title: Habilitando a depuração por anexação JIT
ms.date: 03/30/2017
helpviewer_keywords:
- JIT-attach debugging
- debugging [.NET Framework], JIT-attach debugging
ms.assetid: f91fc5f7-de5a-4f23-b6ac-f450e63c662e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 005395beabd956767b59e0cebd563fe883f6fe53
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489792"
---
# <a name="enabling-jit-attach-debugging"></a>Habilitando a depuração por anexação JIT
A depuração de anexação JIT é a expressão usada para descrever a anexação de um depurador a um processo quando você encontra erros ou ela pode ser disparada por funções ou métodos específicos.  
  
 A depuração de anexação JIT é usada nas seguintes condições de falha:  
  
- Exceções sem tratamento (no código nativo e gerenciado).  
  
- Método <xref:System.Environment.FailFast%2A?displayProperty=nameWithType> ou função [RaiseFailFastException](https://go.microsoft.com/fwlink/?LinkId=182107) (família Windows 7).  
  
- Erros fatais de tempo de execução.  
  
 A depuração de anexação JIT também é disparada por chamadas às seguintes funções e métodos:  
  
- Método <xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType>.  
  
- Método <xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType>.  
  
- Função [DebugBreak](https://go.microsoft.com/fwlink/?LinkId=182106) (Win32).  
  
 Antes do .NET Framework 4, o .NET Framework fornecia chaves do registro separadas para controlar o comportamento dos depuradores nativos e gerenciados. Começando com o .NET Framework 4, o controle é consolidado em uma única chave do registro: HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\Current version\aedebug. Os valores que podem ser definidos para essa chave determinam se um depurador é invocado e, nesse caso, se ele é invocado com uma caixa de diálogo que exige a interação do usuário. Para obter informações sobre como definir essa chave do registro, consulte [Configurando a depuração automática](https://go.microsoft.com/fwlink/?LinkId=181767).  
  
## <a name="see-also"></a>Consulte também

- [Depuração, rastreamento e criação de perfil](../../../docs/framework/debug-trace-profile/index.md)
- [Facilitando a depuração de uma imagem](../../../docs/framework/debug-trace-profile/making-an-image-easier-to-debug.md)
