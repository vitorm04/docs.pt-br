---
title: Padrão (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Default
helpviewer_keywords:
- defaults, properties
- properties [Visual Basic], default
- default properties, in Visual Basic
- Default keyword [Visual Basic]
- default properties
ms.assetid: 45fce9b9-d212-4b2d-ab86-6e359b8b57af
ms.openlocfilehash: 555e15110c7af501de05d1f395a72ca4b7800054
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33595129"
---
# <a name="default-visual-basic"></a>Padrão (Visual Basic)
Identifica uma propriedade como a propriedade padrão de sua classe, estrutura ou interface.  
  
## <a name="remarks"></a>Comentários  
 Uma classe, estrutura ou interface pode designar no máximo uma de suas propriedades como o *propriedade padrão*, desde que a propriedade tem pelo menos um parâmetro. Se o código faz referência a uma classe ou estrutura sem especificar um membro, Visual Basic toma essa referência para a propriedade padrão.  
  
 Propriedades padrão podem resultar em uma pequena redução nos caracteres de código fonte, mas eles podem tornar o seu código mais difícil de ler. Se o código de chamada não está familiarizado com sua classe ou estrutura, quando ele faz referência ao nome de classe ou estrutura não poderá determinar se essa referência acessa a classe ou estrutura em si ou uma propriedade padrão. Isso pode levar a erros de compilador ou erros de lógica de tempo de execução sutis.  
  
 Você tanto pode reduzir a chance de erros de propriedade padrão sempre usando o [instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md) para definir o tipo de compilador verificação `On`.  
  
 Se você estiver planejando usar uma classe ou estrutura predefinidas no seu código, você deve determinar se ela tem uma propriedade padrão e nesse caso, o que seu nome é.  
  
 Devido a essas desvantagens, você deve considerar não definir as propriedades padrão. Para a legibilidade do código, você deve também considerar sempre referir-se a todas as propriedades explicitamente, mesmo propriedades padrão.  
  
 O `Default` modificador pode ser usado neste contexto:  
  
 [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a>Consulte também  
 [Como: declarar e chamar uma propriedade padrão no Visual Basic](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)  
 [Palavras-chave](../../../visual-basic/language-reference/keywords/index.md)
