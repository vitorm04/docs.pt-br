---
title: "Instru&#231;&#227;o Structure | Microsoft Docs"
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
  - "vb.Structure"
  - "Structure"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "tipos de dados compostos"
  - "palavra-chave Structure"
  - "instrução Structure"
  - "tipos [Visual Basic], definido pelo usuário"
  - "UDT (tipos definidos pelo usuário)"
  - "tipos definidos pelo usuário, instrução Structure"
ms.assetid: 9bd1deea-2a89-4cdc-812c-6dcbb947c391
caps.latest.revision: 28
caps.handback.revision: 28
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Instru&#231;&#227;o Structure
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Declara o nome de uma estrutura e introduz a definição de variáveis, propriedades, eventos e procedimentos que a estrutura compacta.  
  
## Sintaxe  
  
```  
[ <attributelist> ] [ accessmodifier ] [ Shadows ] [ Partial ] _  
Structure name [ ( Of typelist ) ]  
    [ Implements interfacenames ]  
    [ datamemberdeclarations ]  
    [ methodmemberdeclarations ]  
End Structure  
```  
  
## Partes  
  
|||  
|-|-|  
|Termo|Definição|  
|`attributelist`|Opcional.  Consulte a [Lista de Atributos](../../../visual-basic/language-reference/statements/attribute-list.md).|  
|`accessmodifier`|Opcional.  Pode ser um dos seguintes:<br /><br /> -   [Público](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [Protegido](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [Particular](../../../visual-basic/language-reference/modifiers/private.md)<br />-   `Protected Friend`<br /><br /> Consulte [Níveis de acesso no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|  
|`Shadows`|Opcional.  Consulte [Sombras](../../../visual-basic/language-reference/modifiers/shadows.md).|  
|`Partial`|Opcional.  Indica uma definição parcial da estrutura.  Consulte [Parcial](../../../visual-basic/language-reference/modifiers/partial.md).|  
|`name`|Obrigatório.  Nome dessa estrutura.  Consulte [Nomes de elemento declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`Of`|Opcional.  Especifica que essa é uma estrutura genérica.|  
|`typelist`|Necessário se usar a palavra\-chave [Of](../../../visual-basic/language-reference/statements/of-clause.md).  Lista de parâmetros de tipo para essa estrutura.  Consulte a [Lista de Tipos](../../../visual-basic/language-reference/statements/type-list.md).|  
|`Implements`|Opcional.  Indica que essa estrutura implementa os membros de uma ou mais interfaces.  Consulte [Instrução Implements](../../../visual-basic/language-reference/statements/implements-statement.md).|  
|`interfacenames`|Necessário se usar a declaração `Implements`.  Os nomes das interfaces que essa estrutura implementa.|  
|`datamemberdeclarations`|Obrigatório.  Zero ou mais declarações de `Const`, `Dim`, `Enum` ou `Event` estão declarando *membros de dados* da estrutura.|  
|`methodmemberdeclarations`|Opcional.  Zero ou mais declarações de procedimentos `Function`, `Operator`, `Property` ou `Sub`, que servem como *membros de método* da estrutura.|  
|`End Structure`|Obrigatório.  Finaliza a definição `Structure`.|  
  
## Comentários  
 A declaração `Structure` define um tipo de valor composto que pode ser personalizado.  Uma *estrutura* é uma generalização do tipo definido pelo usuário \(TDU\) de versões anteriores do Visual Basic.  Para obter mais informações, consulte [Estruturas](../../../visual-basic/programming-guide/language-features/data-types/structures.md).  
  
 As estruturas oferecem suportem a alguns recursos como classes.  Por exemplo, estruturas podem ter propriedades e procedimentos, podem implementar interfaces e ter construtores parametrizados.  Entretanto, existem diferenças significativas entre estruturas e classes em áreas como herança, declarações e utilização.  Além disso, classes são tipos de referência e as estruturas são tipos de valor.  Para obter mais informações, consulte [Estruturas e classes](../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md).  
  
 Só é possível usar `Structure` em nível de namespace ou módulo.  Isso significa que o *contexto da declaração* de uma estrutura deve ser um arquivo de origem, namespace, classe, estrutura, módulo ou interface e não pode ser um procedimento ou bloco.  Para obter mais informações, consulte [Contextos de declaração e níveis de acesso padrão](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 O padrão para estruturas é o acesso [Friend](../../../visual-basic/language-reference/modifiers/friend.md).  É possível ajustar seus níveis de acesso com os modificadores de acesso.  Para obter mais informações, consulte [Níveis de acesso no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## Regras  
  
-   **Aninhamento.** É possível definir uma estrutura dentro de outra.  A estrutura externa é chamada de *estrutura contida* e a estrutura interna é chamada de *estrutura aninhada*.  Entretanto, não é possível acessar membros de uma estrutura aninhada através da estrutura contida  Em vez disso, você deve declarar uma variável do tipo de dados da estrutura aninhada.  
  
-   **Declaração de Membro.** Você deve declarar cada membro de uma estrutura.  O membro de uma estrutura não pode ser [Protegido](../../../visual-basic/language-reference/modifiers/protected.md)ou`Protected Friend`, pois nada pode ser herdado de uma estrutura.  Entretanto, a estrutura em si pode ser `Protected` ou `Protected Friend`.  
  
     Você pode declarar zero ou mais variáveis não compartilhadas, ou eventos não compartilhados, não personalizados em uma estrutura.  Não é possível ter apenas constantes, propriedades e procedimentos, mesmo que alguns deles não sejam compartilhados.  
  
-   **Inicialização.** Não é possível inicializar o valor de qualquer membro de dados não compartilhado de uma estrutura como parte de sua declaração.  Você deve inicializar tal membro de dado através de um construtor parametrizado na estrutura ou atribuir um valor ao membro depois de ter criado uma instância da estrutura.  
  
-   **Herança.** Uma estrutura não pode herdar de qualquer tipo que não seja <xref:System.ValueType>, da qual todas as estruturas são herdadas.  Em particular, uma estrutura não pode ser herdada de outra.  
  
     Não é possível usar [Instrução Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md) em uma definição de estrutura, mesmo que seja para especificar <xref:System.ValueType>.  
  
-   **Implementação.** Se a estrutura usar o [Instrução Implements](../../../visual-basic/language-reference/statements/implements-statement.md), será necessário implementar todos os membros definidos em cada interface que você especificar em `interfacenames`.  
  
-   **Propriedade Padrão.** Uma estrutura pode especificar no máximo uma propriedade como sua *propriedade padrão*, usando o modificador [Padrão](../../../visual-basic/language-reference/modifiers/default.md).  Para obter mais informações, consulte [Padrão](../../../visual-basic/language-reference/modifiers/default.md).  
  
## Comportamento  
  
-   **Nível de Acesso.** Dentro de uma estrutura, é possível declarar cada membro com seu próprio nível de acesso.  Todos membros de estrutura tem como padrão o acesso [Público](../../../visual-basic/language-reference/modifiers/public.md).  Observe que se a própria estrutura tiver mais de um nível de acesso restrito, isso restringe automaticamente o acesso aos seus membros, mesmo que você ajuste seus níveis de acesso com os modificadores de acesso.  
  
-   **Escopo.** Uma estrutura é totalmente seu namespace, classe, estrutura ou módulo contido.  
  
     O escopo de cada membro de estrutura é a estrutura inteira.  
  
-   **Tempo de vida.** Uma estrutura não tem um tempo de vida próprio.  Por sua vez, cada instância dessa estrutura tem um tempo de vida independente de todas as outras instâncias.  
  
     O tempo de vida de uma instância se inicia quando ela é criada por uma cláusula [Operador New](../../../visual-basic/language-reference/operators/new-operator.md).  É finalizada quando o termina tempo de vida da variável que a armazena.  
  
     Não é possível estender o tempo de vida de uma instância de estrutura.  É fornecida uma aproximação da estrutura estática por um módulo.  Para obter mais informações, consulte [Instrução Module](../../../visual-basic/language-reference/statements/module-statement.md).  
  
     Os membros de estrutura têm tempos de vida que dependem de como e onde eles foram declarados.  Para obter mais informações, consulte "Tempo de Vida" em [Instrução Class](../../../visual-basic/language-reference/statements/class-statement.md).  
  
-   **Habilitação.** O código exterior a uma estrutura deve qualificar o nome de um membro como o nome da estrutura.  
  
     Se um código dentro de uma estrutura aninhada fizer referência não qualificada a um elemento de programação, o Visual Basic procura esse elemento primeiramente na estrutura aninhada, em seguida, na sua estrutura contida e assim por diante, até o elemento contido mais externo.  Para obter mais informações, consulte [Referências a elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
-   **Consumo de Memória.** Assim como com todos os tipos de dado compostos, não é possível calcular com segurança o consumo total de memória ao se adicionar as alocações de armazenamento nominais de seus membros.  Além disso, você não pode assumir, com segurança, que a ordem de armazenamento em memória é a mesma das suas declarações.  Se for necessário controlar o layout do armazenamento de uma estrutura, você poderá aplicar o atributo <xref:System.Runtime.InteropServices.StructLayoutAttribute> à instrução `Structure`.  
  
## Exemplo  
 O exemplo a seguir usa a instrução `Structure` para definir um conjunto de dados relacionados para um funcionário.  É mostrado o uso de membros `Public`, `Friend` e `Private` para refletir a sensibilidade dos itens de dados.  Também são exibidos membros de evento, propriedade e procedimento  
  
 [!code-vb[VbVbalrStatements#57](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/structure-statement_1.vb)]  
  
## Consulte também  
 [Instrução Class](../../../visual-basic/language-reference/statements/class-statement.md)   
 [Instrução Interface](../../../visual-basic/language-reference/statements/interface-statement.md)   
 [Instrução Module](../../../visual-basic/language-reference/statements/module-statement.md)   
 [Instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md)   
 [Instrução Const](../../../visual-basic/language-reference/statements/const-statement.md)   
 [Instrução Enum](../../../visual-basic/language-reference/statements/enum-statement.md)   
 [Instrução Event](../../../visual-basic/language-reference/statements/event-statement.md)   
 [Instrução Operator](../../../visual-basic/language-reference/statements/operator-statement.md)   
 [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)   
 [Estruturas e classes](../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)