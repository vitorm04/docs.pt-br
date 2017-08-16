---
title: "Padrões de evento .NET padrão"
description: "Saiba mais sobre como criar padrões de evento .NET e como criar origens de evento padrão, bem como assinar e processar os eventos padrão em seu código."
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 8a3133d6-4ef2-46f9-9c8d-a8ea8898e4c9
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 703b7b13a2175fb9c40ff707f333a1bf1530df8c
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---

# <a name="standard-net-event-patterns"></a>Padrões de evento .NET padrão

[Anterior](events-overview.md)

Os eventos do .NET geralmente seguem alguns padrões conhecidos. Adotar esses padrões significa que os desenvolvedores podem aproveitar o conhecimento desses padrões, que podem ser aplicados a qualquer programa de evento do .NET.

Vamos analisar esses padrões para que você obtenha todo o conhecimento que precisa a fim de criar origens do evento padrão e também assinar e processar eventos padrão em seu código.

## <a name="event-delegate-signatures"></a>Assinaturas de delegado de evento

A assinatura padrão de um delegado de evento do .NET é:

```csharp
void OnEventRaised(object sender, EventArgs args);
```

O tipo de retorno é nulo. Os eventos são baseados em delegados e são delegados multicast. Isso dá suporte a vários assinantes de qualquer origem do evento. O único valor retornado de um método não ajusta a escala para vários assinantes do evento. Qual valor retornado a origem do evento vê depois de gerar um evento? Neste artigo, você verá como criar protocolos de evento que oferecem suporte a assinantes de evento que relatam informações para a origem do evento.

A lista de argumentos contém dois argumentos: o remetente e os argumentos do evento. O tipo de tempo de compilação de `sender` é `System.Object`, mas é provável que você conheça um tipo mais derivado que sempre estaria correto. Por convenção, use `object`.

O segundo argumento normalmente tem sido um tipo derivado de `System.EventArgs`. (Você verá na [próxima seção](modern-events.md) que essa convenção não é mais imposta). Se seu tipo de evento não precisar de nenhum argumento adicional, você ainda fornecerá os dois argumentos.
Há um valor especial, o `EventArgs.Empty`, que você deve usar para indicar que o evento não contém nenhuma informação adicional.

Vamos criar uma classe que lista os arquivos em um diretório ou em qualquer um de seus subdiretórios, que seguem um padrão. Esse componente aciona um evento para cada arquivo encontrado que corresponde ao padrão.

O uso de um modelo de evento fornece algumas vantagens de design. Você pode criar vários ouvintes de eventos que realizam ações diferentes quando um arquivo procurado é encontrado. A combinação de diferentes ouvintes pode criar algoritmos mais robustos.

Aqui está a declaração de argumento de evento inicial para localizar um arquivo pesquisado: 

```csharp
public class FileFoundArgs : EventArgs
{
    public string FoundFile { get; }

    public FileFoundArgs(string fileName)
    {
        FoundFile = fileName;
    }
}
```

Embora esse tipo se pareça com um tipo pequeno de somente dados, você deve seguir a convenção e torná-lo um tipo de referência (`class`). Isso significa que o objeto de argumento será passado por referência e todas as atualizações nos dados serão visualizadas por todos os assinantes. A primeira versão é um objeto imutável. É preferível tornar as propriedades em seu tipo de argumento de evento imutáveis. Dessa forma, um assinante não poderá alterar os valores antes que outro assinante os veja. (Há exceções, como você verá abaixo).  

Em seguida, precisamos criar a declaração de evento na classe FileSearcher. O aproveitamento do tipo `EventHandler<T>` significa que não é necessário criar outra definição de tipo. Você simplesmente usa uma especialização genérica.

Vamos preencher a classe FileSearcher para pesquisar arquivos que correspondam a um padrão e acionar o evento correto quando uma correspondência for descoberta.

```csharp
public class FileSearcher
{
    public event EventHandler<FileFoundArgs> FileFound;

    public void Search(string directory, string searchPattern)
    {
        foreach (var file in Directory.EnumerateFiles(directory, searchPattern))
        {
            FileFound?.Invoke(this, new FileFoundArgs(file));
        }
    }
}
```

## <a name="definining-and-raising-field-like-events"></a>Definindo e acionando eventos semelhantes a campo

A maneira mais simples de adicionar um evento à sua classe é declarar esse evento como um campo público, como no exemplo acima:

```csharp
public event EventHandler<FileFoundArgs> FileFound;
```

