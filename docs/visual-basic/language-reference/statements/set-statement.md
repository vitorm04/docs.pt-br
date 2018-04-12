---
title: Instrução Set (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Set
helpviewer_keywords:
- property procedures [Visual Basic], Set statements
- Set statement [Visual Basic]
- Set statement [Visual Basic], syntax
- write-only properties
- properties [Visual Basic], write-only
ms.assetid: 9ecc27b4-df84-420d-9075-db25455fb3cd
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3b18e6c858e64e78d7ab85fdaafd70e510f7a02f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="set-statement-visual-basic"></a>Instrução Set (Visual Basic)
Declara uma `Set` procedimento de propriedade usado para atribuir um valor a uma propriedade.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
[ <attributelist> ] [ accessmodifier ] Set (ByVal value [ As datatype ])  
    [ statements ]  
End Set  
```  
  
## <a name="parts"></a>Partes  
 `attributelist`  
 Opcional. Consulte [lista de atributos](../../../visual-basic/language-reference/statements/attribute-list.md).  
  
 `accessmodifier`  
 Opcional no máximo uma da `Get` e `Set` instruções nesta propriedade. Pode ser um dos seguintes:  
  
-   [Protegido](../../../visual-basic/language-reference/modifiers/protected.md)  
  
-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
-   [Privado](../../../visual-basic/language-reference/modifiers/private.md)  
  
-   `Protected Friend`  
  
 Consulte [acessar níveis no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 `value`  
 Necessário. Parâmetro que contém o novo valor da propriedade.  
  
 `datatype`  
 Necessário se `Option Strict` é `On`. Tipo de dados a `value` parâmetro. O tipo de dados especificado deve ser o mesmo que o tipo de dados da propriedade onde isso `Set` instrução é declarada.  
  
 `statements`  
 Opcional. Uma ou mais instruções que são executados quando o `Set` é chamado de procedimento de propriedade.  
  
 `End Set`  
 Necessário. Finaliza a definição do `Set` procedimento de propriedade.  
  
## <a name="remarks"></a>Comentários  
 Cada propriedade deve ter uma `Set` procedimento de propriedade, a menos que a propriedade é marcada como `ReadOnly`. O `Set` procedimento é usado para definir o valor da propriedade.  
  
 Visual Basic chama automaticamente uma propriedade `Set` procedimento quando uma instrução de atribuição fornece um valor a ser armazenado na propriedade.  
  
 Visual Basic passa um parâmetro para o `Set` procedimento durante atribuições de propriedade. Se você não fornecer um parâmetro para `Set`, o ambiente de desenvolvimento integrado (IDE) usa uma parâmetro implícito denominada `value`. O parâmetro armazena o valor a ser atribuído à propriedade. Você normalmente armazena esse valor em uma variável local privada e retorná-lo sempre que o `Get` procedimento é chamado.  
  
 O corpo da declaração de propriedade pode conter apenas da propriedade `Get` e `Set` procedimentos entre o [declaração de propriedade](../../../visual-basic/language-reference/statements/property-statement.md) e `End Property` instrução. Não é possível armazenar nada além desses procedimentos. Em particular, não é possível armazenar o valor da propriedade atual. Você deve armazenar esse valor fora da propriedade, porque se você armazená-lo em qualquer um dos procedimentos de propriedade, o outro procedimento de propriedade não é possível acessá-lo. A abordagem comum é para armazenar o valor em uma [privada](../../../visual-basic/language-reference/modifiers/private.md) variável declarada no mesmo nível como a propriedade. Você deve definir um `Set` procedimento dentro da propriedade à qual se aplica.  
  
 O `Set` procedimento padrão é o nível de acesso da propriedade que o contém, a menos que você use `accessmodifier` no `Set` instrução.  
  
## <a name="rules"></a>Regras  
  
-   **Níveis de acesso mistos.** Se você estiver definindo uma propriedade de leitura / gravação, você pode especificar opcionalmente um nível de acesso diferentes para cada uma a `Get` ou `Set` procedimento, mas não ambos. Se você fizer isso, o nível de acesso do procedimento deve ser mais restritivo do que o nível de acesso da propriedade. Por exemplo, se a propriedade é declarada `Friend`, você pode declarar o `Set` procedimento `Private`, mas não `Public`.  
  
     Se você estiver definindo um `WriteOnly` propriedade, o `Set` procedimento representa a propriedade de inteira. Você não pode declarar um acesso a diferentes níveis de `Set`, pois isso configuraria dois níveis de acesso para a propriedade.  
  
## <a name="behavior"></a>Comportamento  
  
-   **Retornando a partir de um procedimento de propriedade.** Quando o `Set` procedimento retorna para o código de chamada, a execução continua seguindo a declaração que forneceu o valor a ser armazenado.  
  
     `Set`procedimentos de propriedade podem retornar usando o [instrução Return](../../../visual-basic/language-reference/statements/return-statement.md) ou [instrução Exit](../../../visual-basic/language-reference/statements/exit-statement.md).  
  
     O `Exit Property` e `Return` instruções causam uma saída imediata de um procedimento de propriedade. Qualquer número de `Exit Property` e `Return` instruções podem aparecer em qualquer lugar no procedimento, e você pode misturar `Exit Property` e `Return` instruções.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `Set` para definir o valor de uma propriedade.  
  
 [!code-vb[VbVbalrStatements#55](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/set-statement_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Get](../../../visual-basic/language-reference/statements/get-statement.md)  
 [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)  
 [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Procedimentos de Propriedade](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
