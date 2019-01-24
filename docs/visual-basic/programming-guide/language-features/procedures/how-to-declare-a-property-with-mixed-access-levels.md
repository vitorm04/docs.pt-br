---
title: 'Como: Declarar uma propriedade com níveis de acesso mistos (Visual Basic)'
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
ms.openlocfilehash: b10f679d735d21ba0002c8a3f4e230836298d4e1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54514251"
---
# <a name="how-to-declare-a-property-with-mixed-access-levels-visual-basic"></a>Como: Declarar uma propriedade com níveis de acesso mistos (Visual Basic)
Se você quiser que o `Get` e `Set` procedimentos de uma propriedade para ter diferentes níveis de acesso, você pode usar o nível mais permissivo na `Property` instrução e o nível mais restritivo em qualquer um os `Get` ou `Set` instrução. Você pode usar níveis de acesso mistos em uma propriedade quando você deseja certas partes do código para ser capaz de obter o valor da propriedade e determinadas outras partes do código para ser capaz de alterar o valor.  
  
 Para obter mais informações sobre níveis de acesso, consulte [acessar níveis no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
### <a name="to-declare-a-property-with-mixed-access-levels"></a>Para declarar uma propriedade com níveis de acesso mistos  
  
1.  Declarar a propriedade da maneira normal e especificar o nível de acesso menos restritivo (como `Public`) na `Property` instrução.  
  
2.  Declare a `Get` ou o `Set` procedimento especificando o nível de acesso mais restritivo (como `Friend`).  
  
3.  Não especifique um nível de acesso em outro procedimento de propriedade. Ele pressupõe que o nível de acesso declarado no `Property` instrução. Você pode restringir o acesso em apenas um dos procedimentos de propriedade.  
  
     [!code-vb[VbVbcnProcedures#10](./codesnippet/VisualBasic/how-to-declare-a-property-with-mixed-access-levels_1.vb)]  
  
     No exemplo anterior, o `Get` procedimento tem o mesmo `Protected` acesso como a própria propriedade, enquanto o `Set` procedimento tem `Private` acesso. Uma classe derivada de `employee` pode ler os `salary` valor, mas apenas o `employee` classe pode defini-lo.  
  
## <a name="see-also"></a>Consulte também
- [Procedimentos](./index.md)
- [Procedimentos de Propriedade](./property-procedures.md)
- [Parâmetros e Argumentos de Procedimento](./procedure-parameters-and-arguments.md)
- [Instrução Property](../../../../visual-basic/language-reference/statements/property-statement.md)
- [Diferenças entre propriedades e variáveis no Visual Basic](./differences-between-properties-and-variables.md)
- [Como: Criar uma propriedade](./how-to-create-a-property.md)
- [Como: Chamar um procedimento de propriedade](./how-to-call-a-property-procedure.md)
- [Como: Declarar e chamar uma propriedade padrão no Visual Basic](./how-to-declare-and-call-a-default-property.md)
- [Como: Inserir um valor em uma propriedade](./how-to-put-a-value-in-a-property.md)
- [Como: Obter um valor de uma propriedade](./how-to-get-a-value-from-a-property.md)
