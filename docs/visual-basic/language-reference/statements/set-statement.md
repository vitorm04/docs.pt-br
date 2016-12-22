---
title: "Instru&#231;&#227;o Set (Visual Basic) | Microsoft Docs"
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
  - "vb.Set"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "propriedades [Visual Basic], somente gravação"
  - "procedimentos de propriedade, instruções Set"
  - "instrução Set"
  - "instrução Set, sintaxe"
  - "propriedades somente gravação"
ms.assetid: 9ecc27b4-df84-420d-9075-db25455fb3cd
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Instru&#231;&#227;o Set (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Declara um procedimento de propriedade `Set` usado para atribuir um valor a uma propriedade.  
  
## Sintaxe  
  
```  
[ <attributelist> ] [ accessmodifier ] Set (ByVal value [ As datatype ])  
    [ statements ]  
End Set  
```  
  
## Partes  
 `attributelist`  
 Opcional.  Veja [Lista de Atributos](../../../visual-basic/language-reference/statements/attribute-list.md).  
  
 `accessmodifier`  
 Opcional, em no máximo uma, das declarações `Get` e `Set` nessa propriedade.  Pode ser um dos seguintes:  
  
-   [Protegido](../../../visual-basic/language-reference/modifiers/protected.md)  
  
-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
-   [Private](../../../visual-basic/language-reference/modifiers/private.md)  
  
-   `Protected Friend`  
  
 Consulte [Níveis de acesso no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 `value`  
 Obrigatório.  Parâmetro contendo o novo valor para a propriedade.  
  
 `datatype`  
 Necessário se `Option Strict` estiver `On`.  Tipo de dado do parâmetro `value` O tipo de dado especificado deve ser o mesmo do tipo de dado da propriedade onde essa declaração `Set` for declarada.  
  
 `statements`  
 Opcional.  Uma ou mais declarações que executam quando o procedimento de propriedade `Set` for chamado.  
  
 `End Set`  
 Obrigatório.  Finaliza a definição do procedimento de propriedade `Set`.  
  
## Comentários  
 Cada propriedade deve ter uma procedimento de propriedade `Set` a não ser que a propriedade seja marcada como `ReadOnly`.  O procedimento `Set` é usado para determinar o valor da propriedade.  
  
 Visual Basic chama automaticamente um procedimento `Set` de propriedade quando uma declaração de atribuição fornece um valor para ser armazenado na propriedade.  
  
 Visual Basic passa um parâmetro para o procedimento `Set` durante atribuições de propriedade.  Se não for fornecido um parâmetro para `Set`, o ambiente de desenvolvimento integrado \(IDE\) usa uma parâmetro implícito de nome `value`.  O parâmetro armazena o valor a ser atribuído à propriedade.  Você, normalmente, armazena esse valor em uma variável local privada e o retorna quando o procedimento `Get` for chamado.  
  
 O corpo da declaração de propriedade pode conter somente os procedimentos `Get` e `Set` de propriedade entre [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md) e a declaração `End Property`.  Não é possível armazenar nada além desses procedimentos.  Em particular, não é possível armazenar o valor atual da propriedade.  Você deve armazenar esse valor fora da propriedade, pois se armazenar no interior de um dos procedimentos de propriedade, o outro procedimento de propriedade não poderá acessá\-lo.  A abordagem usual é armazenar o valor em uma variável [Particular](../../../visual-basic/language-reference/modifiers/private.md) declarada no mesmo nível da propriedade.  Você deve definir um procedimento `Set` no interior da propriedade para o qual se aplica.  
  
 O procedimento `Set` tem como padrão o nível de acesso da propriedade que o contém, a não ser que você usa `accessmodifier` na declaração `Set`.  
  
## Regras  
  
-   **Níveis de Acesso Mistos.** Se você estiver definindo uma propriedade de leitura\-gravação, opcionalmente, você pode especificar um nível de acesso diferente para cada uma a `Get` ou o `Set` procedimento, mas não ambos.  Se isso for feito, o nível de acesso do procedimento deve ser mais restritivo que o nível de acesso da propriedade.  Por exemplo, se a propriedade for declarada como `Friend`, você pode declarar o procedimento `Set` como `Private`, mas não como `Public`.  
  
     Se você estiver definindo uma propriedade `WriteOnly`, o procedimento `Set` representa a propriedade completa.  Você não pode declarar um nível de acesso diferente para `Set`, pois isso configuraria dois níveis de acesso para a propriedade.  
  
## Comportamento  
  
-   **Retornando a partir de um Procedimento de Propriedade.** Quando o `Set` procedimento retorna para o código de chamada, a execução continua após a instrução que forneceu o valor a ser armazenado.  
  
     Os procedimentos de propriedade `Set` podem retornar utilizando\-se [Instrução Return](../../../visual-basic/language-reference/statements/return-statement.md) ou [Instrução Exit](../../../visual-basic/language-reference/statements/exit-statement.md).  
  
     As declarações `Exit Property` e `Return` causam uma saída imediata do procedimento de propriedade.  Qualquer número de declarações `Exit Property` e `Return` pode aparecer em qualquer lugar no procedimento, e você pode misturar declarações `Exit Property` e `Return`.  
  
## Exemplo  
 O exemplo a seguir usa a declaração `Set` para configurar o valor de uma propriedade.  
  
 [!code-vb[VbVbalrStatements#55](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/set-statement_1.vb)]  
  
## Consulte também  
 [Instrução Get](../../../visual-basic/language-reference/statements/get-statement.md)   
 [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)   
 [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Procedimentos de propriedade](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)