---
title: Depuração Silverlight
ms.date: 03/30/2017
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: 5e903e04-17d0-4014-ac9a-a43330ec8b1c
ms.openlocfilehash: b7af03197a43976c47b7ddc30346d622e6b97207
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139144"
---
# <a name="silverlight-debugging"></a>Depuração Silverlight
Os tópicos nesta seção descrevem o ambiente e as interfaces que o Common Language Runtime (CLR) fornece para dar suporte à depuração de aplicativos baseados no Silverlight que estão em execução no sistema operacional Windows ou na plataforma Macintosh.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Função EnumerateCLRs](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)  
 Fornece um mecanismo para enumerar o CLRs em um processo.  
  
 [Função CloseCLREnumeration](../../../../docs/framework/unmanaged-api/debugging/closeclrenumeration-function.md)  
 Fecha qualquer evento válido de inicialização de continuidade do CLR localizado em uma matriz de identificadores retornada pela [função EnumerateCLRs](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)e libera a memória para as matrizes de caminho de cadeia de caracteres e identificador.  
  
 [Função CreateCoreClrDebugTarget](../../../../docs/framework/unmanaged-api/debugging/createcoreclrdebugtarget-function.md)  
 Cria uma conexão com um destino remoto para enumeração de processo e tempo de execução.  
  
 [Função CreateCordbObject](../../../../docs/framework/unmanaged-api/debugging/createcordbobject-function.md)  
 Cria uma interface do depurador que fornece funcionalidade para instanciar uma sessão de depuração gerenciada em um processo remoto.  
  
 [Função CreateVersionStringFromModule](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)  
 Cria uma cadeia de caracteres de versão a partir de um caminho CLR em um processo de destino.  
  
 [Função CreateDebuggingInterfaceFromVersion](../../../../docs/framework/unmanaged-api/debugging/createdebugginginterfacefromversion-function-for-silverlight.md)  
 Aceita uma cadeia de caracteres de versão do CLR retornada da função de [função CreateVersionStringFromModule](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)e retorna uma interface de depurador correspondente.  
  
 [Estrutura CoreClrDebugProcInfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md)  
 Representa um processo que está sendo executado em um computador remoto.  
  
 [Estrutura CoreClrDebugRuntimeInfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugruntimeinfo-structure.md)  
 Representa uma instância do CLR que é carregada em um processo em um computador remoto.  
  
 [Função GetStartupNotificationEvent](../../../../docs/framework/unmanaged-api/debugging/getstartupnotificationevent-function.md)  
 Cria ou abre um identificador de evento que será sinalizado por qualquer Common Language Runtime (CLR) que esteja carregando no processo de destino especificado.  
  
 [Interface ICoreClrDebugTarget](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)  
 Cria uma conexão com um destino remoto para enumeração de processo e tempo de execução.  
  
 [Função InitDbgTransportManager](../../../../docs/framework/unmanaged-api/debugging/initdbgtransportmanager-function.md)  
 Inicializa o Gerenciador de transporte para se conectar a um destino remoto para enumeração de processo e tempo de execução.  
  
 [Função ShutdownDbgTransportManager](../../../../docs/framework/unmanaged-api/debugging/shutdowndbgtransportmanager-function.md)  
 Desliga o Gerenciador de transporte para uma conexão a um computador de destino remoto.  
  
## <a name="see-also"></a>Consulte também

- [Depurando coclasses](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)
- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Depurando funções estáticas globais](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
- [Declarando enumerações](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [Estruturas de depuração](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
