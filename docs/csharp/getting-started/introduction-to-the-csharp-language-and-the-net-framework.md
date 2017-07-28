---
title: "Introdução à linguagem C# e ao .NET Framework"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- C# language, about C# language
- Visual C#, about
ms.assetid: 0a2dff4e-cd84-42ff-8141-e89889b24081
caps.latest.revision: 32
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: d828e5e1914e73193e6449d4fb6d8fb3f0d0775b
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="introduction-to-the-c-language-and-the-net-framework"></a>Introdução à linguagem C# e ao .NET Framework
C# é uma linguagem elegante, orientada a objeto e fortemente tipada, que permite que os desenvolvedores criem uma variedade de aplicativos robustos e seguros executados no [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Você pode usar C# para criar aplicativos de cliente do Windows, serviços Web XML, componentes distribuídos, aplicativos cliente-servidor, aplicativos de banco de dados e muito, muito mais. O Visual C# fornece um editor de código avançado, designers de interface de usuário convenientes, depurador integrado e muitas outras ferramentas para facilitar o desenvolvimento de aplicativos com base na linguagem C# e no [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].  
  
> [!NOTE]
> A documentação do [!INCLUDE[csprcs](~/includes/csprcs-md.md)] pressupõe que você tem uma compreensão dos conceitos básicos de programação. Se você for principiante, convém explorar [!INCLUDE[csprcsxpr](~/includes/csprcsxpr-md.md)], que está disponível na Web. Você também pode tirar proveito de livros e recursos da Web sobre C# para aprender técnicas de programação práticas.  
  
## <a name="c-language"></a>Linguagem C#  
 A sintaxe de C# é altamente expressiva, mas também é simples e fácil de aprender. A sintaxe de chaves de C# será instantaneamente reconhecível para qualquer pessoa familiarizada com C, C++ ou Java. Normalmente, os desenvolvedores que conhecem qualquer uma dessas linguagens são capazes de começar a trabalhar de forma produtiva em C# dentro de um período muito curto. A sintaxe de C# simplifica muitas complexidades de C++ e fornece recursos poderosos como tipos de valor anulável, enumerações, delegados, expressões lambda e acesso direto à memória, que não existem em Java. C# oferece suporte a tipos e métodos genéricos, o que proporciona mais segurança e desempenho para os tipos, e iteradores, que permitem aos implementadores das classes de coleção definir os comportamentos personalizados da iteração simples de usar pelo código do cliente. As expressões [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] tornam a consulta fortemente tipada uma construção de linguagem de primeira classe.  
  
 Por ser uma linguagem orientada a objeto, o C# oferece suporte aos conceitos de encapsulamento, herança e polimorfismo. Todas as variáveis e métodos, incluindo o método `Main`, o ponto de entrada do aplicativo, são encapsulados em definições de classe. Uma classe pode herdar diretamente de uma classe pai, mas pode implementar qualquer quantidade de interfaces. Métodos que substituem métodos virtuais em uma classe pai exigem a palavra-chave `override` como uma forma de evitar uma redefinição acidental. Em C#, um struct é como uma classe simplificada; é um tipo alocado na pilha que pode implementar interfaces, mas não oferece suporte a herança.  
  
 Além desses princípios básicos orientados a objeto, C# facilita o desenvolvimento de componentes de software por meio de várias construções de linguagem inovadoras, incluindo o seguinte:  
  
-   Assinaturas de método encapsulado chamadas de *delegados*, que permitem as notificações de eventos fortemente tipados.  
  
-   Propriedades, que servem como acessadores para variáveis de membro privado.  
  
-   Atributos, que fornecem metadados declarativos sobre os tipos no tempo de execução.  
  
-   Comentários embutidos da documentação XML.  
  
-   [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] que fornece recursos de consulta internos em várias fontes de dados.  
  
 Se você precisar interagir com outros softwares do Windows, como objetos COM ou DLLs Win32 nativas, faça isso em C# através de um processo denominado "Interoperabilidade". A interoperabilidade permite que programas em C# façam quase tudo que um aplicativo C++ nativo pode fazer. C# oferece suporte até mesmo para ponteiros, e o conceito de código "não seguro" para os casos nos quais o acesso direto à memória é absolutamente essencial.  
  
 O processo de compilação de C# é simples comparado ao C e C++, e mais flexível do que em Java. Não há arquivos de cabeçalho separado, e nenhum requisito de que os métodos e os tipos sejam declarados em uma ordem específica. Um arquivo de código-fonte de C# pode definir qualquer quantidade de classes, estruturas, interfaces e eventos.  
  
 Veja a seguir recursos adicionais de C#:  
  
