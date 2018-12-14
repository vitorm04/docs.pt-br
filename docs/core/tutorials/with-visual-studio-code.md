---
title: Introdução ao C# e Visual Studio Code – Guia do C#
description: Saiba como criar e depurar seu primeiro aplicativo .NET Core no C# usando o Visual Studio Code.
author: kendrahavens
ms.author: mairaw
ms.date: 12/05/2018
ms.openlocfilehash: fde2d8a324f3435438a4a92843a9d5b7b0def443
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53129591"
---
# <a name="get-started-with-c-and-visual-studio-code"></a>Introdução ao Visual Studio Code e C#

O .NET Core oferece uma plataforma modular e rápida para a criação de aplicativos que são executados no Windows, Linux e macOS. Use o Visual Studio Code com a extensão do C# para obter uma excelente experiência de edição com suporte completo para IntelliSense em C# (conclusão de código inteligente) e depuração.

## <a name="prerequisites"></a>Pré-requisitos

1. Instalar o [Visual Studio Code](https://code.visualstudio.com/).
2. Instalar o [SDK do .NET Core](https://www.microsoft.com/net/download/core).
3. Instale a [extensão de C#](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp) para o Visual Studio Code. Para saber mais sobre como instalar extensões no Visual Studio Code, confira [Marketplace de extensão de código do VS](https://code.visualstudio.com/docs/editor/extension-gallery).

## <a name="hello-world"></a>Hello World

Vamos começar com um simples programa "Olá, Mundo" no .NET Core:

1. Abra um projeto:

    * Abra o Visual Studio Core.
    * Clique no ícone do Explorer no menu à esquerda e, em seguida, clique em **Abrir Pasta**; ou.
    * Selecione **Arquivo** > **Abrir Pasta** no menu principal para abrir a pasta em que você deseja armazenar seu projeto C# e clique em **Selecionar Pasta**. Para nosso exemplo, estamos criando uma pasta para nosso projeto chamado *HelloWorld*.

      ![VSCodeOpenFolder](media/with-visual-studio-code/vscodeopenfolder.png)

2. Inicialize um projeto em C#:
    * Abra o Terminal Integrado do Visual Studio Code selecionando **Exibir** > **Terminal Integrado** no menu principal.
    * Na janela do terminal, digite `dotnet new console`.
    * Este comando cria um arquivo de projeto `HelloWorld.csproj` e um arquivo de código `Program.cs` com um código simples, que imprime "Hello, World!" quando executado.

      ![O novo comando dotnet](media/with-visual-studio-code/dotnetnew.png)

3. Resolva as dependências de build:

    * Para o **.NET Core 1.x**, digite `dotnet restore`. Executar `dotnet restore` fornece acesso a pacotes .NET Core que são necessários para compilar seu projeto.

      ![O comando de restauração dotnet](media/with-visual-studio-code/dotnetrestore.png)

      [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

4. Execute o programa "Olá, Mundo":

    * Digite `dotnet run`.

      ![O comando de execução dotnet](media/with-visual-studio-code/dotnetrun.png)

Você também pode assistir a um tutorial breve em vídeo para obter ajuda na instalação em [Windows](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core), [macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core-on-MacOS) ou [Linux](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).

## <a name="debug"></a>Depurar

1. Abra *Program.cs* clicando nele. Na primeira vez que um arquivo do C# é aberto no Visual Studio Code, o [OmniSharp](https://www.omnisharp.net/) é carregado no editor.

    ![Abra o arquivo Program.cs](media/with-visual-studio-code/opencs.png)

2. O Visual Studio Code solicitará que você adicione os ativos ausentes para compilar e depurar seu projeto. Selecione **Sim** na barra superior.

    ![Prompt para ativos ausentes](media/with-visual-studio-code/missing-assets.png)

3. Para abrir e exibição Depuração, clique no ícone Depuração no menu do lado esquerdo.

    ![Abra a guia Depurar](media/with-visual-studio-code/opendebug.png)

4. Localize a seta verde na parte superior do painel. Certifique-se que a lista suspensa ao lado tenha `.NET Core Launch (console)` selecionado.

    ![Seleção do .NET Core](media/with-visual-studio-code/selectcore.png)

5. Adicione um ponto de interrupção ao seu projeto. Para isso, clique na **margem do editor** logo à esquerda dos números de linha no editor, próximo à linha 9, ou mova o cursor do texto na linha 9 no editor e pressione <kbd>F9</kbd>.

    ![Definindo um ponto de interrupção](media/with-visual-studio-code/setbreakpoint.png)

6. Para iniciar a depuração, use a tecla <kbd>F5</kbd> ou a seta verde. O depurador interrompe a execução do programa quando ele atinge o ponto de interrupção definido na etapa anterior.
    * Durante a depuração, você pode exibir as variáveis locais no painel superior esquerdo ou usar o console de depuração.

7. Selecione a seta azul na parte superior para continuar a depuração ou escolha o quadrado vermelho na parte superior para interromper o processamento.

    ![Executar e depurar](media/with-visual-studio-code/rundebug.png)

> [!TIP]
> Para obter mais informações e dicas sobre solução de problemas de depuração do .NET Core com o OmniSharp no Visual Studio Code, consulte [Instruções para configurar o depurador .NET Core](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).

## <a name="add-a-class"></a>Adicionar uma classe

1. Para adicionar uma nova classe, clique com o botão direito do mouse no VSCode Explorer e selecione **Novo Arquivo**. Isso adiciona um novo arquivo à pasta que você abriu no VSCode.
2. Nomeie o arquivo como `Class1.cs`. Salve-o com uma extensão `.cs` no final para que ele seja reconhecido como um arquivo csharp.
3. Adicione o código a seguir para criar sua primeira classe. Certifique-se de incluir o namespace correto, para poder fazer referência a ele no seu arquivo `Program.cs`.
``` csharp
using System;

namespace HelloWorld
{
    public class Class1
    {
        public string ReturnMessage()
        {
            return "Happy coding!";
        }
    }
}
```

4. Chame a nova classe do seu método principal em `Program.cs` adicionando o código a seguir.

```csharp
using System;

namespace HelloWorld
{
    class Program
    {
        static void Main(string[] args)
        {
            Class1 c1 = new Class1();
            Console.WriteLine($"Hello World! {c1.ReturnMessage()}");
        }
    }
}
```

5. Salve as alterações e execute o programa novamente. A nova mensagem deve aparecer com a cadeia de caracteres acrescentada.
```console
> dotnet run
Hello World! Happy coding!
```

## <a name="faq"></a>Perguntas Frequentes

### <a name="im-missing-required-assets-to-build-and-debug-c-in-visual-studio-code-my-debugger-says-no-configuration"></a>Faltam os ativos necessários para compilar e depurar C# no Visual Studio Code. Meu depurador diz: "Nenhuma configuração".

A extensão C# do Visual Studio Code pode gerar ativos para compilar e depurar para você. O Visual Studio Code solicita que você gere esses ativos ao abrir um projeto C# pela primeira vez. Se você não gerar os ativos em seguida, você ainda poderá executar esse comando abrindo a paleta de comandos (**Exibição > Paleta de comandos**) e digitando">.NET: Generate Assets for Build and Debug". Selecionar isso gera os arquivos de configuração. vscode, launch.json e tasks.json que você precisa.

## <a name="see-also"></a>Consulte também

* [Configurando o Visual Studio Code](https://code.visualstudio.com/docs/setup/setup-overview)
* [Depurando no Visual Studio Code](https://code.visualstudio.com/Docs/editor/debugging)
