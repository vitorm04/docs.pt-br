---
title: ParamArray (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.ParamArray
- ParamArray
dev_langs:
- VB
helpviewer_keywords:
- ParamArray keyword
- ParamArray keyword, syntax
ms.assetid: a5f18789-92bd-488f-9c7e-cf3719963635
caps.latest.revision: 15
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
ms.openlocfilehash: 10475410eb430b9750d4a5a4eea2c9ef7011d49c
ms.lasthandoff: 03/13/2017

---
# <a name="paramarray-visual-basic"></a>ParamArray (Visual Basic)
Especifica que um parâmetro de procedimento leva uma matriz opcional de elementos do tipo especificado. `ParamArray`pode ser usado apenas no último parâmetro de uma lista de parâmetros.  
  
## <a name="remarks"></a>Comentários  
 `ParamArray`permite que você passe um número arbitrário de argumentos para o procedimento. A `ParamArray` parâmetro sempre é declarado usando [ByVal](../../../visual-basic/language-reference/modifiers/byval.md).  
  
 Você pode fornecer um ou mais argumentos para um `ParamArray` , passando uma matriz de dados apropriados tipo de parâmetro, uma lista separada por vírgulas de valores ou nada todo. Para obter detalhes, consulte "Chamada de ParamArray" [matrizes de parâmetros](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).  
  
> [!IMPORTANT]
>  Sempre que você lida com uma matriz que pode ser indefinidamente grande, há um risco de ultrapassar alguma capacidade interna de seu aplicativo. Se você aceitar uma matriz de parâmetros do código de chamada, você deve testar seu tamanho e tomar as medidas adequadas se ele for muito grande para seu aplicativo.  
  
 O `ParamArray` modificador pode ser usado nesses contextos:  
  
 [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Consulte também  
 [Palavras-chave](../../../visual-basic/language-reference/keywords/index.md)   
 [Matrizes de Parâmetros](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)
