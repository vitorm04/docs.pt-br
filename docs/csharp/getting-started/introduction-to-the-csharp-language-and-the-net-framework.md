---
title: Introdução à linguagem C# e ao .NET Framework
description: Aprenda as noções básicas de C# e .NET. Confira uma visão geral da linguagem C# e do ecossistema .NET.
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, about C# language
- Visual C#, about
ms.assetid: 0a2dff4e-cd84-42ff-8141-e89889b24081
ms.openlocfilehash: 828543b95ed82f465c92212748c6250b7fc84051
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249377"
---
# <a name="introduction-to-the-c-language-and-the-net-framework"></a>Introdução à língua C# e ao Quadro .NET

C# é uma linguagem elegante, orientada a objeto e fortemente tipada, que permite que os desenvolvedores criem uma variedade de aplicativos robustos e seguros executados no .NET Framework. Você pode usar C# para criar aplicativos de cliente do Windows, serviços Web XML, componentes distribuídos, aplicativos cliente-servidor, aplicativos de banco de dados e muito, muito mais. O Visual C# fornece um editor de código avançado, designers de interface do usuário convenientes, depurador integrado e muitas outras ferramentas para facilitar o desenvolvimento de aplicativos com base na linguagem C# e no .NET Framework.  
  
> [!NOTE]
> A documentação do Visual C# considera que você já tenha conhecimento dos conceitos básicos de programação. Se você é principiante, convém explorar o Visual C# Express, que está disponível na Web. Você também pode tirar proveito de livros e recursos da Web sobre C# para aprender técnicas de programação práticas.  
  
## <a name="c-language"></a>Linguagem C#

A sintaxe de C# é altamente expressiva, mas também é simples e fácil de aprender. A sintaxe de cinta encaracolada de C# será instantaneamente reconhecível para qualquer pessoa familiarizada com C, C++ou Java. Normalmente, os desenvolvedores que conhecem qualquer uma dessas linguagens são capazes de começar a trabalhar de forma produtiva em C# dentro de um período muito curto. A sintaxe C# simplifica muitas das complexidades do C++ e fornece recursos poderosos, como tipos anulados, enumerações, delegados, expressões lambda e acesso direto à memória. C# oferece suporte a tipos e métodos genéricos, o que proporciona mais segurança e desempenho para os tipos, e iteradores, que permitem aos implementadores das classes de coleção definir os comportamentos personalizados da iteração simples de usar pelo código do cliente. As expressões LINQ (Language-Integrated Query, consulta integrada ao idioma) tornam a consulta fortemente digitada uma construção de idioma de primeira classe.  
  
 Por ser uma linguagem orientada a objeto, o C# oferece suporte aos conceitos de encapsulamento, herança e polimorfismo. Todas as variáveis e métodos, incluindo o método `Main`, o ponto de entrada do aplicativo, são encapsulados em definições de classe. Uma classe pode herdar diretamente de uma classe pai, mas pode implementar qualquer quantidade de interfaces. Métodos que substituem métodos virtuais em uma classe pai exigem a palavra-chave `override` como uma forma de evitar uma redefinição acidental. Em C#, um struct é como uma classe simplificada; é um tipo alocado na pilha que pode implementar interfaces, mas não oferece suporte a herança.  
  
 Além desses princípios básicos orientados a objeto, C# facilita o desenvolvimento de componentes de software por meio de várias construções de linguagem inovadoras, incluindo o seguinte:  
  
- Assinaturas de método encapsulado chamadas de *delegados*, que permitem as notificações de eventos fortemente tipados.  
  
- Propriedades, que servem como acessadores para variáveis de membro privado.  
  
- Atributos, que fornecem metadados declarativos sobre os tipos no tempo de execução.  
  
- Comentários embutidos da documentação XML.  
  
