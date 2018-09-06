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
ms.openlocfilehash: 89bcd6e0e7c1cc867bf853dc9bbe96628942ace2
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43866971"
---
# <a name="building-from-the-command-line-visual-basic"></a>Compilando a partir da linha de comando (Visual Basic)
Um projeto do Visual Basic é composto por um ou mais arquivos de origem separado. Durante o processo conhecido como compilação, esses arquivos são reunidos em um pacote — um único arquivo executável que pode ser executado como um aplicativo.  
  
 Visual Basic fornece um compilador de linha de comando como uma alternativa para compilar programas de dentro do ambiente de desenvolvimento integrado (IDE) do Visual Studio. O compilador de linha de comando foi projetado para situações em que você não exige o conjunto completo de recursos no IDE — por exemplo, quando você está usando ou escrever para computadores com espaço de memória ou armazenamento do sistema limitados.  
  
  Para compilar arquivos de origem da IDE do Visual Studio, escolha o **construir** comando da **Build** menu.  
  
> [!TIP]
>  Quando você compila arquivos de projeto usando o IDE do Visual Studio, você pode exibir informações sobre associado **vbc** comando e suas opções na janela de saída. Para exibir essas informações, abra o [caixa de diálogo Opções, projetos e soluções, compilação e execução](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run)e, em seguida, defina as **detalhes da saída de build do projeto do MSBuild** para **Normal** ou um nível mais alto de detalhamento. Para obter mais informações, consulte [Como exibir, salvar e configurar arquivos de log de build](https://msdn.microsoft.com/library/75d38b76-26d6-4f43-bbe7-cbacd7cc81e7).  
  
 Você pode compilar arquivos de projeto (. vbproj) em um prompt de comando usando MSBuild. Para obter mais informações, consulte [referência de linha de comando](/visualstudio/msbuild/msbuild-command-line-reference) e [passo a passo: usando o MSBuild](/visualstudio/msbuild/walkthrough-using-msbuild).  
  
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
  
 [Compilando e limpando projetos e soluções no Visual Studio](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio)  
 Descreve como organizar o que será incluído em diferentes compilações, escolha as propriedades do projeto e certifique-se de que os projetos de build na ordem correta.
