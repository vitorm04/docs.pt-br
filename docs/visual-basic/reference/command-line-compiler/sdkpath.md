---
title: -sdkpath
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- sdkpath
- -sdkpath
helpviewer_keywords:
- -sdkpath compiler option [Visual Basic]
- /sdkpath compiler option [Visual Basic]
- sdkpath compiler option [Visual Basic]
ms.assetid: fec8a3f1-b791-4a37-8af7-344859f8212d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5a25755bcbb8d42124cde531f641a611202ae5a1
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="-sdkpath"></a>-sdkpath
Especifica o local de mscorlib. dll e Microsoft.VisualBasic.dll.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
-sdkpath:path  
```  
  
## <a name="arguments"></a>Arguments  
 `path`  
 O diretório que contém as versões de mscorlib. dll e Microsoft.VisualBasic.dll a ser usado para compilação. Esse caminho não é verificado até que ele seja carregado. Coloque o nome do diretório entre aspas ("") se ele contiver um espaço.  
  
## <a name="remarks"></a>Comentários  
 Essa opção informa ao compilador do Visual Basic para carregar o mscorlib.dll e Microsoft.VisualBasic.dll arquivos de um local diferente do padrão. O `-sdkpath` opção foi projetada para ser usado com [- netcf](../../../visual-basic/reference/command-line-compiler/netcf.md). O [!INCLUDE[Compact](~/includes/compact-md.md)] usa diferentes versões desses oferece suporte a bibliotecas para evitar o uso de tipos e recursos de idioma não encontrados nos dispositivos.  
  
> [!NOTE]
>  O `-sdkpath` opção não está disponível no ambiente de desenvolvimento do Visual Studio; está disponível somente quando estiver compilando na linha de comando. O `-sdkpath` opção é definida quando um projeto de dispositivo do Visual Basic é carregado.  
  
 Você pode especificar que o compilador deve compilar sem uma referência à biblioteca de tempo de execução do Visual Basic, usando o `-vbruntime` opção de compilador. Para obter mais informações, consulte [- vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md).  
  
## <a name="example"></a>Exemplo  
 O código a seguir compila `Myfile.vb` com o [!INCLUDE[Compact](~/includes/compact-md.md)], usando as versões de mscorlib. dll e Microsoft.VisualBasic.dll encontrado no diretório de instalação padrão do [!INCLUDE[Compact](~/includes/compact-md.md)] na unidade C. Normalmente, você poderia usar a versão mais recente do [!INCLUDE[Compact](~/includes/compact-md.md)].  
  
```console
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a>Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md)  
 [-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)