- A LINQ (Language-Integrated Query, consulta integrada ao idioma), que fornece recursos de consulta incorporados em uma variedade de fontes de dados.  
  
 Se você precisar interagir com outros softwares do Windows, como objetos COM ou DLLs Win32 nativas, faça isso em C# através de um processo denominado "Interoperabilidade". A interoperabilidade permite que programas em C# façam quase tudo que um aplicativo C++ nativo pode fazer. C# ainda suporta ponteiros e o conceito de código "inseguro" para os casos em que o acesso direto à memória é crítico.  
  
 O processo de compilação de C# é simples comparado ao C e C++, e mais flexível do que em Java. Não há arquivos de cabeçalho separado, e nenhum requisito de que os métodos e os tipos sejam declarados em uma ordem específica. Um arquivo de código-fonte de C# pode definir qualquer quantidade de classes, estruturas, interfaces e eventos.  
  
 Veja a seguir recursos adicionais de C#:  
  
- Para uma boa introdução geral à linguagem, consulte o Capítulo 1 da [Especificação da linguagem C#](/dotnet/csharp/language-reference/language-specification/introduction).  
  
- Para obter informações detalhadas sobre aspectos específicos da linguagem C#, consulte a [Referência de C#](../language-reference/index.md).  
  
- Para obter mais informações sobre linq, consulte [LINQ (Linguagem Integrada de Consulta)](../programming-guide/concepts/linq/index.md).  

## <a name="net-framework-platform-architecture"></a>Arquitetura da plataforma do .NET Framework

 Programas em C# são executados no .NET Framework, um componente integral do Windows que inclui um sistema de execução virtual chamado de CLR (Common Language Runtime) e um conjunto unificado de bibliotecas de classes. O CLR é a implementação comercial da Microsoft da CLI (Common Language Infrastructure), um padrão internacional que é a base para a criação de ambientes de execução e de desenvolvimento nos quais linguagens e bibliotecas funcionam de forma integrada.  
  
 O código fonte escrito em C# é compilado em uma [língua intermediária (IL)](../../standard/managed-code.md) que está em conformidade com a especificação CLI. O código e os recursos de IL, como bitmaps e cadeias de caracteres, são armazenados em disco em um arquivo executável chamado de assembly, normalmente com uma extensão .exe ou .dll. Um assembly contém um manifesto que fornece informações sobre os tipos, a versão, a cultura e os requisitos de segurança do assembly.  
  
 Quando o programa em C# é executado, o assembly é carregado no CLR, que pode executar várias ações de acordo com as informações no manifesto. Em seguida, se os requisitos de segurança forem atendidos, a CLR realizará a compilação Just-In-Time (JIT) para converter o código IL em instruções de máquina nativa. O CLR também oferece outros serviços relacionados à coleta automática de lixo, tratamento de exceções e gerenciamento de recursos. O código executado pela CLR é às vezes referido como "código gerenciado", em contraste com o "código não gerenciado", que é compilado em linguagem de máquina nativa que tem como alvo um sistema específico. O diagrama a seguir ilustra as relações em tempo de compilação e em tempo de execução dos arquivos de código-fonte em C#, as bibliotecas de classe do .NET Framework, assemblies e o CLR.  
  
 ![Do código fonte C# à execução da máquina](./media/introduction-to-the-csharp-language-and-the-net-framework/net-architecture-relationships.png)  
  
 Interoperabilidade de linguagem é um recurso importante do .NET Framework. Como o código de IL produzido pelo compilador de C# está em conformidade com a CTS (Especificação de tipo comum), o código de IL gerado a partir de C# pode interagir com código gerado a partir das versões .NET do Visual Basic, Visual C++ ou qualquer uma das mais de 20 linguagens compatíveis com CTS. Um único assembly pode conter vários módulos escritos em linguagens .NET diferentes, e os tipos podem fazer referencia entre si, como se tivessem sido escritos na mesma linguagem.  
  
 Além dos serviços de tempo de execução, o .NET Framework também inclui uma biblioteca abrangente de mais de 4000 classes organizadas em namespaces, fornecendo uma ampla variedade de funcionalidades úteis para tudo, desde entrada e saída de arquivo para manipulação de cadeia de caracteres até análise XML, além de controles do Windows Forms. O aplicativo típico em C# usa bastante a biblioteca de classes do .NET Framework para lidar com tarefas comuns de "encanamento".  
  
 Para saber mais sobre o .NET Framework, confira [Visão geral do Microsoft .NET Framework](../../framework/get-started/overview.md).  
  
## <a name="see-also"></a>Confira também

- [Guia de Introdução ao Visual C#](/visualstudio/ide/quickstart-csharp-console)
