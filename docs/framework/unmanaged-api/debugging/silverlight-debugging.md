---
title: Depuração Silverlight
ms.date: 03/30/2017
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: 5e903e04-17d0-4014-ac9a-a43330ec8b1c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 80cee666a05432099a380a5ac547a5ca28698c31
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="silverlight-debugging"></a>Depuração Silverlight
Os tópicos nesta seção descrevem o ambiente e interfaces que fornece o common language runtime (CLR) para dar suporte a depuração de aplicativos baseados no Silverlight que estão executando o sistema operacional Windows, ou na plataforma Macintosh.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Função EnumerateCLRs](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)  
 Fornece um mecanismo para enumerar CLRs em um processo.  
  
 [Função CloseCLREnumeration](../../../../docs/framework/unmanaged-api/debugging/closeclrenumeration-function.md)  
 Fecha qualquer evento de inicialização continuar CLR válido localizado em uma matriz de identificadores retornado pelo [função EnumerateCLRs](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)e libera a memória para as matrizes de caminho do identificador e a cadeia de caracteres.  
  
 [Função CreateCoreClrDebugTarget](../../../../docs/framework/unmanaged-api/debugging/createcoreclrdebugtarget-function.md)  
 Cria uma conexão para um destino remoto para enumeração de processo e o tempo de execução.  
  
 [Função CreateCordbObject](../../../../docs/framework/unmanaged-api/debugging/createcordbobject-function.md)  
 Cria uma interface de depurador que fornece funcionalidade para criar uma instância de uma sessão de depuração gerenciada em um processo remoto.  
  
 [Função CreateVersionStringFromModule](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)  
 Cria uma cadeia de caracteres de versão de um caminho CLR em um processo de destino.  
  
 [Função CreateDebuggingInterfaceFromVersion](../../../../docs/framework/unmanaged-api/debugging/createdebugginginterfacefromversion-function-for-silverlight.md)  
 Aceita uma cadeia de caracteres de versão do CLR retornado de [função CreateVersionStringFromModule](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)de função e retorna uma interface de depurador correspondente.  
  
 [Estrutura CoreClrDebugProcInfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md)  
 Representa um processo que está em execução em um computador remoto.  
  
 [Estrutura CoreClrDebugRuntimeInfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugruntimeinfo-structure.md)  
 Representa uma instância do CLR que é carregada em um processo em um computador remoto.  
  
 [Função GetStartupNotificationEvent](../../../../docs/framework/unmanaged-api/debugging/getstartupnotificationevent-function.md)  
 Cria ou abre um identificador de evento será sinalizado após qualquer common language runtime (CLR) que está sendo carregado no processo de destino especificado.  
  
 [Interface ICoreClrDebugTarget](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)  
 Cria uma conexão para um destino remoto para enumeração de processo e o tempo de execução.  
  
 [Função InitDbgTransportManager](../../../../docs/framework/unmanaged-api/debugging/initdbgtransportmanager-function.md)  
 Inicializa o Gerenciador de transporte para se conectar a um destino remoto para enumeração de processo e o tempo de execução.  
  
 [Função ShutdownDbgTransportManager](../../../../docs/framework/unmanaged-api/debugging/shutdowndbgtransportmanager-function.md)  
 Desliga o Gerenciador de transporte para uma conexão a uma máquina de destino remoto.  
  
## <a name="see-also"></a>Consulte também  
 [Depurando coclasses](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
 [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Depurando funções estáticas globais](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)  
 [Declarando enumerações](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
 [Estruturas de depuração](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
