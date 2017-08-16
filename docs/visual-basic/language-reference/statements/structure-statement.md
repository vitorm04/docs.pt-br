---
title: "Declaração de estrutura | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Structure
- Structure
dev_langs:
- VB
helpviewer_keywords:
- user-defined types, Structure statement
- compound data types
- Structure keyword
- Structure statement
- UDT (user-defined types)
- types [Visual Basic], user-defined
ms.assetid: 9bd1deea-2a89-4cdc-812c-6dcbb947c391
caps.latest.revision: 28
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 32e1c6bff0bc1df34407e21053c9b973710550ec
ms.contentlocale: pt-br
ms.lasthandoff: 03/13/2017

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
|`attributelist`|Opcional. Consulte [lista atributo](../../../visual-basic/language-reference/statements/attribute-list.md).|  
|`accessmodifier`|Opcional. Pode ser uma das seguintes opções:<br /><br /> -   [Público](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [Protegido](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [Privado](../../../visual-basic/language-reference/modifiers/private.md)<br />-   `Protected Friend`<br /><br /> Consulte [acessar níveis no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|  
|`Shadows`|Opcional. Consulte [sombras](../../../visual-basic/language-reference/modifiers/shadows.md).|  
|`Partial`|Opcional. Indica uma definição parcial da estrutura. Consulte [parcial](../../../visual-basic/language-reference/modifiers/partial.md).|  
|`name`|Necessário. Nome dessa estrutura. Consulte [nomes de elemento declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`Of`|Opcional. Especifica que esta é uma estrutura genérica.|  
|`typelist`|Necessário se você usar o [de](../../../visual-basic/language-reference/statements/of-clause.md) palavra-chave. Lista de parâmetros de tipo para essa estrutura. Consulte [digite lista](../../../visual-basic/language-reference/statements/type-list.md).|  
|`Implements`|Opcional. Indica que essa estrutura implementa os membros de uma ou mais interfaces. Consulte [implementa a instrução](../../../visual-basic/language-reference/statements/implements-statement.md).|  
|`interfacenames`|Necessário se você usar o `Implements` instrução. Os nomes das interfaces que essa estrutura implementa.|  
|`datamemberdeclarations`|Necessário. Zero ou mais `Const`, `Dim`, `Enum`, ou `Event` instruções declarando *membros de dados* da estrutura.|  
|`methodmemberdeclarations`|Opcional. Zero ou mais declarações de `Function`, `Operator`, `Property`, ou `Sub` procedimentos que servem como *membros método* da estrutura.|  
|`End Structure`|Necessário. Encerra o `Structure` definição.|  
  
## <a name="remarks"></a>Comentários  
 O `Structure` instrução define um tipo de valor composto que você pode personalizar. A *estrutura* é uma generalização do que o tipo definido pelo usuário (UDT) de versões anteriores do Visual Basic. Para obter mais informações, consulte [estruturas](../../../visual-basic/programming-guide/language-features/data-types/structures.md).  
  
 Estruturas oferecem suporte a muitos dos mesmos recursos de classes. Por exemplo, estruturas podem ter propriedades e procedimentos, elas podem implementar interfaces e eles podem ter construtores parametrizados. No entanto, existem diferenças significativas entre as estruturas e classes em áreas como herança, declarações e utilização. Além disso, classes são tipos de referência e estruturas são tipos de valor. Para obter mais informações, consulte [estruturas e Classes](../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md).  
  
 Você pode usar `Structure` somente no nível de namespace ou módulo. Isso significa que o *contexto declaração* para uma estrutura deve ser um arquivo fonte, namespace, classe, estrutura, módulo ou interface e não pode ser um procedimento ou bloco. Para obter mais informações, consulte [contextos de declaração e níveis de acesso padrão](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Padrão para estruturas [amigo](../../../visual-basic/language-reference/modifiers/friend.md) acesso. Você pode ajustar os níveis de acesso com os modificadores de acesso. Para obter mais informações, consulte [níveis de acesso no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="rules"></a>Regras  
  
-   **Aninhamento.** Você pode definir uma estrutura dentro de outra. A estrutura externa é chamada de *contendo a estrutura*, e a estrutura interna é chamada uma *aninhados estrutura*. No entanto, você não pode acessar os membros de uma estrutura aninhada através da estrutura que contém. Em vez disso, você deve declarar uma variável do tipo de dados da estrutura aninhada.  
  
-   **Declaração de membro.** Você deve declarar cada membro de uma estrutura. Não pode ser um membro de estrutura [protegido](../../../visual-basic/language-reference/modifiers/protected.md) ou `Protected Friend` pois nada herda de uma estrutura. A estrutura em si, no entanto, pode ser `Protected` ou `Protected Friend`.  
  
     Você pode declarar zero ou mais variáveis não compartilhadas ou eventos não personalizados não compartilhados em uma estrutura. Você não pode ter apenas constantes, propriedades e procedimentos, mesmo se alguns deles não forem compartilhados.  
  
-   **Inicialização.** Você não pode inicializar o valor de qualquer membro de dado não compartilhado de uma estrutura como parte de sua declaração. Você deve inicializar este membro de dados por meio de um construtor parametrizado na estrutura, ou atribuir um valor para o membro depois de ter criado uma instância da estrutura.  
  
-   **Herança.** Uma estrutura não pode herdar de qualquer tipo diferente de <xref:System.ValueType>, do qual todas as estruturas herdam.</xref:System.ValueType> Em particular, uma estrutura não pode herdar de outra.  
  
     Não é possível usar o [instrução Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md) em uma definição de estrutura, mesmo para especificar <xref:System.ValueType>.</xref:System.ValueType>  
  
-   **Implementação.** Se a estrutura usa a [instrução Implements](../../../visual-basic/language-reference/statements/implements-statement.md), você deve implementar cada membro definido em cada interface que você especificar em `interfacenames`.  
  
-   **Propriedade padrão.** Uma estrutura pode especificar no máximo uma propriedade como sua *propriedade padrão*, usando o [padrão](../../../visual-basic/language-reference/modifiers/default.md) modificador. Para obter mais informações, consulte [padrão](../../../visual-basic/language-reference/modifiers/default.md).  
  
## <a name="behavior"></a>Comportamento  
  
-   **Nível de acesso.** Em uma estrutura, você pode declarar cada membro com seu próprio nível de acesso. Todos os membros de estrutura padrão [pública](../../../visual-basic/language-reference/modifiers/public.md) acesso. Observe que se a própria estrutura tem um nível de acesso mais restrito, isso automaticamente restringe o acesso a seus membros, mesmo se você ajustar os níveis de acesso com os modificadores de acesso.  
  
-   **Escopo.** Uma estrutura é em escopo seu namespace, classe, estrutura ou módulo que contém.  
  
     O escopo de cada membro de estrutura é a estrutura inteira.  
  
-   **Tempo de vida.** Uma estrutura em si tem um tempo de vida. Em vez disso, cada instância dessa estrutura tem um tempo de vida independente de todas as outras instâncias.  
  
     O tempo de vida de uma instância começa quando ela é criada por um [novo operador](../../../visual-basic/language-reference/operators/new-operator.md) cláusula. Ele termina quando o tempo de vida da variável que mantém termina.  
  
     Você não pode estender o tempo de vida de uma instância de estrutura. Uma aproximação estrutura estática é fornecida por um módulo. Para obter mais informações, consulte [instrução Module](../../../visual-basic/language-reference/statements/module-statement.md).  
  
     Membros de estrutura têm tempos de vida dependendo de como e onde eles são declarados. Para obter mais informações, consulte "Tempo de vida" em [instrução Class](../../../visual-basic/language-reference/statements/class-statement.md).  
  
-   **Qualificação.** Código fora de uma estrutura deve qualificar o nome do membro com o nome da estrutura.  
  
     Se o código dentro de uma estrutura aninhada faz uma referência não qualificada a um elemento de programação, Visual Basic procura esse elemento primeiro na estrutura aninhada, em seguida, em sua estrutura, e assim por diante-out para o elemento mais externo. Para obter mais informações, consulte [referências a elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
-   **Consumo de memória.** Assim como acontece com todos os tipos de dados compostos, você não pode calcular com segurança o consumo de memória total de uma estrutura somando as alocações de armazenamento nominais de seus membros. Além disso, você não pode presumir que a ordem de armazenamento em memória é o mesmo que a ordem da declaração. Se você precisa controlar o layout de armazenamento de uma estrutura, você pode aplicar o <xref:System.Runtime.InteropServices.StructLayoutAttribute>de atributo para o `Structure` instrução.</xref:System.Runtime.InteropServices.StructLayoutAttribute>  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `Structure` instrução para definir um conjunto de dados relacionados para um funcionário. Ela mostra o uso de `Public`, `Friend`, e `Private` membros para refletir a sensibilidade dos itens de dados. Ele também mostra os membros de procedimento, propriedade e evento.  
  
 [!code-vb[VbVbalrStatements&#57;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/structure-statement_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Class](../../../visual-basic/language-reference/statements/class-statement.md)   
 [Instrução interface](../../../visual-basic/language-reference/statements/interface-statement.md)   
 [Instrução Module](../../../visual-basic/language-reference/statements/module-statement.md)   
 [Instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md)   
 [Instrução Const](../../../visual-basic/language-reference/statements/const-statement.md)   
 [Instrução Enum](../../../visual-basic/language-reference/statements/enum-statement.md)   
 [Instrução Event](../../../visual-basic/language-reference/statements/event-statement.md)   
 [Instrução Operator](../../../visual-basic/language-reference/statements/operator-statement.md)   
 [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)   
 [Estruturas e Classes](../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)

