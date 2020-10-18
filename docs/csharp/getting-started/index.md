---
title: Introdução-uma introdução à linguagem C# e ao .NET "
description: Aprenda as noções básicas de C# e .NET. Confira uma visão geral da linguagem C# e do ecossistema .NET.
ms.date: 10/13/2020
ms.openlocfilehash: 94d49be28fbdba8f58ca16e959a10643d6467c63
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160952"
---
# <a name="introduction-to-the-c-language-and-net"></a>Introdução à linguagem C# e .NET

O C# é uma linguagem elegante e fortemente tipada orientada a objetos. O C# permite que os desenvolvedores criem muitos tipos de aplicativos seguros e robustos que são executados no ecossistema do .NET.

## <a name="c-language"></a>Linguagem C#

A sintaxe C# é altamente expressiva, mas também é simples e fácil de aprender. A sintaxe de chave do C# será reconhecível instantaneamente para qualquer pessoa que esteja familiarizada com C, C++, Java ou JavaScript. Os desenvolvedores que conhecem qualquer uma dessas linguagens geralmente podem trabalhar de maneira produtiva em C# em um curto período de tempo. O C# fornece recursos avançados, como tipos anuláveis, delegados, expressões lambda, correspondência de padrões e acesso de memória direta seguro. O C# oferece suporte a tipos e métodos genéricos, que fornecem aumento na segurança e no desempenho do tipo. O C# fornece iteradores, que habilitam implementadores de classes de coleção para definir comportamentos personalizados para o código do cliente. As expressões de consulta de Language-Integrated (LINQ) fazem com que a consulta fortemente tipada seja uma construção de linguagem de primeira classe.

Por ser uma linguagem orientada a objeto, o C# oferece suporte aos conceitos de encapsulamento, herança e polimorfismo. Uma classe pode herdar diretamente de uma classe pai, mas pode implementar qualquer quantidade de interfaces. Métodos que substituem métodos virtuais em uma classe pai exigem a palavra-chave `override` como uma forma de evitar uma redefinição acidental. Em C#, um struct é como uma classe leve; é um tipo de pilha alocada que pode implementar interfaces, mas não dá suporte à herança. O C# também fornece registros, que são tipos de classe cuja finalidade é armazenar os valores de dados principalmente.

O C# facilita o desenvolvimento de componentes de software por meio de várias construções de linguagem inovadoras, incluindo:

- Assinaturas de método encapsulado chamadas de *delegados*, que permitem as notificações de eventos fortemente tipados.
- Propriedades, que servem como acessadores para variáveis de membro privado.
- Atributos, que fornecem metadados declarativos sobre os tipos no tempo de execução.
- Comentários embutidos da documentação XML.
- LINQ (consulta de Language-Integrated), que fornece recursos de consulta internos entre diferentes tipos de fontes de dados.
- Correspondência de padrões, que habilita o fluxo de controle inspecionando os tipos de dados e valores.

Você interage com os componentes nativos por meio de um processo chamado "Interop". A interoperabilidade permite que programas em C# façam quase tudo que um aplicativo C++ nativo pode fazer. O C# suporta até mesmo ponteiros e o conceito de código "não seguro" para os casos em que o acesso direto à memória é crítico.

O processo de compilação de C# é simples comparado ao C e C++, e mais flexível do que em Java. Não há arquivos de cabeçalho separado, e nenhum requisito de que os métodos e os tipos sejam declarados em uma ordem específica. Um arquivo de código-fonte de C# pode definir qualquer quantidade de classes, estruturas, interfaces e eventos.

Veja a seguir recursos adicionais de C#:

- Para obter uma boa introdução geral à linguagem, consulte o [Tour do C#](../tour-of-csharp/index.md).
- Para obter informações detalhadas sobre aspectos específicos da linguagem C#, consulte a [Referência de C#](../language-reference/index.md).
- Para obter mais informações sobre LINQ, consulte [LINQ (consulta integrada à linguagem)](../programming-guide/concepts/linq/index.md).

## <a name="net-platform-architecture"></a>Arquitetura da plataforma .NET

Os programas em C# são executados no .NET, um sistema de execução virtual chamado Common Language Runtime (CLR) e um conjunto unificado de bibliotecas de classes. O CLR é a implementação comercial da Microsoft da CLI (Common Language Infrastructure), um padrão internacional. A CLI é a base para a criação de ambientes de execução e desenvolvimento nos quais as linguagens e bibliotecas funcionam em conjunto diretamente.

O código-fonte escrito em C# é compilado em uma [Il (linguagem intermediária)](../../standard/managed-code.md) que está de acordo com a especificação da CLI. O código de IL e os recursos, como bitmaps e cadeias de caracteres, são armazenados em um assembly, normalmente com uma extensão de. dll. Um assembly contém um manifesto que fornece informações sobre os tipos, a versão e a cultura do assembly.

Quando o programa C# é executado, o assembly é carregado no CLR. O CLR executa a compilação JIT (just-in-time) para converter o código IL em instruções de máquina nativa. O CLR fornece outros serviços relacionados à coleta de lixo, manipulação de exceções e gerenciamento de recursos automáticos. O código executado pelo CLR, às vezes, é chamado de "código gerenciado", em oposição ao "código não gerenciado", que é compilado em linguagem de máquina nativa direcionada a um sistema específico.

A interoperabilidade de linguagem é um recurso fundamental do .NET. O código de IL produzido pelo compilador C# está de acordo com a CTS (especificação de tipo comum). O código IL gerado do C# pode interagir com o código gerado nas versões do .NET do F #, Visual Basic, C++ ou em qualquer um dos mais de 20 outros idiomas compatíveis com CTS. Um único assembly pode conter vários módulos escritos em diferentes linguagens .NET, e os tipos podem referenciar um ao outro como se fossem escritos no mesmo idioma.

Além dos serviços de tempo de execução, o .NET também inclui bibliotecas extensivas. Essas bibliotecas dão suporte a várias cargas de trabalho diferentes. Elas são organizadas em namespaces que fornecem uma ampla variedade de funcionalidades úteis para tudo, desde entrada e saída de arquivos até a manipulação de cadeia de caracteres até a análise XML até estruturas de aplicativos Web para Windows Forms controles. O aplicativo C# típico usa a biblioteca de classes .NET extensivamente para lidar com tarefas comuns de "encanamento".

Para obter mais informações sobre o .NET, consulte [visão geral do .net](../../core/introduction.md).
