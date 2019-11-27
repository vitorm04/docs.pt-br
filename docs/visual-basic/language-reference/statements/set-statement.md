---
title: Instrução Set
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
ms.openlocfilehash: 75ad6d87f1785fea13a282d953f117c9c234e203
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349564"
---
# <a name="set-statement-visual-basic"></a>Instrução Set (Visual Basic)
Declara um procedimento de propriedade `Set` usado para atribuir um valor a uma propriedade.  
  
## <a name="syntax"></a>Sintaxe  
  
```vb  
[ <attributelist> ] [ accessmodifier ] Set (ByVal value [ As datatype ])  
    [ statements ]  
End Set  
```  
  
## <a name="parts"></a>Partes  
 `attributelist`  
 Opcional. Consulte a [lista de atributos](../../../visual-basic/language-reference/statements/attribute-list.md).  
  
 `accessmodifier`  
 Opcional em no máximo uma das instruções `Get` e `Set` nesta propriedade. Pode ser um dos seguintes:  
  
- [Protegido](../../../visual-basic/language-reference/modifiers/protected.md)  
  
- [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
- [Privado](../../../visual-basic/language-reference/modifiers/private.md)  
  
- `Protected Friend`  
  
 Consulte [níveis de acesso em Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 `value`  
 Necessária. Parâmetro que contém o novo valor para a propriedade.  
  
 `datatype`  
 Necessário se `Option Strict` for `On`. Tipo de dados do parâmetro `value`. O tipo de dados especificado deve ser o mesmo que o tipo de dados da propriedade em que essa instrução `Set` é declarada.  
  
 `statements`  
 Opcional. Uma ou mais instruções que são executadas quando o procedimento de propriedade de `Set` é chamado.  
  
 `End Set`  
 Necessária. Encerra a definição do procedimento da propriedade `Set`.  
  
## <a name="remarks"></a>Comentários  
 Cada propriedade deve ter um procedimento de propriedade `Set`, a menos que a propriedade seja marcada `ReadOnly`. O procedimento `Set` é usado para definir o valor da propriedade.  
  
 Visual Basic chama automaticamente o procedimento `Set` de uma propriedade quando uma instrução de atribuição fornece um valor a ser armazenado na propriedade.  
  
 Visual Basic passa um parâmetro para o procedimento `Set` durante as atribuições de propriedade. Se você não fornecer um parâmetro para `Set`, o ambiente de desenvolvimento integrado (IDE) usará um parâmetro implícito chamado `value`. O parâmetro contém o valor a ser atribuído à propriedade. Normalmente, você armazena esse valor em uma variável local privada e retorna-o sempre que o procedimento de `Get` é chamado.  
  
 O corpo da declaração de propriedade pode conter apenas os procedimentos `Get` e `Set` da propriedade entre a [instrução de propriedade](../../../visual-basic/language-reference/statements/property-statement.md) e a instrução `End Property`. Ele não pode armazenar nada além desses procedimentos. Em particular, ele não pode armazenar o valor atual da propriedade. Você deve armazenar esse valor fora da propriedade, porque se armazená-lo dentro de qualquer um dos procedimentos de propriedade, o outro procedimento de propriedade não poderá acessá-lo. A abordagem usual é armazenar o valor em uma variável [privada](../../../visual-basic/language-reference/modifiers/private.md) declarada no mesmo nível da propriedade. Você deve definir um procedimento `Set` dentro da propriedade à qual ele se aplica.  
  
 O procedimento `Set` assume como padrão o nível de acesso de sua propriedade contendo, a menos que você use `accessmodifier` na instrução `Set`.  
  
## <a name="rules"></a>Regras  
  
- **Níveis de acesso misto.** Se você estiver definindo uma propriedade de leitura/gravação, poderá opcionalmente especificar um nível de acesso diferente para o `Get` ou para o procedimento `Set`, mas não ambos. Se você fizer isso, o nível de acesso do procedimento deverá ser mais restritivo do que o nível de acesso da propriedade. Por exemplo, se a propriedade for declarada `Friend`, você poderá declarar o procedimento `Set` `Private`, mas não `Public`.  
  
     Se você estiver definindo uma propriedade `WriteOnly`, o procedimento `Set` representará a propriedade inteira. Você não pode declarar um nível de acesso diferente para `Set`, pois isso definiria dois níveis de acesso para a propriedade.  
  
## <a name="behavior"></a>Comportamento  
  
- **Retornando de um procedimento de propriedade.** Quando o procedimento de `Set` retorna ao código de chamada, a execução continua seguindo a instrução que forneceu o valor a ser armazenado.  
  
     `Set` procedimentos de propriedade podem ser retornados usando a [instrução return](../../../visual-basic/language-reference/statements/return-statement.md) ou a [instrução Exit](../../../visual-basic/language-reference/statements/exit-statement.md).  
  
     As instruções `Exit Property` e `Return` causam uma saída imediata de um procedimento de propriedade. Qualquer número de instruções `Exit Property` e `Return` pode aparecer em qualquer lugar no procedimento, e você pode misturar `Exit Property` e instruções `Return`.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa a instrução `Set` para definir o valor de uma propriedade.  
  
 [!code-vb[VbVbalrStatements#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#55)]  
  
## <a name="see-also"></a>Consulte também

- [Instrução Get](../../../visual-basic/language-reference/statements/get-statement.md)
- [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)
- [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Procedimentos de Propriedade](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
