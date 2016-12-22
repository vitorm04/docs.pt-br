---
title: "Instru&#231;&#227;o Module | Microsoft Docs"
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
  - "Module"
  - "vb.Module"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "classes [Visual Basic], x módulos"
  - "declarações, módulos"
  - "instrução Module"
  - "módulos"
  - "módulos, classes"
  - "módulos, declarando"
  - "módulos padrão"
ms.assetid: a1243afc-14a5-45df-95d5-51118aeac362
caps.latest.revision: 24
caps.handback.revision: 24
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Instru&#231;&#227;o Module
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Declara o nome de um módulo e introduz a definição de variáveis, propriedades, eventos e procedimentos que compõem o módulo.  
  
## Sintaxe  
  
```  
[ <attributelist> ] [ accessmodifier ]  Module name  
    [ statements ]  
End Module  
```  
  
## Partes  
 `attributelist`  
 Opcional.  Consulte [Lista de atributos](../../../visual-basic/language-reference/statements/attribute-list.md).  
  
 `accessmodifier`  
 Opcional.  Pode ser um dos seguintes:  
  
-   [Público](../../../visual-basic/language-reference/modifiers/public.md)  
  
-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
 Consulte [Níveis de acesso no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 `name`  
 Obrigatório.  Nome deste módulo.  Consulte [Nomes de elemento declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
 `statements`  
 Opcional.  As instruções que defina as variáveis, propriedades, eventos, procedimentos e tipos aninhados deste módulo.  
  
 `End Module`  
 Finaliza a definição `Module`.  
  
## Comentários  
 Uma instrução `Module` define um tipo de referência disponível em todo o namespace.  Um *módulo* \(às vezes chamado de  *módulo padrão* \)  é semelhante a uma classe, mas com algumas distinções importantes.  Cada módulo tem exatamente uma instância e não precisa ser criada ou atribuída a uma variável.  Módulos não oferecem suporte à heranças ou implementam interfaces.  Observe que um módulo é não um *tipo* no sentido de que uma classe ou estrutura é — você não pode declarar um elemento de programação para ter o tipo de dados de um módulo.  
  
 Você pode usar `Module` somente no nível de namespace.  Isso significa que o *contexto da declaração*  para um módulo deve ser um arquivo fonte ou namespace, e não pode ser uma classe, estrutura, módulo, procedimento, interface ou bloco.  Você não é possível aninhar um módulo dentro de um outro módulo, ou em qualquer tipo.  Para obter mais informações, consulte [Contextos de declaração e níveis de acesso padrão](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Um módulo tem o mesmo tempo de vida que seu programa.  Como seus membros são todos `Shared`, eles também têm vida útil igual a do programa.  
  
 Os módulos têm como padrão acesso [Friend](../../../visual-basic/language-reference/modifiers/friend.md).  Você pode ajustar os seus níveis de acesso com os modificadores de acesso.  Para obter mais informações, consulte [Níveis de acesso no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 Todos os membros de um módulo são implicitamente `Shared`.  
  
## Classes e Módulos  
 Esses elementos têm várias semelhanças, mas há algumas diferenças importantes também.  
  
-   **Terminologia.** Versões anteriores do Visual Basic reconhecem dois tipos de módulos:  *módulos de classe* \(arquivos. CLS\) e  *módulos padrão* \(arquivos. bas\).  A versão atual os chama de *classes* e  *módulos* , respectivamente.  
  
-   **Membros compartilhados.** Você pode controlar se um membro de uma classe é um membro compartilhado ou de instância.  
  
-   **Orientação a Objeto** Classes são orientadas a objeto, mas módulos não são.  Portanto, apenas classes podem ser instanciadas como objetos.  Para obter mais informações, consulte [Objetos e classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).  
  
## Regras  
  
-   **Modificador.** Todos os membros de módulo são implicitamente [Compartilhado](../../../visual-basic/language-reference/modifiers/shared.md).  Você não pode usar a palavra\-chave `Shared` quando declarar um membro, e você não pode alterar o status compartilhado de nenhum membro.  
  
-   **Herança.** Um módulo não pode herdar de qualquer tipo diferente de <xref:System.Object>, do quais todos os módulos herdam.  Em particular, um módulo não pode herdar de outro.  
  
     Você não pode usar [Instrução Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md) em uma definição de módulo, mesmo que seja para especificar <xref:System.Object>.  
  
-   **Propriedade padrão.** Você não pode definir as propriedades padrão em um módulo.  Para obter mais informações, consulte [Padrão](../../../visual-basic/language-reference/modifiers/default.md).  
  
## Comportamento  
  
-   **Nível de acesso.** Dentro de um módulo, você pode declarar cada membro com seu próprio nível de acesso.  Módulo membros tem acesso [Público](../../../visual-basic/language-reference/modifiers/public.md) como padrão, exceto as variáveis e constantes, que têm acesso [Particular](../../../visual-basic/language-reference/modifiers/private.md) como padrão.  Quando um módulo tem mais acesso restrito que um de seus membros, o nível de acesso especificado do módulo tem precedência.  
  
-   **Escopo.** Um módulo está no escopo em todo seu namespace.  
  
     O escopo de cada membro de módulo é todo o módulo.  Observe que todos os membros sofrem *promoção de tipos*,que faz com que o escopo seja promovido para o namespace que contém o módulo.  Para obter mais informações, consulte [Promoção de tipos](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).  
  
-   **Qualificação** Você pode ter vários módulos em um projeto, e você pode declarar membros com o mesmo nome em dois ou mais módulos.  No entanto, você deverá qualificar qualquer referência a esse membro com o nome do módulo apropriado se a referência estiver fora desse módulo.  Para obter mais informações, consulte [Referências a elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
## Exemplo  
 [!code-vb[VbVbalrStatements#69](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/module-statement_1.vb)]  
  
## Consulte também  
 [Instrução Class](../../../visual-basic/language-reference/statements/class-statement.md)   
 [Instrução Namespace](../../../visual-basic/language-reference/statements/namespace-statement.md)   
 [Instrução Structure](../../../visual-basic/language-reference/statements/structure-statement.md)   
 [Instrução Interface](../../../visual-basic/language-reference/statements/interface-statement.md)   
 [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)   
 [Promoção de tipos](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)