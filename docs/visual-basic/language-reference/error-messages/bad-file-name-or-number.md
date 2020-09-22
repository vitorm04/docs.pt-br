---
title: Nome ou número de arquivo inválido
ms.date: 07/20/2015
f1_keywords:
- vbrID52
ms.assetid: d0e96aea-7621-48f6-a78b-5d37d18aaa4e
ms.openlocfilehash: d57a9e78e6ae179d3050e5a92399ca731fa16ba7
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874896"
---
# <a name="bad-file-name-or-number"></a>Nome ou número de arquivo inválido

Ocorreu um erro ao tentar acessar o arquivo especificado. Entre as possíveis causas desse erro estão:  
  
- Uma instrução refere-se a um arquivo com um nome de arquivo ou número que não foi especificado na `FileOpen` instrução ou que foi especificado em uma `FileOpen` instrução, mas foi fechado posteriormente.  
  
- Uma instrução refere-se a um arquivo com um número que está fora do intervalo de números de arquivo.  
  
- Uma instrução refere-se a um nome de arquivo ou número que não é válido.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1. Verifique se o nome do arquivo está especificado em uma `FileOpen` instrução. Observe que, se você chamou a `FileClose` instrução sem argumentos, você pode ter fechado inadvertidamente todos os arquivos abertos.  
  
2. Se o seu código estiver gerando números de arquivo forma algorítmica, verifique se os números são válidos.  
  
3. Verifique os nomes dos arquivos para garantir que eles estejam em conformidade com as convenções do sistema operacional.  
  
## <a name="see-also"></a>Confira também

- <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
- [Convenções de nomenclatura do Visual Basic](../../programming-guide/program-structure/naming-conventions.md)
