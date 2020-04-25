---
title: Um tour pelo C# – Guia do C#
description: Novato em C#? Conheça os fundamentos da linguagem.
ms.date: 02/26/2020
ms.openlocfilehash: 7476356ceab39d5cccb6ccbeb991653f08a324ea
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82141042"
---
# <a name="a-tour-of-the-c-language"></a>Um tour pela linguagem C#

O C# (pronuncia-se "Veja nítido") é uma linguagem de programação moderna, orientada a objeto e de tipo seguro. O C# tem suas raízes na família de linguagens C e os programadores em C, C++, Java e JavaScript a reconhecerão imediatamente.

Este tour fornece uma visão geral dos principais componentes do idioma no C# 8 e versões anteriores. Se você quiser explorar a linguagem por meio de exemplos interativos, experimente a [introdução aos](../tutorials/intro-to-csharp/index.md) tutoriais do C#.

O C# é uma linguagem orientada a objeto, mas inclui ainda suporte para programação ***orientada a componentes***. O design de software atual depende cada vez mais dos componentes de software na forma de pacotes independentes e autodescritivos de funcionalidade. A chave para esses componentes é que eles apresentam um modelo de programação com propriedades, métodos e eventos. Eles têm atributos que fornecem informações declarativas sobre o componente. Eles incorporam sua própria documentação. O c# fornece construções de linguagem para dar suporte diretamente a esses conceitos, tornando o C# uma linguagem natural para criar e usar componentes de software.

Vários recursos do C# auxiliam na construção de aplicativos robustos e duráveis. A ***coleta de lixo*** recupera automaticamente a memória ocupada por objetos não utilizados inacessíveis. A ***manipulação de exceção*** fornece uma abordagem estruturada e extensível para detecção e recuperação de erros. O design de ***tipo seguro*** da linguagem torna impossível a leitura de variáveis não inicializadas, para indexar matrizes além dos limites ou para executar conversões de tipo desmarcadas.

C# tem um ***sistema de tipo unificado***. Todos os tipos do C#, incluindo tipos primitivos, como `int` e `double`, herdam de um único tipo de `object` raiz. Assim, todos os tipos compartilham um conjunto de operações comuns, e valores de qualquer tipo podem ser armazenados, transportados e operados de maneira consistente. Além disso, C# oferece suporte a tipos de referência e tipos de valor definidos pelo usuário, permitindo a alocação dinâmica de objetos, bem como o armazenamento em linha de estruturas leves.

Para garantir que os programas e bibliotecas C# possam evoluir ao longo do tempo de maneira compatível, muito ênfase foi colocado no ***controle de versão*** no design do C#. Muitas linguagens de programação têm pouca atenção para esse problema. Como resultado, os programas escritos nessas outras linguagens são quebrados com mais frequência do que o necessário quando versões mais recentes de bibliotecas dependentes são introduzidas. Aspectos do design do C# que foram influenciados diretamente pelas considerações de controle de versão `virtual` incluem `override` os modificadores and separados, as regras para resolução de sobrecarga de método e suporte para declarações de membro de interface explícitas.

Em versões mais recentes, o C# adotou outros paradigmas de programação. O C# inclui recursos que dão suporte a técnicas de programação funcional como expressões lambda. Outros novos recursos dão suporte à separação de dados e algoritmos, como correspondência de padrões.

## <a name="hello-world"></a>Hello world

O programa "Hello, World" é usado tradicionalmente para introduzir uma linguagem de programação. Este é para C#:

[!code-csharp[Hello World](~/samples/snippets/csharp/tour/hello/Program.cs)]

Os arquivos de origem em C# normalmente têm a extensão de arquivo `.cs`. Para criar esse programa, primeiro Baixe e instale o [SDK do .NET Core](https://dotnet.microsoft.com/download). Em seguida, execute o `dotnet new console -o hello` comando para criar um novo programa e um script de compilação. O programa e o script de Build estão nos `Program.cs` arquivos `hello.csproj`e, respectivamente. Você cria e executa o aplicativo com os `run` comandos:

```dotnetcli
cd hello
dotnet run
```

O programa produz a seguinte saída:

```dotnetcli
Hello, World!
```

O programa "Hello, World" começa com uma diretiva `using` que faz referência ao namespace `System`. Namespaces fornecem um meio hierárquico de organizar bibliotecas e programas em C#. Os namespaces contêm tipos e outros namespaces — por exemplo, o namespace `System` contém uma quantidade de tipos, como a classe `Console` referenciada no programa e diversos outros namespaces, como `IO` e `Collections`. A diretiva `using` que faz referência a um determinado namespace permite o uso não qualificado dos tipos que são membros desse namespace. Devido à diretiva `using`, o programa pode usar `Console.WriteLine` como um atalho para `System.Console.WriteLine`.

A classe `Hello` declarada pelo programa "Hello, World" tem um único membro, o método chamado `Main`. O método `Main` é declarado com o modificador estático. Embora os métodos de instância possam fazer referência a uma determinada instância de objeto delimitador usando a palavra-chave `this`, métodos estáticos operam sem referência a um objeto específico. Por convenção, um método estático denominado `Main` serve como ponto de entrada de um programa.

A saída do programa é produzida pelo método `WriteLine` da classe `Console` no namespace `System`. Essa classe é fornecida pelas bibliotecas de classe padrão, que, por padrão, são referenciadas automaticamente pelo compilador.

## <a name="elements-of-the-c-language"></a>Elementos da linguagem C#

Há muito mais para aprender sobre C#. Os tópicos a seguir fornecem uma visão geral dos elementos da linguagem C#. Essas visões gerais fornecem informações básicas sobre todos os elementos da linguagem e fornecem as informações necessárias para se aprofundar:

- [Estrutura do programa](program-structure.md)
  - Aprenda os principais conceitos organizacionais na linguagem C#: ***programas***, ***namespaces***, ***tipos***, ***membros*** e ***assemblies***.
- [Tipos e variáveis](types-and-variables.md)
  - Saiba mais sobre ***tipos de valor***, ***tipos de referência***, e ***variáveis*** na linguagem C#.
- [Expressões](expressions.md)
  - ***Expressões*** são construídas a partir de ***operandos*** e ***operadores***. As expressões produzem um valor.
- [Instruções](statements.md)
  - Você usa ***instruções*** para expressar as ações de um programa.
- [Classes e objetos](classes-and-objects.md)
  - As ***classes*** são os tipos do C# mais fundamentais. Os ***objetos*** são instâncias de uma classe. As classes são compiladas usando ***membros***, que também são abordados neste tópico.
- [Matrizes](arrays.md)
  - Uma ***matriz*** é uma estrutura de dados que contém algumas variáveis acessadas por meio de índices calculados.
- [Interfaces](interfaces.md)
  - Uma ***interface*** define um contrato que pode ser implementado por classes e estruturas. Uma interface pode conter métodos, propriedades, eventos e indexadores. Uma interface não fornece implementações dos membros que ele define — ela simplesmente especifica os membros que devem ser fornecidos por classes ou estruturas que implementam a interface.
- [Delegados](delegates.md)
  - Um ***delegado*** é um tipo que representa referências aos métodos com uma lista de parâmetros e tipo de retorno específicos. Delegados possibilitam o tratamento de métodos como entidades que podem ser atribuídos a variáveis e passadas como parâmetros. Os delegados são parecidos com o conceito de ponteiros de função em outras linguagens, mas ao contrário dos ponteiros de função, os delegados são orientados a objetos e fortemente tipados.
- [Atributos](attributes.md)
  - ***Atributos*** permitem que programas especifiquem informações declarativas adicionais sobre tipos, membros e outras entidades.
  
> [!NOTE]
> Esses artigos se aplicam ao C# 7,0 e posterior. Alguns recursos podem não estar disponíveis em versões anteriores.

> [!div class="step-by-step"]
> [Avançar](program-structure.md)
