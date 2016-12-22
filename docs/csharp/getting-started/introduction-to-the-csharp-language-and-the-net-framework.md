---
title: "Introduction to the C# Language and the .NET Framework | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "C# language, about C# language"
  - "Visual C#, about"
ms.assetid: 0a2dff4e-cd84-42ff-8141-e89889b24081
caps.latest.revision: 32
caps.handback.revision: 32
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Introduction to the C# Language and the .NET Framework
[!INCLUDE[vs2017banner](../../csharp/includes/vs2017banner.md)]

C\# é uma linguagem orientada a objeto elegante e de tipo seguro que permite aos desenvolvedores criar uma variedade de aplicativos seguros e robustos que são executados no [!INCLUDE[dnprdnshort](../../csharp/getting-started/includes/dnprdnshort_md.md)].  É possível usar C\# para criar muito aplicativos de cliente do Windows, serviços Web XML, componentes distribuídos, aplicativos de cliente\-servidor, aplicativos de banco de dados, e muito mais.  O Visual C\# fornece um editor de códigos avançado, designers de interface de usuário convenientes, depurador integrado, e muitas outras ferramentas para facilitar o desenvolvimento de aplicativos baseados na linguagem C\# e no [!INCLUDE[dnprdnshort](../../csharp/getting-started/includes/dnprdnshort_md.md)].  
  
> [!NOTE]
>  A documentação de [!INCLUDE[csprcs](../../csharp/includes/csprcs_md.md)] presume que você tenha uma compreensão dos conceitos básicos de programação.  Se você for um novato completo, você pode querer explorar [!INCLUDE[csprcsxpr](../../csharp/getting-started/includes/csprcsxpr_md.md)], que está disponível na Web.  Você também pode tirar proveito de livros e recursos da Web sobre C\# para ganhar habilidades práticas de programação.  
  
## Linguagem C\#  
 A sintaxe de C\# é altamente expressiva, mas também é simples e fácil de aprender.  A sintaxe de chave do C\# será imediatamente reconhecível para qualquer pessoa familiarizada com C, C\+\+ ou Java.  Os desenvolvedores que conhecem qualquer uma dessas linguagens normalmente podem começar a trabalhar produtivamente no C\# em muito pouco tempo.  A sintaxe de C\# simplifica muitas das complexidades de C\+\+ e fornece recursos avançados, como tipos que permitem valores nulos, enumerações, representantes, expressões lambda e acesso direto à memória, que não são encontrados em Java.  C\# suporta os métodos e tipos genéricos, que fornecem maior segurança e desempenho de tipo, e iteradores, que permitem implementadores de classes de coleção para definir os comportamentos personalizados de iteração que são simples de usar por código do cliente.  as expressões de [!INCLUDE[vbteclinqext](../../csharp/getting-started/includes/vbteclinqext_md.md)] tornam a consulta fortemente tipada em uma construção de linguagem de primeira classe.  
  
 Como uma linguagem orientada a objeto, C\# oferece suporte aos conceitos de encapsulamento, herança e polimorfismo.  Todas as variáveis e métodos, incluindo o método `Main`, o ponto de entrada do aplicativo, são encapsulados nas definições de classe.  Uma classe pode ser herdada diretamente de uma classe pai, mas ela pode implementar qualquer número de interfaces.  Os métodos que substituem métodos virtuais em uma classe pai requerem a palavra\-chave `override` como uma maneira para evitar a redefinição acidental.  Em C\#, um estrutura é como uma classe leve; é um tipo alocado de pilha capaz de implementar interfaces, mas não dá suporte à herança.  
  
 Além desses princípios básicos orientados a objeto, o C\# facilita o desenvolvimento de componentes de software por meio de vários constructos de linguagem inovadores, inclusive os seguintes:  
  
-   As assinaturas de método encapsuladas chamaram *representantes*, que habilitam notificações de eventos com segurança.  
  
-   Propriedades, que servem como acessadores para variáveis de membro particular.  
  
-   Atributos, que fornecem metadados declarativos sobre tipos em tempo de execução.  
  
-   Comentários Embutidos da Documentação XML.  
  
-   [!INCLUDE[vbteclinqext](../../csharp/getting-started/includes/vbteclinqext_md.md)] que fornece recursos internos de consulta através de várias de fontes de dados.  
  
 Se precisar interagir com outro software do Windows, como objetos COM ou DLLs Win32 nativas, você precisará fazer isso no C\# por meio de um processo chamado "Interop". Interoperabilidade permite programas C\# a fazerem quase tudo o que um aplicativo nativo C\+\+ pode fazer.  C\# tem suporte para ponteiros e o conceito de código “não seguro” para esses casos em que o acesso direto à memória é absolutamente crítico.  
  
 O processo de compilação do C\# é simples em comparação ao C e C\+\+ e mais flexível do que em Java.  Não há nenhum arquivo de cabeçalho separado e nenhum requisito de que métodos e tipos sejam declarados em uma ordem específica.  Um arquivo de origem C\# pode definir qualquer número de classes, estruturas, interfaces e eventos.  
  
 A seguir, recursos C\# adicionais:  
  
