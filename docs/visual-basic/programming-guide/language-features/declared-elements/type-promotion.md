---
title: Promoção de tipos (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declared elements [Visual Basic], scope
- visibility [Visual Basic], declared elements
- Partial keyword [Visual Basic], unexpected results with type promotion
- scope [Visual Basic], declared elements
- scope [Visual Basic], Visual Basic
- type promotion
- declared elements [Visual Basic], visibility
ms.assetid: 035eeb15-e4c5-4288-ab3c-6bd5d22f7051
ms.openlocfilehash: f7ac6bfb944da8bd50e035ba97b2b513176dc661
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61973297"
---
# <a name="type-promotion-visual-basic"></a>Promoção de tipos (Visual Basic)
Quando você declara um elemento de programação em um módulo, o Visual Basic promove seu escopo para o namespace que contém o módulo. Isso é conhecido como *promoção de tipos*.  
  
 O exemplo a seguir mostra uma definição de um módulo e dois membros de módulo.  
  
 [!code-vb[VbVbalrDeclaredElements#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#1)]  
  
 Dentro de `projModule`, programação elementos declarados no nível de módulo são promovidos para `projNamespace`. No exemplo anterior, `basicEnum` e `innerClass` são promovidos, mas `numberSub` não é, pois ele não está declarado no nível de módulo.  
  
## <a name="effect-of-type-promotion"></a>Efeito da promoção de tipo  
 O efeito da promoção de tipos é que uma cadeia de caracteres de qualificação não precisa incluir o nome do módulo. O exemplo a seguir faz duas chamadas para o procedimento no exemplo anterior.  
  
 [!code-vb[VbVbalrDeclaredElements#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#2)]  
  
 No exemplo anterior, a primeira chamada usa cadeias de caracteres de qualificação completa. No entanto, isso não é necessário devido a promoção de tipos. A segunda chamada também acessa os membros do módulo sem incluir `projModule` nas cadeias de caracteres de qualificação.  
  
## <a name="defeat-of-type-promotion"></a>Derrota da promoção de tipo  
 Se o namespace já tiver um membro com o mesmo nome como um membro de módulo, a promoção de tipos é derrotada por esse módulo associado. O exemplo a seguir mostra uma definição de módulo dentro do mesmo namespace e uma enumeração.  
  
 [!code-vb[VbVbalrDeclaredElements#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#3)]  
  
 No exemplo anterior, o Visual Basic não é possível promover a classe `abc` para `thisNameSpace` porque já existe uma enumeração com o mesmo nome no nível de namespace. Para acessar `abcSub`, você deve usar a cadeia de caracteres de qualificação completa `thisNamespace.thisModule.abc.abcSub`. No entanto, a classe `xyz` ainda for promovido, e você pode acessar `xyzSub` com a cadeia de caracteres mais curta qualificação `thisNamespace.xyz.xyzSub`.  
  
### <a name="defeat-of-type-promotion-for-partial-types"></a>Derrota da promoção de tipos para tipos parciais  
 Se uma classe ou estrutura dentro de um módulo usa a [parcial](../../../../visual-basic/language-reference/modifiers/partial.md) palavra-chave, a promoção de tipos é derrotada automaticamente por essa classe ou estrutura, se o namespace tem um membro com o mesmo nome. Outros elementos no módulo ainda estão qualificados para a promoção de tipos.  
  
 **Consequências.** Derrota da promoção de tipo de uma definição parcial pode causar resultados inesperados e até mesmo os erros de compilador. O exemplo a seguir mostra o esqueleto de definições parciais de uma classe, um dos quais é dentro de um módulo.  
  
 [!code-vb[VbVbalrDeclaredElements#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#4)]  
  
 No exemplo anterior, o desenvolvedor pode esperar o compilador para mesclar as duas definições parciais de `sampleClass`. No entanto, o compilador não considera a promoção para a definição parcial dentro `sampleModule`. Como resultado, ele tenta compilar duas classes separados e distintas, ambas chamadas `sampleClass` , mas com caminhos diferentes de qualificação.  
  
 O compilador mescla definições parciais somente quando seus caminhos totalmente qualificados são idênticos.  
  
## <a name="recommendations"></a>Recomendações  
 As recomendações a seguir representam uma boa prática de programação.  
  
- **Nomes exclusivos.** Quando você tem controle total sobre a nomeação de elementos de programação, é sempre uma boa ideia usar nomes exclusivos em todos os lugares. Nomes idênticos exigem qualificação extra e podem tornar seu código mais difícil de ler. Eles também podem levar a erros sutis e resultados inesperados.  
  
- **Qualificação completa.** Quando você estiver trabalhando com módulos e outros elementos no mesmo namespace, a abordagem mais segura é usar sempre qualificação completa para todos os elementos de programação. Se a promoção de tipos seja derrotada para um membro de módulo e você não qualificar totalmente esse membro, você poderá acessar inadvertidamente um elemento de programação diferente.  
  
## <a name="see-also"></a>Consulte também

- [Instrução Module](../../../../visual-basic/language-reference/statements/module-statement.md)
- [Instrução Namespace](../../../../visual-basic/language-reference/statements/namespace-statement.md)
- [Parcial](../../../../visual-basic/language-reference/modifiers/partial.md)
- [Escopo no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [Como: Controlar o escopo de uma variável](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md)
- [Referências a Elementos Declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
