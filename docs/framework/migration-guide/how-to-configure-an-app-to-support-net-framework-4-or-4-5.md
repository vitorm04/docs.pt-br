---
title: Como configurar um aplicativo para oferecer suporte ao .NET Framework 4 ou 4.5 | Microsoft Docs
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring apps to support .NET Framework 4
- .NET Framework 4, configuring apps
- .NET Framework 4.5, configuring apps
ms.assetid: 63c6b9a8-0088-4077-9aa3-521ab7290f79
caps.latest.revision: 14
author: mairaw
ms.author: mairaw
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 86dce70e92c0e424b169b6fc58e87c5652ebcb69
ms.lasthandoff: 04/18/2017

---
# <a name="how-to-configure-an-app-to-support-net-framework-4-or-45"></a>Como configurar um aplicativo para oferecer suporte ao .NET Framework 4 ou 4.5
Todos os aplicativos que hospedam o CLR (Common Language Runtime) precisam iniciar ou *ativar* o CLR para executar o código gerenciado. Normalmente, um aplicativo .NET Framework é executado na versão do CLR em que foi criado, mas você pode alterar esse comportamento para aplicativos de área de trabalho usando um arquivo de configuração do aplicativo (às vezes chamado arquivo app.config). No entanto, você não pode alterar o comportamento padrão de ativação para aplicativos da Windows Store ou Windows Phone usando um arquivo de configuração de aplicativo. Este artigo explica como ativar seu aplicativo de área de trabalho para executar em outra versão do .NET Framework e fornece um exemplo de como utilizar a versão 4 ou 4.5.  
  
 A versão do .NET Framework que um aplicativo executa é determinada da seguinte forma:  
  
-   Arquivo de configuração.  
  
     Se o arquivo de configuração do aplicativo incluir as entradas [\<supportedRuntime>](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) que especificam uma ou mais versões do .NET Framework, e uma dessas versões estiver presente no computador do usuário, o aplicativo será executado naquela versão. O arquivo de configuração lê as entradas [\<supportedRuntime>](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) na ordem em que são listadas e usa a primeira versão do .NET Framework listada que está presente no computador do usuário. (Use o elemento [requiredRuntime>\<](../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md) para a versão 1.0.)  
  
-   Versão compilada.  
  
     Se não houver nenhum arquivo de configuração, mas a versão do .NET Framework na qual o arquivo foi compilado estiver presente no computador do usuário, o aplicativo será executado naquela versão.  
  
-   Versão mais recente instalada.  
  
     Se a versão do .NET Framework para a qual o aplicativo foi compilado não estiver presente e um arquivo de configuração não especificar uma versão em um elemento [\<supportedRuntime>](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md), o aplicativo será executado na versão mais recente do .NET Framework presente no computador.  
  
     No entanto, os aplicativos do .NET Framework 1.0, 1.1, 2.0, 3.0, e 3.5 não são executados automaticamente no .NET Framework 4 ou posterior e, em alguns casos, o usuário pode receber um erro e a instalação do .NET Framework 3.5 pode ser solicitada. O comportamento de ativação também pode depender do sistema operacional do usuário, porque as versões diferentes do sistema do Windows incluem diferentes versões do .NET Framework. Se seu aplicativo suportar tanto o .NET Framework 3.5 quanto 4 ou posterior, recomendamos indicar isso com várias entradas no arquivo de configuração do aplicativo para evitar erros de inicialização do .NET Framework. Para saber mais, confira [Versões e dependências](../../../docs/framework/migration-guide/versions-and-dependencies.md).  
  
 Você também pode configurar os aplicativos do .NET Framework 3.5 para executar no .NET Framework 4 ou 4.5, mesmo em computadores que têm o .NET Framework 3.5 instalado, para aproveitar os aprimoramentos de desempenho nas versões 4 e 4.5.  
  
> [!IMPORTANT]
>  Recomendamos que você teste sempre seu aplicativo em cada versão do .NET Framework à qual oferece suporte. Confira [Compatibilidade da versão](../../../docs/framework/migration-guide/version-compatibility.md) para obter informações sobre como atualizar seu aplicativo a fim de aceitar versões mais recentes do .NET Framework.  
  
 Para saber mais sobre como alterar seus aplicativos do .NET Framework 1.0 e 1.1 para oferecer suporte ao Windows 7 e Windows 8, veja [Migrar do .NET Framework 1.1](../../../docs/framework/migration-guide/migrating-from-the-net-framework-1-1.md).  
  
