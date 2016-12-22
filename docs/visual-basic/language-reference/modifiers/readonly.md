---
title: "ReadOnly (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.ReadOnly"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "propriedades [Visual Basic], somente leitura"
  - "Palavra-chave ReadOnly"
  - "Propriedade ReadOnly"
  - "variáveis somente leitura"
  - "variáveis [Visual Basic], somente leitura"
ms.assetid: e868185d-6142-4359-a2fd-a7965cadfce8
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# ReadOnly (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Especifica que uma variável ou propriedade pode ser lido mas não gravada.  
  
## Comentários  
  
## Regras  
  
-   **Contexto da Declaração.** Você pode usar `ReadOnly` somente no nível de módulo.  Isso significa que o contexto da declaração para um `ReadOnly` elemento deve ser uma classe, estrutura ou módulo e não pode ser um arquivo de origem, o namespace ou o procedimento.  
  
-   **Modificadores Combinados.** Não é possível especificar `ReadOnly` em conjunto com `Static` na mesma declaração.  
  
-   **Atribuir um valor.** Código consumindo um `ReadOnly` propriedade não é possível definir seu valor.  Mas o código que tenha acesso ao armazenamento subjacente pode atribuir ou alterar o valor a qualquer momento.  
  
     Você pode atribuir um valor para um `ReadOnly` variáveis somente na sua declaração ou no construtor de uma classe ou estrutura na qual ela está definida.  
  
## Quando usar uma variável de somente leitura  
 Há situações em que você não pode usar um [Instrução Const](../../../visual-basic/language-reference/statements/const-statement.md) para declarar e atribuir um valor constante.  Por exemplo, o `Const` instrução poderá não aceitar o tipo de dados que você deseja atribuir ou você não poderá calcular o valor em tempo de compilação com uma expressão de constante.  Você pode nem mesmo saiba o valor em tempo de compilação.  Nesses casos, você pode usar um `ReadOnly` variável para armazenar um valor constante.  
  
> [!IMPORTANT]
>  Se o tipo de dados da variável é um tipo de referência, como, por exemplo, uma matriz ou uma instância de classe, seus membros podem ser alterados, mesmo se a variável em si é `ReadOnly`.  O exemplo a seguir ilustra isto:  
  
 `ReadOnly characterArray() As Char = {"x"c, "y"c, "z"c}`  
  
 `Sub changeArrayElement()`  
  
 `characterArray(1) = "M"c`  
  
 `End Sub`  
  
 Quando inicializado, a matriz apontada por `characterArray()` suspensões "x", "y" e "z".  Porque a variável `characterArray` é `ReadOnly`, você não pode alterar seu valor, uma vez que ele é inicializado; ou seja, você não pode atribuir uma nova matriz a ele.  No entanto, você pode alterar os valores de um ou mais dos membros da matriz.  Após uma chamada para o procedimento `changeArrayElement`, a matriz apontada por `characterArray()` suspensões "x", "M" e "z".  
  
 Observe que isso é semelhante ao declarar um parâmetro de procedimento para ser [ByVal](../../../visual-basic/language-reference/modifiers/byval.md), que impede que o procedimento alterando o próprio argumento de chamada, mas permite que ele altere seus membros.  
  
## Exemplo  
 O exemplo a seguir define uma `ReadOnly` propriedade para a data em que um funcionário foi contratado.  Os armazenamentos de classe, o valor da propriedade internamente como um `Private` código de variável e apenas dentro da classe pode alterar esse valor.  No entanto, a propriedade é `Public`, e qualquer código que pode acessar a classe pode ler a propriedade.  
  
 [!code-vb[VbVbalrKeywords#4](../../../visual-basic/language-reference/codesnippet/VisualBasic/readonly_1.vb)]  
  
 O modificador `ReadOnly` pode ser utilizado nestes contextos:  
  
 [Esmaecer declaração](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Propriedade declaração](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## Consulte também  
 [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md)   
 [Palavras\-chave](../../../visual-basic/language-reference/keywords/index.md)