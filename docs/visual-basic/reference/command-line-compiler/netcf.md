---
title: /netcf
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- /netcf
- netcf
helpviewer_keywords:
- -netcf compiler option [Visual Basic]
- netcf compiler option [Visual Basic]
- /netcf compiler option [Visual Basic]
ms.assetid: db7cfa59-c315-401c-a59b-0daf355343d6
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4a75573b0881af71e907a488c2b3c15db3816fc0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="netcf"></a>/netcf
Define o compilador como destino o [!INCLUDE[Compact](~/includes/compact-md.md)].  
  
## <a name="syntax"></a>Sintaxe  
  
```  
/netcf  
```  
  
## <a name="remarks"></a>Comentários  
 O `/netcf` opção faz com que o [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compilador ao destino de [!INCLUDE[Compact](~/includes/compact-md.md)] em vez de toda [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Funcionalidade de idioma que está presente somente no completa [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] está desabilitado.  
  
 O `/netcf` opção é projetada para ser usada com [/sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md). Os recursos de idioma desabilitados por `/netcf` são os mesmos recursos de idioma não está presentes nos arquivos de destino com `/sdkpath`.  
  
> [!NOTE]
>  O `/netcf` opção não está disponível no ambiente de desenvolvimento do Visual Studio; está disponível somente quando estiver compilando na linha de comando. O `/netcf` opção é definida quando um [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] dispositivo projeto é carregado.  
  
 O `/netcf` opção altera os seguintes recursos de idioma:  
  
-   O [final \<palavra-chave > instrução](../../../visual-basic/language-reference/statements/end-keyword-statement.md) palavra-chave que finaliza a execução de um programa, está desabilitada. O programa a seguir compila e executa sem `/netcf` , mas falhar no tempo de compilação com `/netcf`.  
  
     [!code-vb[VbVbalrCompiler#34](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_1.vb)]  
  
-   Associação tardia em todos os formulários, está desabilitada. Erros de tempo de compilação são gerados quando forem encontrados reconhecidos cenários de associação tardia. O programa a seguir compila e executa sem `/netcf` , mas falhar no tempo de compilação com `/netcf`.  
  
     [!code-vb[VbVbalrCompiler#35](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_2.vb)]  
  
-   O [automática](../../../visual-basic/language-reference/modifiers/auto.md), [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md), e [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md) modificadores estão desabilitados. A sintaxe do [instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md) instrução também é modificada para `Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]`. O código a seguir mostra o efeito de `/netcf` em uma compilação.  
  
     [!code-vb[VbVbalrCompiler#36](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_3.vb)]  
  
-   Usando o Visual Basic 6.0 palavras-chave que foram removidas da [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] gera um erro diferente quando `/netcf` é usado. Isso afeta as mensagens de erro para as seguintes palavras-chave:  
  
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
 O código a seguir compila `Myfile.vb` com o [!INCLUDE[Compact](~/includes/compact-md.md)], usando as versões de mscorlib. dll e Microsoft.VisualBasic.dll encontrado no diretório de instalação padrão do [!INCLUDE[Compact](~/includes/compact-md.md)] na unidade C. Normalmente, você poderia usar a versão mais recente do [!INCLUDE[Compact](~/includes/compact-md.md)].  
  
```  
vbc /netcf /sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a>Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [/sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)
