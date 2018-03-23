---
title: Linhas de comando de compilação de exemplo (Visual Basic)
ms.date: 03/13/2018
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- command line [Visual Basic], compilers
- compilation [Visual Basic], command-line
- command-line compilers
- compiling source code [Visual Basic], from command line
- Visual Basic compiler, sample command lines
ms.assetid: 5bfbb487-5f47-4267-969a-39dfb917beeb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a7c3fac318e05c5e3d6fb9dd7117cac70ead03dc
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/22/2018
---
# <a name="sample-compilation-command-lines-visual-basic"></a>Exemplos de linhas de comando de compilação (Visual Basic)
Como uma alternativa para compilar [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] programas no [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)], você pode compilar da linha de comando para produzir arquivos executáveis (.exe) ou arquivos de biblioteca de vínculo dinâmico (. dll).  
  
 O [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compilador de linha de comando dá suporte a um conjunto completo de opções que controlam os arquivos de entrada e saídos, assemblies e de depuração e opções de pré-processador. Cada opção está disponível em duas formas intercambiáveis: `-option` e `/option`. Esta documentação mostra apenas o `-option` formulário.  
  
 A tabela a seguir lista algumas linhas de comando de exemplo que você pode modificar para seu próprio uso.  
  
|Para|Use|  
|--------|---------|  
|Compilar File. vb e criar File.exe|`vbc -reference:Microsoft.VisualBasic.dll File.vb`|  
|Compilar File. vb e criar File. dll|`vbc -target:library File.vb`|  
|Compilar File. vb e criar My.exe|`vbc -out:My.exe File.vb`|  
|Compilar todos os [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] arquivos no diretório atual, com otimizações em e `DEBUG` símbolo definido, produzindo File2.exe|`vbc -define:DEBUG=1 -optimize -out:File2.exe *.vb`|  
|Compilar todos os [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] arquivos no diretório atual, produzindo uma versão de depuração do arquivo File2. dll sem mostrar o logotipo ou avisos|`vbc -target:library -out:File2.dll -nowarn -nologo -debug *.vb`|  
|Compilar todos os [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] arquivos no diretório atual para Something. dll|`vbc -target:library -out:Something.dll *.vb`|  
  
 Ao compilar na linha de comando, você deve referenciar explicitamente o Microsoft [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] biblioteca de tempo de execução por meio de `-reference` opção de compilador.  
  
> [!TIP]
>  Quando você cria um projeto usando o IDE do Visual Studio, você pode exibir informações sobre associado **vbc** com suas opções de compilador na janela de saída. Para exibir essas informações, abra o [caixa de diálogo Opções, projetos e soluções, compilação e execução](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run)e, em seguida, defina o **detalhamento da saída de compilação de projeto MSBuild** para **Normal** ou um nível mais alto de detalhes. Para obter mais informações, consulte [Como exibir, salvar e configurar arquivos de log de build](http://msdn.microsoft.com/library/75d38b76-26d6-4f43-bbe7-cbacd7cc81e7).  
  
## <a name="see-also"></a>Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Compilação Condicional](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
