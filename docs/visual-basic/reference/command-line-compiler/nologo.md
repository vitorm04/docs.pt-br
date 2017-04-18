---
title: /nologo (Visual Basic) | Documentos do Microsoft
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
- -nologo compiler option [Visual Basic]
- banners, suppressing startup
- nologo compiler option [Visual Basic]
- /nologo compiler option [Visual Basic]
ms.assetid: 25ef54b6-d676-4639-a2d2-a747a158bc07
caps.latest.revision: 16
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
ms.openlocfilehash: a0e309a80082f19fb47ccbbb43c00f22c8addd3b
ms.lasthandoff: 03/13/2017

---
# <a name="nologo-visual-basic"></a>/nologo (Visual Basic)
Suprime a exibição da faixa de direitos autorais e mensagens informativas durante a compilação.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
/nologo  
```  
  
## <a name="remarks"></a>Comentários  
 Se você especificar `/nologo`, o compilador não exibirá uma faixa de direitos autorais. Por padrão, `/nologo` não está em vigor.  
  
> [!NOTE]
>  O `/nologo` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ele está disponível apenas quando se compila da linha de comando.  
  
## <a name="example"></a>Exemplo  
 O seguinte código compila `T2.vb` e não exibe uma faixa de direitos autorais.  
  
```  
vbc /nologo t2.vb  
```  
  
## <a name="see-also"></a>Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
