---
title: 'Como: Chamar um procedimento de propriedade (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- Visual Basic code, properties
- procedures [Visual Basic], calling
- properties [Visual Basic], property procedures
- procedure calls [Visual Basic], property procedures
ms.assetid: 96bc4d74-d9c3-4b7a-954d-58ac8553cd94
ms.openlocfilehash: 7b85239f80b4bfa87d1dbb1e3207e63d0cef7eeb
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58827205"
---
# <a name="how-to-call-a-property-procedure-visual-basic"></a>Como: Chamar um procedimento de propriedade (Visual Basic)
Para chamar um procedimento de propriedade, armazenar um valor na propriedade ou recuperar seu valor. Você acessa uma propriedade da mesma maneira que você acessa uma variável.  
  
 A propriedade `Set` procedimento armazena um valor e seu `Get` procedimento recupera o valor. No entanto, você chama explicitamente esses procedimentos por nome. Você usar a propriedade em uma instrução de atribuição ou uma expressão, assim como você poderia armazenar ou recuperar o valor de uma variável. O Visual Basic faz as chamadas para procedimentos da propriedade.  
  
### <a name="to-call-a-propertys-get-procedure"></a>Para chamar um procedimento da propriedade Get  
  
1.  Use o nome da propriedade em uma expressão da mesma maneira que você usaria um nome de variável. Você pode usar uma propriedade em qualquer lugar você pode usar uma variável ou uma constante.  
  
     - ou -  
  
     Use o nome de propriedade seguido de igual (`=`) entrar em uma instrução de atribuição.  
  
     O exemplo a seguir lê o valor da <xref:Microsoft.VisualBasic.DateAndTime.Now%2A> property, implicitamente chamando seu `Get` procedimento.  
  
     [!code-vb[VbVbalrDateProperties#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDateProperties/VB/Module1.vb#4)]  
  
2.  Se a propriedade utiliza argumentos, siga o nome da propriedade com parênteses para incluir a lista de argumentos. Se não houver nenhum argumento, você pode, opcionalmente, omitir os parênteses.  
  
3.  Coloque os argumentos na lista de argumentos entre parênteses, separados por vírgulas. Certifique-se de que fornecer os argumentos na mesma ordem que a propriedade define os parâmetros correspondentes.  
  
 O valor da propriedade participa na expressão apenas como uma variável ou constante seria, ou ele é armazenado na variável ou propriedade no lado esquerdo da instrução de atribuição.  
  
### <a name="to-call-a-propertys-set-procedure"></a>Para chamar uma propriedade do procedimento Set  
  
1.  Use o nome da propriedade no lado esquerdo de uma instrução de atribuição.  
  
     O exemplo a seguir define o valor da <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A> property, implicitamente chamando o `Set` procedimento.  
  
     [!code-vb[VbVbcnProcedures#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#11)]  
  
2.  Se a propriedade utiliza argumentos, siga o nome da propriedade com parênteses para incluir a lista de argumentos. Se não houver nenhum argumento, você pode, opcionalmente, omitir os parênteses.  
  
3.  Coloque os argumentos na lista de argumentos entre parênteses, separados por vírgulas. Certifique-se de que fornecer os argumentos na mesma ordem que a propriedade define os parâmetros correspondentes.  
  
 O valor gerado no lado direito da instrução de atribuição é armazenado na propriedade.  
  
## <a name="see-also"></a>Consulte também

- [Procedimentos de Propriedade](./property-procedures.md)
- [Parâmetros e Argumentos de Procedimento](./procedure-parameters-and-arguments.md)
- [Instrução Property](../../../../visual-basic/language-reference/statements/property-statement.md)
- [Diferenças entre propriedades e variáveis no Visual Basic](./differences-between-properties-and-variables.md)
- [Como: Criar uma propriedade](./how-to-create-a-property.md)
- [Como: Declarar uma propriedade com níveis de acesso mistos](./how-to-declare-a-property-with-mixed-access-levels.md)
- [Como: Declarar e chamar uma propriedade padrão no Visual Basic](./how-to-declare-and-call-a-default-property.md)
- [Como: Inserir um valor em uma propriedade](./how-to-put-a-value-in-a-property.md)
- [Como: Obter um valor de uma propriedade](./how-to-get-a-value-from-a-property.md)
- [Instrução Get](../../../../visual-basic/language-reference/statements/get-statement.md)
- [Instrução Set](../../../../visual-basic/language-reference/statements/set-statement.md)
