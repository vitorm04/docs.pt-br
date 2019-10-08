---
title: -sdkpath
ms.date: 07/20/2015
f1_keywords:
- sdkpath
- -sdkpath
helpviewer_keywords:
- -sdkpath compiler option [Visual Basic]
- /sdkpath compiler option [Visual Basic]
- sdkpath compiler option [Visual Basic]
ms.assetid: fec8a3f1-b791-4a37-8af7-344859f8212d
ms.openlocfilehash: 46cec7ac3cb78c4fc97e299535f9085eff6daeff
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004685"
---
# <a name="-sdkpath"></a>-sdkpath
Especifica o local de mscorlib. dll e Microsoft. VisualBasic. dll.  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
-sdkpath:path  
```  
  
## <a name="arguments"></a>Argumentos  
 `path`  
 O diretório que contém as versões de mscorlib. dll e Microsoft. VisualBasic. dll a serem usadas para compilação. Esse caminho não é verificado até que seja carregado. Coloque o nome do diretório entre aspas ("") se ele contiver um espaço.  
  
## <a name="remarks"></a>Comentários  
 Essa opção informa o compilador de Visual Basic para carregar os arquivos mscorlib. dll e Microsoft. VisualBasic. dll de um local não padrão. A opção `-sdkpath` foi projetada para ser usada com [-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md). O .NET Compact Framework usa versões diferentes dessas bibliotecas de suporte para evitar o uso de tipos e recursos de idioma não encontrados nos dispositivos.  
  
> [!NOTE]
> A opção `-sdkpath` não está disponível no ambiente de desenvolvimento do Visual Studio; Ele está disponível somente durante a compilação na linha de comando. A opção `-sdkpath` é definida quando um projeto de dispositivo Visual Basic é carregado.  
  
 Você pode especificar que o compilador deve compilar sem uma referência para a biblioteca de tempo de execução Visual Basic usando a opção de compilador `-vbruntime`. Para obter mais informações, consulte [-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md).  
  
## <a name="example"></a>Exemplo  
 O código a seguir compila `Myfile.vb` com o .NET Compact Framework, usando as versões de mscorlib. dll e Microsoft. VisualBasic. dll encontrados no diretório de instalação padrão do .NET Compact Framework na unidade C. Normalmente, você usaria a versão mais recente do .NET Compact Framework.  
  
```console
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a>Consulte também

- [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md)
- [-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)
