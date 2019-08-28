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
ms.openlocfilehash: 719ca45403ea56a655f06dbfea7c0fb7e32b34f7
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046436"
---
# <a name="building-from-the-command-line-visual-basic"></a>Compilando a partir da linha de comando (Visual Basic)

Um projeto Visual Basic é composto por um ou mais arquivos de origem separados. Durante o processo conhecido como compilação, esses arquivos são trazidos juntos em um pacote — um único arquivo executável que pode ser executado como um aplicativo.

O Visual Basic fornece um compilador de linha de comando como uma alternativa à compilação de programas de dentro do IDE (ambiente de desenvolvimento integrado) do Visual Studio. O compilador de linha de comando foi projetado para situações em que você não precisa do conjunto completo de recursos no IDE — por exemplo, ao usar ou gravar para computadores com memória limitada do sistema ou espaço de armazenamento.

Para compilar arquivos de origem de dentro do IDE do Visual Studio, escolha o comando **Compilar** no menu **Compilar** .

> [!TIP]
> Ao criar arquivos de projeto usando o IDE do Visual Studio, você pode exibir informações sobre o comando **Vbc** associado e suas opções na janela de saída. Para exibir essas informações, abra a [caixa de diálogo opções, projetos e soluções, compile e execute](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run)e defina o detalhamento de **saída de compilação do projeto MSBuild** como **normal** ou um nível mais alto de detalhamento. Para obter mais informações, confira [Como: Exibir, salvar e configurar arquivos](/visualstudio/ide/how-to-view-save-and-configure-build-log-files)de log de compilação.

Você pode compilar arquivos de projeto (. vbproj) em um prompt de comando usando o MSBuild. Para obter mais informações, consulte [referência de linha](/visualstudio/msbuild/msbuild-command-line-reference) de [comando e passo a passos: Usando o MSBuild](/visualstudio/msbuild/walkthrough-using-msbuild).

## <a name="in-this-section"></a>Nesta seção

[Como: Invocar o compilador de linha de comando](../../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md) \
Descreve como invocar o compilador de linha de comando no prompt do MS-DOS ou em um subdiretório específico.

[Linhas de comando de compilação de exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) \
Fornece uma lista de linhas de comando de exemplo que você pode modificar para seu próprio uso.

## <a name="related-sections"></a>Seções relacionadas

[Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md) \
Fornece listas de opções de compilador, organizadas em ordem alfabética ou por finalidade.

[Compilação condicional](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md) \
Descreve como compilar seções específicas de código.

[Compilando e limpando projetos e soluções no Visual Studio](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio) \
Descreve como organizar o que será incluído em compilações diferentes, escolher Propriedades do projeto e garantir que os projetos sejam criados na ordem correta.
