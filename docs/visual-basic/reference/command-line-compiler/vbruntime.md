---
title: "/vbruntime | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbruntime"
  - "/vbruntime"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Opção de compilador /vbruntime [Visual Basic]"
  - "Opção de compilador vbruntime [Visual Basic]"
  - "Opção de compilador -vbruntime [Visual Basic]"
ms.assetid: 1aa0239e-511a-4c29-957d-fd72877b350a
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /vbruntime
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Especifica que o compilador deve compilar sem uma referência à Biblioteca em Tempo de Execução do Visual Basic ou com uma referência a uma biblioteca em tempo de execução específica.  
  
## Sintaxe  
  
```  
/vbruntime:{ - | + | * | path }  
```  
  
## Argumentos  
 \-  
 Compile sem uma referência à Biblioteca em Tempo de Execução do Visual Basic.  
  
 \+  
 Compile com uma referência à Biblioteca em Tempo de Execução padrão do Visual Basic.  
  
 \*  
 Compilar sem uma referência à biblioteca de tempo de execução Visual Basic e incorporar funcionalidade de núcleo da biblioteca de tempo de execução Visual Basic no assembly.  
  
 `path`  
 Compile com uma referência à biblioteca especificada \(DLL\).  
  
## Comentários  
 A opção `/vbruntime` do compilador permite que você especifique que o compilador deve compilar sem uma referência à Biblioteca em Tempo de Execução do Visual Basic.  Se você compilar sem uma referência à Biblioteca em Tempo de Execução do Visual Basic, erros ou avisos serão registrados em construções de código ou linguagem que geram uma chamada para um auxiliar de tempo de execução do Visual Basic.  \(Um  *Auxiliar de tempo de execução do Visual Basic*  é uma função definida no Microsoft.VisualBasic.dll que é chamada no tempo de execução para executar uma semântica de linguagem específica.\)  
  
 A opção `/vbruntime+` produz o mesmo comportamento que ocorre se nenhuma opção `/vbruntime` for especificada.  Você pode usar a opção `/vbruntime+` para substituir opções `/vbruntime` anteriores.  
  
 A maioria dos objetos da `My` tipo não estão disponíveis quando você usa o `/vbruntime-` ou `vbruntime:``path` opções.  
  
## A incorporação de funcionalidade de núcleo de tempo de execução Visual Basic  
 O `/vbruntime*` opção permite que você compilar sem uma referência a umabibliotecade tempo de execução.   Em vez disso, a funcionalidade principal da biblioteca de tempo de execução Visual Basic é incorporada noassembly usuário.   Você pode usar esta opção se o seu aplicativo é executado em plataformas que não contêm o Visual Basic tempo de execução.  
  
 Os seguintes membros de tempo de execução são incorporados:  
  
-   Classe <xref:Microsoft.VisualBasic.CompilerServices.Conversions>  
  
-   Método <xref:Microsoft.VisualBasic.Strings.AscW%28System.Char%29>  
  
-   Método <xref:Microsoft.VisualBasic.Strings.AscW%28System.String%29>  
  
-   Método <xref:Microsoft.VisualBasic.Strings.ChrW%28System.Int32%29>  
  
-   <xref:Microsoft.VisualBasic.Constants.vbBack>constante  
  
-   <xref:Microsoft.VisualBasic.Constants.vbCr>constante  
  
-   <xref:Microsoft.VisualBasic.Constants.vbCrLf>constante  
  
-   <xref:Microsoft.VisualBasic.Constants.vbFormFeed>constante  
  
-   <xref:Microsoft.VisualBasic.Constants.vbLf>constante  
  
-   <xref:Microsoft.VisualBasic.Constants.vbNewLine>constante  
  
-   <xref:Microsoft.VisualBasic.Constants.vbNullChar>constante  
  
-   <xref:Microsoft.VisualBasic.Constants.vbNullString>constante  
  
-   <xref:Microsoft.VisualBasic.Constants.vbTab>constante  
  
-   <xref:Microsoft.VisualBasic.Constants.vbVerticalTab>constante  
  
-   Alguns objetos da `My` tipo  
  
 Se você compilar usando o `/vbruntime*` opção e seu código faz referência a um membro da biblioteca de tempo de execução Visual Basic que não está incorporado com a funcionalidade central, o compilador retorna um erro que indica que o membro não está disponível.  
  
## Fazendo referência a uma biblioteca de especificada  
 Você pode usar o `path` argumento para compilar com uma referência a umabiblioteca de personalizadas tempo de execuçãoem vez do padrão Visual Basic biblioteca de tempo de execução.  
  
 Se o valor para o argumento `path` for um caminho totalmente qualificado para uma DLL, o compilador usará esse arquivo como a biblioteca em tempo de execução.  Se o valor para o argumento `path` não for um caminho totalmente qualificado para uma DLL, o compilador do Visual Basic irá procurar a DLL identificada na pasta atual primeiro.  Em seguida, ele irá procurar no caminho que você especificou, usando a opção [\/sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md) do compilador.  Se a opção `/sdkpath` do compilador não for usada, o compilador irá procurar a DLL identificada na pasta do .NET Framework \(`%systemroot%\Microsoft.NET\Framework\versionNumber`\).  
  
## Exemplo  
 O exemplo a seguir mostra como usar a opção `/vbruntime` para compilar com uma referência a uma biblioteca personalizada.  
  
```  
vbc /vbruntime:C:\VBLibraries\CustomVBLibrary.dll  
```  
  
## Consulte também  
 [Visual Basic Core – novo modo de compilação no Visual Studio 2010 SP1](http://blogs.msdn.com/b/vbteam/archive/2011/01/10/vb-core-new-compilation-mode-in-visual-studio-2010-sp1.aspx)   
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Linhas de comando de compilação de exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [\/sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)