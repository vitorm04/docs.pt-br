---
title: Classe Statement (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Class
dev_langs:
- VB
helpviewer_keywords:
- class modules
- Class statement
- classes [Visual Basic], fields
- fields, of classes
- class types, class statements
- classes [Visual Basic], creating
- classes [Visual Basic], data members
- data members, of classes
ms.assetid: f2664f38-eb5a-4d4b-a374-1d041521fb6c
caps.latest.revision: 29
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
ms.openlocfilehash: b922cca0438ca5b43d24ab367090b27572c2fd30
ms.contentlocale: pt-br
ms.lasthandoff: 03/13/2017

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
|`attributelist`|Opcional. Consulte [lista atributo](../../../visual-basic/language-reference/statements/attribute-list.md).|  
|`accessmodifier`|Opcional. Pode ser uma das seguintes opções:<br /><br /> -   [Público](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [Protegido](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [Privado](../../../visual-basic/language-reference/modifiers/private.md)<br />-   `Protected Friend`<br /><br /> Consulte [acessar níveis no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|  
|`Shadows`|Opcional. Consulte [sombras](../../../visual-basic/language-reference/modifiers/shadows.md).|  
|`MustInherit`|Opcional. Consulte [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).|  
|`NotInheritable`|Opcional. Consulte [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md).|  
|`Partial`|Opcional. Indica uma definição parcial da classe. Consulte [parcial](../../../visual-basic/language-reference/modifiers/partial.md).|  
|`name`|Necessário. Nome dessa classe. Consulte [nomes de elemento declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`Of`|Opcional. Especifica que esta é uma classe genérica.|  
|`typelist`|Necessário se você usar o [de](../../../visual-basic/language-reference/statements/of-clause.md) palavra-chave. Lista de parâmetros de tipo para essa classe. Consulte [digite lista](../../../visual-basic/language-reference/statements/type-list.md).|  
|`Inherits`|Opcional. Indica que essa classe herda os membros de outra classe. Consulte [instrução Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md).|  
|`classname`|Necessário se você usar o `Inherits` instrução. O nome da classe da qual essa classe deriva.|  
|`Implements`|Opcional. Indica que essa classe implementa os membros de uma ou mais interfaces. Consulte [implementa a instrução](../../../visual-basic/language-reference/statements/implements-statement.md).|  
|`interfacenames`|Necessário se você usar o `Implements` instrução. Os nomes das interfaces que essa classe implementa.|  
|`statements`|Opcional. Instruções que definem os membros dessa classe.|  
|`End Class`|Necessário. Encerra o `Class` definição.|  
  
## <a name="remarks"></a>Comentários  
 Um `Class` instrução define um novo tipo de dados. A *classe* é um componente fundamental da programação orientada a objeto (OOP). Para obter mais informações, consulte [objetos e Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).  
  
 Você pode usar `Class` somente no nível de namespace ou módulo. Isso significa que o *contexto declaração* para uma classe deve ser um arquivo fonte, namespace, classe, estrutura, módulo ou interface e não pode ser um procedimento ou bloco. Para obter mais informações, consulte [contextos de declaração e níveis de acesso padrão](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Cada instância de uma classe tem um tempo de vida independente de todas as outras instâncias. Esse tempo de vida começa quando ela é criada por um [novo operador](../../../visual-basic/language-reference/operators/new-operator.md) cláusula ou por uma função como <xref:Microsoft.VisualBasic.Interaction.CreateObject%2A>.</xref:Microsoft.VisualBasic.Interaction.CreateObject%2A> Ele termina quando todas as variáveis apontam para a instância tem sido definidas a [nada](../../../visual-basic/language-reference/nothing.md) ou instâncias de outras classes.  
  
 Classes padrão [amigo](../../../visual-basic/language-reference/modifiers/friend.md) acesso. Você pode ajustar os níveis de acesso com os modificadores de acesso. Para obter mais informações, consulte [níveis de acesso no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="rules"></a>Regras  
  
-   **Aninhamento.** Você pode definir uma classe dentro de outra. A classe externa é chamada de *que contém a classe*, e a classe interna é chamada uma *classe aninhada*.  
  
-   **Herança.** Se a classe usa o [instrução Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md), você pode especificar apenas uma classe base ou interface. Uma classe não pode herdar de mais de um elemento.  
  
     Uma classe não pode herdar de outra classe com um nível de acesso mais restritivo. Por exemplo, um `Public` classe não pode herdar de um `Friend` classe.  
  
     Uma classe não pode herdar de uma classe aninhada nela.  
  
-   **Implementação.** Se a classe usa o [instrução Implements](../../../visual-basic/language-reference/statements/implements-statement.md), você deve implementar cada membro definido em cada interface que você especificar em `interfacenames`. Uma exceção a isso é Reimplementação de um membro da classe base. Para obter mais informações, consulte "Reimplementação" [implementa](../../../visual-basic/language-reference/statements/implements-clause.md).  
  
-   **Propriedade padrão.** Uma classe pode especificar no máximo uma propriedade como sua *propriedade padrão*. Para obter mais informações, consulte [padrão](../../../visual-basic/language-reference/modifiers/default.md).  
  
## <a name="behavior"></a>Comportamento  
  
-   **Nível de acesso.** Em uma classe, você pode declarar cada membro com seu próprio nível de acesso. Membros de classe padrão [pública](../../../visual-basic/language-reference/modifiers/public.md) acessar, exceto as variáveis e constantes, padrão para [particular](../../../visual-basic/language-reference/modifiers/private.md) acesso. Quando uma classe tem mais acesso restrito que um de seus membros, o nível de acesso da classe terá precedência.  
  
-   **Escopo.** Uma classe está no escopo em todo seu namespace, classe, estrutura ou módulo que contém.  
  
     O escopo de cada membro da classe é a classe inteira.  
  
     **Tempo de vida.** Visual Basic não dá suporte a classes estáticas. O equivalente funcional de uma classe estática é fornecido por um módulo. Para obter mais informações, consulte [instrução Module](../../../visual-basic/language-reference/statements/module-statement.md).  
  
     Membros de classe têm tempos de vida dependendo de como e onde eles são declarados. Para obter mais informações, consulte [tempo de vida no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md).  
  
-   **Qualificação.** Código fora de uma classe deve qualificar o nome do membro com o nome da classe.  
  
     Se o código dentro de uma classe aninhada faz uma referência não qualificada a um elemento de programação, Visual Basic procura o elemento primeiro na classe aninhada, em seguida, em sua classe, e assim por diante-out para o elemento mais externo que contém.  
  
## <a name="classes-and-modules"></a>Classes e módulos  
 Esses elementos têm várias semelhanças, mas há algumas diferenças importantes também.  
  
-   **Terminologia.** Versões anteriores do Visual Basic reconhecem dois tipos de módulos: *módulos de classe* (CLS arquivos) e *módulos padrão* (arquivos. bas). A versão atual chama esses *classes* e *módulos*, respectivamente.  
  
-   **Membros compartilhados.** Você pode controlar se um membro de uma classe é uma chave secreta ou membro de instância.  
  
-   **Orientação a objeto.** Classes são orientadas a objeto, mas módulos não são. Você pode criar uma ou mais instâncias de uma classe. Para obter mais informações, consulte [objetos e Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa um `Class` instrução para definir uma classe e vários membros.  
  
 [!code-vb[VbVbalrStatements&#62;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/class-statement_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Objetos e Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)   
 [Estruturas e Classes](../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)   
 [Instrução interface](../../../visual-basic/language-reference/statements/interface-statement.md)   
 [Instrução Module](../../../visual-basic/language-reference/statements/module-statement.md)   
 [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)   
 [Vida útil do objeto: Como os objetos são criados e destruídos](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)   
 [Tipos genéricos no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [Como usar uma classe genérica](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)

