---
title: Instrução Class (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Class
helpviewer_keywords:
- class modules
- Class statement [Visual Basic]
- classes [Visual Basic], fields
- fields [Visual Basic], of classes
- class types [Visual Basic], class statements
- classes [Visual Basic], creating
- classes [Visual Basic], data members
- data members [Visual Basic], of classes
ms.assetid: f2664f38-eb5a-4d4b-a374-1d041521fb6c
ms.openlocfilehash: 2346823e7b774c21171bd81023cc5b920d34d19a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="class-statement-visual-basic"></a>Instrução Class (Visual Basic)
Declara o nome de uma classe e introduz a definição de variáveis, propriedades, eventos e procedimentos que compõem a classe.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
[ <attributelist> ] [ accessmodifier ] [ Shadows ] [ MustInherit | NotInheritable ] [ Partial ] _  
Class name [ ( Of typelist ) ]  
    [ Inherits classname ]  
    [ Implements interfacenames ]  
    [ statements ]  
End Class  
```  
  
## <a name="parts"></a>Partes  
  
|Termo|Definição|  
|---|---|  
|`attributelist`|Opcional. Consulte [lista de atributos](../../../visual-basic/language-reference/statements/attribute-list.md).|  
|`accessmodifier`|Opcional. Pode ser um dos seguintes:<br /><br /> -   [Público](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [Protegido](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [Privada](../../../visual-basic/language-reference/modifiers/private.md)<br />-   `Protected Friend`<br /><br /> Consulte [acessar níveis no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|  
|`Shadows`|Opcional. Consulte [sombras](../../../visual-basic/language-reference/modifiers/shadows.md).|  
|`MustInherit`|Opcional. Consulte [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).|  
|`NotInheritable`|Opcional. Consulte [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md).|  
|`Partial`|Opcional. Indica uma definição parcial da classe. Consulte [parcial](../../../visual-basic/language-reference/modifiers/partial.md).|  
|`name`|Necessário. Nome desta classe. Consulte [declarado nomes de elemento](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`Of`|Opcional. Especifica que esta é uma classe genérica.|  
|`typelist`|Necessário se você usar o [de](../../../visual-basic/language-reference/statements/of-clause.md) palavra-chave. Lista de parâmetros de tipo para esta classe. Consulte [digite lista](../../../visual-basic/language-reference/statements/type-list.md).|  
|`Inherits`|Opcional. Indica que esta classe herda os membros de outra classe. Consulte [instrução Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md).|  
|`classname`|Necessário se você usar o `Inherits` instrução. O nome da classe da qual essa classe deriva.|  
|`Implements`|Opcional. Indica que esta classe implementa os membros de uma ou mais interfaces. Consulte [implementa a instrução](../../../visual-basic/language-reference/statements/implements-statement.md).|  
|`interfacenames`|Necessário se você usar o `Implements` instrução. Os nomes das interfaces que essa classe implementa.|  
|`statements`|Opcional. Instruções que definem os membros dessa classe.|  
|`End Class`|Necessário. Encerra o `Class` definição.|  
  
## <a name="remarks"></a>Comentários  
 Um `Class` instrução define um novo tipo de dados. Um *classe* é um componente fundamental de programação orientada a objeto (OOP). Para obter mais informações, consulte [objetos e Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).  
  
 Você pode usar `Class` apenas no nível de namespace ou módulo. Isso significa que o *contexto declaração* para uma classe deve ser um arquivo de origem, namespace, classe, estrutura, módulo ou interface e não pode ser um procedimento ou bloco. Para obter mais informações, consulte [Contextos de declaração e níveis de acesso padrão](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Cada instância de uma classe tem um tempo de vida independente de todas as outras instâncias. Esse tempo de vida começa quando ela é criada por um [novo operador](../../../visual-basic/language-reference/operators/new-operator.md) cláusula ou por uma função, como <xref:Microsoft.VisualBasic.Interaction.CreateObject%2A>. Termina quando todas as variáveis que apontam para a instância tem sido definidas a [nada](../../../visual-basic/language-reference/nothing.md) ou instâncias de outras classes.  
  
 Classes de padrão para [Friend](../../../visual-basic/language-reference/modifiers/friend.md) acesso. Você pode ajustar os níveis de acesso com os modificadores de acesso. Para obter mais informações, consulte [acessar níveis no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="rules"></a>Regras  
  
-   **Aninhamento.** Você pode definir uma classe dentro de outra. A classe externa é chamada de *que contém a classe*, e a classe interna é chamada uma *as classes aninhadas*.  
  
-   **Herança.** Se a classe usa a [herda instrução](../../../visual-basic/language-reference/statements/inherits-statement.md), você pode especificar apenas uma classe base ou interface. Uma classe não pode herdar de mais de um elemento.  
  
     Uma classe não pode herdar de outra classe com um nível de acesso mais restritivo. Por exemplo, um `Public` classe não pode herdar de um `Friend` classe.  
  
     Uma classe não pode herdar de uma classe aninhada dentro dele.  
  
-   **Implementação.** Se a classe usa a [instrução Implements](../../../visual-basic/language-reference/statements/implements-statement.md), você deve implementar cada membro definido em cada interface que você especificar na `interfacenames`. Uma exceção a isso é Reimplementação de um membro de classe base. Para obter mais informações, consulte "Reimplementação" [implementa](../../../visual-basic/language-reference/statements/implements-clause.md).  
  
-   **Propriedade padrão.** Uma classe pode especificar no máximo uma propriedade como seu *propriedade padrão*. Para obter mais informações, consulte [padrão](../../../visual-basic/language-reference/modifiers/default.md).  
  
## <a name="behavior"></a>Comportamento  
  
-   **Nível de acesso.** Dentro de uma classe, você pode declarar cada membro com seu próprio nível de acesso. Membros de classe padrão [pública](../../../visual-basic/language-reference/modifiers/public.md) acessar, exceto as variáveis e constantes, padrão para [privada](../../../visual-basic/language-reference/modifiers/private.md) acesso. Quando uma classe tem mais acesso restrito que um de seus membros, o nível de acesso de classe terá precedência.  
  
-   **Escopo.** Uma classe está no escopo em todo o seu namespace, classe, estrutura ou módulo que contém.  
  
     O escopo de cada membro de classe é a classe inteira.  
  
     **Tempo de vida.** Visual Basic não dá suporte a classes estáticas. O equivalente funcional de uma classe estática é fornecido por um módulo. Para obter mais informações, consulte [instrução Module](../../../visual-basic/language-reference/statements/module-statement.md).  
  
     Membros de classe tem tempos de vida dependendo de como e onde eles são declarados. Para obter mais informações, consulte [tempo de vida no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md).  
  
-   **Qualificação.** Código fora de uma classe deve qualificar o nome do membro com o nome de classe.  
  
     Se o código dentro de uma classe aninhada faz uma referência não qualificada para um elemento de programação, Visual Basic procura o elemento primeiro na classe aninhada, em seguida, em sua classe, e assim por diante para o elemento que contém mais externo.  
  
## <a name="classes-and-modules"></a>Classes e módulos  
 Esses elementos têm muitas semelhanças, mas há algumas diferenças importantes também.  
  
-   **Terminologia.** Versões anteriores do Visual Basic reconhecem dois tipos de módulos: *módulos de classe* (arquivos CLS) e *módulos padrão* (arquivos. bas). A versão atual chama esses *classes* e *módulos*, respectivamente.  
  
-   **Membros compartilhados.** Você pode controlar se um membro de uma classe é compartilhado ou membro de instância.  
  
-   **Orientação a objeto.** As classes são orientados a objeto, mas módulos não são. Você pode criar uma ou mais instâncias de uma classe. Para obter mais informações, consulte [objetos e Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa um `Class` instrução para definir uma classe e vários membros.  
  
 [!code-vb[VbVbalrStatements#62](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/class-statement_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Objetos e Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [Estruturas e Classes](../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)  
 [Instrução Interface](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [Instrução Module](../../../visual-basic/language-reference/statements/module-statement.md)  
 [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)  
 [Tempo de vida do objeto: como os objetos são criados e destruídos](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)  
 [Tipos genéricos no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Como usar uma classe genérica](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
