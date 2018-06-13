---
title: MustInherit (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- MustInherit
- vb.MustInherit
helpviewer_keywords:
- classes [Visual Basic], abstract
- MustInherit classes [Visual Basic], MustInherit keyword
- abstract classes [Visual Basic], MustInherit class
- MustInherit keyword [Visual Basic]
ms.assetid: b8f05185-90e3-4dd7-adc2-90d852fab5b4
ms.openlocfilehash: 5d622c1cff77a45c8de7772af7efbb73586f4400
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33602834"
---
# <a name="mustinherit-visual-basic"></a>MustInherit (Visual Basic)
Especifica que uma classe pode ser usada somente como uma classe base e que não é possível criar um objeto diretamente dela.  
  
## <a name="remarks"></a>Comentários  
 A finalidade de um *classe base* (também conhecido como um *classe abstrata*) é definir a funcionalidade que é comum a todas as classes derivadas dela. Isso salva as classes derivadas de ter que redefinir os elementos comuns. Em alguns casos, essa funcionalidade comum não está completa para fazer um objeto utilizável, e cada classe derivada define a funcionalidade ausente. Nesse caso, você deseja que o código para criar objetos somente de classes derivadas. Você usa `MustInherit` na classe base para impor isso.  
  
 Outro uso de um `MustInherit` classe é restringir uma variável para um conjunto de classes relacionadas. Você pode definir uma classe base e derivam todas essas classes relacionadas ele. A classe base não precisa fornecer qualquer funcionalidade comum a todas as classes derivadas, mas pode servir como um filtro para atribuir valores a variáveis. Se o código declara uma variável como a classe base, o Visual Basic permite atribuir apenas um objeto de uma das classes derivadas para a variável.  
  
 O .NET Framework define vários `MustInherit` classes, entre eles <xref:System.Array>, <xref:System.Enum>, e <xref:System.ValueType>. <xref:System.ValueType> é um exemplo de uma classe base que restringe a uma variável. Todos os tipos de valor derivam <xref:System.ValueType>. Se você declarar uma variável como <xref:System.ValueType>, você pode atribuir apenas os tipos de valor para a variável.  
  
## <a name="rules"></a>Regras  
  
-   **Contexto de declaração.** Você pode usar `MustInherit` somente em um `Class` instrução.  
  
-   **Modificadores combinados.** Não é possível especificar `MustInherit` junto com `NotInheritable` na mesma declaração.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra a herança forçada e a substituição forçado. A classe base `shape` define uma variável `acrossLine`. As classes `circle` e `square` derivam `shape`. Eles herdam a definição de `acrossLine`, mas eles devem definir a função `area` porque esse cálculo é diferente para cada tipo de forma.  
  
 [!code-vb[VbVbalrKeywords#2](../../../visual-basic/language-reference/codesnippet/VisualBasic/mustinherit_1.vb)]  
  
 Você pode declarar `shape1` e `shape2` ser do tipo `shape`. No entanto, você não pode criar um objeto de `shape` porque ele não tem a funcionalidade da função `area` e está marcado como `MustInherit`.  
  
 Porque eles são declarados como `shape`, as variáveis `shape1` e `shape2` restrito a objetos das classes derivadas `circle` e `square`. Visual Basic não permitem que você atribua qualquer outro objeto essas variáveis, que dá a você um alto nível de segurança de tipo.  
  
## <a name="usage"></a>Uso  
 O `MustInherit` modificador pode ser usado neste contexto:  
  
 [Instrução Class](../../../visual-basic/language-reference/statements/class-statement.md)  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md)  
 [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md)  
 [Palavras-chave](../../../visual-basic/language-reference/keywords/index.md)  
 [Noções Básicas de Herança](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
