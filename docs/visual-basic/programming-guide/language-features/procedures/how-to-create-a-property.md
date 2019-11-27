---
title: Como criar uma propriedade
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- Visual Basic code, properties
- properties [Visual Basic]
ms.assetid: 4d229712-6be8-4c5c-bac5-06995ce9185a
ms.openlocfilehash: ee5a9f687765ce064eb3c3f84218ed36eb916d9d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349712"
---
# <a name="how-to-create-a-property-visual-basic"></a>Como criar uma propriedade (Visual Basic)
Você coloca uma definição de propriedade entre uma instrução `Property` e uma instrução `End Property`. Nessa definição, você define um procedimento de `Get`, um procedimento de `Set` ou ambos. Todo o código da propriedade está dentro desses procedimentos.  
  
 O procedimento `Get` recupera o valor da propriedade e o procedimento `Set` armazena um valor. Se você quiser que a propriedade tenha acesso de leitura/gravação, você deve definir os dois procedimentos. Para uma propriedade somente leitura, você define apenas `Get`e, para uma propriedade somente gravação, você define somente `Set`.  
  
### <a name="to-create-a-property"></a>Para criar uma propriedade  
  
1. Fora de qualquer propriedade ou procedimento, use uma [instrução de propriedade](../../../../visual-basic/language-reference/statements/property-statement.md), seguida por uma instrução `End Property`.  
  
2. Se a propriedade usar parâmetros, siga a palavra-chave `Property` com o nome do procedimento e, em seguida, a lista de parâmetros entre parênteses.  
  
3. Siga os parênteses com uma cláusula `As` para especificar o tipo de dados do valor da propriedade. Você deve especificar o tipo de dados até mesmo para uma propriedade somente gravação.  
  
4. Adicione `Get` e `Set` procedimentos, conforme apropriado. Consulte as instruções a seguir.  
  
### <a name="to-create-a-get-procedure-that-retrieves-a-property-value"></a>Para criar um procedimento Get que recupera um valor de propriedade  
  
1. Entre as instruções `Property` e `End Property`, escreva uma [instrução Get](../../../../visual-basic/language-reference/statements/get-statement.md), seguida por uma instrução `End Get`. Você não precisa definir parâmetros para o procedimento de `Get`.  
  
2. Coloque as instruções de código para recuperar o valor da propriedade entre as instruções `Get` e `End Get`. Esse código pode incluir outros cálculos e manipulações de dados, além de gerar e retornar o valor da propriedade.  
  
3. Use uma instrução `Return` para retornar o valor da propriedade para o código de chamada.  
  
 Você deve escrever um procedimento de `Get` para uma propriedade de leitura/gravação e para uma propriedade somente leitura. Você não deve definir um procedimento de `Get` para uma propriedade somente gravação.  
  
### <a name="to-create-a-set-procedure-that-writes-a-propertys-value"></a>Para criar um procedimento Set que grava o valor de uma propriedade  
  
1. Entre as instruções `Property` e `End Property`, escreva uma [instrução SET](../../../../visual-basic/language-reference/statements/set-statement.md), seguida por uma instrução `End Set`.  
  
2. Na instrução `Set`, siga a palavra-chave `Set` com uma lista de parâmetros entre parênteses. Essa lista de parâmetros deve incluir pelo menos um parâmetro de valor para o valor passado pelo código de chamada. O nome padrão para esse parâmetro de valor é `Value`, mas você pode usar um nome diferente, se apropriado. O parâmetro de valor deve ter o mesmo tipo de dados que a própria propriedade.  
  
3. Coloque as instruções de código para armazenar um valor na propriedade entre as instruções `Set` e `End Set`. Esse código pode incluir outros cálculos e manipulações de dados, além de validar e armazenar o valor da propriedade.  
  
4. Use o parâmetro value para aceitar o valor fornecido pelo código de chamada. Você pode armazenar esse valor diretamente em uma instrução de atribuição ou usá-lo em uma expressão para calcular o valor interno a ser armazenado.  
  
 Você deve escrever um procedimento de `Set` para uma propriedade de leitura/gravação e para uma propriedade somente gravação. Você não deve definir um procedimento de `Set` para uma propriedade somente leitura.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria uma propriedade de leitura/gravação que armazena um nome completo como dois nomes de constituintes, o primeiro nome e o sobrenome. Quando o código de chamada lê `fullName`, o procedimento `Get` combina os dois nomes constituintes e retorna o nome completo. Quando o código de chamada atribui um novo nome completo, o procedimento `Set` tenta dividi-lo em dois nomes de constituintes. Se não encontrar um espaço, ele o armazenará como o primeiro nome.  
  
 [!code-vb[VbVbcnProcedures#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#8)]  
  
 O exemplo a seguir mostra as chamadas típicas para os procedimentos de propriedade de `fullName`. A primeira chamada define o valor da propriedade e a segunda chamada a recupera.  
  
 [!code-vb[VbVbcnProcedures#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#9)]  
  
## <a name="see-also"></a>Consulte também

- [Procedimentos](./index.md)
- [Procedimentos de Propriedade](./property-procedures.md)
- [Parâmetros e Argumentos de Procedimento](./procedure-parameters-and-arguments.md)
- [Diferenças entre propriedades e variáveis no Visual Basic](./differences-between-properties-and-variables.md)
- [Como declarar uma propriedade com níveis de acesso mistos](./how-to-declare-a-property-with-mixed-access-levels.md)
- [Como chamar um procedimento de propriedade](./how-to-call-a-property-procedure.md)
- [Como: declarar e chamar uma propriedade padrão no Visual Basic](./how-to-declare-and-call-a-default-property.md)
- [Como inserir um valor em uma propriedade](./how-to-put-a-value-in-a-property.md)
- Como obter um valor de uma propriedade (Visual Basic)[Como obter um valor de uma propriedade](./how-to-get-a-value-from-a-property.md)
