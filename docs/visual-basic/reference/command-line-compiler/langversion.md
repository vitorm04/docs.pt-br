---
title: -langversion (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- /langversion compiler option [Visual Basic]
- langversion compiler option [Visual Basic]
- -langversion compiler option [Visual Basic]
ms.assetid: 59b7b0c8-2dde-4e9b-94e7-0237f7e0bafb
ms.openlocfilehash: 82a7114027451d1342e6dc0846799933ce44d968
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="-langversion-visual-basic"></a>-langversion (Visual Basic)
Faz com que o compilador aceitar somente a sintaxe que está incluída na versão de idioma especificado do Visual Basic.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
-langversion:version  
```  
  
## <a name="arguments"></a>Arguments  
 `version`  
 Necessário. A versão do idioma a ser usado durante a compilação. Os valores aceitos são `9`, `9.0`, `10`, e `10.0`.  
  
## <a name="remarks"></a>Comentários  
 O `-langversion` opção especifica que o compilador aceita de sintaxe. Por exemplo, se você especificar que a versão de idioma é 9.0, o compilador gera erros de sintaxe que é válido somente na versão 10.0 e posterior.  
  
 Você pode usar essa opção ao desenvolver aplicativos que destino as diferentes versões do .NET Framework. Por exemplo, se você estiver direcionando o .NET Framework 3.5, você pode usar essa opção para garantir que você não use a sintaxe da versão de idioma 10.0.  
  
 Você pode definir `-langversion` diretamente usando a linha de comando. Para obter mais informações, consulte [Definindo uma Versão Específica do .NET Framework como Destino](/visualstudio/ide/targeting-a-specific-dotnet-framework-version).  
  
## <a name="example"></a>Exemplo  
 O código a seguir compila `sample.vb` para o Visual Basic 9.0.  
  
```console  
vbc -langversion:9.0 sample.vb  
```  
  
## <a name="see-also"></a>Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [Direcionamento de uma versão específica do .NET Framework](/visualstudio/ide/targeting-a-specific-dotnet-framework-version)
