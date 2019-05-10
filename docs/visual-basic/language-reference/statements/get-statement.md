---
title: Obter Statement (Visual Basic)
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
ms.openlocfilehash: 33fa6811f952d240fb86bbdf59ca83df0afc03ad
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64625523"
---
# <a name="get-statement"></a>Instrução Get
Declara um `Get` procedimento de propriedade usado para recuperar o valor de uma propriedade.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
[ <attributelist> ] [ accessmodifier ] Get()  
    [ statements ]  
End Get  
```  
  
## <a name="parts"></a>Partes  
  
|Termo|Definição|  
|---|---|  
|`attributelist`|Opcional. Ver [lista de atributos](../../../visual-basic/language-reference/statements/attribute-list.md).|  
|`accessmodifier`|Opcional no máximo um dos `Get` e `Set` as instruções nesta propriedade. Pode ser uma das seguintes opções:<br /><br /> -   [Protegido](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [privado](../../../visual-basic/language-reference/modifiers/private.md)<br />-   `Protected Friend`<br /><br /> Ver [acessar níveis no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|  
|`statements`|Opcional. Uma ou mais instruções que são executados quando o `Get` procedimento de propriedade é chamado.|  
|`End Get`|Necessário. Finaliza a definição do `Get` procedimento de propriedade.|  
  
## <a name="remarks"></a>Comentários  
 Cada propriedade deve ter uma `Get` procedimento de propriedade, a menos que a propriedade é marcada como `WriteOnly`. O `Get` procedimento é usado para retornar o valor atual da propriedade.  
  
 Visual Basic chama automaticamente uma propriedade `Get` procedimento quando uma expressão solicita o valor da propriedade.  
  
 O corpo da declaração de propriedade pode conter apenas da propriedade `Get` e `Set` procedimentos entre as [instrução Property](../../../visual-basic/language-reference/statements/property-statement.md) e o `End Property` instrução. Não é possível armazenar qualquer coisa além desses procedimentos. Em particular, ele não é possível armazenar o valor da propriedade atual. Você deve armazenar esse valor fora da propriedade, porque se você armazená-lo dentro de qualquer um dos procedimentos de propriedade, o outro procedimento de propriedade não é possível acessá-lo. A abordagem comum é armazenar o valor em uma [privada](../../../visual-basic/language-reference/modifiers/private.md) variável declarada no mesmo nível que a propriedade. Você deve definir um `Get` procedimento dentro da propriedade à qual se aplica.  
  
 O `Get` procedimento assume como padrão o nível de acesso de sua propriedade contendo a menos que você use `accessmodifier` no `Get` instrução.  
  
## <a name="rules"></a>Regras  
  
- **Níveis de acesso mistos.** Se você estiver definindo uma propriedade de leitura / gravação, você pode, opcionalmente, especificar um nível de acesso diferentes para qualquer um de `Get` ou o `Set` procedimento, mas não ambos. Se você fizer isso, o nível de acesso do procedimento deve ser mais restritivo do que o nível de acesso da propriedade. Por exemplo, se a propriedade é declarada `Friend`, você pode declarar o `Get` procedimento `Private`, mas não `Public`.  
  
     Se você estiver definindo uma `ReadOnly` propriedade, o `Get` procedimento representa a propriedade de inteira. Você não pode declarar um acesso a diferentes níveis para `Get`, pois isso configuraria dois níveis de acesso para a propriedade.  
  
- **Tipo de retorno.** O [declaração de propriedade](../../../visual-basic/language-reference/statements/property-statement.md) pode declarar o tipo de dados do valor que ele retorna. O `Get` procedimento retorna automaticamente esse tipo de dados. Você pode especificar qualquer tipo de dados ou o nome de uma enumeração, estrutura, classe ou interface.  
  
     Se o `Property` instrução não especifica `returntype`, o procedimento retornará `Object`.  
  
## <a name="behavior"></a>Comportamento  
  
- **Retornando de um procedimento.** Quando o `Get` procedimento retorna para o código de chamada, a execução continuará dentro da instrução que solicitou o valor da propriedade.  
  
     `Get` procedimentos de propriedade podem retornar um valor usando o [instrução Return](../../../visual-basic/language-reference/statements/return-statement.md) ou atribuindo o valor de retorno para o nome da propriedade. Para obter mais informações, consulte "Valor de retorno" em [instrução Function](../../../visual-basic/language-reference/statements/function-statement.md).  
  
     O `Exit Property` e `Return` instruções fazem com que uma saída imediata de um procedimento de propriedade. Qualquer número de `Exit Property` e `Return` instruções podem aparecer em qualquer lugar no procedimento, e você pode misturar `Exit Property` e `Return` instruções.  
  
- **Valor de retorno.** Para retornar um valor de uma `Get` procedimento, você pode atribuir o valor para o nome da propriedade ou incluí-lo em um [instrução Return](../../../visual-basic/language-reference/statements/return-statement.md). O `Return` instrução atribui simultaneamente o `Get` de valor e finaliza o procedimento de retorno de procedimento.  
  
     Se você usar `Exit Property` sem atribuir um valor para o nome da propriedade, o `Get` procedimento retorna o valor padrão para o tipo de dados da propriedade. Para obter mais informações, consulte "Valor de retorno" em [instrução Function](../../../visual-basic/language-reference/statements/function-statement.md).  
  
     O exemplo a seguir ilustra duas maneiras a propriedade somente leitura `quoteForTheDay` pode retornar o valor mantido na variável particular `quoteValue`.  
  
     [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]  
  
     [!code-vb[VbVbalrStatements#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#28)]  
  
     [!code-vb[VbVbalrStatements#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#29)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `Get` instrução para retornar o valor de uma propriedade.  
  
 [!code-vb[VbVbalrStatements#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#30)]  
  
## <a name="see-also"></a>Consulte também

- [Instrução Set](../../../visual-basic/language-reference/statements/set-statement.md)
- [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)
- [Instrução Exit](../../../visual-basic/language-reference/statements/exit-statement.md)
- [Objetos e Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [Passo a passo: Definindo Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/walkthrough-defining-classes.md)
