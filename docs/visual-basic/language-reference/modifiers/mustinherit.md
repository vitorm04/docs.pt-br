---
title: MustInherit (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- MustInherit
- vb.MustInherit
dev_langs:
- VB
helpviewer_keywords:
- classes [Visual Basic], abstract
- MustInherit classes, MustInherit keyword
- abstract classes, MustInherit class
- MustInherit keyword
ms.assetid: b8f05185-90e3-4dd7-adc2-90d852fab5b4
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
ms.openlocfilehash: 5f169a3e2e9a955266d03c1c577ed790167b874c
ms.lasthandoff: 03/13/2017

---
# <a name="mustinherit-visual-basic"></a>MustInherit (Visual Basic)
Especifica que uma classe pode ser usada somente como uma classe base e que você não pode criar um objeto diretamente dela.  
  
## <a name="remarks"></a>Comentários  
 A finalidade de um *classe base* (também conhecido como um *classe abstrata*) é definir a funcionalidade comum a todas as classes derivadas dela. Isso salva as classes derivadas de ter que redefinir os elementos comuns. Em alguns casos, essa funcionalidade comum não é completa para fazer um objeto utilizável, e cada classe derivada define a funcionalidade ausente. Nesse caso, convém que o código para criar objetos somente de classes derivadas. Você usa `MustInherit` na classe base para impor isso.  
  
 Outro uso de um `MustInherit` classe é restringir uma variável a um conjunto de classes relacionadas. Você pode definir uma classe base e derivam todas essas classes relacionadas ele. A classe base não precisa fornecer qualquer funcionalidade comum a todas as classes derivadas, mas pode servir como um filtro para atribuir valores a variáveis. Se seu código declara uma variável como a classe base, o Visual Basic permite atribuir apenas um objeto de uma das classes derivadas para a variável.  
  
 O .NET Framework define vários `MustInherit` classes, entre eles <xref:System.Array>, <xref:System.Enum>e <xref:System.ValueType>.</xref:System.ValueType> </xref:System.Enum> </xref:System.Array> <xref:System.ValueType>é um exemplo de uma classe base que restringe a uma variável.</xref:System.ValueType> Todos os tipos de valor derivam <xref:System.ValueType>.</xref:System.ValueType> Se você declarar uma variável como <xref:System.ValueType>, você pode atribuir apenas os tipos de valor para a variável.</xref:System.ValueType>  
  
## <a name="rules"></a>Regras  
  
-   **Contexto de declaração.** Você pode usar `MustInherit` somente em um `Class` instrução.  
  
-   **Modificadores combinados.** Não é possível especificar `MustInherit` junto com `NotInheritable` na mesma declaração.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra a herança forçada e a substituição forçado. A classe base `shape` define uma variável `acrossLine`. As classes `circle` e `square` derivam de `shape`. Eles herdam a definição de `acrossLine`, mas eles devem definir a função `area` porque esse cálculo é diferente para cada tipo de forma.  
  
 [!code-vb[VbVbalrKeywords n º&2;](../../../visual-basic/language-reference/codesnippet/VisualBasic/mustinherit_1.vb)]  
  
 Você pode declarar `shape1` e `shape2` para ser do tipo `shape`. No entanto, você não pode criar um objeto de `shape` porque ele não tem a funcionalidade da função `area` e está marcado como `MustInherit`.  
  
 Porque elas são declaradas como `shape`, as variáveis `shape1` e `shape2` são restritos aos objetos de classes derivadas `circle` e `square`. Visual Basic não permite atribuir qualquer outro objeto para essas variáveis, que oferece um alto nível de segurança de tipo.  
  
## <a name="usage"></a>Uso  
 O `MustInherit` modificador pode ser usado neste contexto:  
  
 [Instrução Class](../../../visual-basic/language-reference/statements/class-statement.md)  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md)   
 [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md)   
 [Palavras-chave](../../../visual-basic/language-reference/keywords/index.md)   
 [Noções Básicas de Herança](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
