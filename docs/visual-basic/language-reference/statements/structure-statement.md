---
title: Instrução Structure (Visual Basic)
ms.date: 05/12/2018
f1_keywords:
- vb.Structure
- Structure
helpviewer_keywords:
- user-defined types [Visual Basic], Structure statement
- compound data types [Visual Basic]
- Structure keyword [Visual Basic]
- Structure statement [Visual Basic]
- UDT (user-defined types)
- types [Visual Basic], user-defined
ms.assetid: 9bd1deea-2a89-4cdc-812c-6dcbb947c391
ms.openlocfilehash: 9377d889f56049720ab10439582300913f5cbb37
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/20/2018
ms.locfileid: "46490290"
---
# <a name="structure-statement"></a>Instrução Structure
Declara o nome de uma estrutura e introduz a definição de variáveis, propriedades, eventos e procedimentos que compõem a estrutura.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
[ <attributelist> ] [ accessmodifier ] [ Shadows ] [ Partial ] _  
Structure name [ ( Of typelist ) ]  
    [ Implements interfacenames ]  
    [ datamemberdeclarations ]  
    [ methodmemberdeclarations ]  
End Structure  
```  
  
## <a name="parts"></a>Partes  
  
|Termo|Definição|  
|---|---|  
|`attributelist`|Opcional. Ver [lista de atributos](../../../visual-basic/language-reference/statements/attribute-list.md).|  
|`accessmodifier`|Opcional. Pode ser uma das seguintes opções:<br /><br /> -   [Público](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [Protegido](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [privado](../../../visual-basic/language-reference/modifiers/private.md)<br />- [Friend protegido](../../language-reference/modifiers/protected-friend.md)<br/>- [Privado protegido](../../language-reference/modifiers/private-protected.md) <br /><br /> Ver [acessar níveis no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|  
|`Shadows`|Opcional. Ver [sombras](../../../visual-basic/language-reference/modifiers/shadows.md).|  
|`Partial`|Opcional. Indica uma definição parcial da estrutura. Ver [parcial](../../../visual-basic/language-reference/modifiers/partial.md).|  
|`name`|Necessário. Nome dessa estrutura. Ver [nomes de elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`Of`|Opcional. Especifica que esta é uma estrutura genérica.|  
|`typelist`|Necessário se você usar o [de](../../../visual-basic/language-reference/statements/of-clause.md) palavra-chave. Lista de parâmetros de tipo para essa estrutura. Ver [lista de tipos](../../../visual-basic/language-reference/statements/type-list.md).|  
|`Implements`|Opcional. Indica que essa estrutura implementa os membros de uma ou mais interfaces. Ver [implementa a instrução](../../../visual-basic/language-reference/statements/implements-statement.md).|  
|`interfacenames`|Necessário se você usar o `Implements` instrução. Os nomes das interfaces que essa estrutura implementa.|  
|`datamemberdeclarations`|Necessário. Zero ou mais `Const`, `Dim`, `Enum`, ou `Event` instruções declarando *membros de dados* da estrutura.|  
|`methodmemberdeclarations`|Opcional. Zero ou mais declarações de `Function`, `Operator`, `Property`, ou `Sub` procedimentos, que servem como *membros método* da estrutura.|  
|`End Structure`|Necessário. Encerra o `Structure` definição.|  
  
## <a name="remarks"></a>Comentários  
 O `Structure` instrução define um tipo de valor composto que você pode personalizar. Um *estrutura* é uma generalização do que o tipo definido pelo usuário (UDT) de versões anteriores do Visual Basic. Para obter mais informações, consulte [estruturas](../../../visual-basic/programming-guide/language-features/data-types/structures.md).  
  
 Estruturas oferecem suporte a muitos dos mesmos recursos como classes. Por exemplo, estruturas podem ter propriedades e procedimentos, podem implementar interfaces, e eles podem ter construtores parametrizados. No entanto, há diferenças significativas entre estruturas e classes em áreas como herança, declarações e uso. Além disso, as classes são tipos de referência e estruturas são tipos de valor. Para obter mais informações, consulte [estruturas e Classes](../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md).  
  
 Você pode usar `Structure` apenas no nível de namespace ou módulo. Isso significa que o *contexto de declaração* para uma estrutura deve ser um arquivo de origem, namespace, classe, estrutura, módulo ou interface e não pode ser um procedimento ou bloco. Para obter mais informações, consulte [Contextos de declaração e níveis de acesso padrão](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Padrão para estruturas [amigo](../../../visual-basic/language-reference/modifiers/friend.md) acesso. Você pode ajustar os níveis de acesso com os modificadores de acesso. Para obter mais informações, consulte [acessar níveis no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="rules"></a>Regras  
  
-   **Aninhamento.** Você pode definir uma estrutura dentro de outra. A estrutura externa é chamada a *que contém a estrutura*, e a estrutura interna é chamada uma *aninhados estrutura*. No entanto, você não pode acessar membros de uma estrutura aninhada através da estrutura contida. Em vez disso, você deve declarar uma variável do tipo de dados da estrutura aninhada.  
  
-   **Declaração de membro.** Você deve declarar cada membro de uma estrutura. Um membro da estrutura não pode ser [Protected](../../../visual-basic/language-reference/modifiers/protected.md) ou `Protected Friend` porque nada pode herdar de uma estrutura. A estrutura em si, no entanto, pode ser `Protected` ou `Protected Friend`.  
  
     Você pode declarar zero ou mais variáveis não compartilhadas ou compartilhadas, ou eventos em uma estrutura. Você não pode ter apenas constantes, propriedades e procedimentos, mesmo se algumas delas sejam compartilhadas.  
  
-   **Inicialização.** Você não pode inicializar o valor de qualquer membro de dados não compartilhado de uma estrutura como parte de sua declaração. Você deve inicializar tal membro de dados por meio de um construtor parametrizado na estrutura, ou atribuir um valor ao membro depois de ter criado uma instância da estrutura.  
  
-   **Herança.** Uma estrutura não pode herdar de qualquer tipo diferente de <xref:System.ValueType>, de que todas as estruturas herdam. Em particular, uma estrutura não pode herdar de outra.  
  
     Não é possível usar o [instrução Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md) em uma definição de estrutura, mesmo para especificar <xref:System.ValueType>.  
  
-   **Implementação.** Se a estrutura usa a [instrução Implements](../../../visual-basic/language-reference/statements/implements-statement.md), você deve implementar todos os membros definidos em cada interface que você especificar no `interfacenames`.  
  
-   **Propriedade padrão.** Uma estrutura pode especificar no máximo uma propriedade como seu *propriedade padrão*, usando o [padrão](../../../visual-basic/language-reference/modifiers/default.md) modificador. Para obter mais informações, consulte [padrão](../../../visual-basic/language-reference/modifiers/default.md).  
  
## <a name="behavior"></a>Comportamento  
  
-   **Nível de acesso.** Dentro de uma estrutura, você pode declarar cada membro com seu próprio nível de acesso. Todos os membros de estrutura padrão [pública](../../../visual-basic/language-reference/modifiers/public.md) acesso. Observe que se a própria estrutura tem um nível de acesso mais restrito, isso restringe automaticamente o acesso a seus membros, mesmo se você ajustar seus níveis de acesso com os modificadores de acesso.  
  
-   **Escopo.** Uma estrutura está no escopo em todo o seu namespace, classe, estrutura ou módulo recipiente.  
  
     O escopo de cada membro de estrutura é a estrutura inteira.  
  
-   **Tempo de vida.** Uma estrutura em si tem um tempo de vida. Em vez disso, cada instância dessa estrutura tem um tempo de vida independente de todas as outras instâncias.  
  
     O tempo de vida de uma instância começa quando ela é criada por um [novo operador](../../../visual-basic/language-reference/operators/new-operator.md) cláusula. Ela termina quando o tempo de vida da variável que contém termina.  
  
     Você não pode estender o tempo de vida de uma instância da estrutura. Uma aproximação da estrutura estática é fornecida por um módulo. Para obter mais informações, consulte [declaração de módulo](../../../visual-basic/language-reference/statements/module-statement.md).  
  
     Membros de estrutura têm tempos de vida, dependendo de como e onde eles são declarados. Para obter mais informações, consulte "Tempo de vida" em [declaração de classe](../../../visual-basic/language-reference/statements/class-statement.md).  
  
-   **Qualificação.** Código fora de uma estrutura deve qualificar o nome do membro com o nome da estrutura.  
  
     Se o código dentro de uma estrutura aninhada fizer uma referência não qualificada a um elemento de programação, Visual Basic procura esse elemento primeiramente na estrutura aninhada, em seguida, em sua estrutura contida e assim por diante-out para o elemento contido mais externo. Para obter mais informações, consulte [referências a elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
-   **Consumo de memória.** Assim como acontece com todos os tipos de dados compostos, você não pode calcular com segurança o consumo de memória total de uma estrutura somando as alocações de armazenamento nominais de seus membros. Além disso, você não pode presumir com segurança que a ordem de armazenamento na memória é a mesma que sua ordem de declaração. Se você precisar controlar o layout de armazenamento de uma estrutura, você pode aplicar a <xref:System.Runtime.InteropServices.StructLayoutAttribute> de atributo para o `Structure` instrução.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `Structure` instrução para definir um conjunto de dados relacionados de um funcionário. Ele mostra o uso de `Public`, `Friend`, e `Private` membros para refletir a sensibilidade dos itens de dados. Ele também mostra os membros de procedimento, propriedade e evento.  
  
 [!code-vb[VbVbalrStatements#57](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/structure-statement_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Class](../../../visual-basic/language-reference/statements/class-statement.md)  
 [Instrução Interface](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [Instrução Module](../../../visual-basic/language-reference/statements/module-statement.md)  
 [Instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [Instrução Const](../../../visual-basic/language-reference/statements/const-statement.md)  
 [Instrução Enum](../../../visual-basic/language-reference/statements/enum-statement.md)  
 [Instrução Event](../../../visual-basic/language-reference/statements/event-statement.md)  
 [Instrução Operator](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)  
 [Estruturas e Classes](../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
