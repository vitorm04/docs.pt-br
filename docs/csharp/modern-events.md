---
title: "O padrão de eventos atualizado do .NET Core Event"
description: "O padrão de eventos atualizado do .NET Core Event"
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 9aa627c3-3222-4094-9ca8-7e88e1071e06
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: d750209f2d970044aac2f3b8b119412a58595171
ms.lasthandoff: 03/13/2017

---

# <a name="the-updated-net-core-event-pattern"></a>O padrão de eventos atualizado do .NET Core Event

[Anterior](event-pattern.md)

O artigo anterior abordou os padrões de eventos mais comuns. O .NET Core tem um padrão mais flexível. Nesta versão, a definição `EventHandler<TEventArgs>` não tem a restrição de que `TEventArgs` deve ser uma classe derivada de `System.EventArgs`.

Isso aumenta a flexibilidade para você e é compatível com versões anteriores. Vamos começar com a flexibilidade. A classe System.EventArgs introduz um método: `MemberwiseClone()`, que cria uma cópia superficial do objeto.
Esse método deve usar a [reflexão](reflection.md) para implementar sua funcionalidade para qualquer classe derivada de `EventArgs`. Essa funcionalidade é mais fácil de criar em uma classe derivada específica. Na prática, isso significa que a derivação de System.EventArgs é uma restrição que limita seus designs, mas não oferece nenhum benefício adicional.
Na verdade, você pode alterar as definições de `FileFoundArgs` e `SearchDirectoryArgs` para que eles não derivem de `EventArgs`.
O programa funcionará exatamente da mesma forma.

Você também pode alterar o `SearchDirectoryArgs` para um struct se também fazer mais uma alteração:

```csharp  
internal struct SearchDirectoryArgs  
{  
    internal string CurrentSearchDirectory { get; }  
    internal int TotalDirs { get; }  
    internal int CompletedDirs { get; }  
    
    internal SearchDirectoryArgs(string dir, int totalDirs, 
        int completedDirs) : this()  
    {  
        CurrentSearchDirectory = dir;  
        TotalDirs = totalDirs;  
        CompletedDirs = completedDirs;  
    }  
}  
```   

A alteração adicional é chamar o construtor padrão antes de inserir o construtor que inicializa todos os campos. Sem esse acréscimo, as regras de C# informariam que as propriedades estão sendo acessadas antes de terem sido atribuídas.

Você não deve alterar o `FileFoundArgs` de uma classe (tipo de referência) para um struct (tipo de valor). Isso ocorre porque o protocolo para manipular cancelamentos exige que os argumentos do evento sejam passados por referência. Se você fizesse a mesma alteração, a classe de pesquisa de arquivo nunca observaria as alterações feitas por qualquer um dos assinantes do evento. Uma nova cópia da estrutura seria usada para cada assinante e essa cópia seria uma cópia diferente daquela vista pelo objeto de pesquisa de arquivo.

Em seguida, vamos considerar como essa alteração pode ser compatível com versões anteriores.
A remoção da restrição não afeta nenhum código existente. Qualquer tipo de argumento de evento existente ainda deriva de `System.EventArgs`.
A compatibilidade com versões anteriores é um dos principais motivos pelos quais eles vão continuar derivando de `System.EventArgs`. Assinantes de eventos existentes serão assinantes de um evento que seguiu o padrão clássico.

Seguindo uma lógica semelhante, qualquer tipo de argumento de evento criado agora não teria assinantes nas bases de código existentes. Novos tipos de evento que não derivam de `System.EventArgs` não quebram essas bases de código.

## <a name="events-with-async-subscribers"></a>Eventos com assinantes assíncronos

Você tem um último padrão para aprender: como escrever corretamente os assinantes do evento que chamam o código assíncrono. O desafio é descrito no artigo em [async e await](async.md). Métodos assíncronos podem ter um tipo de retorno nulo, mas isso não é recomendável. Quando seu código de assinante de evento chama um método assíncrono, você não terá outra escolha além de criar um método `async void`. A assinatura do manipulador de eventos o exige.

Você precisa conciliar essas diretrizes opostas. De alguma forma, você precisa criar um método `async void` seguro. As noções básicas do padrão que você precisa implementar estão abaixo:

```csharp
worker.StartWorking += async (sender, eventArgs) =>
{
    try 
    {
        await DoWorkAsync();
    }
    catch (Exception e)
    {
        //Some form of logging.
        Console.WriteLine($"Async task failure: {e.ToString()}");
        // Consider gracefully, and quickly exiting.
    }
};
```

Primeiro, observe que o manipulador está marcado como um manipulador assíncrono. Como está sendo atribuído a um tipo de delegado de manipulador de eventos, ele terá um tipo de retorno nulo. Isso significa que você deve seguir o padrão mostrado no manipulador e não permitir que qualquer exceção seja gerada fora do contexto do manipulador assíncrono. Como ele não retorna uma tarefa, não há nenhuma tarefa que pode relatar o erro entrando no estado de falha. Como o método é assíncrono, ele não pode simplesmente gerar a exceção. (O método de chamada continua a execução porque é `async`.) O comportamento de tempo de execução real será definido de forma diferente para ambientes diferentes. Ele pode encerrar o thread, pode encerrar o programa ou pode deixar o programa em um estado indeterminado. Nenhum desses são bons resultados.

É por isso que você deve encapsular a instrução await para a tarefa assíncrona em seu próprio bloco de teste. Se isso causar uma tarefa com falha, você pode registrar o erro em log. Se for um erro do qual não é possível recuperar o aplicativo, você pode sair do programa rápida e normalmente

Essas são as principais atualizações do padrão de eventos do .NET. Você verá muitos exemplos das versões anteriores nas bibliotecas com que trabalhar. No entanto, você também precisa compreender quais são os padrões mais recentes.

O próximo artigo desta série ajuda a distinguir entre o uso de `delegates` e de `events` em seus designs. Eles são conceitos similares e artigo o ajudará a tomar a melhor decisão para seus programas.

[Avançar](distinguish-delegates-events.md)

