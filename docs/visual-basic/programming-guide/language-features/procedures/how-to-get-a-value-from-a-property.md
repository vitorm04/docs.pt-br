---
title: Como obter um valor a partir de uma propriedade (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: 3954423e-6ab7-4a4c-b55c-a8d27be47891
ms.openlocfilehash: 9f97669e8d18e7fc633cb0e691d973a611a8cea0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648402"
---
# <a name="how-to-get-a-value-from-a-property-visual-basic"></a>Como obter um valor a partir de uma propriedade (Visual Basic)
Para recuperar um valor de propriedade, incluindo o nome da propriedade em uma expressão.  
  
 A propriedade `Get` procedimento recupera o valor, mas você não o chama explicitamente por nome. Você usa a propriedade exatamente como você usaria uma variável. Visual Basic faz as chamadas aos procedimentos da propriedade.  
  
### <a name="to-retrieve-a-value-from-a-property"></a>Para recuperar um valor de uma propriedade  
  
1.  Use o nome da propriedade em uma expressão da mesma maneira que você usaria um nome de variável. Você pode usar uma propriedade em qualquer lugar você pode usar uma variável ou constante.  
  
     -ou-  
  
     Use o nome de propriedade seguido de igual (`=`) entrar em uma instrução de atribuição.  
  
     O exemplo a seguir lê o valor do Visual Basic `Now` property, implicitamente chamando seu `Get` procedimento.  
  
     [!code-vb[VbVbalrDateProperties#4](./codesnippet/VisualBasic/how-to-get-a-value-from-a-property_1.vb)]  
  
2.  Se a propriedade utiliza argumentos, siga o nome da propriedade com parênteses para incluir a lista de argumentos. Se não houver nenhum argumento, opcionalmente, você pode omitir os parênteses.  
  
3.  Coloque os argumentos na lista de argumentos dentro dos parênteses, separados por vírgulas. Certifique-se de que fornecer os argumentos na mesma ordem que a propriedade define os parâmetros correspondentes.  
  
 O valor da propriedade participa na expressão apenas como uma variável ou constante seria, ou ele é armazenado na variável ou propriedade no lado esquerdo da instrução de atribuição.  
  
## <a name="see-also"></a>Consulte também  
 [Procedimentos](./index.md)  
 [Procedimentos de Propriedade](./property-procedures.md)  
 [Parâmetros e Argumentos de Procedimento](./procedure-parameters-and-arguments.md)  
 [Instrução Property](../../../../visual-basic/language-reference/statements/property-statement.md)  
 [Diferenças entre propriedades e variáveis no Visual Basic](./differences-between-properties-and-variables.md)  
 [Como criar uma propriedade](./how-to-create-a-property.md)  
 [Como declarar uma propriedade com níveis de acesso mistos](./how-to-declare-a-property-with-mixed-access-levels.md)  
 [Como chamar um procedimento de propriedade](./how-to-call-a-property-procedure.md)  
 [Como: declarar e chamar uma propriedade padrão no Visual Basic](./how-to-declare-and-call-a-default-property.md)  
 [Como inserir um valor em uma propriedade](./how-to-put-a-value-in-a-property.md)
