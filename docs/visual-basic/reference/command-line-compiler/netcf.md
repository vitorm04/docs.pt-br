---
title: "/netcf | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/netcf"
  - "netcf"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Opção de compilador /netcf [Visual Basic]"
  - "Opção de compilador netcf [Visual Basic]"
  - "Opção de compilador -netcf [Visual Basic]"
ms.assetid: db7cfa59-c315-401c-a59b-0daf355343d6
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /netcf
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Define o compilador como destino o [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)].  
  
## Sintaxe  
  
```  
/netcf  
```  
  
## Comentários  
 O `/netcf` opção faz com que o [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilador para o destino do [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)] em vez de biblioteca de classes [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)].  Funcionalidade de linguagem que está presente apenas na versão completa [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] está desativado.  
  
 O `/netcf` opção foi projetada para ser usado com [\/sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md).  Os recursos de linguagem desabilitados por `/netcf` são os mesmos recursos de idioma não está presentes em arquivos de destino com `/sdkpath`.  
  
> [!NOTE]
>  A opção `/netcf` não está disponível de dentro do ambiente de desenvolvimento Visual Studio. Ela está disponível apenas quando se compila da linha de comando.  O `/netcf` opção é definida quando um [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] o projeto de dispositivo for carregado.  
  
 O `/netcf` opção altera os seguintes recursos de idioma:  
  
-   O [Instrução End \<keyword\>](../../../visual-basic/language-reference/statements/end-keyword-statement.md) palavra\-chave, que termina a execução de um programa, está desativado.  O programa a seguir compila e executa sem `/netcf` , mas falhar em tempo de compilação com `/netcf`.  
  
     [!code-vb[VbVbalrCompiler#34](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_1.vb)]  
  
-   Ligação tardia em todos os formulários, está desativado.  Erros de compilação são gerados quando os cenários de ligação atrasada reconhecidos são encontrados.  O programa a seguir compila e executa sem `/netcf` , mas falhar em tempo de compilação com `/netcf`.  
  
     [!code-vb[VbVbalrCompiler#35](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_2.vb)]  
  
-   O [Auto](../../../visual-basic/language-reference/modifiers/auto.md), [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md), e [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md) modificadores estão desabilitados.  A sintaxe do [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md) declaração também é modificada para `Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]`.  O código a seguir mostra o efeito da `/netcf` em uma compilação.  
  
     [!code-vb[VbVbalrCompiler#36](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_3.vb)]  
  
-   Usando palavras\-chave Visual Basic 6.0 que foram removidas da [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] gera um erro diferente quando `/netcf` é usado.  Isso afeta as mensagens de erro para as seguintes palavras\-chave:  
  
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
  
## Exemplo  
 O código a seguir compila `Myfile.vb` com o [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)], usar as versões do mscorlib. dll e Microsoft.VisualBasic.dll encontrado no diretório de instalação padrão da [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)] na unidade C.  Normalmente, você usaria a versão mais recente da [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)].  
  
```  
vbc /netcf /sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Linhas de comando de compilação de exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [\/sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)