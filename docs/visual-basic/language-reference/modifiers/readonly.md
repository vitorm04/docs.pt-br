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
ms.openlocfilehash: e2957bf49292dfcafab8e78f4b997247c34ad279
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="readonly-visual-basic"></a>ReadOnly (Visual Basic)
Especifica que uma variável ou propriedade pode ser lida mas não gravada.  
  
## <a name="remarks"></a>Comentários  
  
## <a name="rules"></a>Regras  
  
-   **Contexto de declaração.** Você pode usar `ReadOnly` apenas no nível de módulo. Isso significa que o contexto da declaração para um `ReadOnly` elemento deve ser uma classe, estrutura ou módulo e não pode ser um arquivo de origem, namespace ou procedimento.  
  
-   **Modificadores combinados.** Não é possível especificar `ReadOnly` junto com `Static` na mesma declaração.  
  
-   **Atribuindo um valor.** Código de consumo um `ReadOnly` propriedade não é possível definir seu valor. Mas o código que tenha acesso ao armazenamento subjacente pode atribuir ou alterar o valor a qualquer momento.  
  
     Você pode atribuir um valor para um `ReadOnly` variável somente em sua declaração ou no construtor de uma classe ou estrutura na qual ela está definida.  
  
## <a name="when-to-use-a-readonly-variable"></a>Quando usar uma variável somente leitura  
 Há situações em que você não pode usar um [Declaração Const](../../../visual-basic/language-reference/statements/const-statement.md) declarar e atribuir um valor constante. Por exemplo, o `Const` instrução não pode aceitar o tipo de dados que você deseja atribuir ou você não poderá calcular o valor em tempo de compilação com uma expressão constante. Você pode não saber até mesmo o valor em tempo de compilação. Nesses casos, você pode usar um `ReadOnly` variável para conter um valor constante.  
  
> [!IMPORTANT]
>  Se o tipo de dados da variável é um tipo de referência, como uma matriz ou uma instância da classe, seus membros podem ser alterados, mesmo se a variável em si é `ReadOnly`. O exemplo a seguir ilustra essa situação.  
  
 `ReadOnly characterArray() As Char = {"x"c, "y"c, "z"c}`  
  
 `Sub changeArrayElement()`  
  
 `characterArray(1) = "M"c`  
  
 `End Sub`  
  
 Quando inicializado, a matriz apontada pelo `characterArray()` mantém "x", "y" e "z". Porque a variável `characterArray` é `ReadOnly`, você não pode alterar seu valor quando ele é inicializado; o que é, você não pode atribuir uma nova matriz para ele. No entanto, você pode alterar os valores de um ou mais membros da matriz. Uma chamada para o procedimento a seguir `changeArrayElement`, a matriz apontada pelo `characterArray()` mantém "x", "M" e "z".  
  
 Observe que isso é semelhante ao declarar um parâmetro de procedimento para ser [ByVal](../../../visual-basic/language-reference/modifiers/byval.md), que impede que o procedimento altere o argumento de chamada, mas permite que a mudança de seus membros.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir define um `ReadOnly` propriedade para a data em que um funcionário foi contratado. Os repositórios de classe, o valor da propriedade internamente como um `Private` código variável e somente dentro da classe pode alterar esse valor. No entanto, a propriedade é `Public`, e qualquer código que pode acessar a classe pode ler a propriedade.  
  
 [!code-vb[VbVbalrKeywords#4](../../../visual-basic/language-reference/codesnippet/VisualBasic/readonly_1.vb)]  
  
 O `ReadOnly` modificador pode ser usado nesses contextos:  
  
 [Instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a>Consulte também  
 [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md)  
 [Palavras-chave](../../../visual-basic/language-reference/keywords/index.md)
