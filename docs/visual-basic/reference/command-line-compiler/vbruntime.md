---
title: /vbruntime | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbruntime
- /vbruntime
dev_langs:
- VB
helpviewer_keywords:
- vbruntime compiler option [Visual Basic]
- -vbruntime compiler option [Visual Basic]
- /vbruntime compiler option [Visual Basic]
ms.assetid: 1aa0239e-511a-4c29-957d-fd72877b350a
caps.latest.revision: 17
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
ms.openlocfilehash: 455f950988b540b74874ce38882c59059f77ea8f
ms.lasthandoff: 03/13/2017

---
# <a name="vbruntime"></a>/vbruntime
Especifica que o compilador deve compilar sem uma referência à biblioteca de tempo de execução do Visual Basic ou com uma referência a uma biblioteca de tempo de execução específico.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
/vbruntime:{ - | + | * | path }  
```  
  
## <a name="arguments"></a>Arguments  
 \-  
 Compile sem uma referência à biblioteca de tempo de execução do Visual Basic.  
  
 \+  
 Compile com uma referência à biblioteca de tempo de execução do Visual Basic padrão.  
  
 \*  
 Compilar sem uma referência à biblioteca de tempo de execução do Visual Basic e incorporar a funcionalidade principal da biblioteca de tempo de execução do Visual Basic no assembly.  
  
 `path`  
 Compile com uma referência à biblioteca especificada (DLL).  
  
## <a name="remarks"></a>Comentários  
 O `/vbruntime` opção de compilador permite que você especifique que o compilador deve compilar sem uma referência à biblioteca de tempo de execução do Visual Basic. Se você compilar sem uma referência à biblioteca de tempo de execução do Visual Basic, erros ou avisos serão registrados em construções de código ou linguagem que geram uma chamada para um auxiliar de tempo de execução do Visual Basic. (Um *auxiliar de tempo de execução do Visual Basic* é uma função definida no Microsoft.VisualBasic.dll que é chamada no tempo de execução para executar uma semântica de linguagem específica.)  
  
 O `/vbruntime+` opção produz o mesmo comportamento que ocorre se nenhuma `/vbruntime` opção é especificada. Você pode usar o `/vbruntime+` opção Substituir anterior `/vbruntime` comutadores.  
  
 A maioria dos objetos do `My` tipo não estão disponíveis quando você usa o `/vbruntime-` ou `vbruntime:``path` opções.  
  
## <a name="embedding-visual-basic-runtime-core-functionality"></a>Incorporar a funcionalidade básica de tempo de execução do Visual Basic  
 O `/vbruntime*` opção permite que você compilar sem uma referência a uma biblioteca de tempo de execução. Em vez disso, a funcionalidade básica da biblioteca de tempo de execução do Visual Basic é inserida no assembly de usuário. Você pode usar essa opção se seu aplicativo é executado em plataformas que não contêm o tempo de execução do Visual Basic.  
  
 Os seguintes membros de tempo de execução são inseridos:  
  
-   <xref:Microsoft.VisualBasic.CompilerServices.Conversions>classe</xref:Microsoft.VisualBasic.CompilerServices.Conversions>  
  
-   <xref:Microsoft.VisualBasic.Strings.AscW%28System.Char%29>método</xref:Microsoft.VisualBasic.Strings.AscW%28System.Char%29>  
  
-   <xref:Microsoft.VisualBasic.Strings.AscW%28System.String%29>método</xref:Microsoft.VisualBasic.Strings.AscW%28System.String%29>  
  
-   <xref:Microsoft.VisualBasic.Strings.ChrW%28System.Int32%29>método</xref:Microsoft.VisualBasic.Strings.ChrW%28System.Int32%29>  
  
-   <xref:Microsoft.VisualBasic.Constants.vbBack>constante</xref:Microsoft.VisualBasic.Constants.vbBack>  
  
-   <xref:Microsoft.VisualBasic.Constants.vbCr>constante</xref:Microsoft.VisualBasic.Constants.vbCr>  
  
-   <xref:Microsoft.VisualBasic.Constants.vbCrLf>constante</xref:Microsoft.VisualBasic.Constants.vbCrLf>  
  
-   <xref:Microsoft.VisualBasic.Constants.vbFormFeed>constante</xref:Microsoft.VisualBasic.Constants.vbFormFeed>  
  
-   <xref:Microsoft.VisualBasic.Constants.vbLf>constante</xref:Microsoft.VisualBasic.Constants.vbLf>  
  
-   <xref:Microsoft.VisualBasic.Constants.vbNewLine>constante</xref:Microsoft.VisualBasic.Constants.vbNewLine>  
  
-   <xref:Microsoft.VisualBasic.Constants.vbNullChar>constante</xref:Microsoft.VisualBasic.Constants.vbNullChar>  
  
-   <xref:Microsoft.VisualBasic.Constants.vbNullString>constante</xref:Microsoft.VisualBasic.Constants.vbNullString>  
  
-   <xref:Microsoft.VisualBasic.Constants.vbTab>constante</xref:Microsoft.VisualBasic.Constants.vbTab>  
  
-   <xref:Microsoft.VisualBasic.Constants.vbVerticalTab>constante</xref:Microsoft.VisualBasic.Constants.vbVerticalTab>  
  
-   Alguns objetos do `My` tipo  
  
 Se você compilar usando o `/vbruntime*` opção e seu código referencia um membro da biblioteca de tempo de execução do Visual Basic não são inseridos com a funcionalidade básica, o compilador retorna um erro que indica que o membro não está disponível.  
  
## <a name="referencing-a-specified-library"></a>Fazendo referência a uma biblioteca especificada  
 Você pode usar o `path` argumento para compilar com uma referência a uma biblioteca de tempo de execução personalizado em vez do padrão de biblioteca de tempo de execução do Visual Basic.  
  
 Se o valor para o `path` argumento é um caminho totalmente qualificado para uma DLL, o compilador usará esse arquivo como a biblioteca de tempo de execução. Se o valor para o `path` argumento não é um caminho totalmente qualificado para uma DLL, o compilador do Visual Basic irá procurar a DLL identificada na pasta atual primeiro. Em seguida, ele irá procurar no caminho especificado usando o [/sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md) opção de compilador. Se o `/sdkpath` opção de compilador não for usada, o compilador irá procurar a DLL identificada na pasta do .NET Framework (`%systemroot%\Microsoft.NET\Framework\versionNumber`).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar o `/vbruntime` opção para compilar com uma referência a uma biblioteca personalizada.  
  
```  
vbc /vbruntime:C:\VBLibraries\CustomVBLibrary.dll  
```  
  
## <a name="see-also"></a>Consulte também  
 [Núcleo do Visual Basic – novo modo de compilação no Visual Studio 2010 SP1](http://blogs.msdn.com/b/vbteam/archive/2011/01/10/vb-core-new-compilation-mode-in-visual-studio-2010-sp1.aspx)   
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Exemplos de linhas de comando de compilação](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [/sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)
