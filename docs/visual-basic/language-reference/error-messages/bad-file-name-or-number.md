---
title: Nome ou número de arquivo inválido
ms.date: 07/20/2015
f1_keywords:
- vbrID52
ms.assetid: d0e96aea-7621-48f6-a78b-5d37d18aaa4e
ms.openlocfilehash: c57f431350d4f63507ee7374616b62ca32151c86
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54639400"
---
# <a name="bad-file-name-or-number"></a>Nome ou número de arquivo inválido
Ocorreu um erro ao tentar acessar o arquivo especificado. Entre as causas possíveis desse erro são:  
  
-   Uma declaração se refere a um arquivo com um nome de arquivo ou um número que não foi especificado no `FileOpen` instrução ou que foi especificado em um `FileOpen` instrução, mas foi subsequentemente fechado.  
  
-   Uma declaração se refere a um arquivo com um número que está fora do intervalo de números de arquivos.  
  
-   Uma declaração se refere a um nome de arquivo ou um número que não é válido.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Verifique se o nome do arquivo é especificado em um `FileOpen` instrução. Observe que, se você chamou o `FileClose` instrução sem argumentos, você talvez tenha fechado todos os arquivos abertos.  
  
2.  Se seu código está gerando números de arquivo de forma algorítmica, verifique se que os números são válidos.  
  
3.  Verifique os nomes de arquivo para certificar-se de que eles estão em conformidade com as convenções do sistema operacional.  
  
## <a name="see-also"></a>Consulte também
- <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
- [Convenções de nomenclatura do Visual Basic](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
