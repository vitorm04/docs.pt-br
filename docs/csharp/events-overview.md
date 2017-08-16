---
title: "Introdução a Eventos"
description: "Introdução a Eventos"
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 9b8d2a00-1584-4a5b-8994-5003d54d8e0c
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: a2eb8daef0883b78769a185be7d64e43c88b1d15
ms.lasthandoff: 03/13/2017

---

# <a name="introduction-to-events"></a>Introdução a Eventos

[Anterior](delegates-patterns.md)

Eventos são, assim como delegados, um mecanismo de *associação tardia*. De fato, os eventos são criados com base no suporte de linguagem para delegados.

Os eventos são uma forma de um objeto difundir (para todos os componentes interessados do sistema) que algo aconteceu. Qualquer outro componente pode assinar ao evento e ser notificado quando um evento for gerado.

Provavelmente, você usou eventos em alguma parte de sua programação. Muitos sistemas gráficos têm um modelo de evento para informar a interação do usuário. Esses eventos informariam movimentos do mouse, pressionamentos de botão e interações semelhantes. Esse é um dos cenários mais comuns, mas certamento não o único cenário em que eventos são usados.

Você pode definir os eventos que devem ser gerados para suas classes. Uma consideração importante ao trabalhar com eventos é que pode não haver nenhum objeto registrado para um determinado evento. Você deve escrever seu código de modo que ele não gere eventos quando nenhum ouvinte estiver configurado.

Assinar um evento também cria um acoplamento entre dois objetos (a origem do evento e o coletor do evento). Você precisa garantir que o coletor do evento cancele a assinatura da origem do evento quando não houver mais interesse nos eventos.

## <a name="design-goals-for-event-support"></a>Metas de design para o suporte a eventos

O design de linguagem para eventos tem como alvo essas metas.

Primeiro, habilite o acoplamento mínimo entre uma origem de evento e um coletor de evento. Esses dois componentes não podem ter sido escritos pela mesma organização e podem até mesmo ser atualizados segundo cronogramas totalmente diferentes.

Em segundo lugar, deve ser muito simples assinar em um evento e cancelar a assinatura desse mesmo evento.

E, por fim, fontes de eventos devem dar suporte a vários assinantes do evento. Elas também devem dar suporte a não ter assinantes de evento anexados.

Você pode ver que as metas para os eventos são muito semelhantes às metas para delegados.
É por isso que o suporte à linguagem do evento é baseado no suporte à linguagem do delegado.

## <a name="language-support-for-events"></a>Suporte de linguagem para eventos

A sintaxe para definir eventos e se inscrever ou cancelar a inscrição em eventos é uma extensão da sintaxe de delegados.

Para definir um evento, você use a palavra-chave `event`:

```csharp
public event EventHandler<FileListArgs> Progress;
```

O tipo de evento (`EventHandler<FileListArgs>` neste exemplo) deve ser um tipo delegado. Há uma série de convenções que você deve seguir ao declarar um evento. Normalmente, o tipo de delegado do evento tem um retorno nulo.
Declarações de evento devem ser um verbo ou uma frase verbal.
Use o tempo passado (como neste exemplo) quando o evento informar que algo aconteceu. Use um tempo verbal presente (por exemplo, `Closing`) para informar algo que está prestes a ocorrer. Frequentemente, usar o tempo presente indica que sua classe dá suporte a algum tipo de comportamento de personalização. Um dos cenários mais comuns é dar suporte ao cancelamento. Por exemplo, um evento `Closing` pode incluir um argumento que indicaria se a operação de encerramento deve continuar ou não.  Outros cenários podem permitir que os chamadores modifiquem o comportamento atualizando propriedades dos argumentos do evento. Você pode acionar um evento para indicar uma próxima ação proposta que um algoritmo usará. O manipulador de eventos pode forçar uma ação diferente modificando as propriedades do argumento do evento.

Quando quiser acionar o evento, você pode chamar os manipuladores de eventos usando a sintaxe de invocação de delegado:

```csharp
Progress?.Invoke(this, new FileListArgs(file));
```

Conforme discutido na seção sobre [delegados](delegates-patterns.md), o operador ?.
torna fácil garantir que você não tente acionar o evento quando não houver nenhum assinante do evento.
 
Assine um evento usando o operador `+=`:

```csharp
EventHandler<FileListArgs> onProgress = (sender, eventArgs) => 
    Console.WriteLine(eventArgs.FoundFile);
lister.Progress += OnProgress;
```

O método do manipulador normalmente é o prefixo "On" seguido do nome do evento, conforme mostrado acima.

Cancele a assinatura usando o operador `-=`:

```csharp
lister.Progress -= onProgress;
```

É importante observar que eu declarei um variável local para a expressão que representa o manipulador de eventos. Isso garante que o cancelamento da assinatura remova o manipulador.
Se, em vez disso, você tiver usado o corpo da expressão lambda, você estará tentando remover um manipulador que nunca foi anexado, o que não faz nada.

No próximo artigo, você aprenderá mais sobre padrões de evento típicos e diferentes variações deste exemplo.

[Avançar](event-pattern.md)