-   Para uma boa introdução geral para a linguagem, consulte o capítulo 1 do [Especificação da linguagem C\#](../../visual-basic/reference/language-specification.md).  
  
-   Para obter informações detalhadas sobre os aspectos específicos da linguagem C\#, consulte [Referência de C\#](../../csharp/language-reference/index.md).  
  
-   Para obter mais informações sobre [!INCLUDE[vbteclinq](../../csharp/includes/vbteclinq_md.md)], consulte [LINQ \(Consulta Integrada à Linguagem\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md).  
  
-   Para localizar os artigos e os recursos mais recentes da equipe de Visual C\#, consulte [Centro do Desenvolvedor de Visual C\#](http://go.microsoft.com/fwlink/?LinkId=47811).  
  
## Arquitetura da plataforma do .NET Framework  
 Os programas C\# executam no [!INCLUDE[dnprdnshort](../../csharp/getting-started/includes/dnprdnshort_md.md)], um componente integral do Windows que inclui um sistema virtual de execução chamado CLR \(Common Language Runtime\) e um conjunto unificado de bibliotecas de classes.  O CLR é a implementação comercial feita pela Microsoft da CLI \(common language infrastructure\), um padrão internacional que é a base da criação de ambientes de execução e de desenvolvimento nos quais linguagens e bibliotecas funcionam juntos perfeitamente.  
  
 O código fonte escrito em C\# é compilado em uma linguagem intermediária \(IL\) que está de acordo com a especificação CLI.  O código e os recursos do IL, como bitmaps e cadeias de caracteres, são armazenados em disco em um arquivo executável chamado assembly, geralmente com uma extensão .exe ou .dll.  Um assembly contém um manifesto que fornece informações sobre os tipos do assembly, a versão, a cultura e os requisitos de segurança.  
  
 Quando o programa C\# é executado, o assembly é carregado no CLR, que pode executar várias ações com base nas informações contidas no manifesto.  Em seguida, se os requisitos de segurança forem atendidos, o CLR executará a compilação JIT \(just in time\) para converter o código IL em instruções de computador nativo.  O CLR também oferece outros serviços relacionados à coleta de lixo automática, à manipulação de exceções e o gerenciamento de recursos.  O código que é executado pelo CLR geralmente é conhecido como “código gerenciado”, em contraste com o “código não gerenciado” que é compilado na linguagem de máquina nativa que direciona um sistema específico.  O diagrama a seguir ilustra as relações de tempo de compilação e de execução de arquivos de código\-fonte C\#, as bibliotecas de classe do .NET Framework, assemblies e o CLR.  
  
 ![Do código&#45;fonte C&#35; para execução de máquina](../../csharp/getting-started/media/netarchitecture.png "NETarchitecture")  
  
 Interoperabilidade de linguagem é um recurso chave de [!INCLUDE[dnprdnshort](../../csharp/getting-started/includes/dnprdnshort_md.md)].  Como o código IL gerado pelo compilador C\# está de acordo com a CTS \(Especificação de Tipo Comum\), código IL gerado de C\# pode interagir com o código que foi gerado das versões .NET do Visual Basic, Visual C\+\+, ou qualquer uma das outras 20 linguagens compatíveis com CTS.  Um único assembly pode conter vários módulos escritos em diferentes linguagens do .NET, e os tipos podem fazer referência uns aos outros como se fossem escritos exatamente na mesma linguagem.  
  
 Além dos serviços de tempo de execução, [!INCLUDE[dnprdnshort](../../csharp/getting-started/includes/dnprdnshort_md.md)] também inclui uma biblioteca abrangente de mais de 4.000 classes organizadas em namespaces que fornecem uma ampla variedade de funcionalidade útil para tudo, da entrada e da saída de arquivo à manipulação da cadeia de caracteres, além da análise de XML e dos controles dos Windows Forms.  O aplicativo típico C\# usa extensivamente a biblioteca de classes [!INCLUDE[dnprdnshort](../../csharp/getting-started/includes/dnprdnshort_md.md)] para manipular tarefas comuns de "encanamento".  
  
 Para obter mais informações sobre o .NET Framework, consulte [Overview of the Microsoft .NET Framework](http://msdn.microsoft.com/pt-br/d05daf50-00fe-45c7-8383-06fe41697355).  
  
## Capítulos do Livro em Destaque  
 [C\# Language Fundamentals](http://go.microsoft.com/fwlink/?LinkId=195416) em [Learning C\# 3.0: Master the fundamentals of C\# 3.0](http://go.microsoft.com/fwlink/?LinkId=195412)  
  
 [C\# and .NET Programming](http://go.microsoft.com/fwlink/?LinkId=195413) em [Learning C\# 3.0: Master the fundamentals of C\# 3.0](http://go.microsoft.com/fwlink/?LinkId=195412)  
  
 [Apresentando C\#](http://go.microsoft.com/fwlink/?LinkId=221226) em [Iniciando o Visual C\# 2010](http://go.microsoft.com/fwlink/?LinkId=221214)  
  
 [Visual Studio 2008 and C\# Express 2008](http://go.microsoft.com/fwlink/?LinkId=195414) em [Learning C\# 3.0: Master the fundamentals of C\# 3.0](http://go.microsoft.com/fwlink/?LinkId=195412)  
  
## Consulte também  
 [C\#](../../csharp/csharp.md)   
 [Introdução ao Visual C\# e ao Visual Basic](/visual-studio/ide/getting-started-with-visual-csharp-and-visual-basic)