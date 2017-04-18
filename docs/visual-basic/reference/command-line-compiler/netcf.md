---
title: /netcf | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- /netcf
- netcf
dev_langs:
- VB
helpviewer_keywords:
- -netcf compiler option [Visual Basic]
- netcf compiler option [Visual Basic]
- /netcf compiler option [Visual Basic]
ms.assetid: db7cfa59-c315-401c-a59b-0daf355343d6
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: d8e2328eb5434ea0e73238709c429975ae29e6d0
ms.lasthandoff: 03/13/2017

---
# <a name="netcf"></a>/netcf
Define o compilador como destino o [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)].  
  
## <a name="syntax"></a>Sintaxe  
  
```  
/netcf  
```  
  
## <a name="remarks"></a>Comentários  
 O `/netcf` opção faz com que o [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilador destino o [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)] em vez de toda [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]. Funcionalidade de idioma que está presente somente no total [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] está desabilitado.  
  
 O `/netcf` opção é projetada para ser usado com [/sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md). Os recursos de linguagem desabilitados por `/netcf` são os mesmos recursos de idioma não está presentes nos arquivos de destino com `/sdkpath`.  
  
> [!NOTE]
>  O `/netcf` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ele está disponível apenas quando se compila da linha de comando. O `/netcf` opção é definida quando um [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] dispositivo projeto é carregado.  
  
 O `/netcf` opção altera os seguintes recursos de idioma:  
  
-   O [final \<palavra-chave > instrução](../../../visual-basic/language-reference/statements/end-keyword-statement.md) palavra-chave, que finaliza a execução de um programa, está desabilitado. O programa a seguir compila e executa sem `/netcf` , mas falhar no tempo de compilação com `/netcf`.  
  
     [!code-vb[VbVbalrCompiler&#34;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_1.vb)]  
  
-   Ligação tardia em todos os formulários, está desabilitado. Erros de tempo de compilação são gerados quando reconhecidos cenários de associação tardia são encontrados. O programa a seguir compila e executa sem `/netcf` , mas falhar no tempo de compilação com `/netcf`.  
  
     [!code-vb[VbVbalrCompiler&#35;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_2.vb)]  
  
-   O [automático](../../../visual-basic/language-reference/modifiers/auto.md), [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md), e [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md) modificadores estão desabilitados. A sintaxe de [instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md) instrução também é modificada para `Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]`. O código a seguir mostra o efeito de `/netcf` em uma compilação.  
  
     [!code-vb[VbVbalrCompiler&#36;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_3.vb)]  
  
-   Usando o Visual Basic 6.0 palavras-chave que foram removidas [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] gera um erro diferente quando `/netcf` é usado. Isso afeta as mensagens de erro para as seguintes palavras-chave:  
  
    -   `Open`  
  
    -   `Close`  
  
    -   `Put`  
  
    -   `Print`  
  
    -   `Write`  
  
    -   `Input`  
  
    -   `Lock`  
  
    -   `Unlock`  
  
    -   `Seek`  
  
    -   `Width`  
  
    -   `Name`  
  
    -   `FreeFile`  
  
    -   `EOF`  
  
    -   `Loc`  
  
    -   `LOF`  
  
    -   `Line`  
  
## <a name="example"></a>Exemplo  
 O seguinte código compila `Myfile.vb` com o [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)], usar as versões de mscorlib. dll e Microsoft.VisualBasic.dll encontrado no diretório de instalação padrão do [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)] na unidade C. Normalmente, você poderia usar a versão mais recente do [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)].  
  
```  
vbc /netcf /sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a>Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Exemplos de linhas de comando de compilação](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [/sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)
