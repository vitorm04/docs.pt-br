---
title: "Instru&#231;&#227;o Interface (Visual Basic) | Microsoft Docs"
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
  - "vb.Interface"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "instrução interface [Visual Basic]"
  - "interfaces, definição de interface"
ms.assetid: 8997af73-bda3-4f79-bd41-ca396b610260
caps.latest.revision: 26
caps.handback.revision: 26
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Instru&#231;&#227;o Interface (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Declara o nome de uma interface e apresenta as definições dos membros dos quais a interface se constitui.  
  
## Sintaxe  
  
```  
[ <attributelist> ] [ accessmodifier ] [ Shadows ] _  
Interface name [ ( Of typelist ) ]  
    [ Inherits interfacenames ]  
    [ [ modifiers ] Property membername ]  
    [ [ modifiers ] Function membername ]  
    [ [ modifiers ] Sub membername ]  
    [ [ modifiers ] Event membername ]  
    [ [ modifiers ] Interface membername ]  
    [ [ modifiers ] Class membername ]  
    [ [ modifiers ] Structure membername ]  
End Interface  
```  
  
## Partes  
  
|||  
|-|-|  
|Termo|Definição|  
|`attributelist`|Opcional.  Veja [Lista de Atributos](../../../visual-basic/language-reference/statements/attribute-list.md).|  
|`accessmodifier`|Opcional.  Pode ser um dos seguintes:<br /><br /> -   [Público](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [Protegido](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [Private](../../../visual-basic/language-reference/modifiers/private.md)<br />-   `Protected Friend`<br /><br /> Consulte [Níveis de acesso no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|  
|`Shadows`|Opcional.  Acesse [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).|  
|`name`|Obrigatório.  Nome desta interface.  Consulte [Nomes de elemento declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`Of`|Opcional.  Especifica que esta é uma interface genérica.|  
|`typelist`|Exigido se você usar a palavra\-chave [Of](../../../visual-basic/language-reference/statements/of-clause.md).  Lista de parâmetros de tipo para esta interface.  Opcionalmente, cada parâmetro de tipo pode ser declarado variante usando `In` e `Out` modificadores genéricos.  Consulte [Type List](../../../visual-basic/language-reference/statements/type-list.md).|  
|`Inherits`|Opcional.  Indica que esta interface herda os atributos e membros de outra\(s\) interface\(s\).  Consulte [Instrução Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md).|  
|`interfacenames`|Necessário se você usar a declaração `Inherits`.  Os nomes das interfaces a partir das quais essa interface deriva.|  
|`modifiers`|Opcional.  Modificadores apropriados para o membro de interface sendo definido.|  
|`Property`|Opcional.  Define a propriedade que é um membro da interface.|  
|`Function`|Opcional.  Define um procedimento `Function` que é um membro da interface.|  
|`Sub`|Opcional.  Define um procedimento `Sub` que é um membro da interface.|  
|`Event`|Opcional.  Define um evento que é um membro da interface.|  
|`Interface`|Opcional.  Define uma interface que é um aninhamento dentro desta interface.  A definição aninhada de interface deve terminar com uma declaração `End Interface`.|  
|`Class`|Opcional.  Define uma classe que é um membro da interface.  A definição de classe de membro deve terminar com uma declaração `End Class`.|  
|`Structure`|Opcional.  Define uma estrutura que é membro da interface.  A definição membro de estrutura deve terminar com uma declaração `End Structure`.|  
|`membername`|Necessário para cada propriedade, procedimento, evento, interface, classe ou estrutura definidos como um membro da interface.  O nome do membro.|  
|`End Interface`|Finaliza a definição `Interface`.|  
  
## Comentários  
 Uma *interface* define um conjunto de membros, como propriedades ou procedimentos, que classes e estruturas podem implementar.  A interface define apenas as assinaturas dos membros e não seu funconamento interno.  
  
 Uma classe ou estrutura implementa a interface fornecendo código para todo membro definido pela interface.  Finalmente, quando o aplicativo cria um instância a partir daquela classe ou estrutura, um objeto existe e executa em memória.  Para obter mais informações, consulte [Objetos e classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md) e [Interfaces](../../../visual-basic/reference/command-line-compiler/index.md).  
  
 Você pode usar `Interface` somente em nível de namespace ou módulo.  Isto significa que o *contexto de declaração* para uma interface deve ser um arquivo\-fonte, namespace, estrutura, módulo, interface e não um procedimento ou bloco.  Para obter mais informações, consulte [Contextos de declaração e níveis de acesso padrão](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Interfaces padrão para acesso [Friend](../../../visual-basic/language-reference/modifiers/friend.md).  Você pode ajustar os seus níveis de acesso com os modificadores de acesso.  Para obter mais informações, consulte [Níveis de acesso no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## Regras  
  
-   **Interfaces de Aninhamento.** Você pode definir uma interface dentro de outra.  A interface mais externa é chamada a *interface continente*, e a interface mais interna é chamada uma *interface aninhada*.  
  
-   **Declaração de Membro.** Quando você declara uma propriedade ou um procedimento como um membro de uma interface, você está apenas definindo a  *assinatura* de propriedade ou de procedimento.  Isto inclui o tipo de elemento \(propriedade ou procedimento\), seus parâmetros e tipos de parâmetro, e seu tipo de retorno.  Por causa disso, a definição de membro usa apenas uma linha do código, e declarações de finalização como `End Function` ou `End Property` não são válidas numa interface.  
  
     Por outro lado, quando você define uma enumeração ou estrutura, ou uma classe ou interface aninhada, é necessário incluir seus membros de dados.  
  
-   **Modificadores de membros.** Não é possível usar qualquer modificadores de acesso ao definir os membros do módulo, nem pode especificar [Compartilhado](../../../visual-basic/language-reference/modifiers/shared.md) ou qualquer modificador de procedimento exceto [Sobrecargas](../../../visual-basic/language-reference/modifiers/overloads.md).  Você pode declarar qualquer membro com [Sombras](../../../visual-basic/language-reference/modifiers/shadows.md), e você pode usar [Padrão](../../../visual-basic/language-reference/modifiers/default.md) quando definir uma propriedade, assim como [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md) ou [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md).  
  
-   **Herança.** Se a interface usa o [Instrução Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md), você pode especificar uma ou mais interfaces de base.  Você pode herdar de duas interfaces mesmo que cada uma delas defina um membro com o mesmo nome.  Se fizer dessa forma, o código de implementação deve usar a mesma qualificação de nome para especificar que membro está sendo implementado.  
  
     Uma interface não pode herdar de outra interface com um nível de acesso mais restrito.  Por exemplo, uma interface `Public` não pode herdar de uma interface `Friend`.  
  
     Uma interface não pode herdar de uma interface aninhada nela.  
  
-   **Implementação.** Quando uma classe usa a [Implements](../../../visual-basic/language-reference/statements/implements-clause.md) instrução para implementar essa interface, ele deve implementar cada membro definido dentro da interface.  Além disso, cada assinatura no código de implementação deve coincidir exatamente com a assinatura correpondente definida nesta interface.  Entretanto, o nome do membro no código de implementação não precisa coincidir com o nome do membro definido na interface.  
  
     Quando uma classe está implementando um procedimento, ela não pode designá\-lo como `Shared`.  
  
-   **Propriedade padrão.** Uma interface pode especificar no máximo uma propriedade como sua  *propriedade padrão*, que podem ser referenciados sem usar o nome da propriedade.  Você especifica tal propriedade declarando\-a com o modificador [Padrão](../../../visual-basic/language-reference/modifiers/default.md).  
  
     Observe que isso significa que um interface pode definir uma propriedade padrão apenas se ela não herda nada.  
  
## Comportamento  
  
-   **Nível de acesso.** Todos os membros de interface implicitamente têm [Público](../../../visual-basic/language-reference/modifiers/public.md) acesso.  Você não pode usar nenhum modificador de acesso quando definir um membro.  Entretanto, a classe que implementa a interface pode declarar um nível de acesso para cada membro implementado.  
  
     Se você designar uma instância de classe a uma variável, o nível de acesso a seus membros pode depender de o tipo de dados da variável ser a interface subjacente ou a classe implementadora.  O exemplo a seguir ilustra isto:  
  
     [!code-vb[VbVbalrStatements#39](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/interface-statement_1.vb)]  
  
     Se você acessar membros de classe através de `varAsInterface`, todos eles possuem acesso público.  No entanto, se você acessar membros por meio de `varAsClass`, o `Sub` procedimento `doSomething` tem acesso particular.  
  
-   **Escopo.** Uma interface está em escopo por todo o seu namespace, classe, estrutura ou módulo.  
  
     O escopo de todo membro de interface é a interface inteira.  
  
-   **Tempo de vida.** Uma interface não possui um tempo de vida por ela mesma, nem seus membros.  Quando uma classe implementa uma interface e um objeto é criado como uma instância daquela classe, o objeto possui um tempo de vida dentro do aplicativo no qual ele esa sendo executado.  Para mais informações, consulte "Tempo de Vida" em [Instrução Class](../../../visual-basic/language-reference/statements/class-statement.md).  
  
## Exemplo  
 O exemplo a seguir usa a declaração `Interface` para definir uma interface denominada `thisInterface`, a qual deve ser implementada com uma declaração `Property` e uma `Function`.  
  
 [!code-vb[VbVbalrStatements#40](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/interface-statement_2.vb)]  
  
 Note que as declarações `Property` e `Function` não apresenta blocos terminando em `End Property` e `End Function` dentro da interface.  A interface define apenas assinaturas dos seus membros.  Os blocos inteiros `Property` e `Function` aparecem numa classe que implementa `thisInterface`.  
  
## Consulte também  
 [Interfaces](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Instrução Class](../../../visual-basic/language-reference/statements/class-statement.md)   
 [Instrução Module](../../../visual-basic/language-reference/statements/module-statement.md)   
 [Instrução Structure](../../../visual-basic/language-reference/statements/structure-statement.md)   
 [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)   
 [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)   
 [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Tipos genéricos no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [Variação em interfaces genéricas](../Topic/Variance%20in%20Generic%20Interfaces%20\(C%23%20and%20Visual%20Basic\).md)   
 [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)   
 [Out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)