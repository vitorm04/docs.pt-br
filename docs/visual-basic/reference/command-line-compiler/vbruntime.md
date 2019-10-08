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
ms.openlocfilehash: 8c7789c6af7b82ecb40ecd73d09f64aa1da3fd4b
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005057"
---
# <a name="-vbruntime"></a>-vbruntime
Especifica que o compilador deve compilar sem uma referência para a biblioteca de tempo de execução Visual Basic ou com uma referência a uma biblioteca de tempo de execução específica.  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
-vbruntime:{ - | + | * | path }  
```  
  
## <a name="arguments"></a>Argumentos  
 \-  
 Compile sem uma referência para a biblioteca de tempo de execução Visual Basic.  
  
 \+  
 Compile com uma referência à biblioteca padrão de tempo de execução de Visual Basic.  
  
 \*  
 Compile sem uma referência à biblioteca de tempo de execução Visual Basic e insira a funcionalidade principal da biblioteca de tempo de execução Visual Basic no assembly.  
  
 `path`  
 Compile com uma referência à biblioteca (DLL) especificada.  
  
## <a name="remarks"></a>Comentários  
 A opção de compilador `-vbruntime` permite que você especifique que o compilador deve compilar sem uma referência à biblioteca de tempo de execução de Visual Basic. Se você compilar sem uma referência para a biblioteca de tempo de execução Visual Basic, erros ou avisos serão registrados em constructos de código ou linguagem que geram uma chamada para um auxiliar de tempo de execução Visual Basic. (Um *auxiliar de tempo de execução Visual Basic* é uma função definida em Microsoft. VisualBasic. dll que é chamada em tempo de execução para executar uma semântica de linguagem específica.)  
  
 A opção `-vbruntime+` produz o mesmo comportamento que ocorre se nenhuma opção de `-vbruntime` for especificada. Você pode usar a opção `-vbruntime+` para substituir as opções `-vbruntime` anteriores.  
  
 A maioria dos objetos do tipo `My` não está disponível quando você usa as opções `-vbruntime-` ou `-vbruntime:path`.  
  
## <a name="embedding-visual-basic-runtime-core-functionality"></a>Inserindo Visual Basic funcionalidade básica de tempo de execução  
 A opção `-vbruntime*` permite que você compile sem uma referência a uma biblioteca de tempo de execução. Em vez disso, a funcionalidade básica da biblioteca Visual Basic Runtime é inserida no assembly do usuário. Você pode usar essa opção se seu aplicativo for executado em plataformas que não contêm o tempo de execução de Visual Basic.  
  
 Os seguintes membros de tempo de execução são inseridos:  
  
- Classe <xref:Microsoft.VisualBasic.CompilerServices.Conversions>  
  
- Método <xref:Microsoft.VisualBasic.Strings.AscW%28System.Char%29>  
  
- Método <xref:Microsoft.VisualBasic.Strings.AscW%28System.String%29>  
  
- Método <xref:Microsoft.VisualBasic.Strings.ChrW%28System.Int32%29>  
  
- constante <xref:Microsoft.VisualBasic.Constants.vbBack>  
  
- constante <xref:Microsoft.VisualBasic.Constants.vbCr>  
  
- constante <xref:Microsoft.VisualBasic.Constants.vbCrLf>  
  
- constante <xref:Microsoft.VisualBasic.Constants.vbFormFeed>  
  
- constante <xref:Microsoft.VisualBasic.Constants.vbLf>  
  
- constante <xref:Microsoft.VisualBasic.Constants.vbNewLine>  
  
- constante <xref:Microsoft.VisualBasic.Constants.vbNullChar>  
  
- constante <xref:Microsoft.VisualBasic.Constants.vbNullString>  
  
- constante <xref:Microsoft.VisualBasic.Constants.vbTab>  
  
- constante <xref:Microsoft.VisualBasic.Constants.vbVerticalTab>  
  
- Alguns objetos do tipo `My`  
  
 Se você compilar usando a opção `-vbruntime*` e seu código fizer referência a um membro da biblioteca de tempo de execução do Visual Basic que não esteja incorporada à funcionalidade principal, o compilador retornará um erro que indica que o membro não está disponível.  
  
## <a name="referencing-a-specified-library"></a>Referenciando uma biblioteca especificada  
 Você pode usar o argumento `path` para compilar com uma referência a uma biblioteca de tempo de execução personalizada em vez da biblioteca de tempo de execução de Visual Basic padrão.  
  
 Se o valor do argumento `path` for um caminho totalmente qualificado para uma DLL, o compilador usará esse arquivo como a biblioteca de tempo de execução. Se o valor do argumento `path` não for um caminho totalmente qualificado para uma DLL, o compilador de Visual Basic pesquisará a DLL identificada na pasta atual primeiro. Em seguida, ele pesquisará no caminho que você especificou usando a opção de compilador [-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md) . Se a opção de compilador `-sdkpath` não for usada, o compilador pesquisará a DLL identificada na pasta .NET Framework (`%systemroot%\Microsoft.NET\Framework\versionNumber`).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar a opção `-vbruntime` para compilar com uma referência a uma biblioteca personalizada.  
  
```console
vbc -vbruntime:C:\VBLibraries\CustomVBLibrary.dll  
```  
  
## <a name="see-also"></a>Consulte também

- [Núcleo de Visual Basic – novo modo de compilação no Visual Studio 2010 SP1](https://devblogs.microsoft.com/vbteam/vb-core-new-compilation-mode-in-visual-studio-2010-sp1/)
- [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)
