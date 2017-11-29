---
title: "Como declarar uma propriedade com níveis de acesso mistos (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- access levels [Visual Basic], properties
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- mixed access levels
- Visual Basic code, properties
- properties [Visual Basic], access levels
- Property statement [Visual Basic], declaring mixed access levels
ms.assetid: fdbb2d97-279a-4956-b26c-cbdfbc34915a
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 90fe20303f6f2ed692e54e44ee8cc65897531543
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-declare-a-property-with-mixed-access-levels-visual-basic"></a>Como declarar uma propriedade com níveis de acesso mistos (Visual Basic)
Se você quiser que o `Get` e `Set` procedimentos em uma propriedade com diferentes níveis de acesso, você pode usar o nível mais permissivo no `Property` instrução e o nível mais restritivo no `Get` ou `Set` instrução. Você pode usar níveis de acesso mistos em uma propriedade quando você deseja determinadas partes do código para ser capaz de obter o valor da propriedade e determinadas outras partes do código para ser capaz de alterar o valor.  
  
 Para obter mais informações sobre níveis de acesso, consulte [acessar níveis no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
### <a name="to-declare-a-property-with-mixed-access-levels"></a>Para declarar uma propriedade com níveis de acesso mistos  
  
1.  Declarar a propriedade da maneira normal e especificar o nível de acesso menos restritivo (como `Public`) no `Property` instrução.  
  
2.  Declare o o `Get` ou `Set` procedimento especificando o nível de acesso mais restritivo (como `Friend`).  
  
3.  Não especifique um nível de acesso em outro procedimento de propriedade. Ele pressupõe que o nível de acesso declarado no `Property` instrução. Você pode restringir o acesso em apenas um dos procedimentos de propriedade.  
  
     [!code-vb[VbVbcnProcedures#10](./codesnippet/VisualBasic/how-to-declare-a-property-with-mixed-access-levels_1.vb)]  
  
     No exemplo anterior, o `Get` procedimento tem o mesmo `Protected` acesso da propriedade, enquanto o `Set` procedimento tem `Private` acesso. Uma classe derivada de `employee` pode ler o `salary` valor, mas apenas o `employee` classe pode defini-lo.  
  
## <a name="see-also"></a>Consulte também  
 [Procedimentos](./index.md)  
 [Procedimentos de Propriedade](./property-procedures.md)  
 [Parâmetros e Argumentos de Procedimento](./procedure-parameters-and-arguments.md)  
 [Instrução Property](../../../../visual-basic/language-reference/statements/property-statement.md)  
 [Diferenças entre propriedades e variáveis no Visual Basic](./differences-between-properties-and-variables.md)  
 [Como criar uma propriedade](./how-to-create-a-property.md)  
 [Como chamar um procedimento de propriedade](./how-to-call-a-property-procedure.md)  
 [Como: declarar e chamar uma propriedade padrão no Visual Basic](./how-to-declare-and-call-a-default-property.md)  
 [Como inserir um valor em uma propriedade](./how-to-put-a-value-in-a-property.md)  
 Como obter um valor de uma propriedade (Visual Basic)[Como obter um valor de uma propriedade](./how-to-get-a-value-from-a-property.md)
