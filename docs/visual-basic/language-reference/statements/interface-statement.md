---
title: "Instrução Interface (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Interface
helpviewer_keywords:
- interface statement [Visual Basic]
- interfaces [Visual Basic], interface definition
ms.assetid: 8997af73-bda3-4f79-bd41-ca396b610260
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9418dc86ac6947ae951cb8fb757aed6e092a6668
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="interface-statement-visual-basic"></a>Instrução Interface (Visual Basic)
Declara o nome de uma interface e apresenta as definições dos membros que compreende a interface.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
[ <attributelist> ] [ accessmodifier ] [ Shadows ] _  
Interface name [ ( Of typelist ) ]  
    [ Inherits interfacenames ]  
    [ [ modifiers ] Property membername ]  
    [ [ modifiers ] Function membername ]  
    [ [ modifiers ] Sub membername ]  
    [ [ modifiers ] Event membername ]  
    [ [ modifiers ] Interface membername ]  
    [ [ modifiers ] Class membername ]  
    [ [ modifiers ] Structure membername ]  
End Interface  
```  
  
## <a name="parts"></a>Partes  
  
|Termo|Definição|  
|---|---|  
|`attributelist`|Opcional. Consulte [lista de atributos](../../../visual-basic/language-reference/statements/attribute-list.md).|  
|`accessmodifier`|Opcional. Pode ser um dos seguintes:<br /><br /> -   [Público](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [Protegido](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [Privada](../../../visual-basic/language-reference/modifiers/private.md)<br />-   `Protected Friend`<br /><br /> Consulte [acessar níveis no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|  
|`Shadows`|Opcional. Consulte [sombras](../../../visual-basic/language-reference/modifiers/shadows.md).|  
|`name`|Necessário. Nome desta interface. Consulte [declarado nomes de elemento](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`Of`|Opcional. Especifica que esta é uma interface genérica.|  
|`typelist`|Necessário se você usar o [de](../../../visual-basic/language-reference/statements/of-clause.md) palavra-chave. Lista de parâmetros de tipo para esta interface. Opcionalmente, cada parâmetro de tipo pode ser declarado variante usando `In` e `Out` modificadores genéricos. Consulte [digite lista](../../../visual-basic/language-reference/statements/type-list.md).|  
|`Inherits`|Opcional. Indica que esta interface herda os atributos e membros de outra interface ou interfaces. Consulte [instrução Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md).|  
|`interfacenames`|Necessário se você usar o `Inherits` instrução. Os nomes das interfaces da qual esta interface derivada.|  
|`modifiers`|Opcional. Modificadores apropriados para o membro de interface que está sendo definido.|  
|`Property`|Opcional. Define uma propriedade que é um membro da interface.|  
|`Function`|Opcional. Define uma `Function` procedimento que é um membro da interface.|  
|`Sub`|Opcional. Define uma `Sub` procedimento que é um membro da interface.|  
|`Event`|Opcional. Define um evento que é um membro da interface.|  
|`Interface`|Opcional. Define uma interface que é aninhada dentro desta interface. A definição de interface aninhada deve terminar com um `End Interface` instrução.|  
|`Class`|Opcional. Define uma classe que é um membro da interface. A definição de classe de membro deve terminar com um `End Class` instrução.|  
|`Structure`|Opcional. Define uma estrutura que é um membro da interface. A definição da estrutura de membro deve terminar com um `End Structure` instrução.|  
|`membername`|Necessário para cada propriedade, procedimento, evento, interface, classe ou estrutura definida como um membro da interface. O nome do membro.|  
|`End Interface`|Encerra o `Interface` definição.|  
  
## <a name="remarks"></a>Comentários  
 Um *interface* define um conjunto de membros, como propriedades e procedimentos, que classes e estruturas podem implementar. A interface define apenas as assinaturas dos membros e não suas funções internas.  
  
 Uma classe ou estrutura implementa a interface fornecendo código para todos os membros definidos pela interface. Finalmente, quando o aplicativo cria uma instância da classe ou estrutura, um objeto existe e é executada na memória. Para obter mais informações, consulte [objetos e Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md) e [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md).  
  
 Você pode usar `Interface` apenas no nível de namespace ou módulo. Isso significa que o *contexto declaração* para uma interface deve ser um arquivo de origem, namespace, classe, estrutura, módulo ou interface e não pode ser um procedimento ou bloco. Para obter mais informações, consulte [Contextos de declaração e níveis de acesso padrão](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Interfaces padrão para [Friend](../../../visual-basic/language-reference/modifiers/friend.md) acesso. Você pode ajustar os níveis de acesso com os modificadores de acesso. Para obter mais informações, consulte [acessar níveis no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="rules"></a>Regras  
  
-   **Interfaces de aninhamento.** Você pode definir uma interface dentro de outra. A interface externa é chamada de *que contém a interface*, e a interface interna é chamada uma *interface aninhada*.  
  
-   **Declaração de membro.** Quando você declara uma propriedade ou procedimento como um membro de uma interface, você está definindo apenas o *assinatura* da propriedade ou procedimento. Isso inclui o tipo de elemento (propriedade ou procedimento), seus parâmetros e tipos de parâmetro e seu tipo de retorno. Por isso, a definição de membro usa apenas uma linha de código e declarações de finalização como `End Function` ou `End Property` não são válidos em uma interface.  
  
     Por outro lado, quando você define uma enumeração ou estrutura, ou uma classe aninhada ou interface, é necessário incluir seus membros de dados.  
  
-   **Modificadores de membro.** Você não pode usar quaisquer modificadores de acesso quando definir membros de módulo, nem especificar [compartilhado](../../../visual-basic/language-reference/modifiers/shared.md) ou qualquer modificador de procedimento exceto [sobrecargas](../../../visual-basic/language-reference/modifiers/overloads.md). Você pode declarar qualquer membro com [sombras](../../../visual-basic/language-reference/modifiers/shadows.md), e você pode usar [padrão](../../../visual-basic/language-reference/modifiers/default.md) ao definir uma propriedade, bem como [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md) ou [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md).  
  
-   **Herança.** Se a interface usa o [herda instrução](../../../visual-basic/language-reference/statements/inherits-statement.md), você pode especificar uma ou mais interfaces base. Você pode herdar de duas interfaces mesmo se cada uma define um membro com o mesmo nome. Se você fizer isso, o código de implementação deve usar qualificação de nome para especificar qual membro que está implementando.  
  
     Uma interface não pode herdar de outra interface com um nível de acesso mais restritivo. Por exemplo, um `Public` interface não pode herdar de um `Friend` interface.  
  
     Uma interface não pode herdar de uma interface aninhada dentro dele.  
  
-   **Implementação.** Quando uma classe usa a [implementa](../../../visual-basic/language-reference/statements/implements-clause.md) instrução para implementar esta interface, ele deve implementar todo membro definido dentro da interface. Além disso, cada assinatura no código de implementação deve corresponder exatamente a assinatura correspondente definida nesta interface. No entanto, o nome do membro no código de implementação não precisa corresponder ao nome de membro, conforme definido na interface.  
  
     Quando uma classe está implementando um procedimento, ele não pode designar o procedimento como `Shared`.  
  
-   **Propriedade padrão.** Uma interface pode especificar no máximo uma propriedade como seu *propriedade padrão*, que pode ser referenciado sem usar o nome da propriedade. Você especifica tal propriedade declarando-a com a [padrão](../../../visual-basic/language-reference/modifiers/default.md) modificador.  
  
     Observe que isso significa que uma interface pode definir uma propriedade padrão apenas se ela não herda nada.  
  
## <a name="behavior"></a>Comportamento  
  
-   **Nível de acesso.** Todos os membros de interface possuem implicitamente [pública](../../../visual-basic/language-reference/modifiers/public.md) acesso. Você não pode usar qualquer modificador de acesso quando definir um membro. No entanto, uma classe que implementa a interface pode declarar um nível de acesso para cada membro implementado.  
  
     Se você atribuir uma instância da classe para uma variável, o nível de acesso de seus membros pode depender se o tipo de dados da variável é a interface subjacente ou a classe de implementação. O exemplo a seguir ilustra essa situação.  
  
     [!code-vb[VbVbalrStatements#39](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/interface-statement_1.vb)]  
  
     Se você acessar membros de classe por meio de `varAsInterface`, todos eles possuem acesso público. No entanto, se você acessar membros por meio de `varAsClass`, o `Sub` procedimento `doSomething` possui acesso privado.  
  
-   **Escopo.** Uma interface está no escopo em todo o seu namespace, classe, estrutura ou módulo.  
  
     O escopo de cada membro de interface é a interface inteira.  
  
-   **Tempo de vida.** Uma interface propriamente dito não tem um tempo de vida, nem seus membros. Quando uma classe implementa uma interface e um objeto é criado como uma instância da classe, o objeto tem um tempo de vida do aplicativo no qual ele está em execução. Para obter mais informações, consulte "Tempo de vida" em [instrução Class](../../../visual-basic/language-reference/statements/class-statement.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `Interface` instrução para definir uma interface denominada `thisInterface`, que deve ser implementado com um `Property` instrução e um `Function` instrução.  
  
 [!code-vb[VbVbalrStatements#40](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/interface-statement_2.vb)]  
  
 Observe que o `Property` e `Function` instruções não apresenta blocos terminando com `End Property` e `End Function` dentro da interface. A interface define apenas assinaturas dos seus membros. Completa `Property` e `Function` blocos aparecem em uma classe que implementa `thisInterface`.  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md)  
 [Instrução Class](../../../visual-basic/language-reference/statements/class-statement.md)  
 [Instrução Module](../../../visual-basic/language-reference/statements/module-statement.md)  
 [Instrução Structure](../../../visual-basic/language-reference/statements/structure-statement.md)  
 [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)  
 [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)  
 [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Tipos genéricos no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Variação em Interfaces Genéricas](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)  
 [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)  
 [Saída](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
