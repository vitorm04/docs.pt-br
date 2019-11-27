---
title: Linhas de Comando de Compilação de Exemplo
ms.date: 03/13/2018
helpviewer_keywords:
- command line [Visual Basic], compilers
- compilation [Visual Basic], command-line
- command-line compilers
- compiling source code [Visual Basic], from command line
- Visual Basic compiler, sample command lines
ms.assetid: 5bfbb487-5f47-4267-969a-39dfb917beeb
ms.openlocfilehash: 27a20a5a3525353ffbced729b8ac9c98b3e48fc1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350848"
---
# <a name="sample-compilation-command-lines-visual-basic"></a>Linhas de comando de compilação de exemplo (Visual Basic)

Como alternativa à compilação de Visual Basic programas de dentro do Visual Studio, você pode compilar a partir da linha de comando para produzir arquivos executáveis (. exe) ou arquivos. dll (biblioteca de vínculo dinâmico).

O compilador de linha de comando Visual Basic dá suporte a um conjunto completo de opções que controlam arquivos de entrada e saída, assemblies e opções de depuração e pré-processador. Cada opção está disponível em duas formas intercambiáveis: `-option` e `/option`. Esta documentação mostra apenas o formulário `-option`.

A tabela a seguir lista algumas linhas de comando de exemplo que você pode modificar para seu próprio uso.

|{1&gt;Para&lt;1}|Uso|
|--------|---------|
|Compilar File. vb e criar arquivo. exe|`vbc -reference:Microsoft.VisualBasic.dll File.vb`|
|Compilar File. vb e criar File. dll|`vbc -target:library File.vb`|
|Compilar File. vb e criar My. exe|`vbc -out:My.exe File.vb`|
|Compile File. vb e crie uma biblioteca e um assembly de referência chamado file. dll|`vbc -target:library -ref:.\debug\bin\ref\file.dll File.vb`|
|Compilar todos os arquivos de Visual Basic no diretório atual, com otimizações no e o símbolo de `DEBUG` definido, produzindo file2. exe|`vbc -define:DEBUG=1 -optimize -out:File2.exe *.vb`|
|Compilar todos os arquivos de Visual Basic no diretório atual, produzindo uma versão de depuração de arquivo2. dll sem exibir o logotipo ou avisos|`vbc -target:library -out:File2.dll -nowarn -nologo -debug *.vb`|
|Compilar todos os arquivos de Visual Basic no diretório atual para algo. dll|`vbc -target:library -out:Something.dll *.vb`|

> [!TIP]
> Ao criar um projeto usando o IDE do Visual Studio, você pode exibir informações sobre o comando **Vbc** associado com suas opções de compilador na janela de saída. Para exibir essas informações, abra a [caixa de diálogo opções, projetos e soluções, compile e execute](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run)e defina o **detalhamento de saída de compilação do projeto MSBuild** como **normal** ou um nível mais alto de detalhamento.

## <a name="see-also"></a>Consulte também

- [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Compilação Condicional](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
