---
title: -/vbruntime
ms.date: 03/13/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbruntime
- -vbruntime
helpviewer_keywords:
- vbruntime compiler option [Visual Basic]
- -vbruntime compiler option [Visual Basic]
- /vbruntime compiler option [Visual Basic]
ms.assetid: 1aa0239e-511a-4c29-957d-fd72877b350a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e6c6529fabddc75fb6ac751e0314011f05db7869
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/22/2018
---
# <a name="-vbruntime"></a>-/vbruntime
Especifica que o compilador deve compilar sem uma referência à biblioteca de tempo de execução do Visual Basic, ou com uma referência a uma biblioteca de tempo de execução específica.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
-vbruntime:{ - | + | * | path }  
```  
  
## <a name="arguments"></a>Arguments  
 \-  
 Compile sem uma referência à biblioteca de tempo de execução do Visual Basic.  
  
 \+  
 Compile com uma referência à biblioteca de tempo de execução do Visual Basic padrão.  
  
 \*  
 Compilar sem uma referência à biblioteca de tempo de execução do Visual Basic e inserir a funcionalidade básica da biblioteca de tempo de execução do Visual Basic no assembly.  
  
 `path`  
 Compile com uma referência à biblioteca especificada (DLL).  
  
## <a name="remarks"></a>Comentários  
 O `-vbruntime` opção de compilador permite que você especifique que o compilador deve compilar sem uma referência à biblioteca de tempo de execução do Visual Basic. Se você compilar sem uma referência à biblioteca de tempo de execução do Visual Basic, erros ou avisos serão registrados em construções de código ou linguagem que geram uma chamada para um auxiliar de tempo de execução do Visual Basic. (Um *auxiliar de tempo de execução do Visual Basic* é uma função definida no Microsoft.VisualBasic.dll que é chamado em tempo de execução para executar uma semântica de linguagem específica.)  
  
 O `-vbruntime+` opção produz o mesmo comportamento que ocorre se nenhuma `-vbruntime` opção é especificada. Você pode usar o `-vbruntime+` opção de substituição anterior `-vbruntime` comutadores.  
  
 A maioria dos objetos do `My` tipo não estão disponíveis quando você usa o `-vbruntime-` ou `-vbruntime:path` opções.  
  
## <a name="embedding-visual-basic-runtime-core-functionality"></a>Incorporar a funcionalidade básica de tempo de execução do Visual Basic  
 O `-vbruntime*` opção permite que você compilar sem uma referência a uma biblioteca de tempo de execução. Em vez disso, a funcionalidade básica da biblioteca de tempo de execução do Visual Basic é inserida no assembly de usuário. Você pode usar essa opção se seu aplicativo é executado em plataformas que não contêm o tempo de execução do Visual Basic.  
  
 Os seguintes membros de tempo de execução são inseridos:  
  
-   Classe <xref:Microsoft.VisualBasic.CompilerServices.Conversions>  
  
-   Método <xref:Microsoft.VisualBasic.Strings.AscW%28System.Char%29>  
  
-   Método <xref:Microsoft.VisualBasic.Strings.AscW%28System.String%29>  
  
-   Método <xref:Microsoft.VisualBasic.Strings.ChrW%28System.Int32%29>  
  
-   <xref:Microsoft.VisualBasic.Constants.vbBack> constante  
  
-   <xref:Microsoft.VisualBasic.Constants.vbCr> constante  
  
-   <xref:Microsoft.VisualBasic.Constants.vbCrLf> constante  
  
-   <xref:Microsoft.VisualBasic.Constants.vbFormFeed> constante  
  
-   <xref:Microsoft.VisualBasic.Constants.vbLf> constante  
  
-   <xref:Microsoft.VisualBasic.Constants.vbNewLine> constante  
  
-   <xref:Microsoft.VisualBasic.Constants.vbNullChar> constante  
  
-   <xref:Microsoft.VisualBasic.Constants.vbNullString> constante  
  
-   <xref:Microsoft.VisualBasic.Constants.vbTab> constante  
  
-   <xref:Microsoft.VisualBasic.Constants.vbVerticalTab> constante  
  
-   Alguns objetos do `My` tipo  
  
 Se você compilar usando o `-vbruntime*` opção e seu código faz referência a um membro da biblioteca de tempo de execução do Visual Basic que não são inseridos com a funcionalidade básica, o compilador retorna um erro que indica que o membro não está disponível.  
  
## <a name="referencing-a-specified-library"></a>Fazendo referência a uma biblioteca especificada  
 Você pode usar o `path` argumento para compilar com uma referência a uma biblioteca de tempo de execução personalizado em vez do padrão de biblioteca de tempo de execução do Visual Basic.  
  
 Se o valor para o `path` argumento é um caminho totalmente qualificado para uma DLL, o compilador usará esse arquivo como a biblioteca de tempo de execução. Se o valor para o `path` argumento não é um caminho totalmente qualificado para uma DLL, o compilador do Visual Basic irá procurar a DLL identificada na pasta atual primeiro. Ele procurará no caminho especificado usando o [- sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md) opção de compilador. Se o `-sdkpath` opção de compilador não for usada, o compilador irá procurar a DLL identificada na pasta do .NET Framework (`%systemroot%\Microsoft.NET\Framework\versionNumber`).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar o `-vbruntime` opção para compilar com uma referência a uma biblioteca personalizada.  
  
```console
vbc -vbruntime:C:\VBLibraries\CustomVBLibrary.dll  
```  
  
## <a name="see-also"></a>Consulte também  
 [Núcleo do Visual Basic – novo modo de compilação no Visual Studio 2010 SP1](http://blogs.msdn.com/b/vbteam/archive/2011/01/10/vb-core-new-compilation-mode-in-visual-studio-2010-sp1.aspx)  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)
