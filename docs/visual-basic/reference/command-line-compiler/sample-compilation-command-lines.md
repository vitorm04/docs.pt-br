---
title: Linhas de comando de compilação de exemplo (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- command line [Visual Basic], compilers
- compilation [Visual Basic], command-line
- command-line compilers
- compiling source code [Visual Basic], from command line
- Visual Basic compiler, sample command lines
ms.assetid: 5bfbb487-5f47-4267-969a-39dfb917beeb
ms.openlocfilehash: 0771ed41d6c58ce7cc98435b405f5819e45393db
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58824293"
---
# <a name="sample-compilation-command-lines-visual-basic"></a>Exemplos de linhas de comando de compilação (Visual Basic)
Como uma alternativa para compilar programas do Visual Basic de dentro do Visual Studio, você pode compilar da linha de comando para produzir arquivos executáveis (.exe) ou arquivos de biblioteca de vínculo dinâmico (. dll).  
  
 O compilador de linha de comando do Visual Basic dá suporte a um conjunto completo de opções que controlam a entrada e saída de arquivos, assemblies e opções de depuração e pré-processamento. Cada opção está disponível em duas formas intercambiáveis: `-option` e `/option`. Esta documentação mostra apenas o `-option` formulário.  
  
 A tabela a seguir lista algumas linhas de comando de exemplo que você pode modificar para seu próprio uso.  
  
|Para|Use|  
|--------|---------|  
|Compilar File. vb e criar File.exe|`vbc -reference:Microsoft.VisualBasic.dll File.vb`|  
|Compilar File. vb e criar File. dll|`vbc -target:library File.vb`|  
|Compilar File. vb e criar My.exe|`vbc -out:My.exe File.vb`|  
|Compilar File. vb e criar uma biblioteca e um assembly de referência chamado File. dll|`vbc -target:library -ref:.\debug\bin\ref\file.dll File.vb`|
|Compilar todos os arquivos do Visual Basic no diretório atual, com otimizações em e o `DEBUG` símbolo definido, produzindo File2.exe|`vbc -define:DEBUG=1 -optimize -out:File2.exe *.vb`|  
|Compilar todos os arquivos do Visual Basic no diretório atual, produzindo uma versão de depuração de File2.dll sem exibir o logotipo ou avisos|`vbc -target:library -out:File2.dll -nowarn -nologo -debug *.vb`|  
|Compilar todos os arquivos do Visual Basic no diretório atual para Something. dll|`vbc -target:library -out:Something.dll *.vb`|  
  
> [!TIP]
>  Quando você compila um projeto usando o IDE do Visual Studio, você pode exibir informações sobre associado **vbc** com suas opções de compilador na janela de saída. Para exibir essas informações, abra o [caixa de diálogo Opções, projetos e soluções, compilação e execução](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run)e, em seguida, defina as **detalhes da saída de build do projeto do MSBuild** para **Normal** ou um nível mais alto de detalhamento.   
  
## <a name="see-also"></a>Consulte também

- [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Compilação Condicional](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
