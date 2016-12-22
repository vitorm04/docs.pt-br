---
title: "Como usar uma classe gen&#233;rica (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "parâmetros de tipo, definindo"
  - "argumentos de tipo de dados, definindo"
  - "argumentos [Visual Basic], tipos de dados"
  - "Palavra-chave, usando"
  - "parâmetros genéricos"
  - "parâmetros de tipo de dados"
  - "genéricos [Visual Basic], sobre genéricos"
  - "tipos de dados [Visual Basic], como parâmetros"
  - "tipos de dados [Visual Basic], como argumentos"
  - "parâmetros de tipo"
  - "tipos [Visual Basic] genéricos"
  - "parâmetros genéricos"
  - "genéricos [Visual Basic], Criando tipos genéricos"
  - "argumentos de tipo de dados"
  - "parâmetros de tipo de dados"
  - "parâmetros de tipo de dados, definindo"
  - "argumentos de tipo, definindo"
  - "os tipos de argumentos [Visual Basic]"
ms.assetid: 242dd2a6-86c4-4ce7-83f2-f2661803f752
caps.latest.revision: 24
caps.handback.revision: 24
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como usar uma classe gen&#233;rica (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Uma classe que usa *parâmetros de tipo* é chamado um *classe genérica*. Se você estiver usando uma classe genérica, você pode gerar um *classe construída* dela, fornecendo um *o argumento de tipo* para cada um desses parâmetros. Em seguida, você pode declarar uma variável do tipo de classe construído, e você pode criar uma instância da classe construída e atribuí-lo a essa variável.  
  
 Além de classes, você também pode definir e usar delegados, interfaces, procedimentos e estruturas genéricas.  
  
 O procedimento a seguir usa uma classe genérica definida no [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] e cria uma instância dele.  
  
### <a name="to-use-a-class-that-takes-a-type-parameter"></a>Para usar uma classe que leva um parâmetro de tipo  
  
1.  No início do seu arquivo de origem, inclua um [instrução Imports (tipo e Namespace .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) para importar o <xref:System.Collections.Generic?displayProperty=fullName> namespace. Isso permite que você consulte o <xref:System.Collections.Generic.Queue%601?displayProperty=fullName> classe sem precisar qualificar totalmente para diferenciá-la de outras classes de consulta, como <xref:System.Collections.Queue?displayProperty=fullName>.  
  
2.  Cria o objeto da forma normal, mas adiciona `(Of` `type``)` imediatamente após o nome da classe.  
  
     O exemplo a seguir usa a mesma classe (<xref:System.Collections.Generic.Queue%601?displayProperty=fullName>) para criar dois objetos de fila que mantêm itens de diferentes tipos de dados. Adiciona itens ao final de cada fila e, em seguida, remove e exibe itens da frente de cada fila.  
  
     [!code-vb[VbVbalrDataTypes#9](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/how-to-use-a-generic-class_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [Tipos genéricos no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [Independência da linguagem e componentes independentes de linguagem](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md)   
 [De](../../../../visual-basic/language-reference/statements/of-clause.md)   
 [Instrução Imports (tipo e Namespace .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)   
 [Como: definir uma classe que pode fornecer funcionalidade idêntica em diferentes tipos de dados](../Topic/How%20to:%20Define%20a%20Class%20That%20Can%20Provide%20Identical%20Functionality%20on%20Different%20Data%20Types%20\(Visual%20Basic\).md)   
 [Iteradores](../Topic/Iterators%20\(C%23%20and%20Visual%20Basic\).md)