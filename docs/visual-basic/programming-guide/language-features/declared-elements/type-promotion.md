---
title: "Tipo de promoção (Visual Basic) | Documentos do Microsoft"
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
- declared elements, scope
- visibility, declared elements
- Partial keyword, unexpected results with type promotion
- scope, declared elements
- scope, Visual Basic
- type promotion
- declared elements, visibility
ms.assetid: 035eeb15-e4c5-4288-ab3c-6bd5d22f7051
caps.latest.revision: 17
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
ms.openlocfilehash: d732e765fc28eaedc0deab477dbf9955a40e97c9
ms.lasthandoff: 03/13/2017

---
# <a name="type-promotion-visual-basic"></a>Promoção de tipos (Visual Basic)
Quando você declarar um elemento de programação em um módulo [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] promove seu escopo para o namespace que contém o módulo. Isso é conhecido como *promoção de tipo*.  
  
 O exemplo a seguir mostra uma definição de um módulo e dois membros desse módulo.  
  
 [!code-vb[VbVbalrDeclaredElements n º&1;](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_1.vb)]  
  
 Dentro de `projModule`, programação elementos declarados no nível de módulo são promovidos para `projNamespace`. No exemplo anterior, `basicEnum` e `innerClass` são promovidos, mas `numberSub` não é, pois ele não está declarado no nível de módulo.  
  
## <a name="effect-of-type-promotion"></a>Efeito da promoção de tipo  
 O efeito da promoção de tipos é que uma cadeia de caracteres de qualificação não precisa incluir o nome do módulo. O exemplo a seguir faz duas chamadas para o procedimento no exemplo anterior.  
  
 [!code-vb[VbVbalrDeclaredElements n º&2;](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_2.vb)]  
  
 No exemplo anterior, a primeira chamada usa cadeias de caracteres de qualificação completa. No entanto, isso não é necessário devido a promoção de tipos. A segunda chamada também acessa os membros do módulo sem incluir `projModule` nas sequências de qualificação.  
  
## <a name="defeat-of-type-promotion"></a>Derrota da promoção de tipo  
 Se o namespace já tiver um membro com o mesmo nome como um módulo membro, a promoção de tipos é derrotada por esse módulo associado. O exemplo a seguir mostra uma definição de uma enumeração e um módulo no mesmo namespace.  
  
 [!code-vb[VbVbalrDeclaredElements n º&3;](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_3.vb)]  
  
 No exemplo anterior, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] não é possível promover a classe `abc` para `thisNameSpace` porque já existe uma enumeração com o mesmo nome no nível de namespace. Para acessar `abcSub`, você deve usar a cadeia de caracteres de qualificação completa `thisNamespace.thisModule.abc.abcSub`. No entanto, a classe `xyz` ainda é promovida, e você pode acessar `xyzSub` com a cadeia de caracteres de qualificação mais curta `thisNamespace.xyz.xyzSub`.  
  
### <a name="defeat-of-type-promotion-for-partial-types"></a>Derrota da promoção de tipos para tipos parciais  
 Se uma classe ou estrutura em um módulo usa o [parcial](../../../../visual-basic/language-reference/modifiers/partial.md) palavra-chave, a promoção de tipos é derrotada automaticamente por essa classe ou estrutura, se o namespace tenha um membro com o mesmo nome ou não. Outros elementos no módulo ainda são qualificados para promoção de tipos.  
  
 **Consequências.** Derrota da promoção de tipos de uma definição parcial pode causar resultados inesperados e até mesmo erros de compilador. O exemplo a seguir mostra o esqueleto de definições parciais de uma classe, um deles é dentro de um módulo.  
  
 [!code-vb[VbVbalrDeclaredElements n º&4;](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_4.vb)]  
  
 No exemplo anterior, o desenvolvedor pode esperar o compilador para mesclar as duas definições parciais de `sampleClass`. No entanto, o compilador não considera a promoção para a definição parcial dentro de `sampleModule`. Como resultado, ele tenta compilar duas classes separados e distintas, ambas chamadas `sampleClass` , mas com caminhos diferentes de qualificação.  
  
 O compilador mescla definições parciais somente quando seus caminhos totalmente qualificados são idênticos.  
  
## <a name="recommendations"></a>Recomendações  
 As recomendações a seguir representam uma boa prática de programação.  
  
-   **Nomes exclusivos.** Quando você tem controle total sobre a nomeação de elementos de programação, é sempre uma boa ideia usar nomes exclusivos em todos os lugares. Nomes idênticos exigem qualificação extra e podem tornar seu código mais difícil de ler. Eles também podem levar a erros sutis e resultados inesperados.  
  
-   **Qualificação completa.** Quando você estiver trabalhando com módulos e outros elementos no mesmo namespace, a abordagem mais segura é usar sempre qualificação completa para todos os elementos de programação. Se a promoção de tipos é derrotada por um membro de módulo e você não qualificar esse membro totalmente, você poderá acessar inadvertidamente um elemento de programação diferente.  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Module](../../../../visual-basic/language-reference/statements/module-statement.md)   
 [Instrução Namespace](../../../../visual-basic/language-reference/statements/namespace-statement.md)   
 [Parcial](../../../../visual-basic/language-reference/modifiers/partial.md)   
 [Escopo no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)   
 [Como: controlar o escopo de uma variável](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md)   
 [Referências a Elementos Declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
