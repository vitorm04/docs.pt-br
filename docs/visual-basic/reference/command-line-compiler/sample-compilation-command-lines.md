---
title: "Linhas de comando de compila&#231;&#227;o de exemplo (Visual Basic) | Microsoft Docs"
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
  - "compiladores de linha de comando"
  - "compilação de linha de comando"
  - "compiladores de linha de comando"
  - "Compilando o código-fonte, na linha de comando"
  - "Compilador do Visual Basic, linhas de comando de exemplo"
ms.assetid: 5bfbb487-5f47-4267-969a-39dfb917beeb
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Linhas de comando de compila&#231;&#227;o de exemplo (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Como uma alternativa a compilar programas [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] usando o [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)], você pode compilar da linha de comando para produzir arquivos executáveis \(.exe\) ou bibliotecas de vínculo dinâmico \(.dll\).  
  
 O compilador de linha de comando do [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] suporta um conjunto completo de opções que controlam arquivos de entrada e saída, e opções de depuração e pré\-processamento.  Cada opção está disponível em duas formas intercambiáveis: `-``option` e `/``option`.  Esta documentação mostra apenas a forma `/``option`.  
  
 A tabela a seguir lista algumas linhas de comando como exemplo que você modificar para seu uso próprio.  
  
|Para|Uso|  
|----------|---------|  
|Compilar File.vb e criar File.exe|`vbc /referência:Microsoft.VisualBasic.dll File.vb`|  
|Compilar File.vb e criar File.dll|`vbc /target:library File.vb`|  
|Compilar File.vb e criar My.exe|`vbc /out:My.exe File.vb`|  
|Compilar todos os arquivos [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] no diretório corrent, com otimizações habilitadas e o símbolo `DEBUG` definido, produzindo File2.exe|`vbc /define:DEBUG=1 /optimize /out:File2.exe *.vb`|  
|Compilar todos os arquivos [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] no diretório corrent, produzindo uma versão de depuração do arquivo File2.dll sem mostrar o logotipo ou avisos.|`vbc /target:library /out:File2.dll /nowarn /nologo /debug *.vb`|  
|Compilar todos os arquivos [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] no diretório corrente para Something.dll|`vbc /target:library /out:Something.dll *.vb`|  
  
 Quando compilar da linha de comando, você deve explicitamente referenciar a Biblioteca em Tempo de Execução do Microsoft [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] através da opção `/reference` do compilador.  
  
> [!TIP]
>  Quando você cria um projeto usando o IDE do Visual Studio, você pode exibir informações sobre o comando associado de **vbc** com suas opções do compilador na janela de saída.  Para exibir esta informação, abra [Caixa de diálogo Opções, Projetos e Soluções, Compilar e Executar](/visual-studio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), e defina **Detalhamento da saída de compilação do projeto no MSBuild** a **Normal** ou um nível mais alto de verbosidade.  Para obter mais informações, consulte [Como ver, salvar e configurar arquivos de log de compilação](../Topic/How%20to:%20View,%20Save,%20and%20Configure%20Build%20Log%20Files.md).  
  
## Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Compilação condicional](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)