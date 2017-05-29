---
title: Aplicativo do Console
description: "Este tutorial ensina vários recursos no .NET Core e da linguagem C#."
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 883cd93d-50ce-4144-b7c9-2df28d9c11a0
ms.translationtype: Human Translation
ms.sourcegitcommit: be7974018ce3195dc7344192d647fe64fb2ebcc4
ms.openlocfilehash: 360e93af03e00547116d1af1816c2b9b29524881
ms.contentlocale: pt-br
ms.lasthandoff: 05/22/2017

---

# <a name="console-application"></a>Aplicativo do Console

## <a name="introduction"></a>Introdução
Este tutorial ensina vários recursos no .NET Core e da linguagem C#. Você aprenderá:
*    As noções básicas da CLI (Interface de Linha de Comando) do .NET Core
*    A estrutura de um aplicativo de console C#
*    E/S do Console
*    Fundamentos das APIs de E/S de arquivo no .NET Core
*    Os fundamentos do modelo de programação assíncrona de tarefa no .NET Core

Você compilará um aplicativo que lê um arquivo de texto e exibe o conteúdo desse arquivo de texto no console. A saída para o console será conduzida a fim de corresponder à leitura em voz alta. Você pode acelerar ou diminuir o ritmo pressionando as teclas ‘<’ ou ‘>’.