-   Para uma boa introdução geral à linguagem, consulte o Capítulo 1 da [Especificação da linguagem C#](../../csharp/language-reference/language-specification/index.md).  
  
-   Para obter informações detalhadas sobre aspectos específicos da linguagem C#, consulte a [Referência de C#](../../csharp/language-reference/index.md).  
  
-   Para saber mais sobre [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], confira [LINQ (Consulta Integrada à Linguagem)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d).  
  
-   Para obter os artigos e recursos mais recentes da equipe do Visual C#, confira o [Centro do desenvolvedor em Visual C#](http://go.microsoft.com/fwlink/?LinkId=47811).  
  
## <a name="net-framework-platform-architecture"></a>Arquitetura da plataforma do .NET Framework  
 Programas em C# são executados no [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], um componente integral do Windows que inclui um sistema de execução virtual chamado de CLR (Common Language Runtime) e um conjunto unificado de bibliotecas de classes. O CLR é a implementação comercial da Microsoft da CLI (Common Language Infrastructure), um padrão internacional que é a base para a criação de ambientes de execução e de desenvolvimento nos quais linguagens e bibliotecas funcionam de forma integrada.  
  
 O código-fonte escrito em C# é compilado em uma linguagem intermediária (IL) que está em conformidade com a especificação da CLI. O código e os recursos de IL, como bitmaps e cadeias de caracteres, são armazenados em disco em um arquivo executável chamado de assembly, normalmente com uma extensão .exe ou .dll. Um assembly contém um manifesto que fornece informações sobre os tipos, a versão, a cultura e os requisitos de segurança do assembly.  
  
 Quando o programa em C# é executado, o assembly é carregado no CLR, que pode executar várias ações de acordo com as informações no manifesto. Em seguida, se os requisitos de segurança forem atendidos, o CLR executará a compilação JIT (just in time) para converter o código de IL em instruções nativas da máquina. O CLR também oferece outros serviços relacionados à coleta automática de lixo, tratamento de exceções e gerenciamento de recursos. O código que é executado pelo CLR é, às vezes, chamado de "código gerenciado", ao contrário de "código não gerenciado", que é compilado em linguagem de máquina nativa e visa um sistema específico. O diagrama a seguir ilustra as relações em tempo de compilação e em tempo de execução dos arquivos de código-fonte em C#, as bibliotecas de classe do .NET Framework, assemblies e o CLR.  
  
 ![Do código-fonte de C&#35; até a execução na máquina](../../csharp/getting-started/media/netarchitecture.png "NETarchitecture")  
  
 Interoperabilidade de linguagem é um recurso importante do [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Como o código de IL produzido pelo compilador de C# está em conformidade com a CTS (Especificação de tipo comum), o código de IL gerado a partir de C# pode interagir com código gerado a partir das versões .NET do Visual Basic, Visual C++ ou qualquer uma das mais de 20 linguagens compatíveis com CTS. Um único assembly pode conter vários módulos escritos em linguagens .NET diferentes, e os tipos podem fazer referencia entre si, como se tivessem sido escritos na mesma linguagem.  
  
 Além dos serviços de tempo de execução, o [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] também inclui uma biblioteca abrangente de mais de 4000 classes organizadas em namespaces, fornecendo uma ampla variedade de funcionalidades úteis para tudo, desde entrada e saída de arquivo para manipulação de cadeia de caracteres até análise XML, e controles do Windows Forms. O aplicativo típico em C# usa bastante a biblioteca de classes [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] para lidar com tarefas comuns de "encanamento".  
  
 Para saber mais sobre o .NET Framework, confira [Visão geral do Microsoft .NET Framework](http://msdn.microsoft.com/en-us/d05daf50-00fe-45c7-8383-06fe41697355).  
  
## <a name="see-also"></a>Consulte também  
 [C#](../../csharp/csharp.md)   
 [Introdução ao Visual C# e ao Visual Basic](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic)

