---
title: Instrução Interface
ms.date: 05/12/2018
f1_keywords:
- vb.Interface
helpviewer_keywords:
- interface statement [Visual Basic]
- interfaces [Visual Basic], interface definition
ms.assetid: 8997af73-bda3-4f79-bd41-ca396b610260
ms.openlocfilehash: b606f24cf3baa13746834dfbf7ca6b9215fd3558
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348049"
---
# <a name="interface-statement-visual-basic"></a>Instrução Interface (Visual Basic)
Declara o nome de uma interface e apresenta as definições dos membros que a interface compreende.  
  
## <a name="syntax"></a>Sintaxe  
  
```vb  
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
|`attributelist`|Opcional. Consulte a [lista de atributos](../../../visual-basic/language-reference/statements/attribute-list.md).|  
|`accessmodifier`|Opcional. Pode ser um dos seguintes:<br /><br /> [público](../../../visual-basic/language-reference/modifiers/public.md) -   <br />-   [protegido](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [amigo](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [privado](../../../visual-basic/language-reference/modifiers/private.md)<br />-  [amigo protegido](../../language-reference/modifiers/protected-friend.md)<br/>- [privada protegida](../../language-reference/modifiers/private-protected.md)<br /><br /> Consulte [níveis de acesso em Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|  
|`Shadows`|Opcional. Consulte [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).|  
|`name`|Necessária. Nome desta interface. Consulte [nomes de elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`Of`|Opcional. Especifica que esta é uma interface genérica.|  
|`typelist`|Necessário se você usar a palavra-chave [of](../../../visual-basic/language-reference/statements/of-clause.md) . Lista de parâmetros de tipo para esta interface. Opcionalmente, cada parâmetro de tipo pode ser declarado como Variant usando `In` e `Out` modificadores genéricos. Consulte [lista de tipos](../../../visual-basic/language-reference/statements/type-list.md).|  
|`Inherits`|Opcional. Indica que essa interface herda os atributos e membros de outra interface ou interfaces. Consulte a [instrução Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md).|  
|`interfacenames`|Necessário se você usar a instrução `Inherits`. Os nomes das interfaces das quais essa interface deriva.|  
|`modifiers`|Opcional. Modificadores apropriados para o membro da interface que está sendo definido.|  
|`Property`|Opcional. Define uma propriedade que é um membro da interface.|  
|`Function`|Opcional. Define um procedimento `Function` que é um membro da interface.|  
|`Sub`|Opcional. Define um procedimento `Sub` que é um membro da interface.|  
|`Event`|Opcional. Define um evento que é um membro da interface.|  
|`Interface`|Opcional. Define uma interface que é aninhada dentro desta interface. A definição de interface aninhada deve terminar com uma instrução `End Interface`.|  
|`Class`|Opcional. Define uma classe que é membro da interface. A definição de classe de membro deve terminar com uma instrução `End Class`.|  
|`Structure`|Opcional. Define uma estrutura que é membro da interface. A definição da estrutura do membro deve terminar com uma instrução `End Structure`.|  
|`membername`|Necessário para cada propriedade, procedimento, evento, interface, classe ou estrutura definida como um membro da interface. O nome do membro.|  
|`End Interface`|Encerra a definição de `Interface`.|  
  
## <a name="remarks"></a>Comentários  
 Uma *interface* define um conjunto de membros, como propriedades e procedimentos, que as classes e estruturas podem implementar. A interface define apenas as assinaturas dos membros e não seus trabalhos internos.  
  
 Uma classe ou estrutura implementa a interface fornecendo o código para cada membro definido pela interface. Por fim, quando o aplicativo cria uma instância dessa classe ou estrutura, um objeto existe e é executado na memória. Para obter mais informações, consulte [objetos e classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md) e [interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md).  
  
 Você pode usar `Interface` apenas em nível de namespace ou de módulo. Isso significa que o *contexto de declaração* para uma interface deve ser um arquivo de origem, namespace, classe, estrutura, módulo ou interface e não pode ser um procedimento ou bloco. Para obter mais informações, consulte [Contextos de declaração e níveis de acesso padrão](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Interfaces padrão para acesso [Friend](../../../visual-basic/language-reference/modifiers/friend.md) . Você pode ajustar seus níveis de acesso com os modificadores de acesso. Para obter mais informações, consulte [níveis de acesso em Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="rules"></a>Regras  
  
- **Aninhando interfaces.** Você pode definir uma interface dentro de outra. A interface externa é chamada de *interface que a contém*e a interface interna é chamada de *interface aninhada*.  
  
- **Declaração de membro.** Quando você declara uma propriedade ou um procedimento como membro de uma interface, você está definindo apenas a *assinatura* dessa propriedade ou procedimento. Isso inclui o tipo de elemento (Propriedade ou procedimento), seus parâmetros e tipos de parâmetro e seu tipo de retorno. Por isso, a definição de membro usa apenas uma linha de código e as instruções de término, como `End Function` ou `End Property`, não são válidas em uma interface.  
  
     Por outro lado, quando você define uma enumeração ou uma estrutura, ou uma classe ou interface aninhada, é necessário incluir seus membros de dados.  
  
- **Modificadores de membro.** Você não pode usar nenhum modificador de acesso ao definir membros de módulo, nem pode especificar qualquer modificador [compartilhado](../../../visual-basic/language-reference/modifiers/shared.md) ou de procedimento, exceto [sobrecargas](../../../visual-basic/language-reference/modifiers/overloads.md). Você pode declarar qualquer membro com [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)e pode usar [Default](../../../visual-basic/language-reference/modifiers/default.md) ao definir uma propriedade, bem como [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md) ou [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md).  
  
- **Herança.** Se a interface usar a [instrução Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md), você poderá especificar uma ou mais interfaces base. Você pode herdar de duas interfaces, mesmo se cada uma delas definir um membro com o mesmo nome. Se você fizer isso, o código de implementação deverá usar a qualificação de nome para especificar qual membro está sendo implementado.  
  
     Uma interface não pode herdar de outra interface com um nível de acesso mais restritivo. Por exemplo, uma interface `Public` não pode herdar de uma interface `Friend`.  
  
     Uma interface não pode herdar de uma interface aninhada dentro dela.  
  
- **Implementação.** Quando uma classe usa a instrução [Implements](../../../visual-basic/language-reference/statements/implements-clause.md) para implementar essa interface, ela deve implementar todos os membros definidos na interface. Além disso, cada assinatura no código de implementação deve corresponder exatamente à assinatura correspondente definida nesta interface. No entanto, o nome do membro no código de implementação não precisa corresponder ao nome do membro conforme definido na interface.  
  
     Quando uma classe está implementando um procedimento, ela não pode designar o procedimento como `Shared`.  
  
- **Propriedade padrão.** Uma interface pode especificar, no máximo, uma propriedade como sua *propriedade padrão*, que pode ser referenciada sem usar o nome da propriedade. Você especifica tal propriedade declarando-a com o modificador [padrão](../../../visual-basic/language-reference/modifiers/default.md) .  
  
     Observe que isso significa que uma interface pode definir uma propriedade padrão somente se ela não herda nenhuma.  
  
## <a name="behavior"></a>Comportamento  
  
- **Nível de acesso.** Todos os membros de interface implicitamente têm acesso [público](../../../visual-basic/language-reference/modifiers/public.md) . Você não pode usar nenhum modificador de acesso ao definir um membro. No entanto, uma classe que implementa a interface pode declarar um nível de acesso para cada membro implementado.  
  
     Se você atribuir uma instância de classe a uma variável, o nível de acesso de seus membros poderá depender se o tipo de dados da variável é a interface subjacente ou a classe de implementação. O exemplo a seguir mostra isso.  
  
     [!code-vb[VbVbalrStatements#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#39)]  
  
     Se você acessar membros de classe por meio de `varAsInterface`, todos eles terão acesso público. No entanto, se você acessar membros por meio de `varAsClass`, o procedimento `Sub` `doSomething` terá acesso privado.  
  
- **Com.** Uma interface está no escopo em todo o namespace, classe, estrutura ou módulo.  
  
     O escopo de cada membro de interface é a interface inteira.  
  
- **Existência.** Uma interface não tem, ela própria, um tempo de vida, nem seus membros. Quando uma classe implementa uma interface e um objeto é criado como uma instância dessa classe, o objeto tem um tempo de vida dentro do aplicativo no qual está sendo executado. Para obter mais informações, consulte "Lifetime" na [declaração de classe](../../../visual-basic/language-reference/statements/class-statement.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa a instrução `Interface` para definir uma interface chamada `thisInterface`, que deve ser implementada com uma instrução `Property` e uma instrução `Function`.  
  
 [!code-vb[VbVbalrStatements#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#40)]  
  
 Observe que as instruções `Property` e `Function` não introduzem blocos que terminam com `End Property` e `End Function` dentro da interface. A interface define somente as assinaturas de seus membros. Os blocos Full `Property` e `Function` aparecem em uma classe que implementa `thisInterface`.  
  
## <a name="see-also"></a>Consulte também

- [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
- [Instrução Class](../../../visual-basic/language-reference/statements/class-statement.md)
- [Instrução Module](../../../visual-basic/language-reference/statements/module-statement.md)
- [Instrução Structure](../../../visual-basic/language-reference/statements/structure-statement.md)
- [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)
- [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)
- [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Tipos genéricos no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Variação em Interfaces Genéricas](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)
- [Saída](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
