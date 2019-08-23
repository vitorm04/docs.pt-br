---
title: ReadOnly (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ReadOnly
helpviewer_keywords:
- ReadOnly keyword [Visual Basic]
- variables [Visual Basic], read-only
- ReadOnly property
- properties [Visual Basic], read-only
- read-only variables
ms.assetid: e868185d-6142-4359-a2fd-a7965cadfce8
ms.openlocfilehash: 01c441576cb4247933c053f2043296733f99fdeb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965414"
---
# <a name="readonly-visual-basic"></a>ReadOnly (Visual Basic)
Especifica que uma variável ou propriedade pode ser lida, mas não gravada.  
  
## <a name="remarks"></a>Comentários  
  
## <a name="rules"></a>Regras  
  
- **Contexto de declaração.** Você pode usar `ReadOnly` somente no nível do módulo. Isso significa que o contexto de Declaração `ReadOnly` para um elemento deve ser uma classe, estrutura ou módulo e não pode ser um arquivo de origem, namespace ou procedimento.  
  
- **Modificadores combinados.** Você não pode `ReadOnly` especificar juntos `Static` com na mesma declaração.  
  
- **Atribuindo um valor.** O código que `ReadOnly` consome uma propriedade não pode definir seu valor. Mas o código que tem acesso ao armazenamento subjacente pode atribuir ou alterar o valor a qualquer momento.  
  
     Você pode atribuir um valor a uma `ReadOnly` variável somente em sua declaração ou no construtor de uma classe ou estrutura na qual ela está definida.  
  
## <a name="when-to-use-a-readonly-variable"></a>Quando usar uma variável ReadOnly  
 Há situações em que você não pode usar uma [instrução const](../../../visual-basic/language-reference/statements/const-statement.md) para declarar e atribuir um valor constante. Por exemplo, a `Const` instrução pode não aceitar o tipo de dados que você deseja atribuir, ou talvez você não consiga calcular o valor em tempo de compilação com uma expressão constante. Você pode nem mesmo saber o valor no momento da compilação. Nesses casos, você pode usar uma `ReadOnly` variável para conter um valor constante.  
  
> [!IMPORTANT]
> Se o tipo de dados da variável for um tipo de referência, como uma matriz ou instância de classe, seus membros poderão ser alterados mesmo que a própria variável seja `ReadOnly`. O exemplo a seguir ilustra essa situação.  
  
 `ReadOnly characterArray() As Char = {"x"c, "y"c, "z"c}`  
  
 `Sub changeArrayElement()`  
  
 `characterArray(1) = "M"c`  
  
 `End Sub`  
  
 Quando inicializado, a matriz apontada `characterArray()` mantém "x", "y" e "z". Como a variável `characterArray` é `ReadOnly`, você não pode alterar seu valor depois que ela é inicializada; ou seja, você não pode atribuir uma nova matriz a ela. No entanto, você pode alterar os valores de um ou mais dos membros da matriz. Após uma chamada para o procedimento `changeArrayElement`, a matriz apontada `characterArray()` mantém "x", "M" e "z".  
  
 Observe que isso é semelhante à declaração de um parâmetro de procedimento como [ByVal](../../../visual-basic/language-reference/modifiers/byval.md), o que impede que o procedimento altere o próprio argumento de chamada, mas permite alterar seus membros.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir define `ReadOnly` uma propriedade para a data em que um funcionário foi contratado. A classe armazena o valor da propriedade internamente como `Private` uma variável e somente o código dentro da classe pode alterar esse valor. No entanto, a `Public`propriedade é, e qualquer código que possa acessar a classe pode ler a propriedade.  
  
 [!code-vb[VbVbalrKeywords#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#4)]  
  
 O `ReadOnly` modificador pode ser usado nesses contextos:  
  
 [Instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a>Consulte também

- [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md)
- [Palavras-chave](../../../visual-basic/language-reference/keywords/index.md)
