---
title: Parâmetros de método (Referência de C#)
ms.date: 07/20/2015
helpviewer_keywords:
- methods [C#], parameters
- method parameters [C#]
- parameters [C#]
ms.assetid: 680e39ff-775b-48b0-9f47-4186a5bfc4a1
ms.openlocfilehash: 8a8d300661eec42030900dd9ee85a17e66aa0922
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33269340"
---
# <a name="method-parameters-c-reference"></a>Parâmetros de método (Referência de C#)

Os parâmetros declarados para um método sem [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md) nem [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) são passados para o método chamado pelo valor. Esse valor pode ser alterado no método, mas o valor alterado não será mantido quando o controle passá-lo de volta para o procedimento de chamada. É possível alterar esse comportamento usando uma palavra-chave de parâmetro de método.  
  
 Esta seção descreve as palavras-chave que podem ser usadas ao declarar parâmetros de método:  
  
-   [params](../../../csharp/language-reference/keywords/params.md) especifica que esse parâmetro pode receber um número variável de argumentos.
  
-   [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md) especifica que esse parâmetro é passado por referência, mas é lido apenas pelo método chamado.
  
-   [ref](../../../csharp/language-reference/keywords/ref.md) especifica que esse parâmetro é passado por referência e pode ser lido ou gravado pelo método chamado.
  
-   [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) especifica que esse parâmetro é passado por referência e é gravado pelo método chamado.
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Palavras-chave do C#](../../../csharp/language-reference/keywords/index.md)
