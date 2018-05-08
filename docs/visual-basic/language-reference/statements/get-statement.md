---
title: Instrução Get
ms.date: 07/20/2015
f1_keywords:
- vb.Get
helpviewer_keywords:
- Get statement [Visual Basic], syntax
- Get statement [Visual Basic]
- properties [Visual Basic], read-only
- read-only properties
- Get keyword [Visual Basic]
- property procedures [Visual Basic], Get statements
ms.assetid: 56b05cdc-bd64-4dfd-bb12-824eacec6f94
ms.openlocfilehash: d6a6fdfd191de76871619dea3bd1794b487698aa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="get-statement"></a>Instrução Get
Declara uma `Get` procedimento de propriedade usado para recuperar o valor de uma propriedade.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
[ <attributelist> ] [ accessmodifier ] Get()  
    [ statements ]  
End Get  
```  
  
## <a name="parts"></a>Partes  
  
|Termo|Definição|  
|---|---|  
|`attributelist`|Opcional. Consulte [lista de atributos](../../../visual-basic/language-reference/statements/attribute-list.md).|  
|`accessmodifier`|Opcional no máximo uma da `Get` e `Set` instruções nesta propriedade. Pode ser um dos seguintes:<br /><br /> -   [Protegido](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [Privada](../../../visual-basic/language-reference/modifiers/private.md)<br />-   `Protected Friend`<br /><br /> Consulte [acessar níveis no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|  
|`statements`|Opcional. Uma ou mais instruções que são executados quando o `Get` é chamado de procedimento de propriedade.|  
|`End Get`|Obrigatório. Finaliza a definição do `Get` procedimento de propriedade.|  
  
## <a name="remarks"></a>Comentários  
 Cada propriedade deve ter uma `Get` procedimento de propriedade, a menos que a propriedade é marcada como `WriteOnly`. O `Get` procedimento é usado para retornar o valor atual da propriedade.  
  
 Visual Basic chama automaticamente uma propriedade `Get` procedimento quando uma expressão solicita o valor da propriedade.  
  
 O corpo da declaração de propriedade pode conter apenas da propriedade `Get` e `Set` procedimentos entre o [declaração de propriedade](../../../visual-basic/language-reference/statements/property-statement.md) e `End Property` instrução. Não é possível armazenar nada além desses procedimentos. Em particular, não é possível armazenar o valor da propriedade atual. Você deve armazenar esse valor fora da propriedade, porque se você armazená-lo em qualquer um dos procedimentos de propriedade, o outro procedimento de propriedade não é possível acessá-lo. A abordagem comum é para armazenar o valor em uma [privada](../../../visual-basic/language-reference/modifiers/private.md) variável declarada no mesmo nível como a propriedade. Você deve definir um `Get` procedimento dentro da propriedade à qual se aplica.  
  
 O `Get` procedimento padrão é o nível de acesso da propriedade que o contém, a menos que você use `accessmodifier` no `Get` instrução.  
  
## <a name="rules"></a>Regras  
  
-   **Níveis de acesso mistos.** Se você estiver definindo uma propriedade de leitura / gravação, você pode especificar opcionalmente um nível de acesso diferentes para cada uma a `Get` ou `Set` procedimento, mas não ambos. Se você fizer isso, o nível de acesso do procedimento deve ser mais restritivo do que o nível de acesso da propriedade. Por exemplo, se a propriedade é declarada `Friend`, você pode declarar o `Get` procedimento `Private`, mas não `Public`.  
  
     Se você estiver definindo um `ReadOnly` propriedade, o `Get` procedimento representa a propriedade de inteira. Você não pode declarar um acesso a diferentes níveis de `Get`, pois isso configuraria dois níveis de acesso para a propriedade.  
  
-   **Tipo de retorno.** O [declaração de propriedade](../../../visual-basic/language-reference/statements/property-statement.md) pode declarar o tipo de dados do valor que ele retorna. O `Get` procedimento retorna automaticamente esse tipo de dados. Você pode especificar qualquer tipo de dados ou o nome de uma enumeração, estrutura, classe ou interface.  
  
     Se o `Property` instrução não especificar `returntype`, o procedimento retornará `Object`.  
  
## <a name="behavior"></a>Comportamento  
  
-   **Retornando a partir de um procedimento.** Quando o `Get` procedimento retorna para o código de chamada, a execução continua dentro da declaração que solicitou o valor da propriedade.  
  
     `Get` procedimentos de propriedade podem retornar um valor usando o [instrução Return](../../../visual-basic/language-reference/statements/return-statement.md) ou atribuindo o valor de retorno para o nome da propriedade. Para obter mais informações, consulte "Valor de retorno" em [instrução Function](../../../visual-basic/language-reference/statements/function-statement.md).  
  
     O `Exit Property` e `Return` instruções causam uma saída imediata de um procedimento de propriedade. Qualquer número de `Exit Property` e `Return` instruções podem aparecer em qualquer lugar no procedimento, e você pode misturar `Exit Property` e `Return` instruções.  
  
-   **Valor de retorno.** Para retornar um valor de um `Get` procedimento, você pode atribuir o valor para o nome da propriedade ou incluí-lo em uma [instrução Return](../../../visual-basic/language-reference/statements/return-statement.md). O `Return` instrução simultaneamente atribui o `Get` procedimento retorna o valor e finaliza o procedimento.  
  
     Se você usar `Exit Property` sem atribuir um valor para o nome da propriedade, o `Get` procedimento retorna o valor padrão para o tipo de dados. Para obter mais informações, consulte "Valor de retorno" em [instrução Function](../../../visual-basic/language-reference/statements/function-statement.md).  
  
     O exemplo a seguir ilustra duas maneiras a propriedade somente leitura `quoteForTheDay` pode retornar o valor armazenado na variável particular `quoteValue`.  
  
     [!code-vb[VbVbalrStatements#27](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/get-statement_1.vb)]  
  
     [!code-vb[VbVbalrStatements#28](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/get-statement_2.vb)]  
  
     [!code-vb[VbVbalrStatements#29](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/get-statement_3.vb)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `Get` instrução para retornar o valor de uma propriedade.  
  
 [!code-vb[VbVbalrStatements#30](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/get-statement_4.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Set](../../../visual-basic/language-reference/statements/set-statement.md)  
 [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)  
 [Instrução Exit](../../../visual-basic/language-reference/statements/exit-statement.md)  
 [Objetos e Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [Instruções passo a passo: definindo classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/walkthrough-defining-classes.md)