### <a name="to-configure-your-app-to-run-on-the-net-framework-4-or-45"></a>Para configurar seu aplicativo para executar no .NET Framework 4 ou 4.5  
  
1.  Adicione ou localize o arquivo de configuração para o projeto do .NET Framework. O arquivo de configuração para um aplicativo está no mesmo diretório e tem o mesmo nome que o aplicativo, mas tem uma extensão .config. Por exemplo, no caso de um aplicativo chamado MyExecutable.exe, o arquivo de configuração do aplicativo chama-se MyExecutable.exe.config.  
  
     Para adicionar um arquivo de configuração, na barra de menus do Visual Studio, escolha **Projeto**, **Adicionar Novo Item**. Escolha **Geral** no painel esquerdo e, em seguida, escolha **Arquivo de Configuração**.  Nomeie o arquivo de configuração como *appName*.exe.config. Essas opções de menu não estão disponíveis para projetos de aplicativos da Windows Store ou Windows Phone porque não é possível alterar a política de ativação nessas plataformas.  
  
2.  Adicione o elemento [\<supportedRuntime>](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) como a seguir ao arquivo de configuração do aplicativo:  
  
    ```  
    <configuration>  
      <startup>  
        <supportedRuntime version="<version>"/>  
      </startup>  
    </configuration>  
  
    ```  
  
     em que *\<version>* especifica a versão do CLR que se alinha à versão do .NET Framework suportada por seu aplicativo. Use as cadeias de caracteres a seguir:  
  
    -   .NET Framework 1.0: “v1.0.3705”  
  
    -   .NET Framework 1.1: "v1.1.4322"  
  
    -   .NET Framework 2.0, 3.0 e 3.5: “v2.0.50727”  
  
    -   .NET Framework 4 e 4.5 (incluindo versões pontuais como 4.5.1): “v4.0”  
  
     Você pode adicionar vários elementos [\<supportedRuntime>](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) listados por ordem de preferência para especificar o suporte a várias versões do .NET Framework.  
  
 A tabela a seguir demonstra como as configurações do arquivo de configuração do aplicativo e as versões do .NET Framework instaladas em um computador determinam a versão na qual um aplicativo .NET Framework 3.5 é executado. Os exemplos são específicos para um aplicativo .NET Framework 3.5, mas você pode usar uma lógica semelhante para destinar aplicativos criados com versões anteriores do .NET Framework. Observe que o .NET Framework 2.0 (v2.0.50727) é usado para especificar o .NET Framework 3.5 no arquivo de configuração do aplicativo.  
  
|Configuração do arquivo App.config|Em computadores com a versão 3.5 instalada|Em computadores com as versões 3.5 e 4 ou 4.5 instaladas|Em computadores com a versão 4 ou 4.5 instalada|  
|-|-|-|-|  
|Nenhum|Executa na versão 3.5|Executa na versão 3.5|Exibe uma mensagem de erro que solicita ao usuário instalar a versão correta*|  
|`<supportedRuntime version="v2.0.50727"/>`|Executa na versão 3.5|Executa na versão 3.5|Exibe uma mensagem de erro que solicita ao usuário instalar a versão correta*|  
|`<supportedRuntime version="v2.0.50727"/>` <br /> `<supportedRuntime version="v4.0"/>`|Executa na versão 3.5|Executa na versão 3.5|Executa na versão 4 ou 4.5|  
|`<supportedRuntime version="v4.0"/>` <br /> `<supportedRuntime version="v2.0.50727"/>`|Executa na versão 3.5|Executa na versão 4 ou 4.5|Executa na versão 4 ou 4.5|  
|`<supportedRuntime version="v4.0"/>`|Exibe uma mensagem de erro que solicita ao usuário instalar a versão correta*|Executa na versão 4 ou 4.5|Executa na versão 4 ou 4.5|  
  
 \* Para saber mais sobre essa mensagem de erro e como evitá-la, veja [Erros de inicialização do .NET Framework: Gerenciar a experiência do usuário](../../../docs/framework/deployment/initialization-errors-managing-the-user-experience.md).  
  
## <a name="see-also"></a>Consulte também  
 [Migrar do .NET Framework 1.1](../../../docs/framework/migration-guide/migrating-from-the-net-framework-1-1.md)   
 [Guia de Migração](../../../docs/framework/migration-guide/index.md)
