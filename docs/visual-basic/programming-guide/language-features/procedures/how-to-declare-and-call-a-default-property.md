---
title: "Como: declarar e chamar uma propriedade padrão no Visual Basic | Documentos do Microsoft"
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
- defaults, properties
- properties [Visual Basic], default
- procedures, defining
- default properties, in Visual Basic
- Visual Basic code, procedures
- Visual Basic code, properties
- default properties
ms.assetid: 68b4026e-09ef-4613-808e-f6287494ff63
caps.latest.revision: 23
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
ms.openlocfilehash: ce98e7fe72a395f6c4cde481feaa60be28c6fcc3
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-declare-and-call-a-default-property-in-visual-basic"></a>Como declarar e chamar uma propriedade padrão no Visual Basic
A *propriedade padrão* é uma propriedade de classe ou estrutura que seu código pode acessar sem especificá-la. Ao chamar por apelidos uma classe ou estrutura, mas não uma propriedade e o contexto permite o acesso a uma propriedade [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] decide o acesso à propriedade dessa classe ou da estrutura padrão, se houver.  
  
 Uma classe ou estrutura pode ter no máximo uma propriedade padrão. No entanto, você pode sobrecarregar uma propriedade padrão e ter mais de uma versão dele.  
  
 Para obter mais informações, consulte [padrão](../../../../visual-basic/language-reference/modifiers/default.md).  
  
### <a name="to-declare-a-default-property"></a>Para declarar uma propriedade padrão  
  
1.  Declare a propriedade da maneira normal. Não especifique o `Shared` ou `Private` palavra-chave.  
  
2.  Incluir o `Default` palavra-chave na declaração da propriedade.  
  
3.  Especifique pelo menos um parâmetro para a propriedade. Você não pode definir uma propriedade padrão que têm pelo menos um argumento.  
  
     [!code-vb[17 VbVbcnProcedures](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_1.vb)]  
  
### <a name="to-call-a-default-property"></a>Para chamar uma propriedade padrão  
  
1.  Declare uma variável do tipo de classe ou estrutura que contém.  
  
     [!code-vb[VbVbcnProcedures n º&16;](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_2.vb)]  
  
2.  Use o nome de variável sozinho em uma expressão em que você normalmente incluiria o nome da propriedade.  
  
     [!code-vb[VbVbcnProcedures&#21;](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_3.vb)]  
  
3.  Siga o nome da variável com uma lista de argumentos entre parênteses. Uma propriedade padrão deve receber pelo menos um argumento.  
  
     [!code-vb[20 VbVbcnProcedures](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_4.vb)]  
  
4.  Para recuperar o valor da propriedade padrão, use o nome da variável com uma lista de argumentos, em uma expressão ou depois de igual (`=`) entrar em uma instrução de atribuição.  
  
     [!code-vb[VbVbcnProcedures&#15;](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_5.vb)]  
  
5.  Para definir o valor da propriedade padrão, use o nome da variável com uma lista de argumentos, no lado esquerdo de uma instrução de atribuição.  
  
     [!code-vb[VbVbcnProcedures&#14;](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_6.vb)]  
  
6.  Você sempre pode especificar o nome da propriedade padrão junto com o nome da variável, exatamente como você faria para acessar qualquer outra propriedade.  
  
     [!code-vb[19 VbVbcnProcedures](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_7.vb)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir declara uma propriedade padrão em uma classe.  
  
 [!code-vb[VbVbcnProcedures&#12;](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_8.vb)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra como chamar a propriedade padrão `myProperty` na classe `class1`. As três declarações de atribuição armazenam valores em `myProperty`e o <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>chamada lê os valores.</xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>  
  
 [!code-vb[VbVbcnProcedures&13;](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_9.vb)]  
  
 O uso mais comum de uma propriedade padrão é o <xref:Microsoft.VisualBasic.Collection.Item%2A>propriedade em várias classes de coleção.</xref:Microsoft.VisualBasic.Collection.Item%2A>  
  
## <a name="robust-programming"></a>Programação robusta  
 Propriedades padrão podem resultar em uma pequena redução nos caracteres de código fonte, mas eles podem tornar seu código mais difícil de ler. Se o código de chamada não está familiarizado com sua classe ou estrutura, quando ele faz referência ao nome de classe ou estrutura não poderá determinar se essa referência acessa a classe ou estrutura em si ou uma propriedade padrão. Isso pode levar a erros de compilador ou lógica de tempo de execução sutis.  
  
 Você tanto pode reduzir a chance de erros de propriedade padrão sempre usando o [instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) para definir o tipo do compilador para `On`.  
  
 Se você estiver planejando usar uma classe ou estrutura predefinidas no seu código, você deve determinar se ele tem uma propriedade padrão e, nesse caso, o que seu nome é.  
  
 Por causa dessas desvantagens, você deve considerar não definir as propriedades padrão. Para fins de legibilidade de código, você deve também considerar sempre referir-se a todas as propriedades explicitamente, mesmo propriedades padrão.  
  
## <a name="see-also"></a>Consulte também  
 [Procedimentos de propriedade](./property-procedures.md)   
 [Argumentos e parâmetros de procedimento](./procedure-parameters-and-arguments.md)   
 [Instrução Property](../../../../visual-basic/language-reference/statements/property-statement.md)   
 [Padrão](../../../../visual-basic/language-reference/modifiers/default.md)   
 [Diferenças entre propriedades e variáveis no Visual Basic](./differences-between-properties-and-variables.md)   
 [Como: criar uma propriedade](./how-to-create-a-property.md)   
 [Como: declarar uma propriedade com níveis de acesso mistos](./how-to-declare-a-property-with-mixed-access-levels.md)   
 [Como: chamar um procedimento de propriedade](./how-to-call-a-property-procedure.md)   
 [Como: inserir um valor em uma propriedade](./how-to-put-a-value-in-a-property.md)   
Como obter um valor de uma propriedade (Visual Basic) [Como obter um valor de uma propriedade](./how-to-get-a-value-from-a-property.md)
