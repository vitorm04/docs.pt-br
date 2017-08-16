---
title: "Exemplo de linhas de comando de compilação (Visual Basic) | Documentos do Microsoft"
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
- command line, compilers
- compilation, command-line
- command-line compilers
- compiling source code, from command line
- Visual Basic compiler, sample command lines
ms.assetid: 5bfbb487-5f47-4267-969a-39dfb917beeb
caps.latest.revision: 14
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
ms.openlocfilehash: 918787b3377f2e5a636a6b098046ac2f455efcdd
ms.lasthandoff: 03/13/2017

---
# <a name="sample-compilation-command-lines-visual-basic"></a>Linhas de comando de compilação de exemplo (Visual Basic)
Como uma alternativa para compilar [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] programas no [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)], você pode compilar da linha de comando para produzir arquivos executáveis (.exe) ou arquivos de biblioteca de vínculo dinâmico (. dll).  
  
 O [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilador de linha de comando oferece suporte a um conjunto completo de opções que controlam arquivos de entrada e saídos, assemblies e depuração e pré-processamento. Cada opção está disponível em duas formas intercambiáveis: `-``option` e `/``option`. Esta documentação mostra apenas o `/``option` formulário.  
  
 A tabela a seguir lista algumas linhas de comando de exemplo que você pode modificar para seu próprio uso.  
  
|Para|Uso|  
|--------|---------|  
|Compilar File. vb e criar File.exe|`vbc /reference:Microsoft.VisualBasic.dll File.vb`|  
|Compilar File. vb e criar File. dll|`vbc /target:library File.vb`|  
|Compilar File. vb e criar My.exe|`vbc /out:My.exe File.vb`|  
|Compilar todos os [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] arquivos no diretório atual, com otimizações e o `DEBUG` símbolo definido, produzindo File2.exe|`vbc /define:DEBUG=1 /optimize /out:File2.exe *.vb`|  
|Compilar todos os [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] arquivos no diretório atual, produzindo uma versão de depuração do arquivo File2. dll sem mostrar o logotipo ou avisos|`vbc /target:library /out:File2.dll /nowarn /nologo /debug *.vb`|  
|Compilar todos os [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] arquivos no diretório atual para Something. dll|`vbc /target:library /out:Something.dll *.vb`|  
  
 Quando compilar da linha de comando, você deve explicitamente referenciar o Microsoft [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] biblioteca de tempo de execução por meio de `/reference` opção de compilador.  
  
> [!TIP]
>  Quando você cria um projeto usando o IDE do Visual Studio, você pode exibir informações sobre associado **vbc** comando com suas opções de compilador na janela de saída. Para exibir essas informações, abra o [caixa de diálogo Opções, projetos e soluções, compilação e execução](https://docs.microsoft.com/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run)e defina o **detalhamento da saída de compilação de projeto MSBuild** para **Normal** ou um maior nível de detalhamento. Para obter mais informações, consulte [Como exibir, salvar e configurar arquivos de log de build](http://msdn.microsoft.com/library/75d38b76-26d6-4f43-bbe7-cbacd7cc81e7).  
  
## <a name="see-also"></a>Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Compilação Condicional](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
