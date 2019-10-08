---
title: Instrução Class (Visual Basic)
ms.date: 05/12/2018
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
ms.openlocfilehash: 2e4514686afcbbe0e9ff0b3326c1be212db4f9f8
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005156"
---
# <a name="class-statement-visual-basic"></a>Instrução Class (Visual Basic)
Declara o nome de uma classe e apresenta a definição das variáveis, propriedades, eventos e procedimentos que a classe compõe.  
  
## <a name="syntax"></a>Sintaxe  
  
```vb  
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
|`attributelist`|Opcional. Consulte a [lista de atributos](../../../visual-basic/language-reference/statements/attribute-list.md).|  
|`accessmodifier`|Opcional. Pode ser um dos seguintes:<br /><br /> [público](../../../visual-basic/language-reference/modifiers/public.md) -   <br />-   [protegido](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [particular](../../../visual-basic/language-reference/modifiers/private.md)<br />[amigo protegido](../../language-reference/modifiers/protected-friend.md) do -   <br />- [protegido privada](../../language-reference/modifiers/private-protected.md)<br/><br/> Consulte [níveis de acesso em Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|  
|`Shadows`|Opcional. Consulte [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).|  
|`MustInherit`|Opcional. Consulte [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).|  
|`NotInheritable`|Opcional. Consulte [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md).|  
|`Partial`|Opcional. Indica uma definição parcial da classe. Consulte [parcial](../../../visual-basic/language-reference/modifiers/partial.md).|  
|`name`|Necessário. Nome desta classe. Consulte [nomes de elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`Of`|Opcional. Especifica que esta é uma classe genérica.|  
|`typelist`|Necessário se você usar a palavra-chave [of](../../../visual-basic/language-reference/statements/of-clause.md) . Lista de parâmetros de tipo para esta classe. Consulte [lista de tipos](../../../visual-basic/language-reference/statements/type-list.md).|  
|`Inherits`|Opcional. Indica que essa classe herda os membros de outra classe. Consulte a [instrução Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md).|  
|`classname`|Necessário se você usar a instrução `Inherits`. O nome da classe da qual essa classe deriva.|  
|`Implements`|Opcional. Indica que essa classe implementa os membros de uma ou mais interfaces. Consulte a [instrução Implements](../../../visual-basic/language-reference/statements/implements-statement.md).|  
|`interfacenames`|Necessário se você usar a instrução `Implements`. Os nomes das interfaces que essa classe implementa.|  
|`statements`|Opcional. Instruções que definem os membros dessa classe.|  
|`End Class`|Necessário. Encerra a definição de `Class`.|  
  
## <a name="remarks"></a>Comentários  
 Uma instrução `Class` define um novo tipo de dados. Uma *classe* é um bloco de construção fundamental da OOP (programação orientada a objeto). Para obter mais informações, consulte [objetos e classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).  
  
 Você pode usar `Class` somente em nível de namespace ou de módulo. Isso significa que o *contexto de declaração* para uma classe deve ser um arquivo de origem, namespace, classe, estrutura, módulo ou interface e não pode ser um procedimento ou bloco. Para obter mais informações, consulte [Contextos de declaração e níveis de acesso padrão](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Cada instância de uma classe tem um tempo de vida independente de todas as outras instâncias. Esse tempo de vida começa quando é criado por uma cláusula [New Operator](../../../visual-basic/language-reference/operators/new-operator.md) ou por uma função como <xref:Microsoft.VisualBasic.Interaction.CreateObject%2A>. Ele termina quando todas as variáveis que apontam para a instância foram definidas como [Nothing](../../../visual-basic/language-reference/nothing.md) ou instâncias de outras classes.  
  
 Classes padrão para acesso [Friend](../../../visual-basic/language-reference/modifiers/friend.md) . Você pode ajustar seus níveis de acesso com os modificadores de acesso. Para obter mais informações, consulte [níveis de acesso em Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="rules"></a>Regras  
  
- **Aninhamento.** Você pode definir uma classe dentro de outra. A classe externa é chamada de *classe recipiente*, e a classe interna é chamada de *classe aninhada*.  
  
- **Herança.** Se a classe usar a [instrução Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md), você poderá especificar apenas uma classe base ou interface. Uma classe não pode herdar de mais de um elemento.  
  
     Uma classe não pode herdar de outra classe com um nível de acesso mais restritivo. Por exemplo, uma classe `Public` não pode herdar de uma classe `Friend`.  
  
     Uma classe não pode herdar de uma classe aninhada dentro dela.  
  
- **Implementação.** Se a classe usar a [instrução Implements](../../../visual-basic/language-reference/statements/implements-statement.md), você deverá implementar todos os membros definidos por cada interface especificada no `interfacenames`. Uma exceção a isso é a reimplementação de um membro da classe base. Para obter mais informações, consulte "reimplementação" em [implementações](../../../visual-basic/language-reference/statements/implements-clause.md).  
  
- **Propriedade padrão.** Uma classe pode especificar, no máximo, uma propriedade como sua *propriedade padrão*. Para obter mais informações, consulte [padrão](../../../visual-basic/language-reference/modifiers/default.md).  
  
## <a name="behavior"></a>Comportamento  
  
- **Nível de acesso.** Dentro de uma classe, você pode declarar cada membro com seu próprio nível de acesso. Membros de classe assumem como padrão acesso [público](../../../visual-basic/language-reference/modifiers/public.md) , Exceto variáveis e constantes, que assumem como padrão o acesso [privado](../../../visual-basic/language-reference/modifiers/private.md) . Quando uma classe tem acesso mais restrito que um de seus membros, o nível de acesso da classe tem precedência.  
  
- **Com.** Uma classe está no escopo em todo o namespace, classe, estrutura ou módulo que o contém.  
  
     O escopo de cada membro de classe é a classe inteira.  
  
     **Existência.** Visual Basic não oferece suporte a classes estáticas. O equivalente funcional de uma classe estática é fornecido por um módulo. Para obter mais informações, consulte [instrução de módulo](../../../visual-basic/language-reference/statements/module-statement.md).  
  
     Os membros da classe têm tempos de vida, dependendo de como e onde eles são declarados. Para obter mais informações, consulte [tempo de vida em Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md).  
  
- **Aprovação.** O código fora de uma classe deve qualificar o nome de um membro com o nome dessa classe.  
  
     Se o código dentro de uma classe aninhada fizer uma referência não qualificada a um elemento de programação, Visual Basic pesquisará o elemento primeiro na classe aninhada e, em seguida, na classe que a contém, e assim por diante para o elemento contendo mais externo.  
  
## <a name="classes-and-modules"></a>Classes e módulos  
 Esses elementos têm muitas semelhanças, mas também há algumas diferenças importantes.  
  
- **Terminologia.** As versões anteriores do Visual Basic reconhecem dois tipos de módulos: *módulos de classe* (arquivos. CLS) e *módulos padrão* (arquivos. bas). A versão atual chama essas *classes* e *módulos*, respectivamente.  
  
- **Membros compartilhados.** Você pode controlar se um membro de uma classe é um membro compartilhado ou de instância.  
  
- **Orientação do objeto.** As classes são orientadas a objeto, mas os módulos não são. Você pode criar uma ou mais instâncias de uma classe. Para obter mais informações, consulte [objetos e classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa uma instrução `Class` para definir uma classe e vários membros.  
  
 [!code-vb[VbVbalrStatements#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#62)]  
  
## <a name="see-also"></a>Consulte também

- [Objetos e Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [Estruturas e Classes](../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
- [Instrução Interface](../../../visual-basic/language-reference/statements/interface-statement.md)
- [Instrução Module](../../../visual-basic/language-reference/statements/module-statement.md)
- [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)
- Tempo de vida de @no__t 0Object: Como os objetos são criados e destruídos @ no__t-0
- [Tipos genéricos no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Como: usar uma classe genérica](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