Isso é semelhante à declaração de um campo público, o que parece ser uma prática ruim orientada a objetos. Você deseja proteger o acesso a dados por meio de propriedades ou métodos. Ao mesmo tempo em que isso se parece com uma prática ruim, o código gerado pelo compilador cria wrappers para que os objetos de evento só possam ser acessados de maneiras seguras. As únicas operações disponíveis em um evento semelhante a campo são adicionar manipulador:

```csharp
EventHandler<FileFoundArgs> onFileFound = (sender, eventArgs) =>
    Console.WriteLine(eventArgs.FoundFile);
lister.FileFound += onFIleFound;
```

e remover manipulador:

```csharp
lister.FileFound -= onFileFound;
```

Observe que há uma variável local para o manipulador. Se você usou o corpo de lambda, a operação remover não funcionará corretamente. Ela seria uma instância diferente do delegado e silenciosamente não faria nada.

O código fora da classe não pode acionar o evento nem executar outras operações.

## <a name="returning-values-from-event-subscribers"></a>Valor retornados de assinantes de evento

Sua versão simples está funcionando bem. Vamos adicionar outro recurso: cancelamento.

Quando você acionar o evento encontrado, os ouvintes devem ser capazes de parar o processamento, se esse arquivo for aquele que era procurado.

Os manipuladores de eventos não retornam um valor, por isso você precisa comunicar isso de outra forma. O padrão de evento usa o objeto EventArgs para incluir campos que os assinantes de evento podem usar para comunicar o cancelamento.

Há dois padrões diferentes que podem ser usados, com base na semântica do contrato de cancelamento. Em ambos os casos, você adicionará um campo booliano no EventArguments para o evento de arquivo encontrado. 

Um padrão permitiria a qualquer assinante cancelar a operação.
Para esse padrão, o novo campo é inicializado para `false`. Qualquer assinante pode alterá-lo para `true`. Depois que todos os assinantes viram o evento acionado, o componente FileSearcher examina o valor booliano e toma uma ação.

O segundo padrão só cancelaria a operação se todos os assinantes quisessem que a operação fosse cancelada. Nesse padrão, o novo campo é inicializado para indicar que a operação deve ser cancelada e qualquer assinante poderia alterá-lo para indicar que a operação deve continuar.
Depois que todos os assinantes viram o evento acionado, o componente FileSearcher examina o booliano e toma uma ação. Há uma etapa adicional nesse padrão: o componente precisa saber se algum assinante viu o evento. Se não houver nenhum assinante, o campo indicaria incorretamente um cancelamento.

Vamos implementar a primeira versão deste exemplo. Você precisa adicionar um campo booliano ao tipo FileFoundEventArgs:

```csharp
public class FileFoundArgs : EventArgs
{
    public string FoundFile { get; }
    public bool CancelRequested { get; set; }

    public FileFoundArgs(string fileName)
    {
        FoundFile = fileName;
    }
}
```

Esse novo campo deve ser inicializado como falso, de forma que você não cancele sem motivo. Esse é o valor padrão de um campo booliano, portanto isso acontece automaticamente. A única alteração adicional no componente é verificar o sinalizador depois de acionar o evento, para ver se qualquer um dos assinantes solicitou um cancelamento:

```csharp
public void List(string directory, string searchPattern)
{
    foreach (var file in Directory.EnumerateFiles(directory, searchPattern))
    {
        var args = new FileFoundArgs(file);
        FileFound?.Invoke(this, args);
        if (args.CancelRequested)
            break;
    }
}
```

Uma vantagem desse padrão é que ele não é uma alteração significativa.
Nenhum dos assinantes solicitou um cancelamento antes e ainda não o fizeram. Nenhuma parte do código de assinante precisa ser atualizado, a menos que eles queiram dar suporte ao novo protocolo de cancelamento. Ele é acoplado de forma bem livre.

Vamos atualizar o assinante para que ele solicite um cancelamento, depois de encontrar o primeiro executável:

```csharp
EventHandler<FileFoundArgs> onFileFound = (sender, eventArgs) =>
{
    Console.WriteLine(eventArgs.FoundFile);
    eventArgs.CancelRequested = true;
};
```

## <a name="adding-another-event-declaration"></a>Adicionar outra declaração de evento

Vamos adicionar mais um recurso e demonstrar outras expressões de linguagem para eventos. Vamos adicionar uma sobrecarga do método `Search()` que percorre todas os subdiretórios pesquisando arquivos.

