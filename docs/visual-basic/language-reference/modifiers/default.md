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
ms.openlocfilehash: f78ffe42a9d618d44da2a50c0de831396576430c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61800926"
---
# <a name="default-visual-basic"></a>Padrão (Visual Basic)
Identifica uma propriedade como a propriedade padrão de sua classe, estrutura ou interface.  
  
## <a name="remarks"></a>Comentários  
 Uma classe, estrutura ou interface pode designar no máximo uma de suas propriedades como o *propriedade padrão*, desde que a propriedade tem pelo menos um parâmetro. Se o código faz referência a uma classe ou estrutura sem especificar um membro, o Visual Basic resolve essa referência para a propriedade padrão.  
  
 As propriedades padrão podem resultar em uma pequena redução nos caracteres de código fonte, mas eles podem tornar seu código mais difícil de ler. Se o código de chamada não estiver familiarizado com a sua classe ou estrutura, quando ele faz referência ao nome de classe ou estrutura não poderá determinar se essa referência acessa a classe ou estrutura em si ou uma propriedade padrão. Isso pode levar a erros de compilador ou erros de lógica de tempo de execução sutis.  
  
 Você tanto pode reduzir a chance de erros de propriedade padrão sempre usando o [instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md) para definir o tipo de compilador verificando para `On`.  
  
 Se você estiver planejando usar uma classe ou estrutura predefinidas no seu código, você deve determinar se ele tem uma propriedade padrão e nesse caso, o que seu nome é.  
  
 Por causa dessas desvantagens, você deve considerar não definir as propriedades padrão. Para facilitar a leitura do código, você deve também considerar sempre referir-se a todas as propriedades explicitamente, mesmo propriedades padrão.  
  
 O `Default` modificador pode ser usado neste contexto:  
  
 [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a>Consulte também

- [Como: Declarar e chamar uma propriedade padrão no Visual Basic](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)
- [Palavras-chave](../../../visual-basic/language-reference/keywords/index.md)
