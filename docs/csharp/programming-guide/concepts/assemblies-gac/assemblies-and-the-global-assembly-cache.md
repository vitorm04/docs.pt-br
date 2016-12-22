---
title: "Assemblies e o Cache de Assembly Global (c#) | Microsoft Docs"
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
ms.assetid: 149f5ca5-5b34-4746-9542-1ae43b2d0256
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Assemblies e o Cache de Assembly Global (c#)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Assemblies formam a unidade fundamental de implantação, controle de versão, reutilização, escopo de ativação e permissões de segurança para um. Aplicativo baseado em NET. Assemblies tomam a forma de um arquivo executável \(.exe\) ou dynamic link library \(. dll\) e são os blocos de construção do .NET Framework. Eles fornecem o common language runtime com as informações necessárias para estar ciente das implementações de tipo. Você pode pensar em um assembly como uma coleção de tipos e recursos que formam uma unidade lógica de funcionalidade e são construídos para trabalharem juntos.  
  
 Os assemblies podem conter um ou mais módulos. Por exemplo, projetos maiores podem ser planejados uma forma que vários desenvolvedores individuais trabalham em módulos separados, todos os próximos juntos para criar um único assembly. Para obter mais informações sobre os módulos, consulte o tópico [Como compilar um assembly de vários arquivos](../Topic/How%20to:%20Build%20a%20Multifile%20Assembly.md).  
  
 Os assemblies têm as seguintes propriedades:  
  
-   Assemblies são implementados como arquivos. dll ou. .exe.  
  
-   Você pode compartilhar um assembly entre aplicativos, colocando\-o no cache de assembly global. Assemblies devem ser fortes antes que elas podem ser incluídas no cache de assembly global. Para obter mais informações, consulte [Assemblies de nomes fortes](../Topic/Strong-Named%20Assemblies.md).  
  
-   Assemblies são carregados na memória somente se forem necessários. Se não forem usados, eles não sejam carregados. Isso significa que os assemblies podem ser uma maneira eficiente de gerenciar recursos em projetos grandes.  
  
-   Programaticamente, você pode obter informações sobre um assembly usando reflexão. Para obter mais informações, consulte [Reflexão \(c\#\)](../../../../csharp/programming-guide/concepts/reflection.md).  
  
-   Se você deseja carregar um assembly apenas para inspecioná\-la, use um método como <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A>.  
  
## Manifesto de um assembly  
 Dentro de todo assembly é um *manifesto do assembly*. Semelhante a uma tabela de conteúdo, o manifesto do assembly contém o seguinte:  
  
-   Identidade do assembly \(seu nome e versão\).  
  
-   Uma tabela de arquivo que descreve todos os outros arquivos que compõem o assembly, por exemplo, quaisquer outros assemblies que você criou que seu arquivo. dll ou. .exe depende, ou até mesmo bitmap ou arquivos Leiame.  
  
-   Um *lista de referências de assembly*, que é uma lista de todas as dependências externas, DLLs ou outros arquivos necessidades do aplicativo que podem ter sido criadas por outra pessoa. Referências de assembly contêm referências a objetos globais e privadas. Objetos globais residem no cache de assembly global, uma área disponível para outros aplicativos. Objetos privados devem estar em um diretório no mesmo nível ou abaixo do diretório no qual seu aplicativo está instalado.  
  
 Porque os assemblies contêm informações sobre conteúdo, versão e dependências, os aplicativos que você cria com o c\# não confie em valores de registro do Windows para funcionar corretamente. Assemblies reduzem conflitos de DLL e tornam seus aplicativos mais confiáveis e mais fácil de implantar. Em muitos casos, você pode instalar uma. Aplicativo baseado em NET simplesmente copiando seus arquivos para o computador de destino.  
  
 Para obter mais informações, consulte [Manifesto de um assembly](../Topic/Assembly%20Manifest.md).  
  
## Adicionando uma referência a um Assembly  
 Para usar um assembly, você deve adicionar uma referência a ele. Em seguida, use o [usando a diretiva](../../../../csharp/language-reference/keywords/using-directive.md) para escolher o namespace dos itens que você deseja usar. Quando um assembly é referenciado e importado, todas as classes acessíveis, propriedades, métodos e outros membros de seus namespaces estão disponíveis para o seu aplicativo como se seus códigos fossem parte de seu arquivo de origem.  
  
 No c\#, você também pode usar duas versões do mesmo assembly em um único aplicativo. Para obter mais informações, consulte [alias extern](../../../../csharp/language-reference/keywords/extern-alias.md).  
  
## Criando um Assembly  
 Compilar o aplicativo clicando em **criar** no **criar** menu ou com a compilação da linha de comando usando o compilador de linha de comando. Para obter detalhes sobre como criar assemblies na linha de comando, consulte [Command\-line Building With csc.exe](../../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).  
  
> [!NOTE]
>  Para criar um assembly no Visual Studio, no **criar** menu escolha **criar**.  
  
## Consulte também  
 [Guia de Programação em C\#](../../../../csharp/programming-guide/index.md)   
 [Assemblies no Common Language Runtime](../Topic/Assemblies%20in%20the%20Common%20Language%20Runtime.md)   
 [Assemblies amigáveis \(c\#\)](../../../../csharp/programming-guide/concepts/assemblies-gac/friend-assemblies.md)   
 [Como: compartilhar um Assembly com outros aplicativos \(c\#\)](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-share-an-assembly-with-other-applications.md)   
 [Como: carregar e descarregar Assemblies \(c\#\)](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-load-and-unload-assemblies.md)   
 [Como: determinar se um arquivo é um Assembly \(c\#\)](../Topic/How%20to:%20Determine%20If%20a%20File%20Is%20an%20Assembly%20\(C%23\).md)   
 [Como: criar e usar Assemblies usando a linha de comando \(c\#\)](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md)   
 [Passo a passo: Inserindo tipos de Assemblies gerenciados no Visual Studio \(c\#\)](../../../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md)   
 [Passo a passo: Inserindo informações de tipo de Assemblies do Microsoft Office no Visual Studio \(c\#\)](../../../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-type-information-from-microsoft-office-assemblies.md)