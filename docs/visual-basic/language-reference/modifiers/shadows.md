---
title: "Sombras (Visual Basic) | Microsoft Docs"
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
  - "vb.Shadows"
  - "shadows"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "nomes duplicados"
  - "nomes, sombreamento"
  - "escopo, sombreamento"
  - "sombreamento"
  - "palavra-chave Shadows"
ms.assetid: 6bf687cd-0544-4797-b51b-911125ec57c6
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Sombras (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Especifica que um elemento de programação declarado redeclara e oculta um elemento de nome idêntico, ou conjunto de elementos sobrecarregados, na classe base.  
  
## Comentários  
 O pricipal propósito do sombreamento \(também conhecido como *ocultar pelo nome*\) é preservar a definição de seus membros de classe.  A classe base pode passar por uma mudança que cria um elemento com o mesmo nome que o daquele que você já definiu.  Se isto acontecer, o modificador `Shadows` obriga referências através da sua classe a serem resolvidas ao membro que você definiu, em vez de ser ao novo elemento da classe base.  
  
 Tanto o sombreamento quanto a desautorização redefinem um elemento herdado, mas há diferenças significativas entre as duas abordagens.  Para obter mais informações, consulte [Sombreamento no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).  
  
## Regras  
  
-   **Contexto da Declaração.** Você pode usar `Shadows` somente no nível de classe.  Isso significa que o contexto da declaração para um elemento `Shadows` deve ser uma classe ou estrutura, e não um arquivo fonte, namespace, interface, módulo, estrutura ou procedimento.  
  
     Você pode declarar apenas um elemento de sombreamento numa única declaração de declaração.  
  
-   **Modificadores Combinados.** Não é possível especificar `Shadows` em conjunto com `Overloads`, `Overrides`, ou `Static` na mesma declaração.  
  
-   **Tipos de elemento.** Você pode sombrear qualquer tipo de elemento declarado com qualquer outro tipo.  Se você sombrear uma propriedade ou procedimento com outra propriedade ou procedimento, os parâmetros e o tipo de retorno não têm de se equiupararem na propriedade ou procedimento da classe base.  
  
-   **Acessando.** O elemento sombreado na classe base normalmente está indisponível de dentro da classe derivado que o sombreia.  Entretanto, as seguintes condições se aplicam.  
  
    -   Se o elemento sombreado não está acessível do código referindo\-se a ele, a referência é resolvida para o elemento sombreado.  Por exemplo, se um elemento `Private` sombreia um elemento da classe base, o código que não possui permissão para acessar o elemento `Private` acessa o elemento da classe base em vez disso.  
  
    -   Se você sombrear um elemento, você ainda pode acessar o elemento sombreado através de um objeto declarado com o tipo da classe base.  Você também pode acessá\-lo através de `MyBase`.  
  
 O modificador `Shadows` pode ser utilizado nestes contextos:  
  
 [Declaração de Classe](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Declaração Const](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Instrução Delegate](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [Esmaecer declaração](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Declaração Enum](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [Declaração de evento](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Instrução função](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Interface declaração](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [Propriedade declaração](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Instrução Structure](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## Consulte também  
 [Compartilhado](../../../visual-basic/language-reference/modifiers/shared.md)   
 [Estático](../../../visual-basic/language-reference/modifiers/static.md)   
 [Particular](../../../visual-basic/language-reference/modifiers/private.md)   
 [Me, My, MyBase e MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)   
 [Noções básicas de herança](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)   
 [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)   
 [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)   
 [Sobrecargas](../../../visual-basic/language-reference/modifiers/overloads.md)   
 [Substituível](../../../visual-basic/language-reference/modifiers/overridable.md)   
 [Substituições](../../../visual-basic/language-reference/modifiers/overrides.md)   
 [Sombreamento no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)