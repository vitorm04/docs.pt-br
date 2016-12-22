---
title: "Como criar uma propriedade (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "procedimentos, definindo"
  - "propriedades [Visual Basic]"
  - "código do Visual Basic, procedimentos"
  - "código do Visual Basic, propriedades"
ms.assetid: 4d229712-6be8-4c5c-bac5-06995ce9185a
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como criar uma propriedade (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Você encaixa a uma definição de propriedade entre uma declaração `Property` e uma declaração `End Property`.  Nessa definição você define um procedimento `Get`, um procedimento `Set` ou ambos.  Todo o código da propriedade está situado nesses procedimentos.  
  
 O procedimento `Get` recupera o valor da propriedade e o procedimento `Set` armazena um valor.  Se você quiser que a propriedade tenha acesso de escrita e leitura, você deve definir ambos procedimentos.  Para uma propriedade somente leitura, você define apenas `Get`, e para uma propredade somente escrita, você define apenas `Set`.  
  
### Para criar uma propriedade  
  
1.  Fora de qualquer propriedade ou procedimento, utilize uma declaração [Instrução Property](../../../../visual-basic/language-reference/statements/property-statement.md), seguida de uma declaração `End Property`.  
  
2.  Se a propriedade recebe parâmetros, obedeça à palava\-chave`Property`com o nome do procedimento, e, em seguida, da lista de parâmetros em parênteses.  
  
3.  Siga os parênteses com uma cláusula `As` para especificar o tipo de dado do valor da propriedade.  Você deve especificar o tipo de dado inclusive para uma propriedade somente de escrita.  
  
4.  Adicione procedimentos `Get` e `Set`, como apropriado.  Veja as seguintes instruções:  
  
### Para criar um procedimento Get que recupere um valor de propriedade.  
  
1.  Entre as declarações `Property` e `End Property`, escreva uma declaração [Instrução Get](../../../../visual-basic/language-reference/statements/get-statement.md), seguida por uma `End Get`.  Você não precisa definir nenhum parâmetro para o procedimento `Get`.  
  
2.  Coloque as declarações de código para recuperar o valor da propriedade entre as declarações `Get` e `End Get`.  Este código pode incluir outros cálculos e manipulações de dados, além da geração e retorno do valor da propriedade.  
  
3.  Use a declaração `Return` para retornar o valor da propriedade para o código de chamada.  
  
 Você deve escrever um procedimento `Get` para uma propriedade de leitura e escrita e para uma propriedade somente leitura.  Você não deve definir um procedimento `Get` para uma propriedade somente de escrita.  
  
### Para criar um procedimento Set que escreva um valor de propriedade.  
  
1.  Entre as declarações `Property` e `End Property`, escreva uma declaração [Instrução Set](../../../../visual-basic/language-reference/statements/set-statement.md), seguida por uma `End Set`.  
  
2.  Na declaração `Set`, siga a palava\-chave `Set` com uma lista de parâmetros entre parênteses.  Esta lista de parâmetros deve incluir pelo menos um parâmetro de valor passado pelo código de chamada.  O nome padrão para este parâmetro de valor é `Value`, mas você pode usar um nome diferente se apropriado.  O parâmetro de valor deve ter o mesmo tipo de dado da propriedade.  
  
3.  Coloque as declarações de código para armazenar o valor da propriedade entre as declarações `Set` e `End Set`.  Este código pode incluir outros cálculos e manipulações de dados, além da validação e armazenamento do valor da propriedade.  
  
4.  Use o parâmetro do valor para aceitar o valor fornecido pelo código de chamada.  Você pode tanto armazenar esse valor diretamente numa declaração de atribuição ou usá\-lo como uma expressão para calcular o valor interno a ser armazenado.  
  
 Você deve escrever um procedimento `Set` para uma propriedade de leitura e escrita e para uma propriedade somente escrita.  Você não deve definir um procedimento `Set` para uma propriedade somente de leitura.  
  
## Exemplo  
 O seguinte exemplo cria uma propriedade de leitura e escrita que armazena um nome completo constituído por duas partes: o primeiro nome e o último nome.  Quando o código de chamada lê `fullName`, o `Get` procedimento combinará os dois nomes constituintes e retorna o nome completo.  Quando o código de chamada atribui um novo nome completo, o procedimento `Set` tenta dividi\-lo em duas partes.  Se ele não achar um espaço, armazena o nome completo apenas como o primeiro nome.  
  
 [!code-vb[VbVbcnProcedures#8](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/how-to-create-a-property_1.vb)]  
  
 O seguinte exemplo mostra chamadas típicas para os procedimentos de propriedade do `fullName` Esta primeira chamada determina o valor da propriedade e a segunda chamada o recupera.  
  
 [!code-vb[VbVbcnProcedures#9](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/how-to-create-a-property_2.vb)]  
  
## Consulte também  
 [Procedimentos](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Procedimentos de propriedade](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Parâmetros e argumentos de procedimento](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Diferenças entre propriedades e variáveis no Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md)   
 [Como declarar uma propriedade com níveis de acesso mistos](../Topic/How%20to:%20Declare%20a%20Property%20with%20Mixed%20Access%20Levels%20\(Visual%20Basic\).md)   
 [Como chamar um procedimento de propriedade](../../../../visual-basic/programming-guide/language-features/procedures/how-to-call-a-property-procedure.md)   
 [Como declarar e chamar uma propriedade padrão no Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)   
 [Como inserir um valor em uma propriedade](../../../../visual-basic/programming-guide/language-features/procedures/how-to-put-a-value-in-a-property.md)   
 [Como obter um valor a partir de uma propriedade](../Topic/How%20to:%20Get%20a%20Value%20from%20a%20Property%20\(Visual%20Basic\).md)