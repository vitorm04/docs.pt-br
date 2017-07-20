---
title: "Estrutura do programa C# – um tour pela linguagem C# | Microsoft Docs"
description: "Saiba mais sobre os blocos de construção básicos de um programa em C#"
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 08/10/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 984f0314-507f-47a0-af56-9011243f5e65
ms.translationtype: Human Translation
ms.sourcegitcommit: 4437ce5d344cf06d30e31911def6287999fc6ffc
ms.openlocfilehash: 3642b6525691d6179eca66f11d5002377323cdf3
ms.contentlocale: pt-br
ms.lasthandoff: 05/23/2017

---

# Estrutura do programa
<a id="program-structure" class="xliff"></a>

Os principais conceitos organizacionais em C# são ***programas***, ***namespaces***, ***tipos***, ***membros*** e ***assemblies***. Os programas C# consistem em um ou mais arquivos de origem. Os programas declaram tipos que contêm membros e podem ser organizados em namespaces. Classes e interfaces são exemplos de tipos. Campos, métodos, propriedades e eventos são exemplos de membros. Quando os programas em C# são compilados, eles são empacotados fisicamente em assemblies. Os assemblies normalmente têm a extensão de arquivo `.exe` ou `.dll`, dependendo se eles implementam ***aplicativos*** ou ***bibliotecas***, respectivamente.

O exemplo declara uma classe chamada `Stack` em um namespace chamado `Acme.Collections`:

[!code-csharp[Pilha](../../../samples/snippets/csharp/tour/program-structure/program.cs#L1-L34)]

O nome totalmente qualificado dessa classe é `Acme.Collections.Stack`. A classe contém vários membros: um campo chamado `top`, dois métodos chamados `Push` e `Pop` e uma classe aninhada chamada `Entry`. A classe `Entry` ainda contém três membros: um campo chamado `next`, um campo chamado `data`e um construtor. Supondo que o código-fonte do exemplo seja armazenado no arquivo `acme.cs`, a linha de comando

```
csc /t:library acme.cs
```

compila o exemplo como uma biblioteca (o código sem um ponto de entrada `Main`) e produz um assembly denominado `acme.dll`.

> [!IMPORTANT]
> Os exemplos acima usam `csc` como o compilador C# da linha de comando. Esse compilador é um executável do Windows. Para usar C# em outras plataformas, você deve usar as ferramentas para o .NET Core. O ecossistema do .NET Core usa o CLI `dotnet` para gerenciar as compilações de linha de comando. Isso inclui gerenciamento de dependências e invocação do compilador C#. Consulte [este tutorial](../../core/tutorials/using-with-xplat-cli.md) para obter uma descrição completa dessas ferramentas nas plataformas com suporte do .NET Core.

Os assemblies contêm código executável na forma de instruções de IL (Linguagem Intermediária) e informações simbólicas na forma de metadados. Antes de ser executado, o código de IL em um assembly é automaticamente convertido em código específico do processador pelo compilador JIT (Just-In-Time) do .NET Common Language Runtime.

Como um assembly é uma unidade autodescritiva da funcionalidade que contém o código e os metadados, não é necessário de diretivas `#include` e arquivos de cabeçalho no C#. Os tipos públicos e os membros contidos em um assembly específico são disponibilizados em um programa C# simplesmente fazendo referência a esse assembly ao compilar o programa. Por exemplo, esse programa usa a classe `Acme.Collections.Stack` do assembly `acme.dll`:

[!code-csharp[UsingStack](../../../samples/snippets/csharp/tour/program-structure/Program.cs#L38-L52)]

Se o programa é armazenado no arquivo `example.cs`, quando `example.cs` é compilado, o assembly acme.dll pode ser referenciado usando a opção de /r do compilador:

```
csc /r:acme.dll example.cs
```

Isso cria um assembly executável denominado `example.exe`, que, quando executado, produz a saída:

```
100
10
1
```

O C# permite que o texto de origem de um programa seja armazenado em vários arquivos de origem. Quando um programa em C# com vários arquivo é compilado, todos os arquivos de origem são processados juntos e os arquivos de origem podem referenciar livremente uns aos outros. Conceitualmente, é como se todos os arquivos de origem fossem concatenados em um arquivo grande antes de serem processados. Declarações de encaminhamento nunca são necessárias em C#, porque, com poucas exceções, a ordem de declaração é insignificante. O C# não limita um arquivo de origem para declarar somente um tipo público nem requer o nome do arquivo de origem para corresponder a um tipo declarado no arquivo de origem.

>[!div class="step-by-step"]
[Anterior](index.md)
[Próximo](types-and-variables.md)

