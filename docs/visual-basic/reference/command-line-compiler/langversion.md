---
title: /langversion (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- /langversion compiler option [Visual Basic]
- langversion compiler option [Visual Basic]
- -langversion compiler option [Visual Basic]
ms.assetid: 59b7b0c8-2dde-4e9b-94e7-0237f7e0bafb
caps.latest.revision: 8
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: 9970df0c9babc368210169fae0490b423d77f40d
ms.lasthandoff: 03/13/2017

---
# <a name="langversion-visual-basic"></a>/langversion (Visual Basic)
Faz com que o compilador aceitar somente a sintaxe que está incluído na versão do idioma especificado do Visual Basic.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
/langversion:version  
```  
  
## <a name="arguments"></a>Arguments  
 `version`  
 Necessário. A versão do idioma a ser usado durante a compilação. Os valores aceitos são `9`, `9.0`, `10`, e `10.0`.  
  
## <a name="remarks"></a>Comentários  
 O `/langversion` opção especifica qual sintaxe aceita o compilador. Por exemplo, se você especificar que a versão do idioma 9.0, o compilador gera erros de sintaxe que é válido somente na versão 10.0 e posteriores.  
  
 Você pode usar essa opção ao desenvolver aplicativos que destino as diferentes versões do .NET Framework. Por exemplo, se você estiver direcionando o .NET Framework 3.5, você pode usar esta opção para garantir que você não use a sintaxe da versão de idioma 10.0.  
  
 Você pode definir `/langversion` diretamente usando a linha de comando. Para obter mais informações, consulte [Definindo uma versão específica do .NET Framework como destino](https://docs.microsoft.com/visualstudio/ide/targeting-a-specific-dotnet-framework-version).  
  
## <a name="example"></a>Exemplo  
 O seguinte código compila `sample.vb` para o Visual Basic 9.0.  
  
```  
vbc /langversion:9.0 sample.vb  
```  
  
## <a name="see-also"></a>Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Exemplos de linhas de comando de compilação](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [Direcionamento de uma versão específica do .NET Framework](https://docs.microsoft.com/visualstudio/ide/targeting-a-specific-dotnet-framework-version)
