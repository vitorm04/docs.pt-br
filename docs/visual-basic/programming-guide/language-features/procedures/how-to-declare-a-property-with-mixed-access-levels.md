---
title: Como declarar uma propriedade com níveis de acesso mistos
ms.date: 07/20/2015
helpviewer_keywords:
- access levels [Visual Basic], properties
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- mixed access levels
- Visual Basic code, properties
- properties [Visual Basic], access levels
- Property statement [Visual Basic], declaring mixed access levels
ms.assetid: fdbb2d97-279a-4956-b26c-cbdfbc34915a
ms.openlocfilehash: d74e23f33fbf7d9d29ab84b9b1bd4fc08863ac48
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349691"
---
# <a name="how-to-declare-a-property-with-mixed-access-levels-visual-basic"></a>Como declarar uma propriedade com níveis de acesso mistos (Visual Basic)
Se desejar que os procedimentos `Get` e `Set` em uma propriedade tenham níveis de acesso diferentes, você poderá usar o nível mais permissivo na instrução `Property` e o nível mais restritivo na instrução `Get` ou `Set`. Você usa níveis de acesso misto em uma propriedade quando você quer que determinadas partes do código possam obter o valor da propriedade e algumas outras partes do código possam alterar o valor.  
  
 Para obter mais informações sobre níveis de acesso, consulte [níveis de acesso em Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
### <a name="to-declare-a-property-with-mixed-access-levels"></a>Para declarar uma propriedade com níveis de acesso mistos  
  
1. Declare a propriedade da maneira normal e especifique o nível de acesso menos restritivo (como `Public`) na instrução `Property`.  
  
2. Declare o `Get` ou o procedimento `Set` especificando o nível de acesso mais restritivo (como `Friend`).  
  
3. Não especifique um nível de acesso no outro procedimento de propriedade. Ele assume o nível de acesso declarado na instrução `Property`. Você pode restringir o acesso em apenas um dos procedimentos de propriedade.  
  
     [!code-vb[VbVbcnProcedures#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#10)]  
  
     No exemplo anterior, o procedimento `Get` tem o mesmo acesso `Protected` que a própria propriedade, enquanto o procedimento `Set` tem acesso `Private`. Uma classe derivada de `employee` pode ler o valor de `salary`, mas apenas a classe `employee` pode defini-la.  
  
## <a name="see-also"></a>Consulte também

- [Procedimentos](./index.md)
- [Procedimentos de Propriedade](./property-procedures.md)
- [Parâmetros e Argumentos de Procedimento](./procedure-parameters-and-arguments.md)
- [Instrução Property](../../../../visual-basic/language-reference/statements/property-statement.md)
- [Diferenças entre propriedades e variáveis no Visual Basic](./differences-between-properties-and-variables.md)
- [Como criar uma propriedade](./how-to-create-a-property.md)
- [Como chamar um procedimento de propriedade](./how-to-call-a-property-procedure.md)
- [Como: declarar e chamar uma propriedade padrão no Visual Basic](./how-to-declare-and-call-a-default-property.md)
- [Como inserir um valor em uma propriedade](./how-to-put-a-value-in-a-property.md)
- Como obter um valor de uma propriedade (Visual Basic)[Como obter um valor de uma propriedade](./how-to-get-a-value-from-a-property.md)
