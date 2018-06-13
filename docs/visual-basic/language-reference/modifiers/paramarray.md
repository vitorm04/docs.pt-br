---
title: ParamArray (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ParamArray
- ParamArray
helpviewer_keywords:
- ParamArray keyword [Visual Basic]
- ParamArray keyword [Visual Basic], syntax
ms.assetid: a5f18789-92bd-488f-9c7e-cf3719963635
ms.openlocfilehash: be8ddb7f9ba08535d12890d1c5c82a9b7b485f3d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33597354"
---
# <a name="paramarray-visual-basic"></a>ParamArray (Visual Basic)
Especifica que um parâmetro de procedimento leva uma matriz opcional de elementos do tipo especificado. `ParamArray` pode ser usado apenas no último parâmetro de uma lista de parâmetros.  
  
## <a name="remarks"></a>Comentários  
 `ParamArray` permite que você passe um número arbitrário de argumentos para o procedimento. Um `ParamArray` parâmetro sempre é declarado usando [ByVal](../../../visual-basic/language-reference/modifiers/byval.md).  
  
 Você pode fornecer um ou mais argumentos para um `ParamArray` parâmetro passando uma matriz dos dados apropriados tipo, uma lista separada por vírgulas de valores ou nada em todos os. Para obter detalhes, consulte "Chamada de ParamArray" [matrizes de parâmetro](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).  
  
> [!IMPORTANT]
>  Sempre que você lidar com uma matriz que pode ser indefinidamente grande, há um risco de ultrapassar alguma capacidade interna de seu aplicativo. Se você aceitar uma matriz de parâmetros de código de chamada, você deve testar seu tamanho e execute as etapas apropriadas se ele é muito grande para o seu aplicativo.  
  
 O `ParamArray` modificador pode ser usado nesses contextos:  
  
 [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Consulte também  
 [Palavras-chave](../../../visual-basic/language-reference/keywords/index.md)  
 [Matrizes de Parâmetros](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)
