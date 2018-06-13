---
title: Um tour pelo C# – Guia do C#
description: Novato em C#? Conheça os fundamentos da linguagem.
ms.date: 08/10/2016
ms.assetid: ebc727cd-8112-42e7-b59c-3c2873ad661c
ms.openlocfilehash: bdb8a84083b391c27d39f5c566a01b2db318123f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33359001"
---
# <a name="a-tour-of-the-c-language"></a>Um tour pela linguagem C#  

O C# (pronuncia-se "C Sharp") é uma linguagem de programação simples, moderna, orientada a objeto e fortemente tipada. O C# tem suas raízes na família de linguagens C e os programadores em C, C++, Java e JavaScript a reconhecerão imediatamente.

O C# é uma linguagem orientada a objeto, mas inclui ainda suporte para programação ***orientada a componentes***. O design de software atual depende cada vez mais dos componentes de software na forma de pacotes independentes e autodescritivos de funcionalidade. O principal é que esses componentes apresentam um modelo de programação com propriedades, métodos e eventos; eles têm atributos que fornecem informações declarativas sobre o componente; e incorporam sua própria documentação. C# fornece construções de linguagem para dar suporte diretamente a esses conceitos, tornando C# uma linguagem muito natural para criação e uso de componentes de software.

Vários recursos do C# auxiliam na construção de aplicativos robustos e duradouros: ***Coleta de lixo*** recupera automaticamente a memória ocupada por objetos inacessíveis não utilizados; ***tratamento de exceção*** fornece uma abordagem estruturada e extensível para detecção e recuperação de erros; e o design ***fortemente tipado*** da linguagem impossibilita a leitura das variáveis não inicializadas, a indexação de matrizes além dos seus limites ou a execução de conversões de tipo não verificadas.

C# tem um ***sistema de tipo unificado***. Todos os tipos do C#, incluindo tipos primitivos, como `int` e `double`, herdam de um único tipo de `object` raiz. Assim, todos os tipos compartilham um conjunto de operações comuns, e valores de qualquer tipo podem ser armazenados, transportados e operados de maneira consistente. Além disso, C# oferece suporte a tipos de referência e tipos de valor definidos pelo usuário, permitindo a alocação dinâmica de objetos, bem como o armazenamento em linha de estruturas leves.

Para garantir que os programas e bibliotecas escritos em C# possam evoluir ao longo do tempo de uma maneira compatível, enfatizou-se muito o ***controle de versão*** no design do C#. Muitas linguagens de programação prestam pouca atenção a esse problema e, como resultado, programas escritos nessas linguagens quebram com mais frequência do que o necessário quando versões mais recentes das bibliotecas dependentes são introduzidas. Aspectos do design do C# que foram diretamente influenciados pelas considerações de controle de versão incluem os modificadores separados `virtual` e `override`, as regras de resolução de sobrecarga de método e suporte para declarações explícitas de membro de interface.

## <a name="hello-world"></a>Hello world

O programa "Hello, World" é usado tradicionalmente para introduzir uma linguagem de programação. Este é para C#:

[!code-csharp[Hello World](../../../samples/snippets/csharp/tour/hello/Program.cs#L1-L8)]

Os arquivos de origem em C# normalmente têm a extensão de arquivo `.cs`. Supondo que o programa "Hello, World" esteja armazenado no arquivo `hello.cs`, o programa pode ser compilado usando a linha de comando:

```console
csc hello.cs
```

que produz um assembly executável chamado hello.exe. O resultado produzido pela execução desse aplicativo é:

```console
Hello, World
```

> [!IMPORTANT]
> O comando `csc` compila para o framework completo e talvez não esteja disponível em todas as plataformas.


O programa "Hello, World" começa com uma diretiva `using` que faz referência ao namespace `System`. Namespaces fornecem um meio hierárquico de organizar bibliotecas e programas em C#. Os namespaces contêm tipos e outros namespaces — por exemplo, o namespace `System` contém uma quantidade de tipos, como a classe `Console` referenciada no programa e diversos outros namespaces, como `IO` e `Collections`. A diretiva `using` que faz referência a um determinado namespace permite o uso não qualificado dos tipos que são membros desse namespace. Devido à diretiva `using`, o programa pode usar `Console.WriteLine` como um atalho para `System.Console.WriteLine`.

A classe `Hello` declarada pelo programa "Hello, World" tem um único membro, o método chamado `Main`. O método `Main` é declarado com o modificador estático. Embora os métodos de instância possam fazer referência a uma determinada instância de objeto delimitador usando a palavra-chave `this`, métodos estáticos operam sem referência a um objeto específico. Por convenção, um método estático denominado `Main` serve como ponto de entrada de um programa.

A saída do programa é produzida pelo método `WriteLine` da classe `Console` no namespace `System`. Essa classe é fornecida pelas bibliotecas de classe padrão, que, por padrão, são referenciadas automaticamente pelo compilador.

Há muito mais para aprender sobre C#.  Os tópicos a seguir fornecem uma visão geral dos elementos da linguagem C#. Essas visões gerais fornecerão informações básicas sobre todos os elementos da linguagem e fornecerão as informações necessárias para se aprofundar nos elementos da linguagem C#:

* [Estrutura do programa](program-structure.md)
    - Aprenda os principais conceitos organizacionais na linguagem C#: ***programas***, ***namespaces***, ***tipos***, ***membros*** e ***assemblies***.
* [Tipos e variáveis](types-and-variables.md)
    - Saiba mais sobre ***tipos de valor***, ***tipos de referência***, e ***variáveis*** na linguagem C#.
* [Expressões](expressions.md)
    - ***Expressões*** são construídas a partir de ***operandos*** e ***operadores***. As expressões produzem um valor.
* [Instruções](statements.md)
    - Você usa ***instruções*** para expressar as ações de um programa.
* [Classes e objetos](classes-and-objects.md)
    - As ***classes*** são os tipos do C# mais fundamentais. Os ***objetos*** são instâncias de uma classe. As classes são compiladas usando ***membros***, que também são abordados neste tópico.
* [Estruturas](structs.md)
    - Os ***structs*** são estruturas de dados que, diferentemente das classes, são tipos de valor.
* [Matrizes](arrays.md)
    - Uma ***matriz*** é uma estrutura de dados que contém algumas variáveis acessadas por meio de índices calculados.
* [Interfaces](interfaces.md)
    - Uma ***interface*** define um contrato que pode ser implementado por classes e estruturas. Uma interface pode conter métodos, propriedades, eventos e indexadores. Uma interface não fornece implementações dos membros que define — ela simplesmente especifica os membros que devem ser fornecidos por classes ou estruturas que implementam a interface.
* [Enums](enums.md)
    - Um ***tipo enum*** é um tipo de valor diferente com um conjunto de constantes nomeadas.
* [Delegados](delegates.md)
    - Um ***delegado*** é um tipo que representa referências aos métodos com uma lista de parâmetros e tipo de retorno específicos. Delegados possibilitam o tratamento de métodos como entidades que podem ser atribuídos a variáveis e passadas como parâmetros. Os delegados são parecidos com o conceito de ponteiros de função em outras linguagens, mas ao contrário dos ponteiros de função, os delegados são orientados a objetos e fortemente tipados.
* [Atributos](attributes.md)
    * ***Atributos*** permitem que programas especifiquem informações declarativas adicionais sobre tipos, membros e outras entidades.

>[!div class="step-by-step"]
[Avançar](program-structure.md)
