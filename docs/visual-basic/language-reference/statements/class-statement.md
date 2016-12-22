---
title: "Instru&#231;&#227;o Class (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.Class"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "módulos de classe"
  - "instrução Class"
  - "tipos de classes, instruções class"
  - "classes [Visual Basic], criando"
  - "classes [Visual Basic], membros de dados"
  - "classes [Visual Basic], campos"
  - "membros de dados, de classes"
  - "campos, de classes"
ms.assetid: f2664f38-eb5a-4d4b-a374-1d041521fb6c
caps.latest.revision: 29
caps.handback.revision: 29
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Instru&#231;&#227;o Class (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Declara o nome de uma classe e introduz a definição de variáveis, propriedades, eventos e procedimentos que a classe compreende.  
  
## Sintaxe  
  
```  
[ <attributelist> ] [ accessmodifier ] [ Shadows ] [ MustInherit | NotInheritable ] [ Partial ] _  
Class name [ ( Of typelist ) ]  
    [ Inherits classname ]  
    [ Implements interfacenames ]  
    [ statements ]  
End Class  
```  
  
## Partes  
  
|||  
|-|-|  
|Termo|Definição|  
|`attributelist`|Opcional.  Veja [Lista de Atributos](../../../visual-basic/language-reference/statements/attribute-list.md).|  
|`accessmodifier`|Opcional.  Pode ser um dos seguintes:<br /><br /> -   [Público](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [Protegido](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [Private](../../../visual-basic/language-reference/modifiers/private.md)<br />-   `Protected Friend`<br /><br /> Consulte [Níveis de acesso no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|  
|`Shadows`|Opcional.  Acesse [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).|  
|`MustInherit`|Opcional.  Consulte [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).|  
|`NotInheritable`|Opcional.  Consulte [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md).|  
|`Partial`|Opcional.  Indica uma definição parcial da classe.  Consulte [Parcial](../../../visual-basic/language-reference/modifiers/partial.md).|  
|`name`|Obrigatório.  Nome dessa classe.  Consulte [Nomes de elemento declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`Of`|Opcional.  Especifica que esta é uma classe genérica.|  
|`typelist`|Necessário se você usar a palavra\-chave [Of](../../../visual-basic/language-reference/statements/of-clause.md).  Lista de parâmetros de tipo para esta classe.  Consulte [Type List](../../../visual-basic/language-reference/statements/type-list.md).|  
|`Inherits`|Opcional.  Indica que esta classe herda os membros de outra classe.  Consulte [Instrução Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md).|  
|`classname`|Necessário se você usar a declaração `Inherits`.  O nome da classe a partIr da qual essa classe deriva.|  
|`Implements`|Opcional.  Indica que essa classe implementa os membros de uma ou mais interfaces.  Consulte [Instrução Implements](../../../visual-basic/language-reference/statements/implements-statement.md).|  
|`interfacenames`|Necessário se você usar a declaração `Implements`.  Os nomes das interfaces que essa classe implementa.|  
|`statements`|Opcional.  Instruções que definem os membros dessa classe.|  
|`End Class`|Obrigatório.  Finaliza a definição `Class`.|  
  
## Comentários  
 A `Class` a instrução define um novo tipo de dados.  A  *classe* é um componente fundamental da programação orientada a objeto \(OOP\).  Para obter mais informações, consulte [Objetos e classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).  
  
 Você pode usar `Class` somente em nível de namespace ou módulo.  Isso significa que o  *o contexto de declaração* para uma classe deve ser um arquivo de origem, namespace, classe, estrutura, módulo ou interface e não pode ser um procedimento ou bloco.  Para obter mais informações, consulte [Contextos de declaração e níveis de acesso padrão](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Cada instância de uma classe tem uma vida independente de todas as outras instâncias.  Esse tempo de vida começa quando ele é criado por um [Operador New](../../../visual-basic/language-reference/operators/new-operator.md) cláusula ou por uma função, como <xref:Microsoft.VisualBasic.Interaction.CreateObject%2A>.  Ela termina quando todas as variáveis, apontando para a instância tem sido definidas a [nada](../../../visual-basic/language-reference/nothing.md) ou instâncias de outras classes.  
  
 Classes padrão para [Friend](../../../visual-basic/language-reference/modifiers/friend.md) acesso.  Você pode ajustar os seus níveis de acesso com os modificadores de acesso.  Para obter mais informações, consulte [Níveis de acesso no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## Regras  
  
-   **Aninhamento.** Você pode definir uma classe dentro de outro.  A classe externa é chamada a  *que contém a classe*, e é chamada de classe interna um  *classe aninhada*.  
  
-   **Herança.** Se a classe usa a [Instrução Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md), você pode especificar somente uma classe base ou interface.  Uma classe não pode herdar de mais de um elemento.  
  
     Uma classe não pode herdar de outra classe com um nível de acesso mais restritivo.  Por exemplo, um `Public` classe não pode herdar de uma `Friend` classe.  
  
     Uma classe não pode herdar de um classe que esteja aninhada nela.  
  
-   **Implementação.** Se a classe usa a [Instrução Implements](../../../visual-basic/language-reference/statements/implements-statement.md), você deve implementar cada membro definido por cada interface especificada em `interfacenames`.  Uma exceção a isso é reimplementação de um membro da classe base.  Para obter mais informações, consulte "Reimplementação" em [Implements](../../../visual-basic/language-reference/statements/implements-clause.md).  
  
-   **Propriedade padrão.** Uma classe pode especificar no máximo uma propriedade como sua  *propriedade padrão*.  Para obter mais informações, consulte [Padrão](../../../visual-basic/language-reference/modifiers/default.md).  
  
## Comportamento  
  
-   **Nível de acesso.** Dentro de uma classe, você pode declarar cada membro com o seu próprio nível de acesso.  Membros da classe padrão para [Público](../../../visual-basic/language-reference/modifiers/public.md) acessar, exceto as variáveis e constantes, padrão para [Particular](../../../visual-basic/language-reference/modifiers/private.md) acesso.  Quando uma classe mais restringiu o acesso que um de seus membros, o nível de acesso de classe terá precedência.  
  
-   **Escopo.** Uma classe está no escopo em toda sua contendo namespace, classe, estrutura ou módulo.  
  
     O escopo de cada membro da classe é toda a turma.  
  
     **Tempo de vida.** Visual Basic não oferece suporte a classes estáticas.  O equivalente funcional de uma classe estática é fornecido por um módulo.  Para obter mais informações, consulte [Instrução Module](../../../visual-basic/language-reference/statements/module-statement.md).  
  
     Os membros de classe têm vidas úteis dependendo de como e onde elas são declaradas.  Para obter mais informações, consulte [Tempo de vida no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md).  
  
-   **Qualificação** Código fora de uma classe deve qualificar o nome de um membro com o nome dessa classe.  
  
     Se o código dentro de uma classe aninhada faz uma referência não qualificada para um elemento de programação, Visual Basic pesquisa para o elemento primeiro na classe aninhada, em seguida, na sua classe, e assim por diante para fora para o elemento que contém mais externo.  
  
## Classes e Módulos  
 Esses elementos têm várias semelhanças, mas há algumas diferenças importantes também.  
  
-   **Terminologia.** Versões anteriores do Visual Basic reconhecem dois tipos de módulos:  *módulos de classe* \(arquivos. CLS\) e  *módulos padrão* \(arquivos. bas\).  A versão atual os chama de *classes* e  *módulos* , respectivamente.  
  
-   **Membros compartilhados.** Você pode controlar se um membro de uma classe é um membro compartilhado ou de instância.  
  
-   **Orientação a Objeto** Classes são orientadas a objeto, mas módulos não são.  Você pode criar uma ou mais instâncias de uma classe.  Para obter mais informações, consulte [Objetos e classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).  
  
## Exemplo  
 O exemplo a seguir usa um `Class` a instrução para definir uma classe e vários membros.  
  
 [!code-vb[VbVbalrStatements#62](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/class-statement_1.vb)]  
  
## Consulte também  
 [Objetos e classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)   
 [Estruturas e classes](../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)   
 [Instrução Interface](../../../visual-basic/language-reference/statements/interface-statement.md)   
 [Instrução Module](../../../visual-basic/language-reference/statements/module-statement.md)   
 [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)   
 [Tempo de vida do objeto: como os objetos são criados e destruídos](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)   
 [Tipos genéricos no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [Como usar uma classe genérica](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)