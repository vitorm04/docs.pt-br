---
title: "Como declarar e chamar uma propriedade padr&#227;o no Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "propriedades padrão"
  - "propriedades padrão, em Visual Basic"
  - "padrões, propriedades"
  - "procedimentos, definindo"
  - "propriedades [Visual Basic], default"
  - "código do Visual Basic, procedimentos"
  - "código do Visual Basic, propriedades"
ms.assetid: 68b4026e-09ef-4613-808e-f6287494ff63
caps.latest.revision: 23
caps.handback.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como declarar e chamar uma propriedade padr&#227;o no Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Uma *propriedade padrão*  é uma propriedade de classe ou estrutura que seu código pode acessar sem especificá\-la.  Ao chamar por apelidos uma classe ou estrutura, mas não uma propriedade e o contexto permite o acesso a uma propriedade, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] decide o acesso à propriedade padrão dessa classe ou estrutura se uma existir.  
  
 Uma classe ou estrutura pode ter no máximo uma propriedade padrão.  No entanto, você pode sobrecarregar uma propriedade padrão e ter mais de uma versão dela.  
  
 Para mais informações, consulte [Padrão](../../../../visual-basic/language-reference/modifiers/default.md).  
  
### Declarar uma propriedade padrão  
  
1.  Declare a propriedade da forma normal.  Não especifique as palavras\-chave `Shared` ou `Private`.  
  
2.  Inclua a palavra\-chave `Default` na declaração da propriedade.  
  
3.  Especifique pelo menos um parâmetro para a propriedade.  Não é possível definir uma propriedade padrão que não tem pelo menos um argumento.  
  
     [!code-vb[VbVbcnProcedures#17](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_1.vb)]  
  
### Chamar uma propriedade padrão  
  
1.  Declare uma variável do tipo recipiente da classe ou estrutura.  
  
     [!code-vb[VbVbcnProcedures#16](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_2.vb)]  
  
2.  Use o nome de variável sozinho em uma expressão em que você normalmente incluiria o nome da propriedade.  
  
     [!code-vb[VbVbcnProcedures#21](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_3.vb)]  
  
3.  Após o nome da variável, coloque uma lista de argumentos entre parênteses.  Uma propriedade padrão deve receber ao menos um argumento.  
  
     [!code-vb[VbVbcnProcedures#20](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_4.vb)]  
  
4.  Para recuperar o valor da propriedade padrão, use o nome da variável, com uma lista de argumentos, em uma expressão ou depois do sinal de igual \(`=`\) em uma declaração de atribuição.  
  
     [!code-vb[VbVbcnProcedures#15](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_5.vb)]  
  
5.  Para definir o valor da propriedade padrão, use o nome de variável, com um lista de argumentos, no lado esquerdo de uma declaração de atribuição.  
  
     [!code-vb[VbVbcnProcedures#14](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_6.vb)]  
  
6.  Você sempre pode especificar o nome da propriedade padrão juntamente with o nome da variável, do mesmo modo que você faria para acessar qualquer outra propriedade.  
  
     [!code-vb[VbVbcnProcedures#19](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_7.vb)]  
  
## Exemplo  
 O exemplo a seguir declara uma propriedade padrão em uma classe.  
  
 [!code-vb[VbVbcnProcedures#12](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_8.vb)]  
  
## Exemplo  
 O exemplo a seguir demonstra como chamar a propriedade padrão `myProperty` na classe `class1`.  As três declarações de atribuição armazenam valores em `myProperty`, e a chamada <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> lê os valores.  
  
 [!code-vb[VbVbcnProcedures#13](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_9.vb)]  
  
 O uso mais comum de uma propriedade padrão é o <xref:Microsoft.VisualBasic.Collection.Item%2A> propriedade em várias classes de coleção.  
  
## Programação robusta  
 As propriedades padrão podem resultar em uma pequena redução nos caracteres do código\-fonte, mas elas podem deixar seu código mais difícil de ler.  Se o código de chamada não está familiarizado com sua classe ou estrutura, quando ele faz uma referência ao nome de classe ou estrutura não poderá determinar se essa referência acessa a classe ou estrutura em si ou uma propriedade padrão.  Isso pode levar a erros de compilador ou a sutis erros de lógica em tempo de execução.  
  
 Você tanto pode reduzir a chance de erros de propriedade padrão sempre usando a [Instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) para configurar a verificação do tipo do compilador como `On`.  
  
 Se você estiver planejando usar uma classe ou estrutura predefinidas no seu código, você deve determinar se ela tem uma propriedade padrão, e em caso afirmativo, qual seu nome.  
  
 Por causa dessas desvantagens, você deve considerar não definir as propriedades padrão.  Para legibilidade de código, você deve também considerar sempre referir\-se a todas as propriedades explicitamente, mesmo propriedades padrão.  
  
## Consulte também  
 [Procedimentos de propriedade](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Parâmetros e argumentos de procedimento](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Instrução Property](../../../../visual-basic/language-reference/statements/property-statement.md)   
 [Padrão](../../../../visual-basic/language-reference/modifiers/default.md)   
 [Diferenças entre propriedades e variáveis no Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md)   
 [Como criar uma propriedade](../../../../visual-basic/programming-guide/language-features/procedures/how-to-create-a-property.md)   
 [Como declarar uma propriedade com níveis de acesso mistos](../Topic/How%20to:%20Declare%20a%20Property%20with%20Mixed%20Access%20Levels%20\(Visual%20Basic\).md)   
 [Como chamar um procedimento de propriedade](../../../../visual-basic/programming-guide/language-features/procedures/how-to-call-a-property-procedure.md)   
 [Como inserir um valor em uma propriedade](../../../../visual-basic/programming-guide/language-features/procedures/how-to-put-a-value-in-a-property.md)   
 [Como obter um valor a partir de uma propriedade](../Topic/How%20to:%20Get%20a%20Value%20from%20a%20Property%20\(Visual%20Basic\).md)