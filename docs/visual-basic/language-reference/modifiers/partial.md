---
title: Parcial (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Partial
- partial
helpviewer_keywords:
- structures [Visual Basic], partial
- classes [Visual Basic]
- partial, types [Visual Basic]
- partial, structures
- partial, classes [Visual Basic]
- classes [Visual Basic], partial
- Partial keyword [Visual Basic]
- type promotion
ms.assetid: 7adaef80-f435-46e1-970a-269fff63b448
ms.openlocfilehash: c94c3bf1a1e3e4c724f90690f52e97e8216cb9a7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="partial-visual-basic"></a>Parcial (Visual Basic)
Indica que uma declaração de tipo é uma definição parcial do tipo.  
  
 Você pode dividir a definição de um tipo entre várias declarações usando o `Partial` palavra-chave. Você pode usar quantas declarações parciais conforme desejado, em quantos arquivos de origem diferente conforme desejado. No entanto, todas as declarações devem estar no mesmo assembly e no mesmo namespace.  
  
> [!NOTE]
>  Visual Basic oferece suporte *métodos parciais*, que são normalmente implementado em classes parciais. Para obter mais informações, consulte [métodos parciais](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md) e [instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
[ <attrlist> ] [ accessmodifier ] [ Shadows ] [ MustInherit | NotInheritable ] _  
Partial { Class | Structure | Interface | Module } name [ (Of typelist) ]  
    [ Inherits classname ]  
    [ Implements interfacenames ]  
    [ variabledeclarations ]  
    [ proceduredeclarations ]  
{ End Class | End Structure }  
```  
  
## <a name="parts"></a>Partes  
  
|Termo|Definição|  
|---|---|  
|`attrlist`|Opcional. Lista de atributos que se aplicam a esse tipo. Você deve colocar o [a lista de atributos](../../../visual-basic/language-reference/statements/attribute-list.md) entre colchetes angulares (`< >`).|  
|`accessmodifier`|Opcional. Especifica o código pode acessar esse tipo. Consulte [acessar níveis no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|  
|`Shadows`|Opcional. Consulte [sombras](../../../visual-basic/language-reference/modifiers/shadows.md).|  
|`MustInherit`|Opcional. Consulte [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).|  
|`NotInheritable`|Opcional. Consulte [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md).|  
|`name`|Necessário. Nome deste tipo. Deve corresponder ao nome definido em todas as outras declarações parciais do mesmo tipo.|  
|`Of`|Opcional. Especifica que se trata de um tipo genérico. Consulte [tipos genéricos no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).|  
|`typelist`|Necessário se você usar [de](../../../visual-basic/language-reference/statements/of-clause.md). Consulte [digite lista](../../../visual-basic/language-reference/statements/type-list.md).|  
|`Inherits`|Opcional. Consulte [instrução Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md).|  
|`classname`|Necessário se você usar `Inherits`. O nome da classe ou interface da qual essa classe deriva.|  
|`Implements`|Opcional. Consulte [implementa a instrução](../../../visual-basic/language-reference/statements/implements-statement.md).|  
|`interfacenames`|Necessário se você usar `Implements`. Os nomes das interfaces que implementa esse tipo.|  
|`variabledeclarations`|Opcional. Instruções que declaram variáveis adicionais e eventos para o tipo.|  
|`proceduredeclarations`|Opcional. Instruções que declaram e definem procedimentos adicionais para o tipo.|  
|`End Class` ou `End Structure`|Encerra esta parcial `Class` ou `Structure` definição.|  
  
## <a name="remarks"></a>Comentários  
 Visual Basic usa definições de classe parcial para separar o código gerado no código de autoria do usuário nos arquivos de origem separados. Por exemplo, o **Windows Form Designer** define classes parciais para controles, como <xref:System.Windows.Forms.Form>. Você não deve modificar o código gerado nesses controles.  
  
 Todas as regras para a classe, estrutura, interface e criação de módulo, como aquelas para o uso de modificador e herança, se aplicam ao criar um tipo parcial.  
  
## <a name="best-practices"></a>Práticas recomendadas  
  
-   Em circunstâncias normais, você não deve dividir o desenvolvimento de um único tipo entre dois ou mais declarações. Portanto, na maioria dos casos você não precisa de `Partial` palavra-chave.  
  
-   Para facilitar a leitura, cada declaração parcial de um tipo deve incluir o `Partial` palavra-chave. O compilador permite no máximo uma declaração parcial omitir a palavra-chave; Se dois ou mais omiti-lo o compilador sinaliza um erro.  
  
## <a name="behavior"></a>Comportamento  
  
-   **União de declarações.** O compilador trata o tipo como a união de todas as suas declarações parciais. Cada modificador de cada definição parcial aplica-se ao tipo de inteiro e todos os membros de cada definição parcial estão disponível para o tipo inteiro.  
  
-   **Promoção de tipo não permitida para tipos parciais em módulos.** Se for uma definição parcial dentro de um módulo, promoção de tipo desse tipo é desfeita automaticamente. Nesse caso, um conjunto de definições parciais pode causar resultados inesperados e até mesmo erros de compilador. Para obter mais informações, consulte [promoção de tipo](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).  
  
     O compilador mescla definições parciais somente quando seus caminhos totalmente qualificados são idênticos.  
  
 O `Partial` palavra-chave pode ser usada nesses contextos:  
  
 [Instrução Class](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Instrução Structure](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir divide a definição de classe `sampleClass` em duas declarações, cada uma delas define outro `Sub` procedimento.  
  
 [!code-vb[VbVbalrKeywords#3](../../../visual-basic/language-reference/codesnippet/VisualBasic/partial_1.vb)]  
  
 As duas definições parciais no exemplo anterior podem ser no mesmo arquivo de origem ou em dois arquivos de origem diferente.  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Class](../../../visual-basic/language-reference/statements/class-statement.md)  
 [Instrução Structure](../../../visual-basic/language-reference/statements/structure-statement.md)  
 [Tipo de promoção](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)  
 [Sombras](../../../visual-basic/language-reference/modifiers/shadows.md)  
 [Tipos genéricos no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Métodos Parciais](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
