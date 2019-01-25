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
ms.openlocfilehash: 7a246e2565ec6d96e828654fef74500c4cf896b8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54627662"
---
# <a name="mustinherit-visual-basic"></a>MustInherit (Visual Basic)
Especifica que uma classe pode ser usada apenas como uma classe base e que não é possível criar um objeto diretamente a partir dele.  
  
## <a name="remarks"></a>Comentários  
 A finalidade de um *classe base* (também conhecido como um *classe abstrata*) é definir a funcionalidade comum a todas as classes derivadas dela. Isso salva as classes derivadas de ter que redefinir os elementos comuns. Em alguns casos, essa funcionalidade comum não está completa o suficiente para fazer um objeto utilizável e cada classe derivada define a funcionalidade ausente. Nesse caso, você deseja que o código para criar objetos somente de classes derivadas de consumo. Você usa `MustInherit` na classe base para impor isso.  
  
 Outro uso de um `MustInherit` classe é restringir a uma variável a um conjunto de classes relacionadas. Você pode definir uma classe base e derivar todas essas classes relacionadas ele. A classe base não precisa fornecer qualquer funcionalidade comum a todas as classes derivadas, mas ele pode servir como um filtro para atribuir valores a variáveis. Se seu código consumidor declara uma variável como a classe base, o Visual Basic permite que você atribuir apenas um objeto de uma das classes derivadas para a variável.  
  
 O .NET Framework define várias `MustInherit` classes, entre elas <xref:System.Array>, <xref:System.Enum>, e <xref:System.ValueType>. <xref:System.ValueType> é um exemplo de uma classe base que restringe a uma variável. Todos os tipos de valor derivam <xref:System.ValueType>. Se você declarar uma variável como <xref:System.ValueType>, você pode atribuir apenas os tipos de valor para a variável.  
  
## <a name="rules"></a>Regras  
  
-   **Contexto da declaração.** Você pode usar `MustInherit` somente em um `Class` instrução.  
  
-   **Modificadores combinados.** Não é possível especificar `MustInherit` junto com `NotInheritable` na mesma declaração.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra a herança forçada e o substituindo forçado. A classe base `shape` define uma variável `acrossLine`. As classes `circle` e `square` derivam `shape`. Eles herdam a definição de `acrossLine`, mas eles devem definir a função `area` porque esse cálculo é diferente para cada tipo de forma.  
  
 [!code-vb[VbVbalrKeywords#2](../../../visual-basic/language-reference/codesnippet/VisualBasic/mustinherit_1.vb)]  
  
 Você pode declarar `shape1` e `shape2` ser do tipo `shape`. No entanto, você não pode criar um objeto de `shape` porque ele não tem a funcionalidade da função `area` e é marcado como `MustInherit`.  
  
 Porque elas são declaradas como `shape`, as variáveis `shape1` e `shape2` são restritos aos objetos de classes derivadas `circle` e `square`. Visual Basic não permitem que você atribua qualquer outro objeto para essas variáveis, que lhe dá um alto nível de segurança de tipos.  
  
## <a name="usage"></a>Uso  
 O `MustInherit` modificador pode ser usado neste contexto:  
  
 [Instrução Class](../../../visual-basic/language-reference/statements/class-statement.md)  
  
## <a name="see-also"></a>Consulte também
- [Instrução Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md)
- [Palavras-chave](../../../visual-basic/language-reference/keywords/index.md)
- [Noções Básicas de Herança](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
