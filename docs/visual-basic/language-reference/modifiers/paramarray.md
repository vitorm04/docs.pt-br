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
ms.openlocfilehash: 8fc5d1afd9e9723e6b3c58e100b0519ef8fdfab4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968369"
---
# <a name="paramarray-visual-basic"></a>ParamArray (Visual Basic)
Especifica que um parâmetro de procedimento usa uma matriz opcional de elementos do tipo especificado. `ParamArray`pode ser usado somente no último parâmetro de uma lista de parâmetros.  
  
## <a name="remarks"></a>Comentários  
 `ParamArray`permite que você passe um número arbitrário de argumentos para o procedimento. Um `ParamArray` parâmetro é sempre declarado usando [ByVal](../../../visual-basic/language-reference/modifiers/byval.md).  
  
 Você pode fornecer um ou mais argumentos a um `ParamArray` parâmetro passando uma matriz do tipo de dados apropriado, uma lista de valores separados por vírgula ou nada. Para obter detalhes, consulte "chamando um ParamArray" em matrizes de [parâmetros](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).  
  
> [!IMPORTANT]
> Sempre que você lida com uma matriz que pode ser indefinidamente grande, há um risco de sobreexecutar alguma capacidade interna de seu aplicativo. Se você aceitar uma matriz de parâmetros do código de chamada, deverá testar seu comprimento e tomar as medidas apropriadas se for muito grande para seu aplicativo.  
  
 O `ParamArray` modificador pode ser usado nesses contextos:  
  
 [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Consulte também

- [Palavras-chave](../../../visual-basic/language-reference/keywords/index.md)
- [Matrizes de Parâmetros](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)
