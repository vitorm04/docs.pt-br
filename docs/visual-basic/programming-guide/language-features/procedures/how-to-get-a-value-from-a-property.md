---
title: Como obter um valor a partir de uma propriedade (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: 3954423e-6ab7-4a4c-b55c-a8d27be47891
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7161052b9d9b388d8da8bd421c3b220f15037805
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
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
