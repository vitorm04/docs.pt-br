---
title: /sdkpath | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- sdkpath
- /sdkpath
dev_langs:
- VB
helpviewer_keywords:
- -sdkpath compiler option [Visual Basic]
- /sdkpath compiler option [Visual Basic]
- sdkpath compiler option [Visual Basic]
ms.assetid: fec8a3f1-b791-4a37-8af7-344859f8212d
caps.latest.revision: 15
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
ms.openlocfilehash: 3584daa49bca699f022a1afd34e3d450b8442060
ms.lasthandoff: 03/13/2017

---
# <a name="sdkpath"></a>/sdkpath
Especifica o local de mscorlib. dll e Microsoft.VisualBasic.dll.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
/sdkpath:path  
```  
  
## <a name="arguments"></a>Arguments  
 `path`  
 O diretório que contém as versões de mscorlib. dll e Microsoft.VisualBasic.dll para usar para a compilação. Esse caminho não é verificado até que ele seja carregado. Coloque o nome do diretório entre aspas ("") se ele contiver um espaço.  
  
## <a name="remarks"></a>Comentários  
 Essa opção informa o [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilador para carregar os arquivos de mscorlib. dll e Microsoft.VisualBasic.dll de um local não padrão. O `/sdkpath` opção foi projetada para ser usado com [/netcf](../../../visual-basic/reference/command-line-compiler/netcf.md). O [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)] usa versões diferentes desses oferece suporte a bibliotecas para evitar o uso de tipos e recursos de linguagem não encontrados nos dispositivos.  
  
> [!NOTE]
>  O `/sdkpath` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ele está disponível apenas quando se compila da linha de comando. O `/sdkpath` opção é definida quando um [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] dispositivo projeto é carregado.  
  
 Você pode especificar que o compilador deve compilar sem uma referência à biblioteca de tempo de execução do Visual Basic usando o `/vbruntime` opção de compilador. Para obter mais informações, consulte [/vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md).  
  
## <a name="example"></a>Exemplo  
 O seguinte código compila `Myfile.vb` com o [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)], usar as versões de mscorlib. dll e Microsoft.VisualBasic.dll encontrado no diretório de instalação padrão do [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)] na unidade C. Normalmente, você poderia usar a versão mais recente do [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)].  
  
```  
vbc /netcf /sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a>Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Exemplos de linhas de comando de compilação](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [/netcf](../../../visual-basic/reference/command-line-compiler/netcf.md)   
 [/vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)
