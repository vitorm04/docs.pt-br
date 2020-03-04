---
title: Estrutura de um programa em C# - um tour pela linguagem C#
description: Saiba mais sobre os blocos de construção básicos de um programa em C#
ms.date: 02/25/2020
ms.assetid: 984f0314-507f-47a0-af56-9011243f5e65
ms.openlocfilehash: 828146ba509daf9427e6dd1a4ebf3ad747ac7c39
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159111"
---
# <a name="program-structure"></a>Estrutura do programa

Os principais conceitos organizacionais em C# são ***programas***, ***namespaces***, ***tipos***, ***membros*** e ***assemblies***. Os programas C# consistem em um ou mais arquivos de origem. Os programas declaram tipos que contêm membros e podem ser organizados em namespaces. Classes e interfaces são exemplos de tipos. Campos, métodos, propriedades e eventos são exemplos de membros. Quando C# os programas são compilados, eles são fisicamente empacotados em assemblies. Os assemblies normalmente têm a extensão de arquivo `.exe` ou `.dll`, dependendo se eles implementam ***aplicativos*** ou ***bibliotecas***, respectivamente.

Você pode criar um projeto de biblioteca chamado *Acme* usando o comando `dotnet new`:

```console
dotnet new classlib -o acme
```

Nesse projeto, declare uma classe chamada `Stack` em um namespace chamado `Acme.Collections`:

[!code-csharp[Stack](../../../samples/snippets/csharp/tour/program-structure/program.cs#L1-L34)]

O nome totalmente qualificado dessa classe é `Acme.Collections.Stack`. A classe contém vários membros: um campo chamado `top`, dois métodos chamados `Push` e `Pop` e uma classe aninhada chamada `Entry`. A classe `Entry` ainda contém três membros: um campo chamado `next`, um campo chamado `data`e um construtor. O comando:

```console
dotnet build 
```

compila o exemplo como uma biblioteca (o código sem um ponto de entrada `Main`) e produz um assembly denominado `acme.dll`.

Os assemblies contêm código executável na forma de instruções de IL (Linguagem Intermediária) e informações simbólicas na forma de metadados. Antes de ser executado, o compilador JIT (just-in-time) do .NET Common Language Runtime converte o código IL em um assembly para o código específico do processador.

Como um assembly é uma unidade de funcionalidade autodescreveda que contém o código e os metadados, não há necessidade de `#include` diretivas e arquivos de C#cabeçalho no. Os tipos públicos e os membros contidos em um assembly específico são disponibilizados em um programa C# simplesmente fazendo referência a esse assembly ao compilar o programa. Por exemplo, esse programa usa a classe `Acme.Collections.Stack` do assembly `acme.dll`:

[!code-csharp[UsingStack](../../../samples/snippets/csharp/tour/program-structure/Program.cs#L38-L52)]

O arquivo *csproj* do projeto do programa anterior deve incluir um nó de referência para que C# o compilador resolva as referências às classes no assembly `acme.dll`:

```xml
  <ItemGroup>
    <ProjectReference Include="..\acme\acme.csproj" />
  </ItemGroup>
```

Após essa adição, `dotnet build` cria um assembly executável chamado `example.exe`, que, quando executado, produz a saída:

```console
100
10
1
```

O C# permite que o texto de origem de um programa seja armazenado em vários arquivos de origem. Quando um programa em C# com vários arquivo é compilado, todos os arquivos de origem são processados juntos e os arquivos de origem podem referenciar livremente uns aos outros. Conceitualmente, é como se todos os arquivos de origem fossem concatenados em um arquivo grande antes de serem processados. Declarações de encaminhamento nunca são C# necessárias em porque, com poucas exceções, a ordem da declaração é insignificante. O C# não limita um arquivo de origem para declarar somente um tipo público nem requer o nome do arquivo de origem para corresponder a um tipo declarado no arquivo de origem.

>[!div class="step-by-step"]
>[Anterior](index.md)
>[Próximo](types-and-variables.md)
