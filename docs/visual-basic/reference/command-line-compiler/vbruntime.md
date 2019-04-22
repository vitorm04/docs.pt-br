---
title: -vbruntime
ms.date: 03/13/2018
f1_keywords:
- vbruntime
- -vbruntime
helpviewer_keywords:
- vbruntime compiler option [Visual Basic]
- -vbruntime compiler option [Visual Basic]
- /vbruntime compiler option [Visual Basic]
ms.assetid: 1aa0239e-511a-4c29-957d-fd72877b350a
ms.openlocfilehash: a1988fcd19c6629d85ae0e739681fd39fe033c0d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58843858"
---
# <a name="-vbruntime"></a>-vbruntime
Especifica que o compilador deve compilar sem uma referência à biblioteca de tempo de execução do Visual Basic, ou com uma referência a uma biblioteca de tempo de execução específico.  
  
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
 Compilar sem uma referência à biblioteca de tempo de execução do Visual Basic e incorporar a funcionalidade de núcleo da biblioteca de tempo de execução do Visual Basic no assembly.  
  
 `path`  
 Compile com uma referência para a biblioteca especificada (DLL).  
  
## <a name="remarks"></a>Comentários  
 O `-vbruntime` opção de compilador permite que você especifique que o compilador deve compilar sem uma referência à biblioteca de tempo de execução do Visual Basic. Se você compilar sem uma referência à biblioteca de tempo de execução do Visual Basic, erros ou avisos serão registrados em construções de código ou linguagem que geram uma chamada para um auxiliar de tempo de execução do Visual Basic. (Um *auxiliar de tempo de execução do Visual Basic* é uma função definida no VisualBasic é chamado em tempo de execução para executar uma semântica de linguagem específica.)  
  
 O `-vbruntime+` opção produz o mesmo comportamento que ocorre se nenhuma `-vbruntime` opção for especificada. Você pode usar o `-vbruntime+` opção de substituir anterior `-vbruntime` comutadores.  
  
 A maioria dos objetos do `My` tipo não estão disponíveis quando você usa o `-vbruntime-` ou `-vbruntime:path` opções.  
  
## <a name="embedding-visual-basic-runtime-core-functionality"></a>Inserir a funcionalidade básica de tempo de execução do Visual Basic  
 O `-vbruntime*` opção permite que você compilar sem uma referência a uma biblioteca de tempo de execução. Em vez disso, a funcionalidade básica da biblioteca de tempo de execução do Visual Basic é inserida no assembly de usuário. Você pode usar essa opção se seu aplicativo é executado em plataformas que não contêm o tempo de execução do Visual Basic.  
  
 Os seguintes membros de tempo de execução são inseridos:  
  
-   Classe <xref:Microsoft.VisualBasic.CompilerServices.Conversions>  
  
-   Método <xref:Microsoft.VisualBasic.Strings.AscW%28System.Char%29>  
  
-   Método <xref:Microsoft.VisualBasic.Strings.AscW%28System.String%29>  
  
-   Método <xref:Microsoft.VisualBasic.Strings.ChrW%28System.Int32%29>  
  
-   <xref:Microsoft.VisualBasic.Constants.vbBack> Constante  
  
-   <xref:Microsoft.VisualBasic.Constants.vbCr> Constante  
  
-   <xref:Microsoft.VisualBasic.Constants.vbCrLf> Constante  
  
-   <xref:Microsoft.VisualBasic.Constants.vbFormFeed> Constante  
  
-   <xref:Microsoft.VisualBasic.Constants.vbLf> Constante  
  
-   <xref:Microsoft.VisualBasic.Constants.vbNewLine> Constante  
  
-   <xref:Microsoft.VisualBasic.Constants.vbNullChar> Constante  
  
-   <xref:Microsoft.VisualBasic.Constants.vbNullString> Constante  
  
-   <xref:Microsoft.VisualBasic.Constants.vbTab> Constante  
  
-   <xref:Microsoft.VisualBasic.Constants.vbVerticalTab> Constante  
  
-   Alguns objetos do `My` tipo  
  
 Se você compilar usando o `-vbruntime*` opção e seu código faz referência a um membro da biblioteca de tempo de execução do Visual Basic que não são inseridos com a funcionalidade básica, o compilador retorna um erro que indica que o membro não está disponível.  
  
## <a name="referencing-a-specified-library"></a>Fazendo referência a uma biblioteca especificada  
 Você pode usar o `path` argumento para compilar com uma referência a uma biblioteca de tempo de execução personalizado em vez do padrão de biblioteca de tempo de execução do Visual Basic.  
  
 Se o valor para o `path` argumento é um caminho totalmente qualificado para uma DLL, o compilador usará esse arquivo como a biblioteca de tempo de execução. Se o valor para o `path` argumento não é um caminho totalmente qualificado para uma DLL, o compilador do Visual Basic irá procurar a DLL identificada na pasta atual primeiro. Em seguida, ele pesquisará no caminho especificado usando o [- sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md) opção de compilador. Se o `-sdkpath` opção de compilador não for usada, o compilador irá procurar a DLL identificada na pasta do .NET Framework (`%systemroot%\Microsoft.NET\Framework\versionNumber`).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar o `-vbruntime` permite que você compile com uma referência a uma biblioteca personalizada.  
  
```console
vbc -vbruntime:C:\VBLibraries\CustomVBLibrary.dll  
```  
  
## <a name="see-also"></a>Consulte também

- [Visual Basic Core – novo modo de compilação no Visual Studio 2010 SP1](https://devblogs.microsoft.com/vbteam/vb-core-new-compilation-mode-in-visual-studio-2010-sp1/)
- [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)
