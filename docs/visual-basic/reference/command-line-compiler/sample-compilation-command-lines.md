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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7b0f1fc1d269801efdbf2e89d10679dc8159851f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="sample-compilation-command-lines-visual-basic"></a>Exemplos de linhas de comando de compilação (Visual Basic)
Como uma alternativa para compilar programas em Visual Basic de dentro do Visual Studio, você pode compilar da linha de comando para produzir arquivos executáveis (.exe) ou arquivos de biblioteca de vínculo dinâmico (. dll).  
  
 O compilador de linha de comando do Visual Basic oferece suporte a um conjunto completo de opções que controlam a entrada e saída de arquivos, assemblies e a depuração e opções de pré-processador. Cada opção está disponível em duas formas intercambiáveis: `-option` e `/option`. Esta documentação mostra apenas o `-option` formulário.  
  
 A tabela a seguir lista algumas linhas de comando de exemplo que você pode modificar para seu próprio uso.  
  
|Para|Use|  
|--------|---------|  
|Compilar File. vb e criar File.exe|`vbc -reference:Microsoft.VisualBasic.dll File.vb`|  
|Compilar File. vb e criar File. dll|`vbc -target:library File.vb`|  
|Compilar File. vb e criar My.exe|`vbc -out:My.exe File.vb`|  
|Compilar File. vb e criar uma biblioteca e uma referência de assembly chamado pendente|`vbc -target:library -ref:.\debug\bin\ref\file.dll File.vb`|
|Compilar todos os arquivos do Visual Basic no diretório atual, com otimizações em e `DEBUG` símbolo definido, produzindo File2.exe|`vbc -define:DEBUG=1 -optimize -out:File2.exe *.vb`|  
|Compilar todos os arquivos do Visual Basic no diretório atual, produzindo uma versão de depuração do arquivo File2. dll sem mostrar o logotipo ou avisos|`vbc -target:library -out:File2.dll -nowarn -nologo -debug *.vb`|  
|Compilar todos os arquivos do Visual Basic no diretório atual para Something. dll|`vbc -target:library -out:Something.dll *.vb`|  
  
> [!TIP]
>  Quando você cria um projeto usando o IDE do Visual Studio, você pode exibir informações sobre associado **vbc** com suas opções de compilador na janela de saída. Para exibir essas informações, abra o [caixa de diálogo Opções, projetos e soluções, compilação e execução](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run)e, em seguida, defina o **detalhamento da saída de compilação de projeto MSBuild** para **Normal** ou um nível mais alto de detalhes.   
  
## <a name="see-also"></a>Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Compilação Condicional](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
