---
title: Partial (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Partial
- partial
dev_langs:
- VB
helpviewer_keywords:
- structures, partial
- classes [Visual Basic]
- partial, types [Visual Basic]
- partial, structures
- partial, classes [Visual Basic]
- classes [Visual Basic], partial
- Partial keyword [Visual Basic]
- type promotion
ms.assetid: 7adaef80-f435-46e1-970a-269fff63b448
caps.latest.revision: 36
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: b42752438e4f603029859d34031074f9e52c20d3
ms.lasthandoff: 03/13/2017

---
# <a name="partial-visual-basic"></a>Parcial (Visual Basic)
Indica que uma declaração de tipo é uma definição parcial do tipo.  
  
 Você pode dividir a definição de um tipo entre várias declarações usando o `Partial` palavra-chave. Você pode usar quantas declarações parciais conforme desejado, em quantos arquivos de origem diferentes conforme desejado. No entanto, todas as declarações devem estar no mesmo assembly e no mesmo namespace.  
  
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
|`accessmodifier`|Opcional. Especifica qual código pode acessar esse tipo. Consulte [acessar níveis no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|  
|`Shadows`|Opcional. Consulte [sombras](../../../visual-basic/language-reference/modifiers/shadows.md).|  
|`MustInherit`|Opcional. Consulte [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).|  
|`NotInheritable`|Opcional. Consulte [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md).|  
|`name`|Necessário. Nome desse tipo. Deve corresponder ao nome definido em todas as outras declarações parciais do mesmo tipo.|  
|`Of`|Opcional. Especifica que se trata de um tipo genérico. Consulte [tipos genéricos no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).|  
|`typelist`|Necessário se você usar [de](../../../visual-basic/language-reference/statements/of-clause.md). Consulte [digite lista](../../../visual-basic/language-reference/statements/type-list.md).|  
|`Inherits`|Opcional. Consulte [instrução Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md).|  
|`classname`|Necessário se você usar `Inherits`. O nome da classe ou da interface da qual essa classe deriva.|  
|`Implements`|Opcional. Consulte [implementa a instrução](../../../visual-basic/language-reference/statements/implements-statement.md).|  
|`interfacenames`|Necessário se você usar `Implements`. Os nomes das interfaces que esse tipo implementa.|  
|`variabledeclarations`|Opcional. Instruções que declaram variáveis adicionais e eventos para o tipo.|  
|`proceduredeclarations`|Opcional. Instruções que declare e definem procedimentos adicionais para o tipo.|  
|`End Class` ou `End Structure`|Termina a essa parcial `Class` ou `Structure` definição.|  
  
## <a name="remarks"></a>Comentários  
 Visual Basic usa definições de classe parcial para separar o código gerado de usuário-autoria código em arquivos de origem separado. Por exemplo, o **Windows Form Designer** define classes parciais para controles como <xref:System.Windows.Forms.Form>.</xref:System.Windows.Forms.Form> Você não deve modificar o código gerado nesses controles.  
  
 Todas as regras para a classe, estrutura, interface e criação de módulo, como aqueles para uso de modificador e herança, se aplicam ao criar um tipo parcial.  
  
## <a name="best-practices"></a>Práticas recomendadas  
  
-   Em circunstâncias normais, você não deve dividir o desenvolvimento de um único tipo entre dois ou mais declarações. Portanto, na maioria dos casos você não precisa de `Partial` palavra-chave.  
  
-   Para facilitar a leitura, cada declaração parcial de um tipo deve incluir o `Partial` palavra-chave. O compilador permite no máximo uma declaração parcial omitir a palavra-chave; Se dois ou mais omiti-lo o compilador sinaliza um erro.  
  
## <a name="behavior"></a>Comportamento  
  
-   **União de declaração.** O compilador trata o tipo como a união de todas as suas declarações parciais. Cada modificador de cada definição parcial aplica ao tipo de inteiro, e cada membro de cada definição parcial está disponível para o tipo inteiro.  
  
-   **Promoção de tipo não permitida para tipos parciais em módulos.** Se for uma definição parcial dentro de um módulo, promoção de tipo desse tipo será automaticamente derrotada. Nesse caso, um conjunto de definições parciais pode causar resultados inesperados e até mesmo erros de compilador. Para obter mais informações, consulte [promoção de tipo](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).  
  
     O compilador mescla definições parciais somente quando seus caminhos totalmente qualificados são idênticos.  
  
 O `Partial` palavra-chave pode ser usada nesses contextos:  
  
 [Instrução Class](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Instrução Structure](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir divide a definição de classe `sampleClass` em duas declarações, cada um deles define outro `Sub` procedimento.  
  
 [!code-vb[VbVbalrKeywords n º&3;](../../../visual-basic/language-reference/codesnippet/VisualBasic/partial_1.vb)]  
  
 As duas definições parciais no exemplo anterior pode ser no mesmo arquivo de origem ou em dois arquivos de origem diferentes.  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Class](../../../visual-basic/language-reference/statements/class-statement.md)   
 [Instrução Structure](../../../visual-basic/language-reference/statements/structure-statement.md)   
 [Promoção de tipo](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)   
 [Sombras](../../../visual-basic/language-reference/modifiers/shadows.md)   
 [Tipos genéricos no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [Métodos Parciais](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
