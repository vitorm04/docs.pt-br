---
title: Conversão implícita de '<typename1>' em '<typename2>' ao copiar o valor do parâmetro 'ByRef' '<parametername>' para o argumento correspondente.
ms.date: 07/20/2015
f1_keywords:
- vbc41999
- bc41999
helpviewer_keywords:
- BC41999
ms.assetid: ae48c738-dff8-4c0f-8931-bbb70b2c8b03
ms.openlocfilehash: f875206b15ee048311e43624e197e78413de522e
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55279611"
---
# <a name="implicit-conversion-from-typename1-to-typename2-in-copying-the-value-of-byref-parameter-parametername-back-to-the-matching-argument"></a>Conversão implícita de '\<typename1 >' para '\<typename2 >' ao copiar o valor do parâmetro 'ByRef' '\<parametername >' para o argumento correspondente.
Um procedimento é chamado com um [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) argumento de um tipo diferente do seu parâmetro correspondente.  
  
 Se você passar um argumento `ByRef`, Visual Basic, às vezes, copia o valor do argumento para uma variável local no procedimento em vez de passar uma referência. Nesse caso, quando o procedimento retorna, Visual Basic deve, em seguida, copie o valor da variável local volta para o argumento no código de chamada.  
  
 Se um `ByRef` o valor do argumento é copiado para o procedimento e o argumento e o parâmetro são do mesmo tipo, nenhuma conversão é necessária. Mas se os tipos forem diferentes, o Visual Basic deve converter em ambas as direções. Porque você não pode usar `CType` ou qualquer um dos outras conversão palavras-chave em um argumento de procedimento ou parâmetro, essa conversão é sempre implícita.  
  
 Por padrão, esta mensagem é um aviso. Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID do erro:** BC41999  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Se possível, use um argumento de chamada do mesmo tipo como o parâmetro de procedimento, portanto, o Visual Basic não precisa fazer nenhuma conversão.  
  
-   Se você precisar chamar o procedimento com um argumento de tipo diferente do tipo de parâmetro, mas não precisa retornar um valor para o argumento de chamada, defina o parâmetro para ser [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) em vez de `ByRef`.  
  
## <a name="see-also"></a>Consulte também
- [Procedimentos](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [Parâmetros e Argumentos de Procedimento](../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)
- [Passando Argumentos por Valor e por Referência](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
- [Conversões Implícitas e Explícitas](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
