---
title: "Padrão (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Default
helpviewer_keywords:
- defaults, properties
- properties [Visual Basic], default
- default properties, in Visual Basic
- Default keyword [Visual Basic]
- default properties
ms.assetid: 45fce9b9-d212-4b2d-ab86-6e359b8b57af
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 18126a0a5b6254da0b43e806b3de1f5b2127e6a9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
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
