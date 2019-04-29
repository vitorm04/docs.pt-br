---
title: 'Como: Declarar e chamar uma propriedade padrão no Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- defaults [Visual Basic], properties
- properties [Visual Basic], default
- procedures [Visual Basic], defining
- default properties [Visual Basic], in Visual Basic
- Visual Basic code, procedures
- Visual Basic code, properties
- default properties
ms.assetid: 68b4026e-09ef-4613-808e-f6287494ff63
ms.openlocfilehash: 9ca9a0ccdac3ac13429928233a0c09d58427ce74
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61665761"
---
# <a name="how-to-declare-and-call-a-default-property-in-visual-basic"></a>Como: Declarar e chamar uma propriedade padrão no Visual Basic
Um *propriedade padrão* é uma propriedade de classe ou estrutura que seu código pode acessar sem especificá-lo. Ao chamar código nomes de uma classe ou estrutura, mas não uma propriedade e o contexto permite o acesso a uma propriedade, Visual Basic decide o acesso à propriedade dessa classe ou da estrutura padrão, se houver.  
  
 Uma classe ou estrutura pode ter no máximo uma propriedade padrão. No entanto, você pode sobrecarregar uma propriedade padrão e ter mais de uma versão dele.  
  
 Para obter mais informações, consulte [padrão](../../../../visual-basic/language-reference/modifiers/default.md).  
  
### <a name="to-declare-a-default-property"></a>Para declarar uma propriedade padrão  
  
1. Declare a propriedade da maneira normal. Não especifique a `Shared` ou `Private` palavra-chave.  
  
2. Incluir o `Default` palavra-chave na declaração de propriedade.  
  
3. Especifique pelo menos um parâmetro para a propriedade. Você não pode definir uma propriedade padrão que têm pelo menos um argumento.  
  
     [!code-vb[VbVbcnProcedures#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#17)]  
  
### <a name="to-call-a-default-property"></a>Para chamar uma propriedade padrão  
  
1. Declare uma variável do tipo recipiente de classe ou estrutura.  
  
     [!code-vb[VbVbcnProcedures#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#16)]  
  
2. Use o nome da variável sozinho em uma expressão em que você normalmente incluiria o nome da propriedade.  
  
     [!code-vb[VbVbcnProcedures#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#21)]  
  
3. Siga o nome da variável com uma lista de argumentos entre parênteses. Uma propriedade de padrão deve ter pelo menos um argumento.  
  
     [!code-vb[VbVbcnProcedures#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#20)]  
  
4. Para recuperar o valor da propriedade padrão, use o nome da variável, com uma lista de argumentos, em uma expressão ou igual a seguir (`=`) entrar em uma instrução de atribuição.  
  
     [!code-vb[VbVbcnProcedures#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#15)]  
  
5. Para definir o valor da propriedade padrão, use o nome da variável, com uma lista de argumentos no lado esquerdo de uma instrução de atribuição.  
  
     [!code-vb[VbVbcnProcedures#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#14)]  
  
6. Você sempre pode especificar o nome da propriedade padrão junto com o nome da variável, exatamente como você faria para acessar qualquer outra propriedade.  
  
     [!code-vb[VbVbcnProcedures#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#19)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir declara uma propriedade padrão em uma classe.  
  
 [!code-vb[VbVbcnProcedures#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#12)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra como chamar a propriedade padrão `myProperty` na classe `class1`. As três declarações de atribuição armazenam valores em `myProperty`e o <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> chamada lê os valores.  
  
 [!code-vb[VbVbcnProcedures#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#13)]  
  
 O uso mais comum de uma propriedade padrão é o <xref:Microsoft.VisualBasic.Collection.Item%2A> propriedade em várias classes de coleção.  
  
## <a name="robust-programming"></a>Programação robusta  
 As propriedades padrão podem resultar em uma pequena redução nos caracteres de código fonte, mas eles podem tornar seu código mais difícil de ler. Se o código de chamada não estiver familiarizado com a sua classe ou estrutura, quando ele faz referência ao nome de classe ou estrutura não poderá determinar se essa referência acessa a classe ou estrutura em si ou uma propriedade padrão. Isso pode levar a erros de compilador ou erros de lógica de tempo de execução sutis.  
  
 Você tanto pode reduzir a chance de erros de propriedade padrão sempre usando o [instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) para definir o tipo de compilador verificando para `On`.  
  
 Se você estiver planejando usar uma classe ou estrutura predefinidas no seu código, você deve determinar se ele tem uma propriedade padrão e nesse caso, o que seu nome é.  
  
 Por causa dessas desvantagens, você deve considerar não definir as propriedades padrão. Para facilitar a leitura do código, você deve também considerar sempre referir-se a todas as propriedades explicitamente, mesmo propriedades padrão.  
  
## <a name="see-also"></a>Consulte também

- [Procedimentos de Propriedade](./property-procedures.md)
- [Parâmetros e Argumentos de Procedimento](./procedure-parameters-and-arguments.md)
- [Instrução Property](../../../../visual-basic/language-reference/statements/property-statement.md)
- [Padrão](../../../../visual-basic/language-reference/modifiers/default.md)
- [Diferenças entre propriedades e variáveis no Visual Basic](./differences-between-properties-and-variables.md)
- [Como: Criar uma propriedade](./how-to-create-a-property.md)
- [Como: Declarar uma propriedade com níveis de acesso mistos](./how-to-declare-a-property-with-mixed-access-levels.md)
- [Como: Chamar um procedimento de propriedade](./how-to-call-a-property-procedure.md)
- [Como: Inserir um valor em uma propriedade](./how-to-put-a-value-in-a-property.md)
- [Como: Obter um valor de uma propriedade](./how-to-get-a-value-from-a-property.md)
