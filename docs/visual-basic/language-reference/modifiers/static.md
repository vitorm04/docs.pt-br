---
title: "Estático (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Static
dev_langs:
- VB
helpviewer_keywords:
- static modifier
- Static keyword
ms.assetid: 19013910-4658-47b6-a22e-1744b527979e
caps.latest.revision: 22
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
ms.openlocfilehash: 328c754d16ab0ef654acd4bb82c5a557af16b05e
ms.lasthandoff: 03/13/2017

---
# <a name="static-visual-basic"></a>Estático (Visual Basic)
Especifica que um ou mais variáveis locais declaradas devem continuar a existir e manter seus valores mais recentes após o término do procedimento no qual elas são declaradas.  
  
## <a name="remarks"></a>Comentários  
 Normalmente, uma variável local em um procedimento deixa de existir assim que o procedimento para. Uma variável estática continua a existir e mantém seu valor mais recente. Na próxima vez em que seu código chama o procedimento, a variável não será reinicializada, e ela ainda mantém o valor mais recente que você atribuiu a ele. Uma variável estática continua a existir durante o tempo de vida da classe ou módulo que é definido em.  
  
## <a name="rules"></a>Regras  
  
-   **Contexto de declaração.** Você pode usar `Static` somente nas variáveis locais. Isso significa que o contexto da declaração para um `Static` variável deve ser um procedimento ou um bloco em um procedimento e não pode ser um arquivo fonte, namespace, classe, estrutura ou módulo.  
  
     Não é possível usar `Static` dentro de um procedimento de estrutura.  
  
-   Os tipos de dados de `Static` variáveis locais não podem ser inferidas. Para obter mais informações, consulte [inferência de tipo Local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).  
  
-   **Modificadores combinados.** Não é possível especificar `Static` junto com `ReadOnly`, `Shadows`, ou `Shared` na mesma declaração.  
  
## <a name="behavior"></a>Comportamento  
 Quando você declara uma variável estática em uma `Shared` procedimento, apenas uma cópia da variável estática está disponível para o aplicativo inteiro. Você chamar um `Shared` nome do procedimento, usando a classe, não uma variável que aponta para uma instância da classe.  
  
 Quando você declara uma variável estática em um procedimento que não seja `Shared`, somente uma cópia da variável está disponível para cada instância da classe. Você pode chamar um procedimento não compartilhado usando uma variável que aponta para uma instância específica da classe.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra o uso de `Static`.  
  
 [!code-vb[VbVbalrKeywords n º&5;](../../../visual-basic/language-reference/codesnippet/VisualBasic/static_1.vb)]  
  
 O `Static` variável `totalSales` foi inicializada para 0 somente uma vez. Cada vez que você inserir `updateSales`, `totalSales` ainda tem o valor mais recente que você calculou para ela.  
  
 O `Static` modificador pode ser usado neste contexto:  
  
 [Instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
## <a name="see-also"></a>Consulte também  
 [Sombras](../../../visual-basic/language-reference/modifiers/shadows.md)   
 [Compartilhado](../../../visual-basic/language-reference/modifiers/shared.md)   
 [Tempo de vida no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)   
 [Declaração de variável](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)   
 [Estruturas](../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Inferência de tipo local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Objetos e Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
