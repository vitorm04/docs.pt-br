---
title: Instrução Set (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Set
helpviewer_keywords:
- property procedures [Visual Basic], Set statements
- Set statement [Visual Basic]
- Set statement [Visual Basic], syntax
- write-only properties
- properties [Visual Basic], write-only
ms.assetid: 9ecc27b4-df84-420d-9075-db25455fb3cd
ms.openlocfilehash: 0a8d95ffbabf03a0e6c9d88edb28c248b60f3252
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58839074"
---
# <a name="set-statement-visual-basic"></a>Instrução Set (Visual Basic)
Declara um `Set` procedimento de propriedade usado para atribuir um valor a uma propriedade.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
[ <attributelist> ] [ accessmodifier ] Set (ByVal value [ As datatype ])  
    [ statements ]  
End Set  
```  
  
## <a name="parts"></a>Partes  
 `attributelist`  
 Opcional. Ver [lista de atributos](../../../visual-basic/language-reference/statements/attribute-list.md).  
  
 `accessmodifier`  
 Opcional no máximo um dos `Get` e `Set` as instruções nesta propriedade. Pode ser uma das seguintes opções:  
  
-   [Protegido](../../../visual-basic/language-reference/modifiers/protected.md)  
  
-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
-   [Privado](../../../visual-basic/language-reference/modifiers/private.md)  
  
-   `Protected Friend`  
  
 Ver [acessar níveis no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 `value`  
 Necessário. Parâmetro que contém o novo valor da propriedade.  
  
 `datatype`  
 Necessário se `Option Strict` é `On`. Tipo de dados do `value` parâmetro. O tipo de dados especificado deve ser o mesmo que o tipo de dados da propriedade em que isso `Set` instrução é declarada.  
  
 `statements`  
 Opcional. Uma ou mais instruções que são executados quando o `Set` procedimento de propriedade é chamado.  
  
 `End Set`  
 Necessário. Finaliza a definição do `Set` procedimento de propriedade.  
  
## <a name="remarks"></a>Comentários  
 Cada propriedade deve ter uma `Set` procedimento de propriedade, a menos que a propriedade é marcada como `ReadOnly`. O `Set` procedimento é usado para definir o valor da propriedade.  
  
 Visual Basic chama automaticamente uma propriedade `Set` procedimento quando uma instrução de atribuição fornece um valor a ser armazenado na propriedade.  
  
 Visual Basic passa um parâmetro para o `Set` procedimento durante atribuições de propriedade. Se você não fornecer um parâmetro para `Set`, o ambiente de desenvolvimento integrado (IDE) usa uma parâmetro implícito chamada `value`. O parâmetro contém o valor a ser atribuído à propriedade. Você normalmente armazena esse valor em uma variável local privada e retorná-lo sempre que o `Get` procedimento é chamado.  
  
 O corpo da declaração de propriedade pode conter apenas da propriedade `Get` e `Set` procedimentos entre as [instrução Property](../../../visual-basic/language-reference/statements/property-statement.md) e o `End Property` instrução. Não é possível armazenar qualquer coisa além desses procedimentos. Em particular, ele não é possível armazenar o valor da propriedade atual. Você deve armazenar esse valor fora da propriedade, porque se você armazená-lo dentro de qualquer um dos procedimentos de propriedade, o outro procedimento de propriedade não é possível acessá-lo. A abordagem comum é armazenar o valor em uma [privada](../../../visual-basic/language-reference/modifiers/private.md) variável declarada no mesmo nível que a propriedade. Você deve definir um `Set` procedimento dentro da propriedade à qual se aplica.  
  
 O `Set` procedimento assume como padrão o nível de acesso de sua propriedade contendo a menos que você use `accessmodifier` no `Set` instrução.  
  
## <a name="rules"></a>Regras  
  
-   **Níveis de acesso mistos.** Se você estiver definindo uma propriedade de leitura / gravação, você pode, opcionalmente, especificar um nível de acesso diferentes para qualquer um de `Get` ou o `Set` procedimento, mas não ambos. Se você fizer isso, o nível de acesso do procedimento deve ser mais restritivo do que o nível de acesso da propriedade. Por exemplo, se a propriedade é declarada `Friend`, você pode declarar o `Set` procedimento `Private`, mas não `Public`.  
  
     Se você estiver definindo uma `WriteOnly` propriedade, o `Set` procedimento representa a propriedade de inteira. Você não pode declarar um acesso a diferentes níveis para `Set`, pois isso configuraria dois níveis de acesso para a propriedade.  
  
## <a name="behavior"></a>Comportamento  
  
-   **Retornando de um procedimento de propriedade.** Quando o `Set` procedimento retorna para o código de chamada, a execução continua seguindo a declaração que forneceu o valor a ser armazenado.  
  
     `Set` procedimentos de propriedade podem retornar utilizando-se a [instrução Return](../../../visual-basic/language-reference/statements/return-statement.md) ou o [instrução Exit](../../../visual-basic/language-reference/statements/exit-statement.md).  
  
     O `Exit Property` e `Return` instruções fazem com que uma saída imediata de um procedimento de propriedade. Qualquer número de `Exit Property` e `Return` instruções podem aparecer em qualquer lugar no procedimento, e você pode misturar `Exit Property` e `Return` instruções.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `Set` instrução para definir o valor de uma propriedade.  
  
 [!code-vb[VbVbalrStatements#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#55)]  
  
## <a name="see-also"></a>Consulte também

- [Instrução Get](../../../visual-basic/language-reference/statements/get-statement.md)
- [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)
- [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Procedimentos de Propriedade](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
