---
title: Compilando na linha de comando (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- builds [Visual Basic], command-line
- Visual Basic compiler, about Visual Basic compiler
- command line [Visual Basic], compilers
- command line [Visual Basic], building from
- command line [Visual Basic], builds
- compilers, invoking from command line
- command-line builds
- compiling source code
- command-line compilers, Visual Basic
- command line [Visual Basic], Visual Basic
ms.assetid: e61947e9-a42e-4717-a699-5f70a98cdd03
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 49f84c221e18457ab46534ca46da7c4764a8ee40
ms.lasthandoff: 03/13/2017

---
# <a name="building-from-the-command-line-visual-basic"></a>Compilando a partir da linha de comando (Visual Basic)
Um [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] projeto é composto de um ou mais arquivos de origem separado. Durante o processo conhecido como compilação, esses arquivos são reunidos em um único pacote — um único arquivo executável que pode ser executado como um aplicativo.  
  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]Fornece um compilador de linha de comando como uma alternativa para compilar programas de dentro do [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] ambiente de desenvolvimento integrado (IDE). O compilador de linha de comando destina-se a situações em que não exigem que o conjunto completo de recursos no IDE — por exemplo, quando você estiver usando ou escrevendo para computadores com sistema limitados memória ou espaço de armazenamento.  
  
 Quando compilar da linha de comando, você deve explicitamente referenciar o Microsoft [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] biblioteca de tempo de execução por meio de `/reference` opção de compilador.  
  
 Para compilar os arquivos de origem de dentro de [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] IDE, escolha o **criar** comando do **criar** menu.  
  
> [!TIP]
>  Quando você cria arquivos de projeto usando o IDE do Visual Studio, você pode exibir informações sobre associado **vbc** comando e suas opções na janela de saída. Para exibir essas informações, abra o [caixa de diálogo Opções, projetos e soluções, compilação e execução](https://docs.microsoft.com/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run)e defina o **detalhamento da saída de compilação de projeto MSBuild** para **Normal** ou um maior nível de detalhamento. Para obter mais informações, consulte [Como exibir, salvar e configurar arquivos de log de build](http://msdn.microsoft.com/library/75d38b76-26d6-4f43-bbe7-cbacd7cc81e7).  
  
 Você pode compilar os arquivos de projeto (. vbproj) em um prompt de comando usando o MSBuild. Para obter mais informações, consulte [referência de linha de comando](https://docs.microsoft.com/visualstudio/msbuild/msbuild-command-line-reference) e [passo a passo: usando MSBuild](http://msdn.microsoft.com/library/b8a8b866-bb07-4abf-b9ec-0b40d281c310).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Como invocar o compilador de linha de comando](../../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md)  
 Descreve como invocar o compilador de linha de comando no prompt do MS-DOS ou de um subdiretório específico.  
  
 [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 Fornece uma lista de linhas de comando de exemplo que você pode modificar para seu próprio uso.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 Fornece listas de opções do compilador, organizadas em ordem alfabética ou por finalidade.  
  
 [Compilação Condicional](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 Descreve como compilar determinadas seções de código.  
  
 [Compilando e limpando projetos e soluções no Visual Studio](https://docs.microsoft.com/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio)  
 Descreve como organizar o que será incluído em diferentes compilações, escolha Propriedades do projeto e certifique-se de que projetos são compilados na ordem correta.
