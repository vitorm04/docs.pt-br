---
title: Prompt de Comando do Desenvolvedor para o Visual Studio
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- command prompt, Windows SDK
- Visual Studio command prompt
- command prompt, Visual Studio
- SDK command prompt
- tools [.NET Framework], setting environment variables
- environment variables, setting for tools
- developer command prompt
ms.assetid: 94fcf524-9045-4993-bfb2-e2d8bad44219
caps.latest.revision: "45"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e93a1d116ac0480c80e259ddbadbc65fd9539389
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="developer-command-prompt-for-visual-studio"></a>Prompt de Comando do Desenvolvedor para o Visual Studio
O Prompt de Comando do Desenvolvedor do Visual Studio define automaticamente as variáveis de ambiente que permitem usar as ferramentas do .NET Framework com facilidade. O Prompt de Comando do Desenvolvedor é instalado com as edições completa ou Community do Visual Studio. Ele não é instalado com as versões Express do Visual Studio.  
  
<a name="find"></a>   
## <a name="searching-for-the-command-prompt-on-your-machine"></a>Procurar o prompt de comando no computador  
 Você pode consultar vários prompts de comando, dependendo da versão do Visual Studio e de todos os SDKs adicionais instalados. Por exemplo, as versões 64 bits do Visual Studio oferecem prompts de comando 32 e 64 bits. (As versões 32 e 64 bits da maioria das ferramentas são idênticas; porém, algumas ferramentas fazem alterações específicas em ambientes 32 e 64 bits.) Se estas etapas abaixo não funcionarem, tente [Localizar manualmente os arquivos em seu computador](#alternative) ou [Executar o prompt de comando de dentro do Visual Studio](#visualstudio).  
  
 **No Windows 10**  
  
1.  Abra o menu **Iniciar** pressionando a tecla do logotipo do Windows ![Logotipo do Windows](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") no seu teclado, por exemplo.  
  
2.  No menu **Iniciar**, digite `dev`. Isso exibirá uma lista de aplicativos instalados que correspondem ao seu padrão de pesquisa. Se você estiver procurando por um prompt de comando diferente, experimente digitar um termo de pesquisa diferente, como `prompt`.  
  
3.  Escolha o **Prompt de Comando do Desenvolvedor** (ou o prompt de comando que você deseja usar).  
  
 **No Windows 8.1**  
  
1.  Abra a tela **Iniciar** pressionando a tecla do logotipo do Windows ![Logotipo do Windows](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") no seu teclado, por exemplo.  
  
2.  Na tela **Iniciar**, pressione `CTRL + TAB` para abrir a lista **Aplicativos** e digite `V`. Isso mostrará uma lista que inclui todos os prompts de comando do Visual Studio instalados.  
  
3.  Escolha o **Prompt de Comando do Desenvolvedor** (ou o prompt de comando que você deseja usar).  
  
 **No Windows 8**  
  
1.  Abra a tela **Iniciar** pressionando a tecla do logotipo do Windows ![Logotipo do Windows](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") no seu teclado, por exemplo.  
  
2.  Na tela **Iniciar**, pressione a tecla do logotipo do Windows ![Logotipo do Windows](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") `+ Z`.  
  
3.  Escolha o ícone **Exibição de aplicativos** na parte inferior da tela e digite `V`. Isso mostrará uma lista que inclui todos os prompts de comando do Visual Studio instalados.  
  
4.  Escolha o **Prompt de Comando do Desenvolvedor** (ou o prompt de comando que você deseja usar).  
  
 **No Windows 7**  
  
1.  Escolha **Iniciar**, expanda **Todos os Programas** e expanda **Microsoft Visual Studio**.  
  
2.  Dependendo da versão do Visual Studio que você instalou, escolha **Ferramentas do Visual Studio**, **Prompt de Comando do Visual Studio** ou o prompt de comando que você deseja usar.  
  
 Se você tiver o [SDK do Windows](http://msdn.microsoft.com/windows/desktop/aa904949) ou o [SDK do Windows Phone](https://dev.windowsphone.com/downloadsdk), você poderá ver prompts de comando adicionais para arquiteturas ARM, x86 ou x64. Consulte a documentação das ferramentas individuais para determinar qual versão do prompt de comando você deve usar.  
  
<a name="alternative"></a>   
## <a name="manually-locating-the-files-on-your-machine"></a>Localizar manualmente os arquivos em seu computador  
  Normalmente, os atalhos para os prompts de comando que você instalou serão colocados na pasta **Menu Iniciar** do Visual Studio, como em C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Visual Studio 2015\Visual Studio Tools.    Porém, se por algum motivo a pesquisa do prompt de comando não produzir os resultados esperados, você poderá tentar localizar manualmente o atalho em seu computador para usá-lo.   Tente pesquisar pelo nome de arquivo do prompt de comando como VsDevCmd.bat ou acesse a pasta das Ferramentas como C:\Program Files (x86)\Microsoft Visual Studio 14.0\Common7\Tools (o caminho será alterado de acordo com seu local de instalação e da versão do Visual Studio).  
  
<a name="visualstudio"></a>   
## <a name="running-command-prompt-from-inside-visual-studio"></a>Executar o prompt de comando de dentro do Visual Studio  
 Para facilitar o acesso, você pode adicionar o Prompt de Comando do Visual Studio Developer ou qualquer outro prompt de comando ao menu Ferramentas no Visual Studio, adicionando-o à lista de ferramentas externas. Faça isso da seguinte forma:  
  
1.  Abra o Visual Studio.  
  
2.  Selecione o menu **Ferramentas** e escolha **Ferramentas Externas...**.  
  
3.  Na caixa de diálogo **Ferramentas Externas**, escolha o botão **Adicionar**. Uma nova entrada será exibida  
  
4.  Insira um **Título** para o novo item de menu, como `Command Prompt`.  
  
5.  No campo **Comando**, especifique o arquivo que você deseja iniciar, como `%comspec%` ou `C:\Windows\System32\cmd.exe`.  
  
6.  No campo **Argumentos**, especifique onde encontrar o prompt de comando específico que você deseja usar, como `/k "C:\Program Files (x86)\Microsoft Visual Studio 14.0\Common7\Tools\VsDevCmd.bat"` (isso iniciar o Prompt de Comando do Desenvolvedor instalado com [!INCLUDE[vs_dev14](../../../includes/vs-dev14-md.md)]). Esse valor precisa ser alterado de acordo com seu local de instalação e da versão do Visual Studio.  
  
7.  Escolha um valor para o campo **Diretório inicial**, como **Diretório do Projeto**.  
  
8.  Selecione o botão **OK**.  
  
 Depois disso, o novo item de menu será adicionado e você poderá acessar o prompt de comando no menu **Ferramentas**.  
  
## <a name="see-also"></a>Consulte também  
 [Ferramentas](../../../docs/framework/tools/index.md)  
 [Gerenciando ferramentas externas](/visualstudio/ide/managing-external-tools)
