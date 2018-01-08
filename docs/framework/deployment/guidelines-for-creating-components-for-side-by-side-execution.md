---
title: "Diretrizes para criação de componentes para execução lado a lado"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- side-by-side execution, multiple application versions
- side-by-side execution, multiple component versions
ms.assetid: 5c540161-6e40-42e9-be92-6175aee2c46a
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0c914b566727d882939c23a982fad5db12985de5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="guidelines-for-creating-components-for-side-by-side-execution"></a>Diretrizes para criação de componentes para execução lado a lado
Siga estas diretrizes gerais para criar aplicativos gerenciados ou componentes projetados para execução lado a lado:  
  
-   Associe a identidade de tipo a uma versão específica de um arquivo.  
  
     O Common Language Runtime vincula a identidade de tipo a uma versão de arquivo específica usando assemblies de nome forte. Para criar um aplicativo ou componente para execução lado a lado, você deve atribuir um nome forte a todos os assemblies. Isso cria a identidade de tipo preciso e garante que a resolução de qualquer tipo seja direcionada para o arquivo correto. Um assembly de nome forte contém a versão, a cultura e as informações do publicador que o tempo de execução usa para localizar o arquivo correto para atender a uma solicitação de associação.  
  
-   Use o armazenamento com reconhecimento de versão.  
  
     O tempo de execução usa cache de assembly global para fornecer o armazenamento com reconhecimento de versão. O cache de assembly global é uma estrutura de diretórios com reconhecimento de versão instalada em todos os computadores que usam o .NET Framework. Os assemblies instalados no cache de assembly global não são substituídos quando uma nova versão do assembly é instalada.  
  
-   Crie um aplicativo ou componente que é executado isoladamente.  
  
     Um aplicativo ou componente que é executado isoladamente deve gerenciar recursos para evitar conflitos quando duas instâncias do aplicativo ou componente forem executadas simultaneamente. O aplicativo ou componente também deve usar uma estrutura de arquivos específica da versão.  
  
## <a name="application-and-component-isolation"></a>Isolamento de componente e de aplicativo  
 Uma chave para criar com êxito um aplicativo ou componente para execução lado a lado é o isolamento. O aplicativo ou componente deve gerenciar todos os recursos, especialmente E/S de arquivos, de maneira isolada. Siga estas diretrizes para garantir que seu aplicativo ou componente seja executado isoladamente:  
  
-   Grave o Registro de uma maneira específica da versão. Armazene valores em hives ou chaves que indicam a versão e não compartilham informações ou o estado entre as versões de um componente. Isso impede que dois aplicativos ou componentes em execução ao mesmo tempo substituam as informações.  
  
-   Torne os objetos kernel nomeados específicos da versão para que não ocorra uma condição de corrida. Por exemplo, uma condição de corrida ocorre quando dois semáforos de duas versões do mesmo aplicativo esperam um pelo outro.  
  
-   Deixe os nomes de arquivo e diretório com reconhecimento de versão. Isso significa que as estruturas de arquivos devem contar com informações de versão.  
  
-   Crie grupos e contas de usuário de uma maneira específica da versão. Contas de usuário e grupos criados por um aplicativo devem ser identificados pela versão. Não compartilhe as contas de usuário e grupos entre versões de um aplicativo.  
  
## <a name="installing-and-uninstalling-versions"></a>Instalando e desinstalando versões  
 Ao criar um aplicativo para a execução lado a lado, siga estas diretrizes sobre a instalação e desinstalação de versões:  
  
-   Não exclua informações do Registro que podem ser necessárias para outros aplicativos em execução em uma versão diferente do .NET Framework.  
  
-   Não substitua informações no Registro que podem ser necessárias para outros aplicativos em execução em uma versão diferente do .NET Framework.  
  
-   Não cancele o registro de componentes COM que podem ser necessários para outros aplicativos em execução em uma versão diferente do .NET Framework.  
  
-   Não altere **InprocServer32** ou outras entradas do Registro para um servidor COM que já foi registrado.  
  
-   Não exclua contas de usuário ou grupos que podem ser necessários para outros aplicativos em execução em uma versão diferente do .NET Framework.  
  
-   Não adicione nada ao Registro que contenha um caminho sem versão.  
  
## <a name="file-version-number-and-assembly-version-number"></a>Número de versão do arquivo e número de versão do Assembly  
 A versão do arquivo é um recurso de versão do Win32 que não é usado pelo tempo de execução. Em geral, você atualiza a versão do arquivo até mesmo para uma atualização in-loco. Dois arquivos idênticos podem ter informações de versão de arquivo diferentes e dois arquivos diferentes podem ter as mesmas informações de versão do arquivo.  
  
 A versão do assembly é usada pelo tempo de execução para a associação do assembly. Dois assemblies idênticos com números de versão diferentes são tratados como dois assemblies diferentes pelo tempo de execução.  
  
 A [ferramenta Cache de Assembly Global (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) permite que você substitua um assembly quando apenas o número de versão do arquivo é mais recente. O instalador geralmente não instala em um assembly, a menos que o número de versão do assembly seja maior.  
  
## <a name="see-also"></a>Consulte também  
 [Execução lado a lado](../../../docs/framework/deployment/side-by-side-execution.md)  
 [Como habilitar e desabilitar o redirecionamento automático de associações](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)