Isso poderia se tornar uma operação demorada em um diretório com muitos subdiretórios. Vamos adicionar um evento que é acionado no início de cada nova pesquisa de diretório. Isso permite que os assinantes acompanhem o progresso e atualizem o usuário sobre o progresso. Todos os exemplos que você criou até agora são públicos. Vamos fazer com que esse seja um evento interno. Isso significa que você também pode fazer com que os tipos usados para os argumentos sejam internos.

Você começará criando a nova classe derivada EventArgs para relatar o novo diretório e o andamento. 

```csharp
internal class SearchDirectoryArgs : EventArgs
{
    internal string CurrentSearchDirectory { get; }
    internal int TotalDirs { get; }
    internal int CompletedDirs { get; }

    internal SearchDirectoryArgs(string dir, int totalDirs, int completedDirs)
    {
        CurrentSearchDirectory = dir;
        TotalDirs = totalDirs;
        CompletedDirs = completedDirs;
    }
}
``` 

Novamente, você pode seguir as recomendações para criar um tipo de referência imutável para os argumentos do evento.

Em seguida, defina o evento. Desta vez, você usará uma sintaxe diferente. Além de usar a sintaxe de campo, você pode explicitamente criar a propriedade com os manipuladores adicionar e remover. Neste projeto de exemplo, você não precisará de código extra nos manipuladores, mas será mostrado como criá-los.

```csharp
internal event EventHandler<SearchDirectoryArgs> DirectoryChanged
{
    add { directoryChanged += value; }
    remove { directoryChanged -= value; }
}
private EventHandler<SearchDirectoryArgs> directoryChanged;
```

O código que você escreverá aqui é bem parecido com o código que o compilador gera para as definições de evento de campo vistas anteriormente. Você cria o evento usando uma sintaxe muito parecida àquela utilizada para [propriedades](properties.md). Observe que os manipuladores têm nomes diferentes: `add` e `remove`. Eles são chamados para assinar o evento ou cancelar a inscrição do evento. Observe que você também deve declarar um campo de suporte particular para armazenar a variável de evento. Ele é inicializado como null.

Em seguida, vamos adicionar a sobrecarga do método Search() que percorre os subdiretórios e aciona os dois eventos. A maneira mais fácil de fazer isso é usar um argumento padrão para especificar que você deseja pesquisar todas as pastas:

```csharp
public void Search(string directory, string searchPattern, bool searchSubDirs = false)
{
    if (searchSubDirs)
    {
        var allDirectories = Directory.GetDirectories(directory, "*.*", SearchOption.AllDirectories);
        var completedDirs = 0;
        var totalDirs = allDirectories.Length + 1;
        foreach (var dir in allDirectories)
        {
            directoryChanged?.Invoke(this,
                new SearchDirectoryArgs(dir, totalDirs, completedDirs++));
            // Recursively search this child directory:
            SearchDirectory(dir, searchPattern);
        }
        // Include the Current Directory:
        directoryChanged?.Invoke(this,
            new SearchDirectoryArgs(directory, totalDirs, completedDirs++));
        SearchDirectory(directory, searchPattern);
    }
    else
    {
        SearchDirectory(directory, searchPattern);
    }
}

private void SearchDirectory(string directory, string searchPattern)
{
    foreach (var file in Directory.EnumerateFiles(directory, searchPattern))
    {
        var args = new FileFoundArgs(file);
        FileFound?.Invoke(this, args);
        if (args.CancelRequested)
            break;
    }
}
```

Neste momento, você pode executar o aplicativo, chamando a sobrecarga para pesquisar todos os subdiretórios. Não há nenhum assinante no novo evento `ChangeDirectory`, mas o uso da expressão `?.Invoke()` garante que isso funcione corretamente.

 Vamos adicionar um manipulador para escrever uma linha que mostra o andamento na janela do console. 

```csharp
lister.DirectoryChanged += (sender, eventArgs) =>
{
    Console.Write($"Entering '{eventArgs.CurrentSearchDirectory}'.");
    Console.WriteLine($" {eventArgs.CompletedDirs} of {eventArgs.TotalDirs} completed...");
};
```

Você viu os padrões que são seguidos em todo o ecossistema do .NET.
Ao aprender esses padrões e convenções, você escreverá expressões idiomáticas de C# e .NET rapidamente.

Em seguida, você verá algumas alterações nesses padrões na versão mais recente do .NET.

[Avançar](modern-events.md)