Há vários recursos neste tutorial. Vamos compilá-los individualmente. 
## <a name="prerequisites"></a>Pré-requisitos
Você precisará configurar seu computador para executar o .NET Core. Você encontrará as instruções de instalação na página do [.NET Core](https://www.microsoft.com/net/core). Execute esse aplicativo no Windows, Linux, macOS ou em um contêiner do Docker. Será necessário instalar o editor de código de sua preferência. 
## <a name="create-the-application"></a>Criar o aplicativo
A primeira etapa é criar um novo aplicativo. Abra um prompt de comando e crie um novo diretório para seu aplicativo. Torne ele o diretório atual. Digite o comando `dotnet new console` no prompt de comando. Isso cria os arquivos iniciais de um aplicativo "Olá, Mundo" básico.

Antes de começar as modificações, vamos percorrer as etapas para execução do aplicativo simples Hello World. Depois de criar o aplicativo, digite `dotnet restore` no prompt de comando. Esse comando executa o processo de restauração do pacote NuGet. O NuGet é um gerenciador de pacotes do .NET. Esse comando baixa qualquer uma das dependências ausentes para seu projeto. Como esse é um novo projeto, nenhuma das dependências foram aplicadas, portanto, a primeira execução baixará a estrutura do .NET Core. Após essa etapa inicial, você só precisará executar o `dotnet restore` ao adicionar novos pacotes dependentes, ou atualizar as versões de qualquer uma de suas dependências. Esse processo também cria o arquivo de bloqueio do projeto (project.lock.json) no diretório de seu projeto. Esse arquivo ajuda a gerenciar as dependências do projeto. Ele contém o local de todas as dependências do projeto. Você não precisa colocar o arquivo no controle do código-fonte; ele será gerado quando você executar `dotnet restore`. 

Depois de restaurar os pacotes, execute `dotnet build`. Isso executa o mecanismo de compilação e cria o executável de seu aplicativo. Por fim, execute `dotnet run` para executar o aplicativo.  

O código simples do aplicativo Hello World está totalmente em Program.cs. Abra esse arquivo com o seu editor de texto favorito. Estamos prestes a fazer nossas primeiras alterações.
Na parte superior do arquivo, confira uma instrução using:

```csharp
using System;
```

Essa instrução informa ao compilador que quaisquer tipos do namespace `System` estão dentro do escopo. Assim como em outras linguagens orientadas a objeto que você pode ter usado, o C# usa namespaces para organizar tipos. Este programa olá, mundo não é diferente. Você pode ver que o programa está entre o namespace `ConsoleApplication`. Esse não é um nome muito descritivo, portanto, mude-o para `TeleprompterConsole`:

```csharp
namespace TeleprompterConsole
```

## <a name="reading-and-echoing-the-file"></a>Como ler e exibir o arquivo
O primeiro recurso a ser adicionado é a capacidade de ler um arquivo de texto e a exibição de todo esse texto para um console. Primeiro, vamos adicionar um arquivo de texto. Copie o arquivo [sampleQuotes.txt](https://raw.githubusercontent.com/dotnet/docs/master/samples/csharp/getting-started/console-teleprompter/sampleQuotes.txt) do repositório do GitHub para este [exemplo](https://github.com/dotnet/docs/tree/master/samples/csharp/getting-started/console-teleprompter) no diretório de seu projeto. Isso servirá como o script de seu aplicativo. Se desejar obter informações sobre como baixar o aplicativo de exemplo para este tópico, consulte as instruções no tópico [Exemplos e Tutoriais](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

Em seguida, adicione o seguinte método em sua classe Program (logo abaixo do método `Main`):

```csharp
static IEnumerable<string> ReadFrom(string file)
{
    string line;
    using (var reader = File.OpenText(file))
    {
        while ((line = reader.ReadLine()) != null)
        {
            yield return line;
        }
    }
}
```

Esse método usa tipos de dois namespaces novos. Para que isso seja compilado, será necessário adicionar as duas linhas a seguir na parte superior do arquivo:

```csharp
using System.Collections.Generic;
using System.IO;
```

A interface `IEnumerable<T>` é definida no namespace `System.Collections.Generic`. A classe @System.IO.File é definida no namespace `System.IO`.

Esse método é um tipo especial de método C# chamado de *Método enumerador*. Os métodos enumeradores retornam sequências que são avaliadas lentamente. Isso significa que cada item na sequência é gerado conforme a solicitação do código que está consumindo a sequência. Os métodos enumeradores contêm uma ou mais instruções `yield return`. O objeto retornado pelo método `ReadFrom` contém o código para gerar cada item na sequência. Neste exemplo, isso envolve a leitura da próxima linha de texto do arquivo de origem e o retorno dessa cadeia de caracteres. Toda vez que o código de chamada solicita o próximo item da sequência, o código lê a próxima linha de texto do arquivo e a retorna. Após a leitura completa do arquivo, a sequência indicará que não há mais itens.

Há dois outros elementos da sintaxe em C# que podem ser novidade para você. A instrução `using` nesse método gerencia a limpeza de recursos. A variável inicializada na instrução `using` (`reader`, neste exemplo) deve implementar a interface `IDisposable`. A interface @System.IDisposable define um único método, `Dispose`, que deve ser chamado quando o recurso for liberado. O compilador gera essa chamada quando a execução atingir a chave de fechamento da instrução `using`. O código gerado pelo compilador garante que o recurso seja liberado, mesmo se uma exceção for lançada do código no bloco definido pela instrução using.

A variável `reader` é definida usando a palavra-chave `var`. `var` define uma *variável local de tipo implícito*. Isso significa que o tipo da variável é determinado pelo tipo de tempo de compilação do objeto atribuído à variável. Aqui, esse é o valor de retorno de @System.IO.File.OpenText, que é um objeto @System.IO.StreamReader.
 
Agora, vamos preencher o código para ler o arquivo no método `Main`: 

```csharp
var lines = ReadFrom("sampleQuotes.txt");
foreach (var line in lines)
{
    Console.WriteLine(line); 
}
```

Execute o programa (usando `dotnet run`, e você poderá ver todas as linhas impressa no console).  

## <a name="adding-delays-and-formatting-output"></a>Adicionar atrasos e formatar a saída
O que você possui está sendo exibido muito rápido para permitir a leitura em voz alta. Agora você precisa adicionar os atrasos na saída. Ao começar, você compilará parte do código principal que permite o processamento assíncrono. No entanto, essas primeiras etapas seguirão alguns antipadrões. Os antipadrões são indicados nos comentários durante a adição do código, e o código será atualizado em etapas posteriores.

Há duas etapas nesta seção. Primeiro, você atualizará o método iterador a fim de retornar palavras individuais em vez de linhas inteiras. Isso é feito com estas modificações. Substitua a instrução `yield return line;` pelo seguinte código:

```csharp
var words = line.Split(' ');
foreach (var word in words)
{
    yield return word + " ";
}
yield return Environment.NewLine;
```

Em seguida, será necessário modificar a forma como você consume as linhas do arquivo, e adicionar um atraso depois de escrever cada palavra. Substitua a instrução `Console.WriteLine(line)` no método `Main` pelo seguinte bloco:

```csharp
Console.Write(line);
if (!string.IsNullOrWhiteSpace(line))
{
    var pause = Task.Delay(200);
    // Synchronously waiting on a task is an
    // anti-pattern. This will get fixed in later
    // steps.
    pause.Wait();
}
```

A classe `Task` é o namespace `System.Threading.Tasks`, portanto, você precisa adicionar essa instrução `using` na parte superior do arquivo:

```csharp
using System.Threading.Tasks;
```

Execute o exemplo e verifique a saída. Agora, cada palavra única é impressa, seguida por um atraso de 200 ms. No entanto, a saída exibida mostra alguns problemas, pois o arquivo de texto de origem contém várias linhas com mais de 80 caracteres sem uma quebra de linha. Isso pode ser difícil de ler durante a rolagem da tela. Mas também é fácil de corrigir. Apenas mantenha o controle do comprimento de cada linha e gere uma nova linha sempre que o comprimento atingir um certo limite. Declare uma variável local após a declaração de `words` que contém o comprimento da linha:

```csharp
var lineLength = 0;
```
 
Em seguida, adicione o seguinte código após a instrução `yield return word + " ";` (antes da chave de fechamento):

```csharp
lineLength += word.Length + 1;
if (lineLength > 70)
{
    yield return Environment.NewLine;
    lineLength = 0;
}
```
 
Execute o exemplo e você poderá ler em voz alta de acordo com o ritmo pré-configurado.

## <a name="async-tasks"></a>Tarefas assíncronas
Nesta etapa final, você adicionará o código para gravar a saída de forma assíncrona em uma tarefa, enquanto executa também outra tarefa para ler a entrada do usuário, casos ele queira acelerar ou diminuir o ritmo da exibição do texto. Essa etapa tem alguns passos e, no final, você terá todas as atualizações necessárias.
A primeira etapa é criar um método de retorno @System.Threading.Tasks.Task assíncrono que representa o código que você criou até agora para ler e exibir o arquivo.

Adicione este método à sua classe `Program` (ele é obtido do corpo de seu método `Main`):

```csharp
private static async Task ShowTeleprompter()
{
    var words = ReadFrom("sampleQuotes.txt");
    foreach (var line in words)
    {
        Console.Write(line);
        if (!string.IsNullOrWhiteSpace(line))
        {
            await Task.Delay(200);
        }
    }
}
```

Você observará duas alterações. Primeiro, no corpo do método, em vez de chamar @System.Threading.Tasks.Task.Wait para aguardar de forma síncrona a conclusão de uma tarefa, essa versão usa a palavra-chave `await`. Para fazer isso, você precisa adicionar o modificador `async` à assinatura do método. Esse método retorna `Task`. Observe que não há instruções return que retornam um objeto `Task`. Em vez disso, esse objeto `Task` é criado pelo código gerado pelo compilador quando você usa o operador `await`. Você pode imaginar que esse método retorna quando atinge um `await`. A `Task` retornada indica que o trabalho não foi concluído.
O método será retomado quando a tarefa em espera for concluída. Após a execução completa, a `Task` retornada indicará a conclusão.
O código de chamada pode monitorar essa `Task` retornada para determinar quando ela foi concluída.

Chame esse novo método em seu método `Main`:

```csharp
ShowTeleprompter().Wait();
```

Aqui, em `Main`, o código aguarda de forma síncrona. Use o operador `await` em vez de esperar de forma síncrona sempre que possível. Porém, no método `Main` do aplicativo de console, não é possível usar o operador `await`. Isso resultaria no encerramento do aplicativo antes da conclusão de todas as tarefas.

Em seguida, você precisa escrever o segundo método assíncrono para ler no Console e ficar atento às teclas ‘<’ e ‘>’. Este é o método que você adiciona à tarefa:

```csharp
private static async Task GetInput()
{
    var delay = 200;
    Action work = () =>
    {
        do {
            var key = Console.ReadKey(true);
            if (key.KeyChar == '>')
            {
                delay -= 10;
            }
            else if (key.KeyChar == '<')
            {
                delay += 10;
            }
        } while (true);
    };
    await Task.Run(work);
}
```

Isso cria uma expressão lambda para representar um delegado @System.Action que lê uma tecla do Console e modifica uma variável local representando o atraso quando o usuário pressiona as teclas ‘<’ ou ‘>’. Esse método usa @System.Console.ReadKey para bloquear e aguardar até que o usuário pressione uma tecla.

Para concluir esse recurso, você precisa criar um novo método de retorno `async Task` que inicia essas duas tarefas (`GetInput` e `ShowTeleprompter`) e também gerencia os dados compartilhados entre essas tarefas.
 
É hora de criar uma classe que pode manipular os dados compartilhados entre essas duas tarefas. Essa classe contém duas propriedades públicas: o atraso, e um sinalizador para indicar que o arquivo foi lido completamente:

```csharp
namespace TeleprompterConsole
{
    internal class TelePrompterConfig
    {
        private object lockHandle = new object();
        public int DelayInMilliseconds { get; private set; } = 200;

        public void UpdateDelay(int increment) // negative to speed up
        {
            var newDelay = Min(DelayInMilliseconds + increment, 1000);
            newDelay = Max(newDelay, 20);
            lock (lockHandle)
            {
                DelayInMilliseconds = newDelay;
            }
        }
    }
}
```

Coloque essa classe em um novo arquivo e cerque-a pelo namespace `TeleprompterConsole`, conforme mostrado acima. Também é necessário adicionar uma instrução `using static` para que você possa fazer referência ao método `Min` e `Max` sem os nomes de classe ou namespace delimitadores. Uma instrução `using static` importa os métodos de uma classe. Isso é o oposto das instruções `using` usadas até este ponto, as quais importaram todas as classes de um namespace.

```csharp
using static System.Math;
```

O outro recurso de linguagem novo é a instrução `lock`. Essa instrução garante a existência de apenas um thread nesse código a qualquer momento. Se houver um thread na seção bloqueada, outros threads deverão aguardar até que o primeiro thread saia dessa seção. A instrução `lock` usa um objeto que protege a seção de bloqueio. Essa classe segue uma linguagem padrão para bloquear um objeto privado na classe.

Em seguida, atualize os métodos `ShowTeleprompter` e `GetInput` para usar o novo objeto `config`. Escreva um método final `async` de retorno de `Task` para iniciar as duas tarefas e sair quando a primeira tarefa for concluída:

```csharp
private static async Task RunTeleprompter()
{
    var config = new TelePrompterConfig();
    var displayTask = ShowTeleprompter(config);

    var speedTask = GetInput(config);
    await Task.WhenAny(displayTask, speedTask);
}
```

O único método novo aqui é a chamada @System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[]). Isso cria uma `Task` que termina assim que qualquer uma das tarefas na lista de argumentos for concluída.

Depois, atualize os métodos `ShowTeleprompter` e `GetInput` para usar o objeto `config` para o atraso:

```csharp
private static async Task ShowTeleprompter(TelePrompterConfig config)
{
    var words = ReadFrom("sampleQuotes.txt");
    foreach (var line in words)
    {
        Console.Write(line);
        if (!string.IsNullOrWhiteSpace(line))
        {
            await Task.Delay(config.DelayInMilliseconds);
        }
    }
    config.SetDone();
}

private static async Task GetInput(TelePrompterConfig config)
{

    Action work = () =>
    {
        do {
            var key = Console.ReadKey(true);
            if (key.KeyChar == '>')
                config.UpdateDelay(-10);
            else if (key.KeyChar == '<')
                config.UpdateDelay(10);
        } while (!config.Done);
    };
    await Task.Run(work);
}
```

Essa nova versão de `ShowTeleprompter` chama um novo método na classe `TeleprompterConfig`. Agora, você precisa atualizar `Main` para chamar `RunTeleprompter` em vez de `ShowTeleprompter`:

```csharp
RunTeleprompter().Wait();
```

Para concluir, você precisará adicionar o método `SetDone` e a propriedade `Done` à classe `TelePrompterConfig`:

```csharp
public bool Done => done;

private bool done;

public void SetDone()
{
    done = true;    
}
```

## <a name="conclusion"></a>Conclusão
Este tutorial mostrou a você alguns recursos da linguagem C# e as bibliotecas .NET Core relacionadas ao trabalho em aplicativos de Console.
Use esse conhecimento como base para explorar mais sobre a linguagem e sobre as classes apresentadas aqui. Você já viu os fundamentos de E/S do Arquivo e do Console, uso com bloqueio e sem bloqueio do modelo de programação assíncrono com base em tarefa, um tour pela linguagem C# e como os programas em C# são organizados, além da Interface de linha de comando e ferramentas do .NET Core.
 

