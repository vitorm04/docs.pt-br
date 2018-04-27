---
title: Promoção de tipos (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- declared elements [Visual Basic], scope
- visibility [Visual Basic], declared elements
- Partial keyword [Visual Basic], unexpected results with type promotion
- scope [Visual Basic], declared elements
- scope [Visual Basic], Visual Basic
- type promotion
- declared elements [Visual Basic], visibility
ms.assetid: 035eeb15-e4c5-4288-ab3c-6bd5d22f7051
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ddb0d61f0f1c94e8e28493d0c62afe1e09503804
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="type-promotion-visual-basic"></a>Promoção de tipos (Visual Basic)
Quando você declara um elemento de programação em um módulo, o Visual Basic promove seu escopo para o namespace que contém o módulo. Isso é conhecido como *promoção de tipo*.  
  
 O exemplo a seguir mostra uma definição de um módulo e dois membros desse módulo.  
  
 [!code-vb[VbVbalrDeclaredElements#1](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_1.vb)]  
  
 Dentro de `projModule`, programação elementos declarados no nível de módulo são promovidos para `projNamespace`. No exemplo anterior, `basicEnum` e `innerClass` são promovidos, mas `numberSub` não é, pois ele não está declarado no nível de módulo.  
  
## <a name="effect-of-type-promotion"></a>Efeito da promoção de tipo  
 O efeito da promoção de tipos é que uma cadeia de caracteres de qualificação não precisa incluir o nome do módulo. O exemplo a seguir faz duas chamadas para o procedimento no exemplo anterior.  
  
 [!code-vb[VbVbalrDeclaredElements#2](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_2.vb)]  
  
 No exemplo anterior, a primeira chamada usa cadeias de caracteres de qualificação completa. No entanto, isso não é necessário devido a promoção de tipo. A segunda chamada também acessa os membros do módulo sem incluir `projModule` nas cadeias de qualificação.  
  
## <a name="defeat-of-type-promotion"></a>Falha da promoção de tipo  
 Se o namespace já tiver um membro com o mesmo nome como um módulo membro, a promoção de tipo é desfeita por esse módulo associado. O exemplo a seguir mostra uma definição de uma enumeração e um módulo no mesmo namespace.  
  
 [!code-vb[VbVbalrDeclaredElements#3](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_3.vb)]  
  
 No exemplo anterior, o Visual Basic não é possível promover a classe `abc` para `thisNameSpace` porque já existe uma enumeração com o mesmo nome no nível de namespace. Para acessar `abcSub`, você deve usar a cadeia de caracteres de qualificação completa `thisNamespace.thisModule.abc.abcSub`. No entanto, a classe `xyz` ainda é promovida, e você pode acessar `xyzSub` com a cadeia de caracteres de qualificação mais curto `thisNamespace.xyz.xyzSub`.  
  
### <a name="defeat-of-type-promotion-for-partial-types"></a>Falha da promoção de tipo para tipos parciais  
 Se uma classe ou estrutura em um módulo usa o [parcial](../../../../visual-basic/language-reference/modifiers/partial.md) palavra-chave, promoção de tipo é desfeita automaticamente por essa classe ou estrutura, se o espaço para nome tem um membro com o mesmo nome ou não. Outros elementos no módulo ainda são qualificados para promoção de tipo.  
  
 **Consequências.** Falha da promoção de tipo de uma definição parcial pode causar resultados inesperados e até mesmo erros de compilador. O exemplo a seguir mostra as definições parciais de esqueleto de uma classe, um dos quais está dentro de um módulo.  
  
 [!code-vb[VbVbalrDeclaredElements#4](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_4.vb)]  
  
 No exemplo anterior, o desenvolvedor pode esperar o compilador para mesclar as duas definições parciais de `sampleClass`. No entanto, o compilador não considera a promoção para a definição parcial dentro `sampleModule`. Como resultado, ele tenta compilar duas classes separados e distintos, ambos nomeados `sampleClass` , mas com caminhos diferentes de qualificação.  
  
 O compilador mescla definições parciais somente quando seus caminhos totalmente qualificados são idênticos.  
  
## <a name="recommendations"></a>Recomendações  
 As recomendações a seguir representam uma boa prática de programação.  
  
-   **Nomes exclusivos.** Quando você tem controle total sobre a nomeação de elementos de programação, é sempre uma boa ideia usar nomes exclusivos em todos os lugares. Nomes idênticos exigem qualificação extra e podem tornar mais difícil de ler seu código. Eles também podem levar a erros sutis e resultados inesperados.  
  
-   **Total de qualificação.** Quando você estiver trabalhando com módulos e outros elementos no mesmo namespace, a abordagem mais segura é usar sempre qualificação completa de todos os elementos de programação. Se a promoção de tipo é desfeita para um membro de módulo e você não qualificar esse membro totalmente, você poderá acessar inadvertidamente um elemento de programação diferente.  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Module](../../../../visual-basic/language-reference/statements/module-statement.md)  
 [Instrução Namespace](../../../../visual-basic/language-reference/statements/namespace-statement.md)  
 [Parcial](../../../../visual-basic/language-reference/modifiers/partial.md)  
 [Escopo no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)  
 [Como controlar o escopo de uma variável](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md)  
 [Referências a Elementos Declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
