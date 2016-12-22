---
title: "Operador New (Visual Basic) | Microsoft Docs"
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
  - "vb.new"
  - "vb.NewConstraint"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "restrições, palavra-chave New"
  - "restrições, tipos genéricos do Visual Basic"
  - "genéricos [Visual Basic], restrições"
  - "New constraint"
  - "palavra-chave New"
ms.assetid: d7d566d7-fe0e-4336-91f7-641a542de4d0
caps.latest.revision: 23
caps.handback.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Operador New (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Apresenta um `New` cláusula para criar uma nova instância do objeto, especifica uma restrição de construtor em um parâmetro de tipo ou identifica um `Sub` procedimento como um construtor de classe.  
  
## Comentários  
 Em uma declaração ou instrução de atribuição, um `New` cláusula deve especificar uma classe definida do qual a instância pode ser criada.  Isso significa que a classe deve expor um ou mais construtores que o código chamador pode acessar.  
  
 Você pode usar um `New` cláusula em uma instrução de declaração ou uma instrução de atribuição.  Quando a instrução é executado, ele chama o construtor apropriado da classe especificada, passando quaisquer argumentos que você forneceu.  O exemplo a seguir demonstra isso através da criação de instâncias de um `Customer` classe que tem dois construtores, sendo que um sem parâmetros e outro que aceita um parâmetro de seqüência de caracteres.  
  
 [!code-vb[VbVbalrKeywords#11](../../../visual-basic/language-reference/codesnippet/VisualBasic/new-operator_1.vb)]  
  
 Desde que as matrizes são classes, `New` pode criar uma nova instância de matriz, como mostrado nos exemplos a seguir.  
  
 [!code-vb[VbVbalrKeywords#12](../../../visual-basic/language-reference/codesnippet/VisualBasic/new-operator_2.vb)]  
  
 O common language runtime \(CLR\) lança um <xref:System.OutOfMemoryException> erro se não houver memória suficiente para criar a nova instância.  
  
> [!NOTE]
>  O `New` palavra\-chave também é usado nas listas de parâmetro de tipo para especificar que o tipo fornecido deve expor um construtor sem parâmetros acessível.  Para obter mais informações sobre parâmetros de tipo e restrições, consulte [Lista de tipos](../../../visual-basic/language-reference/statements/type-list.md).  
  
 Para criar um procedimento de construtor para uma classe, defina o nome de um `Sub` procedimento para o `New` palavra\-chave.  Para obter mais informações, consulte [Tempo de vida do objeto: como os objetos são criados e destruídos](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).  
  
 A palavra\-chave `New` pode ser usada nesses contextos:  
  
 [Instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Of](../../../visual-basic/language-reference/statements/of-clause.md)  
  
 [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## Consulte também  
 <xref:System.OutOfMemoryException>   
 [Palavras\-chave](../../../visual-basic/language-reference/keywords/index.md)   
 [Lista de tipos](../../../visual-basic/language-reference/statements/type-list.md)   
 [Tipos genéricos no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [Tempo de vida do objeto: como os objetos são criados e destruídos](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)