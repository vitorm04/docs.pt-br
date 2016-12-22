---
title: "Assemblies e o Cache de Assembly Global (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
ms.assetid: fcf78ff1-f1ab-4a5d-b6d8-00d2046b6c80
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Assemblies e o Cache de Assembly Global (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Assemblies formam a unidade fundamental de implantação, controle de versão, reutilização, escopo de ativação e permissões de segurança para um. Aplicativo baseado em NET. Assemblies tomam a forma de um arquivo executável \(.exe\) ou dynamic link library \(. dll\) e são os blocos de construção do .NET Framework. Eles fornecem o common language runtime com as informações necessárias para estar ciente das implementações de tipo. Você pode pensar em um assembly como uma coleção de tipos e recursos que formam uma unidade lógica de funcionalidade e são construídos para trabalharem juntos.  
  
 Os assemblies podem conter um ou mais módulos. Por exemplo, projetos maiores podem ser planejados uma forma que vários desenvolvedores individuais trabalham em módulos separados, todos os próximos juntos para criar um único assembly. Para obter mais informações sobre os módulos, consulte o tópico [Como compilar um assembly de vários arquivos](../Topic/How%20to:%20Build%20a%20Multifile%20Assembly.md).  
  
 Os assemblies têm as seguintes propriedades:  
  
-   Assemblies são implementados como arquivos. dll ou. .exe.  
  
-   Você pode compartilhar um assembly entre aplicativos, colocando\-o no cache de assembly global. Assemblies devem ser fortes antes que elas podem ser incluídas no cache de assembly global. Para obter mais informações, consulte [Assemblies de nomes fortes](../Topic/Strong-Named%20Assemblies.md).  
  
-   Assemblies são carregados na memória somente se forem necessários. Se não forem usados, eles não sejam carregados. Isso significa que os assemblies podem ser uma maneira eficiente de gerenciar recursos em projetos grandes.  
  
-   Programaticamente, você pode obter informações sobre um assembly usando reflexão. Para obter mais informações, consulte [Reflexão \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/reflection.md).  
  
-   Se você deseja carregar um assembly apenas para inspecioná\-la, use um método como <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A>.  
  
## Manifesto de um assembly  
 Dentro de todo assembly é um *manifesto do assembly*. Semelhante a uma tabela de conteúdo, o manifesto do assembly contém o seguinte:  
  
-   Identidade do assembly \(seu nome e versão\).  
  
-   Uma tabela de arquivo que descreve todos os outros arquivos que compõem o assembly, por exemplo, quaisquer outros assemblies que você criou que seu arquivo. dll ou. .exe depende, ou até mesmo bitmap ou arquivos Leiame.  
  
-   Um *lista de referências de assembly*, que é uma lista de todas as dependências externas, DLLs ou outros arquivos necessidades do aplicativo que podem ter sido criadas por outra pessoa. Referências de assembly contêm referências a objetos globais e privadas. Objetos globais residem no cache de assembly global, uma área disponível para outros aplicativos, um pouco semelhante ao diretório System32. O <xref:Microsoft.VisualBasic?displayProperty=fullName> namespace é um exemplo de um assembly no cache de assembly global. Objetos privados devem estar em um diretório no mesmo nível ou abaixo do diretório no qual seu aplicativo está instalado.  
  
 Porque os assemblies contêm informações sobre conteúdo, versão e dependências, os aplicativos criados com o Visual Basic não confie em valores de registro do Windows para funcionar corretamente. Assemblies reduzem conflitos de DLL e tornam seus aplicativos mais confiáveis e mais fácil de implantar. Em muitos casos, você pode instalar uma. Aplicativo baseado em NET simplesmente copiando seus arquivos para o computador de destino.  
  
 Para obter mais informações, consulte [Manifesto de um assembly](../Topic/Assembly%20Manifest.md).  
  
## Adicionando uma referência a um Assembly  
 Para usar um assembly, você deve adicionar uma referência a ele. Em seguida, use o [instrução Imports](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) para escolher o namespace dos itens que você deseja usar. Quando um assembly é referenciado e importado, todas as classes acessíveis, propriedades, métodos e outros membros de seus namespaces estão disponíveis para o seu aplicativo como se seus códigos fossem parte de seu arquivo de origem.  
  
## Criando um Assembly  
 Compile o aplicativo com a compilação da linha de comando usando o compilador de linha de comando. Para obter detalhes sobre como criar assemblies na linha de comando, consulte [Compilando a partir da linha de comando](../../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).  
  
> [!NOTE]
>  Para criar um assembly no Visual Studio, no **criar** menu escolha **criar**.  
  
## Consulte também  
 [Guia de programação do Visual Basic](../../../../visual-basic/programming-guide/index.md)   
 [Assemblies no Common Language Runtime](../Topic/Assemblies%20in%20the%20Common%20Language%20Runtime.md)   
 [Assemblies amigáveis \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/friend-assemblies.md)   
 [Como: compartilhar um Assembly com outros aplicativos \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-share-an-assembly-with-other-applications.md)   
 [Como: carregar e descarregar Assemblies \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-load-and-unload-assemblies.md)   
 [Como: determinar se um arquivo é um Assembly \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-determine-if-a-file-is-an-assembly.md)   
 [Como: criar e usar Assemblies usando a linha de comando \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md)   
 [Passo a passo: Inserindo tipos de Assemblies gerenciados no Visual Studio \(Visual Basic\)](../Topic/Walkthrough:%20Embedding%20Types%20from%20Managed%20Assemblies%20in%20Visual%20Studio%20\(Visual%20Basic\).md)   
 [Passo a passo: Inserindo informações de tipo de Assemblies do Microsoft Office no Visual Studio \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-type-information-from-microsoft-office-assemblies-in-vs.md)