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
ms.openlocfilehash: 9560faf90d531c32f104dbd053a7c1f5584cfb1b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351179"
---
# <a name="get-statement"></a>Instrução Get
Declara um procedimento de propriedade `Get` usado para recuperar o valor de uma propriedade.  
  
## <a name="syntax"></a>Sintaxe  
  
```vb  
[ <attributelist> ] [ accessmodifier ] Get()  
    [ statements ]  
End Get  
```  
  
## <a name="parts"></a>Partes  
  
|Termo|Definição|  
|---|---|  
|`attributelist`|Opcional. Consulte a [lista de atributos](../../../visual-basic/language-reference/statements/attribute-list.md).|  
|`accessmodifier`|Opcional em no máximo uma das instruções `Get` e `Set` nesta propriedade. Pode ser um dos seguintes:<br /><br /> -   [protegido](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [amigo](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [privado](../../../visual-basic/language-reference/modifiers/private.md)<br />-   `Protected Friend`<br /><br /> Consulte [níveis de acesso em Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|  
|`statements`|Opcional. Uma ou mais instruções que são executadas quando o procedimento de propriedade de `Get` é chamado.|  
|`End Get`|Necessária. Encerra a definição do procedimento da propriedade `Get`.|  
  
## <a name="remarks"></a>Comentários  
 Cada propriedade deve ter um procedimento de propriedade `Get`, a menos que a propriedade seja marcada `WriteOnly`. O procedimento `Get` é usado para retornar o valor atual da propriedade.  
  
 Visual Basic chama automaticamente o procedimento `Get` de uma propriedade quando uma expressão solicita o valor da propriedade.  
  
 O corpo da declaração de propriedade pode conter apenas os procedimentos `Get` e `Set` da propriedade entre a [instrução de propriedade](../../../visual-basic/language-reference/statements/property-statement.md) e a instrução `End Property`. Ele não pode armazenar nada além desses procedimentos. Em particular, ele não pode armazenar o valor atual da propriedade. Você deve armazenar esse valor fora da propriedade, porque se armazená-lo dentro de qualquer um dos procedimentos de propriedade, o outro procedimento de propriedade não poderá acessá-lo. A abordagem usual é armazenar o valor em uma variável [privada](../../../visual-basic/language-reference/modifiers/private.md) declarada no mesmo nível da propriedade. Você deve definir um procedimento `Get` dentro da propriedade à qual ele se aplica.  
  
 O procedimento `Get` assume como padrão o nível de acesso de sua propriedade contendo, a menos que você use `accessmodifier` na instrução `Get`.  
  
## <a name="rules"></a>Regras  
  
- **Níveis de acesso misto.** Se você estiver definindo uma propriedade de leitura/gravação, poderá opcionalmente especificar um nível de acesso diferente para o `Get` ou para o procedimento `Set`, mas não ambos. Se você fizer isso, o nível de acesso do procedimento deverá ser mais restritivo do que o nível de acesso da propriedade. Por exemplo, se a propriedade for declarada `Friend`, você poderá declarar o procedimento `Get` `Private`, mas não `Public`.  
  
     Se você estiver definindo uma propriedade `ReadOnly`, o procedimento `Get` representará a propriedade inteira. Você não pode declarar um nível de acesso diferente para `Get`, pois isso definiria dois níveis de acesso para a propriedade.  
  
- **Tipo de retorno.** A [instrução Property](../../../visual-basic/language-reference/statements/property-statement.md) pode declarar o tipo de dados do valor que ele retorna. O procedimento `Get` retorna automaticamente esse tipo de dados. Você pode especificar qualquer tipo de dados ou o nome de uma enumeração, estrutura, classe ou interface.  
  
     Se a instrução `Property` não especificar `returntype`, o procedimento retornará `Object`.  
  
## <a name="behavior"></a>Comportamento  
  
- **Retornando de um procedimento.** Quando o procedimento de `Get` retorna ao código de chamada, a execução continua dentro da instrução que solicitou o valor da propriedade.  
  
     `Get` procedimentos de propriedade podem retornar um valor usando a [instrução return](../../../visual-basic/language-reference/statements/return-statement.md) ou atribuindo o valor de retorno ao nome da propriedade. Para obter mais informações, consulte "valor de retorno" na [instrução function](../../../visual-basic/language-reference/statements/function-statement.md).  
  
     As instruções `Exit Property` e `Return` causam uma saída imediata de um procedimento de propriedade. Qualquer número de instruções `Exit Property` e `Return` pode aparecer em qualquer lugar no procedimento, e você pode misturar `Exit Property` e instruções `Return`.  
  
- **Valor de retorno.** Para retornar um valor de um procedimento `Get`, você pode atribuir o valor ao nome da propriedade ou incluí-lo em uma [instrução return](../../../visual-basic/language-reference/statements/return-statement.md). A instrução `Return` atribui simultaneamente o valor de retorno do procedimento `Get` e sai do procedimento.  
  
     Se você usar `Exit Property` sem atribuir um valor ao nome da propriedade, o procedimento `Get` retornará o valor padrão para o tipo de dados da propriedade. Para obter mais informações, consulte "valor de retorno" na [instrução function](../../../visual-basic/language-reference/statements/function-statement.md).  
  
     O exemplo a seguir ilustra duas maneiras como a propriedade somente leitura `quoteForTheDay` pode retornar o valor mantido na variável privada `quoteValue`.  
  
     [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]  
  
     [!code-vb[VbVbalrStatements#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#28)]  
  
     [!code-vb[VbVbalrStatements#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#29)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa a instrução `Get` para retornar o valor de uma propriedade.  
  
 [!code-vb[VbVbalrStatements#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#30)]  
  
## <a name="see-also"></a>Consulte também

- [Instrução Set](../../../visual-basic/language-reference/statements/set-statement.md)
- [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)
- [Instrução Exit](../../../visual-basic/language-reference/statements/exit-statement.md)
- [Objetos e Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [Instruções passo a passo: definindo classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/walkthrough-defining-classes.md)
