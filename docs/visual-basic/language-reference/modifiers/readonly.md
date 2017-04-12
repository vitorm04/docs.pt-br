---
title: ReadOnly (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.ReadOnly
dev_langs:
- VB
helpviewer_keywords:
- ReadOnly keyword
- variables [Visual Basic], read-only
- ReadOnly property
- properties [Visual Basic], read-only
- read-only variables
ms.assetid: e868185d-6142-4359-a2fd-a7965cadfce8
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: 5090f02d12f84a542066978241456bb64ad1b495
ms.lasthandoff: 03/13/2017

---
# <a name="readonly-visual-basic"></a>ReadOnly (Visual Basic)
Especifica que uma variável ou propriedade pode ser lido mas não gravada.  
  
## <a name="remarks"></a>Comentários  
  
## <a name="rules"></a>Regras  
  
-   **Contexto de declaração.** Você pode usar `ReadOnly` somente no nível de módulo. Isso significa que o contexto da declaração para um `ReadOnly` elemento deve ser uma classe, estrutura ou módulo e não pode ser um arquivo fonte, namespace ou procedimento.  
  
-   **Modificadores combinados.** Não é possível especificar `ReadOnly` junto com `Static` na mesma declaração.  
  
-   **Atribuir um valor.** Código consumindo um `ReadOnly` propriedade não é possível definir seu valor. Mas o código que tenha acesso ao armazenamento subjacente pode atribuir ou alterar o valor a qualquer momento.  
  
     Você pode atribuir um valor para um `ReadOnly` variável somente na sua declaração ou no construtor de uma classe ou estrutura na qual ela está definida.  
  
## <a name="when-to-use-a-readonly-variable"></a>Quando usar uma variável somente leitura  
 Há situações em que você não pode usar um [instrução Const](../../../visual-basic/language-reference/statements/const-statement.md) para declarar e atribua um valor constante. Por exemplo, o `Const` instrução pode não aceitar o tipo de dados que você deseja atribuir ou você não poderá calcular o valor em tempo de compilação com uma expressão constante. Você pode não saber até o valor em tempo de compilação. Nesses casos, você pode usar um `ReadOnly` variável para conter um valor constante.  
  
> [!IMPORTANT]
>  Se o tipo de dados da variável é um tipo de referência, como uma matriz ou uma instância da classe, seus membros podem ser alterados, mesmo se a variável em si é `ReadOnly`. O exemplo a seguir ilustra essa situação.  
  
 `ReadOnly characterArray() As Char = {"x"c, "y"c, "z"c}`  
  
 `Sub changeArrayElement()`  
  
 `characterArray(1) = "M"c`  
  
 `End Sub`  
  
 Quando inicializado, a matriz apontada por `characterArray()` mantém "x", "y" e "z". Porque a variável `characterArray` é `ReadOnly`, você não pode alterar seu valor quando ele é inicializado; o que é, você não pode atribuir uma nova matriz para ele. No entanto, você pode alterar os valores de um ou mais membros da matriz. Uma chamada para o procedimento a seguir `changeArrayElement`, a matriz apontada por `characterArray()` mantém "x", "M" e "z".  
  
 Observe que isso é semelhante ao declarar um parâmetro de procedimento ser [ByVal](../../../visual-basic/language-reference/modifiers/byval.md), que impede que o procedimento altere o argumento de chamada, mas permite que a mudança de seus membros.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir define uma `ReadOnly` propriedade para a data em que um funcionário foi contratado. Os armazenamentos de classe, o valor da propriedade internamente como um `Private` variável e apenas código dentro da classe pode alterar esse valor. No entanto, a propriedade é `Public`, e qualquer código que pode acessar a classe pode ler a propriedade.  
  
 [!code-vb[VbVbalrKeywords n º&4;](../../../visual-basic/language-reference/codesnippet/VisualBasic/readonly_1.vb)]  
  
 O `ReadOnly` modificador pode ser usado nesses contextos:  
  
 [Instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a>Consulte também  
 [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md)   
 [Palavras-chave](../../../visual-basic/language-reference/keywords/index.md)
