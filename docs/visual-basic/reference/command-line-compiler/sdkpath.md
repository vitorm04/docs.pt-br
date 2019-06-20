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
ms.openlocfilehash: 91f64756b2fbf14dc96550420cd936973e6bec87
ms.sourcegitcommit: 4c41ec195caf03d98b7900007c3c8e24eba20d34
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/20/2019
ms.locfileid: "67268299"
---
# <a name="-sdkpath"></a>-sdkpath
Especifica o local de mscorlib. dll e VisualBasic.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
-sdkpath:path  
```  
  
## <a name="arguments"></a>Arguments  
 `path`  
 O diretório que contém as versões de mscorlib. dll e VisualBasic a ser usado para compilação. Esse caminho não é verificado até que ele seja carregado. Coloque o nome do diretório entre aspas ("") se ele contiver um espaço.  
  
## <a name="remarks"></a>Comentários  
 Essa opção informa ao compilador do Visual Basic para carregar o mscorlib. dll e VisualBasic arquivos de um local não padrão. O `-sdkpath` opção foi projetada para ser usado com [- netcf](../../../visual-basic/reference/command-line-compiler/netcf.md). As versões diferentes do .NET Compact Framework usa dessas dar suporte a bibliotecas para evitar o uso de tipos e recursos de linguagem não encontrados nos dispositivos.  
  
> [!NOTE]
>  O `-sdkpath` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ele está disponível somente durante a compilação da linha de comando. O `-sdkpath` opção é definida quando um projeto de dispositivo do Visual Basic é carregado.  
  
 Você pode especificar que o compilador deve compilar sem uma referência à biblioteca de tempo de execução do Visual Basic usando o `-vbruntime` opção de compilador. Para obter mais informações, consulte [- vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md).  
  
## <a name="example"></a>Exemplo  
 O seguinte código compila `Myfile.vb` com o .NET Compact Framework, usando as versões de mscorlib. dll e VisualBasic seja localizado no diretório de instalação padrão do .NET Compact Framework na unidade C. Normalmente, você poderia usar a versão mais recente do .NET Compact Framework.  
  
```console
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a>Consulte também

- [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md)
- [-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)
