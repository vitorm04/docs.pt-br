---
title: Nome ou número de arquivo inválido
ms.date: 07/20/2015
f1_keywords:
- vbrID52
ms.assetid: d0e96aea-7621-48f6-a78b-5d37d18aaa4e
ms.openlocfilehash: 903be68e71ad590b4b669545afd077175534ef4d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="bad-file-name-or-number"></a>Nome ou número de arquivo inválido
Ocorreu um erro ao tentar acessar o arquivo especificado. Entre as causas possíveis desse erro são:  
  
-   Uma declaração se refere a um arquivo com um nome de arquivo ou um número que não foi especificado no `FileOpen` instrução ou que foi especificado em um `FileOpen` instrução, mas foi subsequentemente fechado.  
  
-   Uma instrução refere-se a um arquivo com um número que está fora do intervalo de números de arquivos.  
  
-   Uma instrução faz referência a um nome de arquivo ou um número que não é válido.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Verifique se o nome do arquivo especificado em um `FileOpen` instrução. Observe que, se você chamou o `FileClose` instrução sem argumentos, você talvez tenha fechado todos os arquivos abertos.  
  
2.  Se seu código está gerando números de arquivos de maneira algorítmica, verifique se que os números são válidos.  
  
3.  Verifique os nomes de arquivo para garantir que estejam em conformidade com as convenções do sistema operacional.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>  
 [Convenções de nomenclatura do Visual Basic](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
