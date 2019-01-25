---
title: 'Como: Inserir um valor em uma propriedade (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: c39401e5-b5fc-4439-8f31-ed640f7ce6ed
ms.openlocfilehash: d40ca98f94f410bb20c8df0e7f1a3f216cf53bf9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54589159"
---
# <a name="how-to-put-a-value-in-a-property-visual-basic"></a>Como: Inserir um valor em uma propriedade (Visual Basic)
Você pode armazenar um valor em uma propriedade, colocando o nome da propriedade no lado esquerdo de uma instrução de atribuição.  
  
 A propriedade `Set` procedimento armazena um valor, mas você não o chame explicitamente por nome. Você usar a propriedade, assim como você usaria uma variável. O Visual Basic faz as chamadas para procedimentos da propriedade.  
  
### <a name="to-store-a-value-in-a-property"></a>Para armazenar um valor em uma propriedade  
  
1.  Use o nome da propriedade no lado esquerdo de uma instrução de atribuição.  
  
     O exemplo a seguir define o valor do Visual Basic `TimeOfDay` propriedade para o meio-dia, implicitamente chamando seu `Set` procedimento.  
  
     [!code-vb[VbVbcnProcedures#11](./codesnippet/VisualBasic/how-to-put-a-value-in-a-property_1.vb)]  
  
2.  Se a propriedade utiliza argumentos, siga o nome da propriedade com parênteses para incluir a lista de argumentos. Se não houver nenhum argumento, você pode, opcionalmente, omitir os parênteses.  
  
3.  Coloque os argumentos na lista de argumentos entre parênteses, separados por vírgulas. Certifique-se de que fornecer os argumentos na mesma ordem que a propriedade define os parâmetros correspondentes.  
  
4.  O valor gerado no lado direito da instrução de atribuição é armazenado na propriedade.  
  
## <a name="see-also"></a>Consulte também
- <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A>
- [Procedimentos de Propriedade](./property-procedures.md)
- [Parâmetros e Argumentos de Procedimento](./procedure-parameters-and-arguments.md)
- [Instrução Property](../../../../visual-basic/language-reference/statements/property-statement.md)
- [Diferenças entre propriedades e variáveis no Visual Basic](./differences-between-properties-and-variables.md)
- [Como: Criar uma propriedade](./how-to-create-a-property.md)
- [Como: Declarar uma propriedade com níveis de acesso mistos](./how-to-declare-a-property-with-mixed-access-levels.md)
- [Como: Chamar um procedimento de propriedade](./how-to-call-a-property-procedure.md)
- [Como: Declarar e chamar uma propriedade padrão no Visual Basic](./how-to-declare-and-call-a-default-property.md)
- [Como: Obter um valor de uma propriedade](./how-to-get-a-value-from-a-property.md)
