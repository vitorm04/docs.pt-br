---
title: "Est&#225;tico (Visual Basic) | Microsoft Docs"
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
  - "vb.Static"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "palavra-chave Static"
  - "modificador estático"
ms.assetid: 19013910-4658-47b6-a22e-1744b527979e
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Est&#225;tico (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Especifica que uma ou mais variáveis locais declaradas devem continuar a existir e manter seus valores mais recentes após o término do procedimento no qual elas são declaradas.  
  
## Comentários  
 Normalmente, uma variável local em um procedimento deixa de existir assim que o procedimento pára.  Uma variável estática continua a existir e mantém seu valor mais recente.  Na próxima vez em que seu código chamar o procedimento, a variável não será reinicializada, e ele ainda conterá o valor mais recente que você atribuiu a ela.  Uma variável estática continua a existir durante o tempo de vida da classe ou do módulo no qual ela está definida.  
  
## Regras.  
  
-   **Contexto da Declaração.** Você pode usar `Static` somente em variáveis locais.  Isso significa que o contexto da declaração para uma variável `Static` deve ser um procedimento ou um bloco em um procedimento, e ele não pode ser um arquivo de origem, namespace, classe, estrutura ou módulo.  
  
     Não é possível usar `Static` dentro de um procedimento de estrutura.  
  
-   Os tipos de dados de variáveis locais `Static` não podem ser inferidos.  Para mais informações, consulte [Inferência de tipo local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).  
  
-   **Modificadores Combinados.** Não é possível especificar `Static` com `ReadOnly`, `Shadows`, ou `Shared` na mesma declaração.  
  
## Comportamento  
 Quando você declara uma variável estática em uma `Shared` procedimento, somente uma cópia da variável estática está disponível para o aplicativo inteiro.  Você chamar um `Shared` nome do procedimento, usando a classe, não uma variável que aponta para uma instância da classe.  
  
 Quando você declara uma variável estática em um procedimento que não `Shared`, somente uma cópia da variável está disponível para cada instância da classe.  Chamar um procedimento não compartilhado usando uma variável que aponta para uma instância específica da classe.  
  
## Exemplo  
 O exemplo a seguir demonstra o uso de `Static`.  
  
 [!code-vb[VbVbalrKeywords#5](../../../visual-basic/language-reference/codesnippet/VisualBasic/static_1.vb)]  
  
 A variável `Static` `totalSales` foi inicializada para 0 somente uma vez.  Cada vez que você inserir `updateSales`,`totalSales` ainda tem o valor mais recente que você calculou para ela.  
  
 O modificador `Static` pode ser utilizado neste contexto:  
  
 [Instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
## Consulte também  
 [Sombras](../../../visual-basic/language-reference/modifiers/shadows.md)   
 [Compartilhado](../../../visual-basic/language-reference/modifiers/shared.md)   
 [Tempo de vida no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)   
 [Declaração de variável](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)   
 [Estruturas](../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Inferência de tipo local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Objetos e classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)