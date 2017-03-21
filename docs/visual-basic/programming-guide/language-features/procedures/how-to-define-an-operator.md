---
title: 'Como: definir um operador (Visual Basic) | Documentos do Microsoft'
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
- procedures, defining
- Visual Basic code, procedures
- operators [Visual Basic], defining
- procedures, operator
- Visual Basic code, operators
- syntax, Operator procedures
- operators [Visual Basic], overloading
- operator procedures, about operator procedures
- return values, Operator procedures
- operator overloading
ms.assetid: d4b0e253-092a-4e6e-9fe2-01f562140a29
caps.latest.revision: 15
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
ms.openlocfilehash: a7b4634975468a91a1f9f3f829665143c1c1b77c
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-define-an-operator-visual-basic"></a>Como definir um operador (Visual Basic)
Se você tiver definido uma classe ou estrutura, você pode definir o comportamento de um operador padrão (como `*`, `<>`, ou `And`) quando um ou ambos os operandos é do tipo de sua classe ou estrutura.  
  
 Defina o operador padrão como um procedimento de operador dentro da classe ou estrutura. Todos os procedimentos de operador devem ser `Public` `Shared`.  
  
 Definir um operador em uma classe ou estrutura também é chamado *sobrecarga* o operador.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir define o `+` chamado de operador para uma estrutura `height`. A estrutura usa alturas medidas em pés e polegadas. Um *polegadas* é 2,54 centímetros e *pés* é 12 polegadas. Para garantir que os valores normalizados (polegadas < 12.0),="" the="" constructor="" performs=""> </> *módulo* 12 aritmética. O `+` operador usa o construtor para gerar valores normalizados.  
  
 [!code-vb[25 VbVbcnProcedures](./codesnippet/VisualBasic/how-to-define-an-operator_1.vb)]  
  
 Você pode testar a estrutura `height` com o código a seguir.  
  
 [!code-vb[VbVbcnProcedures&#26;](./codesnippet/VisualBasic/how-to-define-an-operator_2.vb)]  
  
 Para obter mais informações e exemplos, consulte [sobrecarga de operador no Visual Basic 2005](http://go.microsoft.com/fwlink/?LinkId=101703).  
  
## <a name="see-also"></a>Consulte também  
 [Procedimentos de operador](./operator-procedures.md)   
 [Como: definir um operador de conversão](./how-to-define-a-conversion-operator.md)   
 [Como: chamar um procedimento de operador](./how-to-call-an-operator-procedure.md)   
 [Como: usar uma classe que define operadores](./how-to-use-a-class-that-defines-operators.md)   
 [Instrução Operator](../../../../visual-basic/language-reference/statements/operator-statement.md)   
 [Instrução Structure](../../../../visual-basic/language-reference/statements/structure-statement.md)   
 [Como: declarar uma estrutura](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)   
 [Operador Mod](../../../../visual-basic/language-reference/operators/mod-operator.md)
