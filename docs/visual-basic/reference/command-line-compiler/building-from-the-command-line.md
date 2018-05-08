---
title: Compilando a partir da linha de comando (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- builds [Visual Basic], command-line
- Visual Basic compiler, about Visual Basic compiler
- command line [Visual Basic], compilers
- command line [Visual Basic], building from
- command line [Visual Basic], builds
- compilers [Visual Basic], invoking from command line
- command-line builds
- compiling source code
- command-line compilers [Visual Basic], Visual Basic
- command line [Visual Basic], Visual Basic
ms.assetid: e61947e9-a42e-4717-a699-5f70a98cdd03
ms.openlocfilehash: 391e16da86aa741a1b78f35d9afd95688f33c4db
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="building-from-the-command-line-visual-basic"></a>Compilando a partir da linha de comando (Visual Basic)
Um projeto do Visual Basic é composto por um ou mais arquivos de origem separados. Durante o processo conhecido como compilação, esses arquivos são agrupados em um pacote — um único arquivo executável que pode ser executado como um aplicativo.  
  
 Visual Basic fornece um compilador de linha de comando como uma alternativa para compilar programas de dentro do ambiente de desenvolvimento integrado (IDE) do Visual Studio. O compilador de linha de comando é projetado para situações em que você não exigir o conjunto completo de recursos no IDE — por exemplo, quando você está usando ou gravar para computadores com sistema limitados memória ou espaço de armazenamento.  
  
  Para compilar arquivos de origem a partir do IDE do Visual Studio, escolha o **criar** comando o **criar** menu.  
  
> [!TIP]
>  Quando você cria arquivos de projeto usando o IDE do Visual Studio, você pode exibir informações sobre associado **vbc** comando e suas opções na janela de saída. Para exibir essas informações, abra o [caixa de diálogo Opções, projetos e soluções, compilação e execução](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run)e, em seguida, defina o **detalhamento da saída de compilação de projeto MSBuild** para **Normal** ou um nível mais alto de detalhes. Para obter mais informações, consulte [Como exibir, salvar e configurar arquivos de log de build](http://msdn.microsoft.com/library/75d38b76-26d6-4f43-bbe7-cbacd7cc81e7).  
  
 Você pode compilar os arquivos de projeto (. vbproj) em um prompt de comando usando o MSBuild. Para obter mais informações, consulte [referência de linha de comando](/visualstudio/msbuild/msbuild-command-line-reference) e [passo a passo: usando MSBuild](/visualstudio/msbuild/walkthrough-using-msbuild).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Como invocar o compilador de linha de comando](../../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md)  
 Descreve como chamar o compilador de linha de comando no prompt do MS-DOS ou de um subdiretório específico.  
  
 [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 Fornece uma lista de linhas de comando de exemplo que você pode modificar para seu próprio uso.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 Fornece listas de opções do compilador, organizadas em ordem alfabética ou finalidade.  
  
 [Compilação Condicional](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 Descreve como compilar determinadas seções de código.  
  
 [Compilando e limpando projetos e soluções no Visual Studio](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio)  
 Descreve como organizar o que será incluído em diferentes compilações, escolha Propriedades do projeto e certifique-se de compilação dos projetos na ordem correta.
