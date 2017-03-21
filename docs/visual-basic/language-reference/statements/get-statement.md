---
title: "Instrução Get | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Get
dev_langs:
- VB
helpviewer_keywords:
- Get statement, syntax
- Get statement
- properties [Visual Basic], read-only
- read-only properties
- Get keyword
- property procedures, Get statements
ms.assetid: 56b05cdc-bd64-4dfd-bb12-824eacec6f94
caps.latest.revision: 19
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: 8dbefcca3a83214997fd6bccdb5ef2788319899f
ms.lasthandoff: 03/13/2017

---
# <a name="get-statement"></a>Instrução Get
Declara um `Get` usado para recuperar o valor de uma propriedade do procedimento de propriedade.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
[ <attributelist> ] [ accessmodifier ] Get()  
    [ statements ]  
End Get  
```  
  
## <a name="parts"></a>Partes  
  
|Termo|Definição|  
|---|---|  
|`attributelist`|Opcional. Consulte [lista atributo](../../../visual-basic/language-reference/statements/attribute-list.md).|  
|`accessmodifier`|Opcional, no máximo uma do `Get` e `Set` instruções nessa propriedade. Pode ser uma das seguintes opções:<br /><br /> -   [Protegido](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [Privado](../../../visual-basic/language-reference/modifiers/private.md)<br />-   `Protected Friend`<br /><br /> Consulte [acessar níveis no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|  
|`statements`|Opcional. Uma ou mais declarações que executam quando o `Get` procedimento de propriedade é chamado.|  
|`End Get`|Necessário. Finaliza a definição de `Get` procedimento de propriedade.|  
  
## <a name="remarks"></a>Comentários  
 Cada propriedade deve ter uma `Get` procedimento de propriedade, a menos que a propriedade é marcada como `WriteOnly`. O `Get` procedimento é usado para retornar o valor atual da propriedade.  
  
 Visual Basic chama automaticamente uma propriedade `Get` procedimento quando uma expressão solicita o valor da propriedade.  
  
 O corpo da declaração de propriedade pode conter somente da propriedade `Get` e `Set` procedimentos entre o [declaração de propriedade](../../../visual-basic/language-reference/statements/property-statement.md) e `End Property` instrução. Não é possível armazenar nada além desses procedimentos. Em particular, não é possível armazenar o valor da propriedade atual. Você deve armazenar esse valor fora da propriedade, porque se você armazená-lo em qualquer um dos procedimentos de propriedade, o outro procedimento de propriedade não pode acessá-lo. A abordagem usual é armazenar o valor em uma [particular](../../../visual-basic/language-reference/modifiers/private.md) variável declarada no mesmo nível da propriedade. Você deve definir uma `Get` procedimento dentro da propriedade à qual se aplica.  
  
 O `Get` procedimento assume como padrão o nível de acesso da propriedade que contém a menos que você use `accessmodifier` no `Get` instrução.  
  
## <a name="rules"></a>Regras  
  
-   **Níveis de acesso mistos.** Se você estiver definindo uma propriedade de leitura / gravação, você pode opcionalmente especificar um nível de acesso diferente para o `Get` ou `Set` procedimento, mas não ambos. Se você fizer isso, o nível de acesso do procedimento deve ser mais restritivo do que o nível de acesso da propriedade. Por exemplo, se a propriedade é declarada `Friend`, você pode declarar o `Get` procedimento `Private`, mas não `Public`.  
  
     Se você estiver definindo um `ReadOnly` propriedade, o `Get` procedimento representa toda a propriedade. Você não pode declarar um acesso a diferentes níveis de `Get`, pois isso configuraria dois níveis de acesso para a propriedade.  
  
-   **Tipo de retorno.** O [declaração de propriedade](../../../visual-basic/language-reference/statements/property-statement.md) pode declarar o tipo de dados do valor que ele retorna. O `Get` procedimento retorna automaticamente esse tipo de dados. Você pode especificar qualquer tipo de dados ou o nome de uma enumeração, estrutura, classe ou interface.  
  
     Se o `Property` não especifica a instrução `returntype`, o procedimento retornará `Object`.  
  
## <a name="behavior"></a>Comportamento  
  
-   **Retornando a partir de um procedimento.** Quando o `Get` procedimento retorna para o código de chamada, a execução continua dentro da declaração que solicitou o valor da propriedade.  
  
     `Get`procedimentos de propriedade podem retornar um valor usando o [instrução Return](../../../visual-basic/language-reference/statements/return-statement.md) ou atribuindo o valor de retorno ao nome da propriedade. Para obter mais informações, consulte "Valor de retorno" em [declaração de função](../../../visual-basic/language-reference/statements/function-statement.md).  
  
     O `Exit Property` e `Return` instruções causam uma saída imediata de um procedimento de propriedade. Qualquer número de `Exit Property` e `Return` instruções podem aparecer em qualquer lugar no procedimento, e você pode misturar `Exit Property` e `Return` instruções.  
  
-   **Valor de retorno.** Para retornar um valor de uma `Get` procedimento, você pode atribuir o valor ao nome da propriedade ou incluí-lo em uma [instrução Return](../../../visual-basic/language-reference/statements/return-statement.md). O `Return` instrução atribui simultaneamente o `Get` valor e finaliza o procedimento de retorno de procedimento.  
  
     Se você usar `Exit Property` sem atribuir um valor ao nome da propriedade, o `Get` procedimento retorna o valor padrão para o tipo de dados da propriedade. Para obter mais informações, consulte "Valor de retorno" em [declaração de função](../../../visual-basic/language-reference/statements/function-statement.md).  
  
     O exemplo a seguir ilustra duas maneiras a propriedade somente leitura `quoteForTheDay` pode retornar o valor retido na variável privada `quoteValue`.  
  
     [!code-vb[VbVbalrStatements&#27;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/get-statement_1.vb)]  
  
     [!code-vb[VbVbalrStatements&#28;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/get-statement_2.vb)]  
  
     [!code-vb[29 VbVbalrStatements](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/get-statement_3.vb)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `Get` instrução para retornar o valor de uma propriedade.  
  
 [!code-vb[30 VbVbalrStatements](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/get-statement_4.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Set](../../../visual-basic/language-reference/statements/set-statement.md)   
 [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)   
 [Instrução Exit](../../../visual-basic/language-reference/statements/exit-statement.md)   
 [Objetos e Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)   
 [Instruções passo a passo: definindo classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/walkthrough-defining-classes.md)
