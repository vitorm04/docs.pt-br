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
ms.openlocfilehash: 6e361cbe89f4c51f28199b008de817c2d48ef326
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58825385"
---
# <a name="readonly-visual-basic"></a>ReadOnly (Visual Basic)
Especifica que uma variável ou propriedade pode ser lido mas não gravada.  
  
## <a name="remarks"></a>Comentários  
  
## <a name="rules"></a>Regras  
  
-   **Contexto da declaração.** Você pode usar `ReadOnly` apenas no nível de módulo. Isso significa que o contexto da declaração para um `ReadOnly` elemento deve ser uma classe, estrutura ou módulo e não pode ser um arquivo de origem, namespace ou procedimento.  
  
-   **Modificadores combinados.** Não é possível especificar `ReadOnly` junto com `Static` na mesma declaração.  
  
-   **Atribuir um valor.** Código consumindo um `ReadOnly` propriedade não é possível definir seu valor. Mas o código que tem acesso ao armazenamento subjacente pode atribuir ou alterar o valor a qualquer momento.  
  
     Você pode atribuir um valor para um `ReadOnly` variável apenas em sua declaração ou no construtor de uma classe ou estrutura na qual ele está definido.  
  
## <a name="when-to-use-a-readonly-variable"></a>Quando usar uma variável somente leitura  
 Há situações em que você não pode usar um [instrução Const](../../../visual-basic/language-reference/statements/const-statement.md) declarar e atribuir um valor constante. Por exemplo, o `Const` instrução pode não aceitar o tipo de dados que você deseja atribuir, ou você não poderá calcular o valor de tempo de compilação com uma expressão constante. Você pode não saber até mesmo o valor no tempo de compilação. Nesses casos, você pode usar um `ReadOnly` variável para conter um valor constante.  
  
> [!IMPORTANT]
>  Se o tipo de dados da variável é um tipo de referência, como uma matriz ou uma instância da classe, seus membros podem ser alterados, mesmo se a variável em si é `ReadOnly`. O exemplo a seguir ilustra essa situação.  
  
 `ReadOnly characterArray() As Char = {"x"c, "y"c, "z"c}`  
  
 `Sub changeArrayElement()`  
  
 `characterArray(1) = "M"c`  
  
 `End Sub`  
  
 Quando inicializado, a matriz apontada por `characterArray()` mantém "x", "y" e "z". Porque a variável `characterArray` é `ReadOnly`, você não pode alterar seu valor depois que ele é inicializado; o que é, você não pode atribuir uma nova matriz a ela. No entanto, você pode alterar os valores de um ou mais dos membros da matriz. Uma chamada para o procedimento a seguir `changeArrayElement`, a matriz apontada por `characterArray()` mantém "x", "M" e "z".  
  
 Observe que isso é semelhante a declarar um parâmetro de procedimento para ser [ByVal](../../../visual-basic/language-reference/modifiers/byval.md), que impede que o procedimento altere o argumento de chamada em si, mas permite que a mudança de seus membros.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir define uma `ReadOnly` propriedade para a data em que um funcionário foi contratado. A classe armazena o valor da propriedade internamente como um `Private` variável e apenas código dentro da classe pode alterar esse valor. No entanto, a propriedade é `Public`, e qualquer código que pode acessar a classe pode ler a propriedade.  
  
 [!code-vb[VbVbalrKeywords#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#4)]  
  
 O `ReadOnly` modificador pode ser usado nestes contextos:  
  
 [Instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a>Consulte também

- [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md)
- [Palavras-chave](../../../visual-basic/language-reference/keywords/index.md)
