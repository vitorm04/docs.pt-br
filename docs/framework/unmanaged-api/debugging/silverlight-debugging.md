---
title: Depuração Silverlight
ms.date: 03/30/2017
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: 5e903e04-17d0-4014-ac9a-a43330ec8b1c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1d20bc002e52c3c6a42b45c0d1c5d559e65dc52c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59113692"
---
# <a name="silverlight-debugging"></a>Depuração Silverlight
Os tópicos nesta seção descrevem o ambiente e interfaces que o common language runtime (CLR) fornece para dar suporte à depuração de aplicativos baseados no Silverlight que estão em execução no sistema operacional Windows, ou na plataforma Macintosh.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Função EnumerateCLRs](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)  
 Fornece um mecanismo para enumerar os CLRs em um processo.  
  
 [Função CloseCLREnumeration](../../../../docs/framework/unmanaged-api/debugging/closeclrenumeration-function.md)  
 Fecha qualquer eventos de inicialização continuar CLR válidos localizados em uma matriz de identificadores retornado pela [função EnumerateCLRs](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)e libera a memória para as matrizes de caminho do identificador e a cadeia de caracteres.  
  
 [Função CreateCoreClrDebugTarget](../../../../docs/framework/unmanaged-api/debugging/createcoreclrdebugtarget-function.md)  
 Cria uma conexão para um destino remoto para enumeração de processo e o tempo de execução.  
  
 [Função CreateCordbObject](../../../../docs/framework/unmanaged-api/debugging/createcordbobject-function.md)  
 Cria uma interface do depurador que fornece funcionalidade para criar uma instância de uma sessão de depuração gerenciada em um processo remoto.  
  
 [Função CreateVersionStringFromModule](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)  
 Cria uma cadeia de caracteres de versão de um caminho CLR em um processo de destino.  
  
 [Função CreateDebuggingInterfaceFromVersion](../../../../docs/framework/unmanaged-api/debugging/createdebugginginterfacefromversion-function-for-silverlight.md)  
 Aceita uma cadeia de caracteres de versão do CLR retornado de [função CreateVersionStringFromModule](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)de função e retorna uma interface correspondente do depurador.  
  
 [Estrutura CoreClrDebugProcInfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md)  
 Representa um processo que está em execução em um computador remoto.  
  
 [Estrutura CoreClrDebugRuntimeInfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugruntimeinfo-structure.md)  
 Representa uma instância CLR que é carregada em um processo em um computador remoto.  
  
 [Função GetStartupNotificationEvent](../../../../docs/framework/unmanaged-api/debugging/getstartupnotificationevent-function.md)  
 Cria ou abre um identificador de eventos que será sinalizado após qualquer common language runtime (CLR) que está sendo carregada no processo de destino especificado.  
  
 [Interface ICoreClrDebugTarget](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)  
 Cria uma conexão para um destino remoto para enumeração de processo e o tempo de execução.  
  
 [Função InitDbgTransportManager](../../../../docs/framework/unmanaged-api/debugging/initdbgtransportmanager-function.md)  
 Inicializa o Gerenciador de transporte para se conectar a um destino remoto para enumeração de processo e o tempo de execução.  
  
 [Função ShutdownDbgTransportManager](../../../../docs/framework/unmanaged-api/debugging/shutdowndbgtransportmanager-function.md)  
 Desliga o Gerenciador de transporte para uma conexão a uma máquina de destino remoto.  
  
## <a name="see-also"></a>Consulte também

- [Depurando coclasses](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)
- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Depurando funções estáticas globais](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
- [Declarando enumerações](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [Estruturas de depuração](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
