---
title: "Como: usar uma classe genérica (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- type parameters, defining
- data type arguments, defining
- arguments [Visual Basic], data types
- Of keyword, using
- generic parameters
- data type parameters
- generics [Visual Basic], about generics
- data types [Visual Basic], as parameters
- data types [Visual Basic], as arguments
- parameters, type
- types [Visual Basic], generic
- parameters, generic
- generics [Visual Basic], creating generic types
- data type arguments
- parameters, data type
- data type parameters, defining
- type arguments, defining
- arguments [Visual Basic], type
ms.assetid: 242dd2a6-86c4-4ce7-83f2-f2661803f752
caps.latest.revision: 24
author: stevehoag
ms.author: shoag
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: eeb55be1c368e9ca80ab94de814a5e2ba9bc9f1f
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-use-a-generic-class-visual-basic"></a>Como usar uma classe genérica (Visual Basic)
Uma classe que usa *parâmetros de tipo* é chamado um *classe genérica*. Se você estiver usando uma classe genérica, você pode gerar um *classe construída* dela, fornecendo um *o argumento de tipo* para cada um desses parâmetros. Em seguida, você pode declarar uma variável do tipo de classe construído, e você pode criar uma instância da classe construída e atribuí-lo a essa variável.  
  
 Além de classes, você também pode definir e usar delegados, interfaces, procedimentos e estruturas genéricas.  
  
 O procedimento a seguir usa uma classe genérica definida no [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] e cria uma instância dele.  
  
### <a name="to-use-a-class-that-takes-a-type-parameter"></a>Para usar uma classe que leva um parâmetro de tipo  
  
1.  No início do seu arquivo de origem, inclua uma [instrução Imports (tipo e Namespace .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) para importar o <xref:System.Collections.Generic?displayProperty=fullName>namespace.</xref:System.Collections.Generic?displayProperty=fullName> Isso permite que você se referir à <xref:System.Collections.Generic.Queue%601?displayProperty=fullName>classe sem precisar qualificar totalmente para diferenciá-la de outras classes de consulta, como <xref:System.Collections.Queue?displayProperty=fullName>.</xref:System.Collections.Queue?displayProperty=fullName> </xref:System.Collections.Generic.Queue%601?displayProperty=fullName>  
  
2.  Cria o objeto da forma normal, mas adiciona `(Of` `type``)` imediatamente após o nome da classe.  
  
     O exemplo a seguir usa a mesma classe (<xref:System.Collections.Generic.Queue%601?displayProperty=fullName>) para criar dois objetos de fila que mantêm itens de diferentes tipos de dados.</xref:System.Collections.Generic.Queue%601?displayProperty=fullName> Adiciona itens ao final de cada fila e, em seguida, remove e exibe itens da frente de cada fila.  
  
     [!code-vb[VbVbalrDataTypes n º&9;](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/how-to-use-a-generic-class_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [Tipos genéricos no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [Independência da linguagem e componentes independentes de linguagem](https://msdn.microsoft.com/library/12a7a7h3)   
 [De](../../../../visual-basic/language-reference/statements/of-clause.md)   
 [Instrução Imports (tipo e Namespace .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)   
 [Como: definir uma classe que pode fornecer funcionalidade idêntica em diferentes tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md)   
 [Iteradores](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)
