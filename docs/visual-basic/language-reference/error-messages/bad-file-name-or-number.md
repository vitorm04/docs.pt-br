---
title: "Nome ou número de arquivo inválido"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID52
ms.assetid: d0e96aea-7621-48f6-a78b-5d37d18aaa4e
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3d7c8bae3df0e75a1c4f9afacdff681a553503d2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
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
