---
title: "Nome de arquivo inválido ou número | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID52
dev_langs:
- VB
ms.assetid: d0e96aea-7621-48f6-a78b-5d37d18aaa4e
caps.latest.revision: 10
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
ms.openlocfilehash: 30b9b1ee583f93a9228aa63a1b086a4b064ad9a0
ms.lasthandoff: 03/13/2017

---
# <a name="bad-file-name-or-number"></a>Nome ou número de arquivo inválido
Ocorreu um erro ao tentar acessar o arquivo especificado. Entre as possíveis causas para esse erro são:  
  
-   Uma instrução refere-se a um arquivo com um nome de arquivo ou um número que não foi especificado no `FileOpen` instrução ou que foi especificado em um `FileOpen` instrução, mas foi subsequentemente fechado.  
  
-   Uma instrução refere-se a um arquivo com um número que está fora do intervalo de números de arquivos.  
  
-   Uma instrução refere-se a um nome de arquivo ou o número não é válido.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Verifique se o nome do arquivo especificado em um `FileOpen` instrução. Observe que, se você chamou o `FileClose` instrução sem argumentos, você pode ter fechado todos os arquivos abertos.  
  
2.  Se seu código está gerando números de arquivo algorítmica, verifique se que os números são válidos.  
  
3.  Verifique os nomes de arquivo para se certificar de que estejam em conformidade com as convenções do sistema operacional.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A></xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>   
 [Convenções de nomenclatura do Visual Basic](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
