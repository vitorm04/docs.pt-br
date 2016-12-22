---
title: "Compilando a partir da linha de comando (Visual Basic) | Microsoft Docs"
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
helpviewer_keywords: 
  - "compilações [Visual Basic], linha de comando"
  - "Compilador do Visual Basic, sobre o compilador do Visual Basic"
  - "linha de comando [Visual Basic] compiladores"
  - "Compilando a partir de linha de comando [Visual Basic]"
  - "compilações de linha de comando [Visual Basic]"
  - "compiladores, invocando a partir da linha de comando"
  - "builds de linha de comando"
  - "compilando o código-fonte"
  - "compiladores de linha de comando, o Visual Basic"
  - "linha de comando [Visual Basic], Visual Basic"
ms.assetid: e61947e9-a42e-4717-a699-5f70a98cdd03
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Compilando a partir da linha de comando (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Um [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] projeto é composto de um ou mais arquivos de origem separado. Durante o processo conhecido como compilação, esses arquivos são reunidos em um único pacote — um único arquivo executável que pode ser executado como um aplicativo.  
  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] Fornece um compilador de linha de comando como uma alternativa para compilar programas de dentro do [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] ambiente de desenvolvimento integrado \(IDE\). O compilador de linha de comando destina\-se a situações em que não exigem que o conjunto completo de recursos no IDE — por exemplo, quando você estiver usando ou escrevendo para computadores com sistema limitados memória ou espaço de armazenamento.  
  
 Quando compilar da linha de comando, você deve explicitamente referenciar o Microsoft [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] biblioteca de tempo de execução por meio de `/reference` opção de compilador.  
  
 Para compilar os arquivos de origem de dentro a [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] IDE, escolha o **criar** comando o **criar** menu.  
  
> [!TIP]
>  Quando você cria arquivos de projeto usando o IDE do Visual Studio, você pode exibir informações sobre associado **vbc** comando e suas opções na janela de saída. Para exibir essas informações, abra o [Caixa de diálogo Opções, Projetos e Soluções, Compilar e Executar](/visual-studio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), e defina o **detalhamento da saída de compilação de projeto MSBuild** para **Normal** ou um maior nível de detalhamento. Para obter mais informações, consulte [Como ver, salvar e configurar arquivos de log de compilação](../Topic/How%20to:%20View,%20Save,%20and%20Configure%20Build%20Log%20Files.md).  
  
 Você pode compilar os arquivos de projeto \(. vbproj\) em um prompt de comando usando o MSBuild. Para obter mais informações, consulte [Referência de linha de comando](/visual-studio/msbuild/msbuild-command-line-reference) e [Instruções passo a passo: usando o MSBuild](../Topic/Walkthrough:%20Using%20MSBuild.md).  
  
## Nesta seção  
 [Como invocar o compilador de linha de comando](../Topic/How%20to:%20Invoke%20the%20Command-Line%20Compiler%20\(Visual%20Basic\).md)  
 Descreve como invocar o compilador de linha de comando no prompt do MS\-DOS ou de um subdiretório específico.  
  
 [Linhas de comando de compilação de exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 Fornece uma lista de linhas de comando de exemplo que você pode modificar para seu próprio uso.  
  
## Seções relacionadas  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 Fornece listas de opções do compilador, organizadas em ordem alfabética ou por finalidade.  
  
 [Compilação condicional](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 Descreve como compilar determinadas seções de código.  
  
 [Criando e limpando projetos e soluções no Visual Studio](/visual-studio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio)  
 Descreve como organizar o que será incluído em diferentes compilações, escolha Propriedades do projeto e certifique\-se de que projetos são compilados na ordem correta.