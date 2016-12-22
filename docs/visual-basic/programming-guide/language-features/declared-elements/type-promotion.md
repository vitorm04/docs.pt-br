---
title: "Promo&#231;&#227;o de tipos (Visual Basic) | Microsoft Docs"
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
  - "elementos declarados, escopo"
  - "elementos declarados, visibilidade"
  - "Palavra-chave Partial, resultados inesperados com promoção de tipo"
  - "escopo, elementos declarados"
  - "escopo, Visual Basic"
  - "promoção de tipo"
  - "visibilidade, elementos declarados"
ms.assetid: 035eeb15-e4c5-4288-ab3c-6bd5d22f7051
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Promo&#231;&#227;o de tipos (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Quando você declara um elemento de programação em um módulo, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] promove seu escopo para o namespace que contém o módulo.  Isso é conhecido como *promoção de tipos*.  
  
 O exemplo a seguir mostra a definição do esqueleto de um módulo e dois membros desse módulo.  
  
 [!code-vb[VbVbalrDeclaredElements#1](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_1.vb)]  
  
 Em `projModule`, elementos de programação declarados no nível de módulo são promovidos para `projNamespace`.  No exemplo anterior, `basicEnum` e `innerClass` são promovidos, mas `numberSub` não é, pois ele não está declarado no nível de um módulo.  
  
## Efeito da Promoção de Tipo  
 O efeito da promoção de tipos é que uma sequência de qualificação não precisa incluir o nome do módulo.  O exemplo a seguir faz duas chamadas para o procedimento no exemplo anterior.  
  
 [!code-vb[VbVbalrDeclaredElements#2](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_2.vb)]  
  
 No exemplo anterior, a primeira chamada usa sequências de qualificação completa.  No entanto, isso não é necessário, por causa da promoção de tipos.  A segunda chamada também acessa os membros do módulo, sem incluir `projModule` nas sequências de qualificação.  
  
## Falha da Promoção de Tipo  
 Se o namespace já tiver um membro com o mesmo nome como um módulo membro, a promoção de tipos é derrotada por esse módulo associado.  O exemplo a seguir mostra um esqueleto da definição de uma enumeração e de um módulo no mesmo namespace.  
  
 [!code-vb[VbVbalrDeclaredElements#3](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_3.vb)]  
  
 No exemplo anterior, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], não é possível promover a classe `abc` para `thisNameSpace` pois já há uma enumeração com o mesmo nome no nível de namespace.  Para acessar `abcSub`, você deve usar a sequência completa de qualificação `thisNamespace.thisModule.abc.abcSub`.  No entanto, a classe `xyz` ainda é promovida, e você pode acessar `xyzSub` com a sequência de caracteres derrotada mais curta `thisNamespace.xyz.xyzSub`.  
  
### Derrota da Promoção de Tipos para Tipos Parciais  
 Se uma classe ou estrutura em um módulo usa a palavra\-chave [Parcial](../../../../visual-basic/language-reference/modifiers/partial.md), a promoção de tipos é derrotada automaticamente por essa classe ou estrutura, caso o namespace tenha um membro com o mesmo nome ou não.  Outros elementos no módulo ainda são qualificados para promoção de tipos.  
  
 **Consequências.** Derrota da promoção de tipos de uma definição parcial pode causar resultados inesperados e até mesmo erros de compilação.  O exemplo a seguir mostra o esqueleto de definições parciais de uma classe, uma das quais está em um módulo.  
  
 [!code-vb[VbVbalrDeclaredElements#4](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_4.vb)]  
  
 No exemplo anterior, o desenvolvedor pode esperar o compilador para mesclar as duas definições parciais de `sampleClass`.  No entanto, o compilador não considera a promoção para a definição parcial dentro de `sampleModule`.  Como resultado, ele tenta compilar duas classes separados e distintas, ambas chamadas `sampleClass`, mas com caminhos diferentes de qualificação.  
  
 O compilador mescla definições parciais somente quando seus caminhos totalmente qualificado são idênticos.  
  
## Recomendações  
 As recomendações a seguir representam boas práticas de programação.  
  
-   **Nomes exclusivos.** Quando você tem controle total sobre a nomeação de elementos de programação, é sempre uma boa ideia usar nomes exclusivos em todos os lugares.  Nomes idênticos exigem qualificação extra e podem tornar seu código mais difícil de ler.  Eles também podem levar a erros sutis e resultados inesperados.  
  
-   **Qualificação completa.** Quando você estiver trabalhando com módulos e outros elementos no mesmo namespace, a abordagem mais segura é usar sempre qualificação completa para todos os elementos de programação.  Se a promoção de tipos for derrotada por um membro de um módulo e você não qualificar esse membro totalmente, você poderá acessar inadvertidamente um elemento de programação diferente.  
  
## Consulte também  
 [Instrução Module](../../../../visual-basic/language-reference/statements/module-statement.md)   
 [Instrução Namespace](../../../../visual-basic/language-reference/statements/namespace-statement.md)   
 [Parcial](../../../../visual-basic/language-reference/modifiers/partial.md)   
 [Escopo no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)   
 [Como controlar o escopo de uma variável](../Topic/How%20to:%20Control%20the%20Scope%20of%20a%20Variable%20\(Visual%20Basic\).md)   
 [Referências a elementos declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)