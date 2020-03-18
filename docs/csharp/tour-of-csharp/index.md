---
title: Um tour pelo C# – Guia do C#
description: Novato em C#? Conheça os fundamentos da linguagem.
ms.date: 02/26/2020
ms.openlocfilehash: bf5a200f2ee777698ae8564f348ffc117d9abab0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79156838"
---
# <a name="a-tour-of-the-c-language"></a>Um tour pela língua C#

C# (pronuncia-se "See Sharp") é uma linguagem de programação moderna, orientada a objetos e segura de tipo. O C# tem suas raízes na família de linguagens C e os programadores em C, C++, Java e JavaScript a reconhecerão imediatamente.

Este tour fornece uma visão geral dos principais componentes do idioma em C# 8 e anteriormente. Se você quiser explorar o idioma através de exemplos interativos, tente a introdução aos tutoriais [C#.](../tutorials/intro-to-csharp/index.md)

O C# é uma linguagem orientada a objeto, mas inclui ainda suporte para programação ***orientada a componentes***. O design de software atual depende cada vez mais dos componentes de software na forma de pacotes independentes e autodescritivos de funcionalidade. A chave para esses componentes é que eles apresentam um modelo de programação com propriedades, métodos e eventos. Eles têm atributos que fornecem informações declarativas sobre o componente. Eles incorporam sua própria documentação. C# fornece construções linguísticas para apoiar diretamente esses conceitos, tornando c# uma linguagem natural na qual criar e usar componentes de software.

Várias características C# auxiliam na construção de aplicações robustas e duráveis. ***A coleta de lixo*** recupera automaticamente a memória ocupada por objetos não utilizados inalcançáveis. ***O manuseio de exceções*** fornece uma abordagem estruturada e extensível para detecção e recuperação de erros. O design ***seguro de tipo*** da linguagem torna impossível ler a partir de variáveis não inicializadas, para indexar matrizes além de seus limites ou para executar moldes de tipo não controlados.

C# tem um ***sistema de tipo unificado***. Todos os tipos do C#, incluindo tipos primitivos, como `int` e `double`, herdam de um único tipo de `object` raiz. Assim, todos os tipos compartilham um conjunto de operações comuns, e valores de qualquer tipo podem ser armazenados, transportados e operados de maneira consistente. Além disso, C# oferece suporte a tipos de referência e tipos de valor definidos pelo usuário, permitindo a alocação dinâmica de objetos, bem como o armazenamento em linha de estruturas leves.

Para garantir que os programas e bibliotecas C# possam evoluir ao longo do tempo de forma compatível, muita ênfase foi colocada na ***versão*** no design do C#. Muitas linguagens de programação prestam pouca atenção a esta questão. Como resultado, os programas escritos nessas outras línguas quebram com mais frequência do que o necessário quando são introduzidas versões mais recentes de bibliotecas dependentes. Aspectos do design de C#que foram diretamente influenciados pelas `virtual` considerações de versão incluem os modificadores separados e `override` modificadores, as regras para resolução de sobrecarga de método e suporte para declarações explícitas de membros da interface.

Em versões mais recentes, C# abraçou outros paradigmas de programação. C# incluiu recursos que suportam técnicas de programação funcional, como expressões lambda. Outros novos recursos suportam a separação de dados e algoritmos, como a correspondência de padrões.

## <a name="hello-world"></a>Olá, Mundo

O programa "Hello, World" é usado tradicionalmente para introduzir uma linguagem de programação. Este é para C#:

[!code-csharp[Hello World](~/samples/snippets/csharp/tour/hello/Program.cs)]

Os arquivos de origem em C# normalmente têm a extensão de arquivo `.cs`. Para criar este programa, primeiro baixe e instale o [.NET Core SDK](https://dotnet.microsoft.com/download). Em seguida, `dotnet new console -o hello` execute o comando para criar um novo programa e um script de compilação. O script de programa e `Program.cs` `hello.csproj`construção estão nos arquivos e, respectivamente. Você constrói e executa `run` o aplicativo com os comandos:

