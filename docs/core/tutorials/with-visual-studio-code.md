---
title: Introdução ao C# e ao Visual Studio Code
description: Saiba como criar e depurar seu primeiro aplicativo .NET Core no C# usando o Visual Studio Code.
author: kendrahavens
ms.date: 04/23/2020
ms.openlocfilehash: 3dd7c4602fbb27e29bad977f8d3df34b6061bc23
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/29/2020
ms.locfileid: "82506864"
---
# <a name="get-started-with-c-and-visual-studio-code"></a>Introdução ao C# e ao Visual Studio Code

O .NET Core oferece uma plataforma modular e rápida para a criação de aplicativos que são executados no Windows, Linux e macOS. Use o Visual Studio Code com a extensão do C# para obter uma excelente experiência de edição com suporte completo para IntelliSense em C# (conclusão de código inteligente) e depuração.

## <a name="prerequisites"></a>Pré-requisitos

1. Instale o [Visual Studio Code](https://code.visualstudio.com/).
2. Instale o [SDK do .NET Core](https://dotnet.microsoft.com/download).
3. Instale a [extensão de C#](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) para o Visual Studio Code. Para saber mais sobre como instalar extensões no Visual Studio Code, confira [Marketplace de extensão de código do VS](https://code.visualstudio.com/docs/editor/extension-gallery).

## <a name="hello-world"></a>Olá, Mundo

Comece com um programa simples de "Olá, Mundo" no .NET Core:

1. Abra um projeto:

    - Abra o Visual Studio Code.
    - Selecione **arquivo** > **abrir pasta** no menu principal.
    - Crie uma pasta chamada *HelloWorld*e clique em **Selecionar pasta**. O nome da pasta torna-se o nome do projeto e o nome do namespace por padrão. Você adicionará código posteriormente no tutorial que assume que o namespace do projeto `HelloWorld`é.

1. Inicialize um projeto em C#:

    - Abra o terminal de Visual Studio Code selecionando **Exibir** > **terminal** no menu principal.
    - Na janela do terminal, digite `dotnet new console`.

      Este comando cria um arquivo *Program.cs* em sua pasta com um programa simples de "Olá, mundo" já gravado, juntamente com um arquivo de projeto C# chamado *HelloWorld. csproj*.

      ![O novo comando dotnet](media/with-visual-studio-code/dotnet-new-command.png)

1. Execute o programa "Olá, Mundo":

    - Na janela do terminal, digite `dotnet run`.

      ![O comando de execução dotnet](media/with-visual-studio-code/dotnet-run-command.png)

## <a name="debug"></a>Depurar

1. Abra *Program.cs* clicando nele. Na primeira vez que um arquivo do C# é aberto no Visual Studio Code, o [OmniSharp](https://www.omnisharp.net/) é carregado no editor.

    ![Abra o arquivo Program.cs](media/with-visual-studio-code/open-program-cs.png)

1. Visual Studio Code solicita que você adicione os ativos ausentes para compilar e depurar seu aplicativo. Selecione **Sim** na barra superior.

    ![Prompt para ativos ausentes](media/with-visual-studio-code/missing-assets.png)

1. Para abrir e exibição Depuração, clique no ícone Depuração no menu do lado esquerdo.

    ![Abrir a guia Depurar no Visual Studio Code](media/with-visual-studio-code/open-debug-tab.png)

1. Localize a seta verde na parte superior do painel. Certifique-se de que a lista suspensa ao lado dele tenha a **inicialização do .NET Core (console)** selecionada.

    ![Selecionando o .NET Core no Visual Studio Code](media/with-visual-studio-code/select-net-core.png)

1. Adicione um ponto de interrupção ao seu projeto. Para isso, clique na **margem do editor** logo à esquerda dos números de linha no editor, próximo à linha 9, ou mova o cursor do texto na linha 9 no editor e pressione <kbd>F9</kbd>.

    ![Definindo um ponto de interrupção](media/with-visual-studio-code/set-breakpoint-vs-code.png)

1. Para iniciar a depuração, pressione <kbd>F5</kbd> ou selecione a seta verde. O depurador interrompe a execução do programa quando ele atinge o ponto de interrupção definido na etapa anterior.
    - Durante a depuração, você pode exibir suas variáveis locais no painel superior esquerdo ou usar o console de depuração.

1. Selecione a seta azul na parte superior para continuar a depuração ou escolha o quadrado vermelho na parte superior para interromper o processamento.

    ![Execução e depuração no Visual Studio Code](media/with-visual-studio-code/run-debug-vs-code.png)

> [!TIP]
> Para obter mais informações e dicas sobre solução de problemas de depuração do .NET Core com o OmniSharp no Visual Studio Code, consulte [Instruções para configurar o depurador .NET Core](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).

## <a name="add-a-class"></a>Adicionar uma classe

1. Para adicionar uma nova classe, clique com o botão direito do mouse no VSCode Explorer abaixo de *Program.cs* e selecione **novo arquivo**. Isso adiciona um novo arquivo à pasta que você abriu no VSCode.
1. Nomeie o arquivo *MyClass.cs*. Salve-o com uma extensão `.cs` no final para que ele seja reconhecido como um arquivo csharp.
1. Adicione o código a seguir para criar sua primeira classe.

    ``` csharp
    using System;

    namespace HelloWorld
    {
        public class MyClass
        {
            public string ReturnMessage()
            {
                return "Happy coding!";
            }
        }
    }
    ```

1. Chame sua nova classe do seu `Main` método substituindo o código em *Program.cs* pelo seguinte código:

    ```csharp
    using System;

    namespace HelloWorld
    {
        class Program
        {
            static void Main(string[] args)
            {
                var c1 = new MyClass();
                Console.WriteLine($"Hello World! {c1.ReturnMessage()}");
            }
        }
    }
    ```

1. Salve suas alterações.

1. Execute o programa novamente.

    ```dotnetcli
    dotnet run
    ```

    A nova mensagem é exibida com a cadeia de caracteres acrescentada.

    ```console
    Hello World! Happy coding!
    ```

## <a name="faq"></a>Perguntas frequentes

### <a name="im-missing-required-assets-to-build-and-debug-c-in-visual-studio-code-my-debugger-says-no-configuration"></a>Faltam os ativos necessários para compilar e depurar C# no Visual Studio Code. Meu depurador diz: "Nenhuma configuração".

A extensão C# do Visual Studio Code pode gerar ativos para compilar e depurar para você. O Visual Studio Code solicita que você gere esses ativos ao abrir um projeto C# pela primeira vez. Se você não gerar os ativos em seguida, você ainda poderá executar esse comando abrindo a paleta de comandos (**Exibição > Paleta de comandos**) e digitando">.NET: Generate Assets for Build and Debug". Selecionar isso gera os arquivos de configuração *. vscode*, *Launch. JSON*e *Tasks. JSON* necessários.

## <a name="see-also"></a>Confira também

- [Configurar o Visual Studio Code](https://code.visualstudio.com/docs/setup/setup-overview)
- [Depurar no Visual Studio Code](https://code.visualstudio.com/Docs/editor/debugging)
