---
title: "Depurando um aplicativo Olá, Mundo em C# com o Visual Studio 2017"
description: "Saiba como depurar um aplicativo Olá, Mundo escrito em C# com o Visual Studio 2017"
keywords: ".NET Core, aplicativo do console do .NET Core, depuração do .NET Core"
author: stevehoag
ms.author: shoag
ms.date: 10/24/2016
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: cb213625-cc60-438b-9b9e-49aed0e4a974
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 6a6a461984c140d180cf70cd7a1a33818a40b451
ms.lasthandoff: 03/13/2017

---

# <a name="debugging-your-c-hello-world-application-with-visual-studio-2017"></a>Depurando um aplicativo Olá, Mundo em C# com o Visual Studio 2017 #

Até agora, você seguiu as etapas em [Criação de um aplicativo Olá, Mundo em C# com o .NET Core no Visual Studio 2017](.\with-visual-studio-2017.md) para criar e executar um aplicativo de console simples. Após escrever e compilar um aplicativo, você pode começar a testá-lo. O Visual Studio inclui um conjunto abrangente de ferramentas de depuração que você pode usar ao testar e solucionar problemas de seu aplicativo. Vamos examinar alguns deles enquanto depuramos nosso aplicativo.

## <a name="debugging-in-debug-mode"></a>Depurando no modo de depuração ##

O modo de depuração é uma das duas configurações de build padrão do Visual Studio. (A outra é o modo de Versão.) A configuração de build atual é mostrada na barra de ferramentas. A figura a seguir mostra que o aplicativo será compilado no modo de Depuração.

   ![Image](./media/debugmode.jpg)

Você sempre deve começar testando seu programa em modo de Depuração. O modo de depuração desativa a maioria das otimizações do compilador e fornece informações mais sofisticadas na saída do arquivo de banco de dados de símbolo (arquivo .pdb) pelo processo de build.

## <a name="setting-a-breakpoint"></a>Definindo um ponto de interrupção ##

Vamos executar nosso programa no modo de Depuração e testar alguns recursos de depuração:

1. Definir um ponto de interrupção posicionando o cursor na linha que lê `Console.WriteLine("\nHello, {0}, on {1:d} at {1:t}", name, date);` e clicar na margem esquerda da janela de código ou escolher o item de menu **Depurar**, **Alternar Ponto de Interrupção**. (Um ponto de interrupção interrompe temporariamente a execução do aplicativo *antes* de a linha com o ponto de interrupção ser executada.) Como mostra a figura a seguir, o Visual Studio indica a linha na qual o ponto de interrupção é definido, realçando-o e exibindo um círculo vermelho na sua margem esquerda.

   ![Image](./media/setbreakpoint_2017.jpg)

1. Execute o programa no modo de Depuração, selecionando o botão "HelloWorld" com a seta verde na barra de ferramentas, pressionando F5 ou escolhendo **Depurar**, **Iniciar Depuração**.

1. Digite uma cadeia de caracteres na janela do console quando o programa solicitar um nome e pressione Enter.

1. A execução do programa para quando ele atinge o ponto de interrupção e antes de o método `Console.WriteLine` ser executado. O Visual Studio deve ser semelhante à figura a seguir. Observe que a janela **Autos** exibe os valores de variáveis que são usadas ao redor da linha atual. (A janela **Locais** exibe os valores das variáveis que são definidas no método que está sendo executado.)

   ![Image](./media/breakpoint_2017.jpg)

1. Vamos tentar alterar o valor das variáveis para ver como isso afeta nosso programa. Se a **janela Imediato** não estiver visível, exiba-a escolhendo o item de menu **Depurar**, **Windows**, **Imediato**. A **janela Imediato** permite interagir com o aplicativo que você está depurando.

1. Interativamente, você pode alterar os valores das variáveis. Digite `name = "Yuma"` na janela Imediato e pressione Enter.

1. Digite `date = new DateTime(2016,11,01,11,59,00)` na janela Imediato e pressione Enter.

   A imagem a seguir mostra a **janela Imediato**:

   ![Image](./media/immediatewindow.jpg)

   Observe que a janela exibe o valor da variável de cadeia de caracteres e as propriedades do valor @System.DateTime. Além disso, o valor das variáveis é atualizado nas janelas **Autos** e **Locais**.

1. Continue a execução do programa selecionando o botão **Continuar** na barra de ferramentas ou escolhendo o item de menu **Depurar**, **Continuar**. A janela do console resultante deve se assemelhar à seguinte imagem. Observe que os valores exibidos na janela do console também correspondem às alterações feitas na **janela Imediato**.

   ![Image](./media/changed.jpg)

1. Pressione qualquer tecla para sair do modo de Depuração do aplicativo e de término.

## <a name="setting-a-conditional-breakpoint"></a>Definindo um ponto de interrupção condicional ##

Agora sabemos que o nosso programa exibirá a cadeia de caracteres que o usuário digita corretamente. Mas o que acontece se o usuário não inserir nada? Podemos testar isso e, no processo, usar outro recurso de depuração, como a capacidade de definir um ponto de interrupção condicional.

Para definir um ponto de interrupção condicional e testar o que acontece quando o usuário não insere uma cadeia de caracteres, faça o seguinte:

1. Clique com o botão direito do mouse no ponto vermelho que representa o ponto de interrupção. No menu de contexto, selecione **Condições...** para abrir a caixa de diálogo **Configurações de Ponto de Interrupção** mostrada na figura a seguir.

   ![Image](./media/breakpoint_settings.jpg)

1. Na caixa de texto na qual se lê "por exemplo, x == 5", digite o seguinte:

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   Aqui, vamos testar uma condição de código. Também podemos especificar uma contagem de ocorrências, que interrompe a execução do programa antes de uma instrução ser executada um número especificado de vezes, ou uma condição de filtro, que interrompe a execução do programa com base em atributos como identificador de thread, nome do processo e nome do thread.

1. Escolha o botão **Fechar** para fechar o diálogo.

1. Execute o programa no modo de Depuração.

1. Na janela do console, pressione a tecla Enter quando solicitado a inserir seu nome.

1. Como a condição que especificamos foi cumprida – `name` é `null` ou [String.Empty](xref:System.String.Empty) – a execução do programa é parada quando atinge o ponto de interrupção e antes de o método `Console.WriteLine` ser executado.

1. Escolha a janela **Locais**, que mostra os valores de variáveis locais para o método que está sendo executado, nesse caso o método `Main`.

1. Observe que o valor da variável `name` é "" ou [String.Empty](xref:System.String.Empty). Confirmar isso inserindo a seguinte instrução na **janela Imediato**:

   ```csharp
   ? name == String.Empty
   ```

   A figura a seguir mostra o resultado.

   ![Image](./media/emptystring.jpg)

1. Escolha o botão **Continuar** na barra de ferramentas para continuar a execução do programa.

1. Pressione qualquer tecla para fechar a janela do console e sair do modo de Depuração.

1. Limpe o ponto de interrupção clicando no ponto na margem esquerda da janela de código ou escolhendo o item de menu **Depurar**, **Alternar Ponto de Interrupção**.

## <a name="stepping-through-a-program"></a>Percorrendo um programa ##

O Visual Studio também nos permite percorrer linha por linha de um programa e monitorar sua execução. Normalmente, você deve definir um ponto de interrupção e usar esse recurso para seguir o fluxo do programa por uma pequena parte do código do programa. Como nosso programa é pequeno, vamos percorrer todo o programa fazendo o seguinte:

1. Na barra de menus, escolha **Depurar**, **Intervir** ou pressione F11. O Visual Studio destaca e exibe uma seta ao lado da linha será executada em seguida, como mostra a figura a seguir.

   ![Image](./media/step_into.jpg)

   Neste ponto, a janela **Autos** mostra que o nosso programa definiu apenas uma variável, `args`. Como ainda não passamos argumentos de linha de comando para o programa, seu valor é uma matriz de cadeia de caracteres vazia. Além disso, o Visual Studio abriu uma janela de console em branco.

1. Escolha **Depurar**, **Intervir** ou pressione F11. O Visual Studio agora destaca a próxima linha que será executada. Como mostra a figura, a execução do código entre a última instrução e esta levou 3 milissegundos. `args` permanece a única variável declarada, e a janela do console ainda está em branco.

   ![Image](./media/step_into_2.jpg)

1. Escolha **Depurar**, **Intervir** ou pressione F11. O Visual Studio destaca a instrução que inclui a atribuição de variável `name`. A janela **Autos** mostra que `name` é `null`, e a janela do console exibe a cadeia de caracteres "Qual é o seu nome?".

1. Responda à solicitação inserindo uma cadeia de caracteres na janela do console e pressionando Enter. O console não responderá e a cadeia de caracteres que você inserir não será exibida na janela do console, mas o método [Console.ReadLine](xref:System.Console.ReadLine) capturará sua entrada.

1. Escolha **Depurar**, **Intervir** ou pressione F11. O Visual Studio destaca a instrução que inclui a atribuição de variável `date`. A janela **Autos** mostra o valor da propriedade [DateTime.Now](xref:System.DateTime.Now) e o valor retornado pela chamada para o método [Console.ReadLine](xref:System.Console.ReadLine). A janela de console também exibe a cadeia de caracteres inserida quando o console for solicitado para a entrada.

1. Escolha **Depurar**, **Intervir** ou pressione F11. A janela **Autos** agora mostra o valor da variável `date` após a atribuição da propriedade [DateTime.Now](xref:System.DateTime.Now). A janela do console não é alterada.

1. Escolha **Depurar**, **Intervir** ou pressione F11. O Visual Studio chama o método [Console.WriteLine](xref:System.Console.WriteLine(System.String,System.Object,System.Object)). Os valores das variáveis `date` e `name` aparecem na janela **Autos** e a janela de console exibe a cadeia de caracteres formatada.

1. Escolha **Depurar**, **Sair** ou pressione Shift e a tecla F11. Isso interrompe a execução passo a passo. A janela do console exibe uma mensagem e aguarda até que uma tecla seja pressionada.

1. Pressione qualquer tecla para fechar a janela do console e sair do modo de Depuração.

## <a name="building-a-release-version"></a>Compilando uma versão de lançamento ##

Quando tiver testado o build de depuração do seu aplicativo, você deverá compilar e testar a versão de lançamento. A versão de lançamento incorpora otimizações do compilador que, às vezes, podem afetar o comportamento de um aplicativo. Por exemplo, as otimizações de compilador que são projetadas para melhorar o desempenho podem criar condições de corrida em aplicativos multi-threaded ou assíncronos.

Para compilar e testar a versão de liberação do seu aplicativo de console, altere a configuração de build na barra de ferramentas de **Depurar** para **Versão**, conforme mostrado na figura a seguir.

![Image](./media/release.jpg)

Ao pressionar F5 ou escolher **Compilar Solução** no menu **Compilar**, o Visual Studio compila a versão de liberação do seu aplicativo de console para testar. Em seguida, você pode executar e testá-lo como fez com a versão de depuração do aplicativo.

Quando terminar de depurar seu aplicativo, a próxima etapa será publicar uma versão distribuível do seu aplicativo. Para obter informações sobre como fazer isso, consulte [Publicando o aplicativo Olá, Mundo em C# com Visual Studio 2017](./publishing-with-visual-studio-2017.md).