```dotnetcli
cd hello
dotnet run
```

O programa produz a seguinte saída:

```console
Hello, World!
```

O programa "Hello, World" começa com uma diretiva `using` que faz referência ao namespace `System`. Namespaces fornecem um meio hierárquico de organizar bibliotecas e programas em C#. Os namespaces contêm tipos e outros namespaces — por exemplo, o namespace `System` contém uma quantidade de tipos, como a classe `Console` referenciada no programa e diversos outros namespaces, como `IO` e `Collections`. A diretiva `using` que faz referência a um determinado namespace permite o uso não qualificado dos tipos que são membros desse namespace. Devido à diretiva `using`, o programa pode usar `Console.WriteLine` como um atalho para `System.Console.WriteLine`.

A classe `Hello` declarada pelo programa "Hello, World" tem um único membro, o método chamado `Main`. O método `Main` é declarado com o modificador estático. Embora os métodos de instância possam fazer referência a uma determinada instância de objeto delimitador usando a palavra-chave `this`, métodos estáticos operam sem referência a um objeto específico. Por convenção, um método estático denominado `Main` serve como ponto de entrada de um programa.

A saída do programa é produzida pelo método `WriteLine` da classe `Console` no namespace `System`. Essa classe é fornecida pelas bibliotecas de classe padrão, que, por padrão, são referenciadas automaticamente pelo compilador.

## <a name="elements-of-the-c-language"></a>Elementos da linguagem C#

Há muito mais para aprender sobre C#. Os tópicos a seguir fornecem uma visão geral dos elementos da linguagem C#. Essas visões gerais fornecem informações básicas sobre todos os elementos da linguagem e fornecem as informações necessárias para mergulhar mais fundo:

- [Estrutura do programa](program-structure.md)
  - Aprenda os principais conceitos organizacionais na linguagem C#: ***programas***, ***namespaces***, ***tipos***, ***membros*** e ***assemblies***.
- [Tipos e Variáveis](types-and-variables.md)
  - Saiba mais sobre ***tipos de valor***, ***tipos de referência***, e ***variáveis*** na linguagem C#.
- [Expressões](expressions.md)
  - ***Expressões*** são construídas a partir de ***operandos*** e ***operadores***. As expressões produzem um valor.
- [Declarações](statements.md)
  - Você usa ***instruções*** para expressar as ações de um programa.
- [Classes e objetos](classes-and-objects.md)
  - As ***classes*** são os tipos do C# mais fundamentais. Os ***objetos*** são instâncias de uma classe. As classes são compiladas usando ***membros***, que também são abordados neste tópico.
- [Matrizes](arrays.md)
  - Uma ***matriz*** é uma estrutura de dados que contém algumas variáveis acessadas por meio de índices calculados.
- [Interfaces](interfaces.md)
  - Uma ***interface*** define um contrato que pode ser implementado por classes e estruturas. Uma interface pode conter métodos, propriedades, eventos e indexadores. Uma interface não fornece implementações dos membros que define — apenas especifica os membros que devem ser fornecidos por classes ou estruturas que implementam a interface.
- [Delega](delegates.md)
  - Um ***delegado*** é um tipo que representa referências aos métodos com uma lista de parâmetros e tipo de retorno específicos. Delegados possibilitam o tratamento de métodos como entidades que podem ser atribuídos a variáveis e passadas como parâmetros. Os delegados são parecidos com o conceito de ponteiros de função em outras linguagens, mas ao contrário dos ponteiros de função, os delegados são orientados a objetos e fortemente tipados.
- [Atributos](attributes.md)
  - ***Atributos*** permitem que programas especifiquem informações declarativas adicionais sobre tipos, membros e outras entidades.
  
> [!NOTE]
> Estes artigos se aplicam a C# 7.0 e posteriores. Alguns recursos podem não estar disponíveis em versões anteriores.

> [!div class="step-by-step"]
> [Avançar](program-structure.md)
