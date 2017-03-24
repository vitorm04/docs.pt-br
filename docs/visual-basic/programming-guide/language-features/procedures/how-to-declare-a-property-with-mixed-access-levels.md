---
title: "Como: declarar uma propriedade com níveis de acesso mistos (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- access levels, properties
- procedures, defining
- Visual Basic code, procedures
- mixed access levels
- Visual Basic code, properties
- properties [Visual Basic], access levels
- Property statement, declaring mixed access levels
ms.assetid: fdbb2d97-279a-4956-b26c-cbdfbc34915a
caps.latest.revision: 16
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: 8672427cb09c52610649572d6e4e5f68e179cdb8
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-declare-a-property-with-mixed-access-levels-visual-basic"></a>Como declarar uma propriedade com níveis de acesso mistos (Visual Basic)
Se você quiser que o `Get` e `Set` procedimentos de uma propriedade ter diferentes níveis de acesso, você pode usar o nível mais permissivo no `Property` instrução e o nível mais restritivo no `Get` ou `Set` instrução. Você pode usar níveis de acesso mistos em uma propriedade certas partes do código para ser capaz de obter o valor da propriedade e determinadas outras partes do código para poder alterar o valor.  
  
 Para obter mais informações sobre níveis de acesso, consulte [níveis de acesso no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
### <a name="to-declare-a-property-with-mixed-access-levels"></a>Para declarar uma propriedade com níveis de acesso mistos  
  
1.  Declare a propriedade da forma normal e especificar o nível de acesso menos restritivo (como `Public`) no `Property` instrução.  
  
2.  Declare o `Get` ou `Set` procedimento especificando o nível de acesso mais restritivo (como `Friend`).  
  
3.  Não especifica um nível de acesso em outro procedimento de propriedade. Ele pressupõe que o nível de acesso declarado no `Property` instrução. Você pode restringir o acesso em apenas um dos procedimentos de propriedade.  
  
     [!code-vb[VbVbcnProcedures n º&10;](./codesnippet/VisualBasic/how-to-declare-a-property-with-mixed-access-levels_1.vb)]  
  
     No exemplo anterior, o `Get` procedimento tem o mesmo `Protected` acesso que a própria propriedade, enquanto o `Set` procedimento tem `Private` acesso. Uma classe derivada de `employee` pode ler o `salary` valor, mas apenas o `employee` classe pode defini-lo.  
  
## <a name="see-also"></a>Consulte também  
 [Procedimentos](./index.md)   
 [Procedimentos de propriedade](./property-procedures.md)   
 [Argumentos e parâmetros de procedimento](./procedure-parameters-and-arguments.md)   
 [Instrução Property](../../../../visual-basic/language-reference/statements/property-statement.md)   
 [Diferenças entre propriedades e variáveis no Visual Basic](./differences-between-properties-and-variables.md)   
 [Como: criar uma propriedade](./how-to-create-a-property.md)   
 [Como: chamar um procedimento de propriedade](./how-to-call-a-property-procedure.md)   
 [Como: declarar e chamar uma propriedade padrão no Visual Basic](./how-to-declare-and-call-a-default-property.md)   
 [Como: inserir um valor em uma propriedade](./how-to-put-a-value-in-a-property.md)   
Como obter um valor de uma propriedade (Visual Basic) [Como obter um valor de uma propriedade](./how-to-get-a-value-from-a-property.md)
