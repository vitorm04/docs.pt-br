---
title: Declaração de propriedade (Visual Basic)
ms.date: 05/12/2018
f1_keywords:
- vb.PropertySet
- vb.Property
- vb.PropertyGet
helpviewer_keywords:
- Property statement [Visual Basic]
- default modifier
- property procedures [Visual Basic], Property statements
- Property keyword [Visual Basic]
ms.assetid: 3155edaf-8ebd-45c6-9cef-11d5d2dc8d38
ms.openlocfilehash: 21ca15d6a6939d884c7e6abedc1f7919be079edd
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43420375"
---
# <a name="property-statement"></a>Instrução Property
Declara o nome de uma propriedade e os procedimentos de propriedade usados para armazenar e recuperar o valor da propriedade.  
  
## <a name="syntax"></a>Sintaxe  
  
```vb  
[ <attributelist> ] [ Default ] [ accessmodifier ]   
[ propertymodifiers ] [ Shared ] [ Shadows ] [ ReadOnly | WriteOnly ] [ Iterator ]  
Property name ( [ parameterlist ] ) [ As returntype ] [ Implements implementslist ]  
    [ <attributelist> ] [ accessmodifier ] Get  
        [ statements ]  
    End Get  
    [ <attributelist> ] [ accessmodifier ] Set ( ByVal value As returntype [, parameterlist ] )  
        [ statements ]  
    End Set  
End Property  
- or -  
[ <attributelist> ] [ Default ] [ accessmodifier ]   
[ propertymodifiers ] [ Shared ] [ Shadows ] [ ReadOnly | WriteOnly ]   
Property name ( [ parameterlist ] ) [ As returntype ] [ Implements implementslist ]  
```  
  
## <a name="parts"></a>Partes  
  
-   `attributelist`  
  
     Opcional. Lista de atributos que se aplicam a essa propriedade ou `Get` ou `Set` procedimento. Ver [lista de atributos](../../../visual-basic/language-reference/statements/attribute-list.md).  
  
-   `Default`  
  
     Opcional. Especifica que essa propriedade é a propriedade padrão para a classe ou estrutura na qual ele está definido. As propriedades padrão devem aceitar parâmetros e podem ser definidas e recuperadas sem especificar o nome da propriedade. Se você declarar a propriedade como `Default`, você não pode usar `Private` na propriedade ou um de seus procedimentos de propriedade.  
  
-   `accessmodifier`  
  
     Opcional sobre o `Property` instrução e no máximo um da `Get` e `Set` instruções. Pode ser uma das seguintes opções:  
  
    -   [Público](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [Protegido](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [Privado](../../../visual-basic/language-reference/modifiers/private.md)  
  
    - [Friend protegido](../../language-reference/modifiers/protected-friend.md) 

    - [Privado protegido](../../language-reference/modifiers/private-protected.md)
  
     Ver [acessar níveis no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
-   `propertymodifiers`  
  
     Opcional. Pode ser uma das seguintes opções:  
  
    -   [Sobrecargas](../../../visual-basic/language-reference/modifiers/overloads.md)  
  
    -   [Substituições](../../../visual-basic/language-reference/modifiers/overrides.md)  
  
    -   [Substituível](../../../visual-basic/language-reference/modifiers/overridable.md)  
  
    -   [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
  
    -   [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
  
    -   `MustOverride Overrides`  
  
    -   `NotOverridable Overrides`  
  
-   `Shared`  
  
     Opcional. Ver [compartilhado](../../../visual-basic/language-reference/modifiers/shared.md).  
  
-   `Shadows`  
  
     Opcional. Ver [sombras](../../../visual-basic/language-reference/modifiers/shadows.md).  
  
-   `ReadOnly`  
  
     Opcional. Ver [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
-   `WriteOnly`  
  
     Opcional. Ver [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md).  
  
-   `Iterator`  
  
     Opcional. Ver [iterador](../../../visual-basic/language-reference/modifiers/iterator.md).  
  
-   `name`  
  
     Necessário. Nome da propriedade. Ver [nomes de elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
-   `parameterlist`  
  
     Opcional. Lista de nomes de variável local que representa os parâmetros da propriedade e possíveis parâmetros adicionais do `Set` procedimento. Ver [lista de parâmetros](../../../visual-basic/language-reference/statements/parameter-list.md).  
  
-   `returntype`  
  
     Necessário se `Option Strict` é `On`. Tipo de dados do valor retornado por essa propriedade.  
  
-   `Implements`  
  
     Opcional. Indica que essa propriedade implementa uma ou mais propriedades, cada uma delas definida em uma interface implementada pela classe ou estrutura que contém essa propriedade. Ver [implementa a instrução](../../../visual-basic/language-reference/statements/implements-statement.md).  
  
-   `implementslist`  
  
     Necessário se `Implements` for fornecido. Lista de propriedades que está sendo implementado.  
  
     `implementedproperty [ , implementedproperty ... ]`  
  
     Cada `implementedproperty` tem a seguinte sintaxe e partes:  
  
     `interface.definedname`  
  
    |Parte|Descrição|  
    |---|---|  
    |`interface`|Necessário. Que contém o nome de uma interface implementada por esta propriedade de classe ou estrutura.|  
    |`definedname`|Necessário. Nome pelo qual a propriedade é definida no `interface`.|  
  
-   `Get`  
  
     Opcional. Necessário se a propriedade é marcada como `WriteOnly`. Inicia uma `Get` procedimento de propriedade que é usado para retornar o valor da propriedade.  
  
-   `statements`  
  
     Opcional. Bloco de instruções para executar dentro de `Get` ou `Set` procedimento.  
  
-   `End Get`  
  
     Encerra o `Get` procedimento de propriedade.  
  
-   `Set`  
  
     Opcional. Necessário se a propriedade é marcada como `ReadOnly`. Inicia uma `Set` procedimento de propriedade que é usado para armazenar o valor da propriedade.  
  
-   `End Set`  
  
     Encerra o `Set` procedimento de propriedade.  
  
-   `End Property`  
  
     Finaliza a definição dessa propriedade.  
  
## <a name="remarks"></a>Comentários  
 O `Property` instrução introduz a declaração de uma propriedade. Uma propriedade pode ter um `Get` procedimento (somente leitura), um `Set` procedimento (somente gravação), ou ambos (leitura-gravação). Você pode omitir as `Get` e `Set` procedimento ao usar uma propriedade implementada automaticamente. Para obter mais informações, consulte [Propriedades autoimplementadas](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md).  
  
 Você pode usar `Property` apenas no nível de classe. Isso significa que o *contexto de declaração* para uma propriedade deve ser uma classe, estrutura, módulo ou interface e não pode ser um arquivo de origem, namespace, procedimento ou bloco. Para obter mais informações, consulte [Contextos de declaração e níveis de acesso padrão](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Por padrão, as propriedades usam acesso público. Você pode ajustar o nível de acesso da propriedade com um modificador de acesso a `Property` instrução e, opcionalmente, pode ajustar um dos seus procedimentos de propriedade para um nível de acesso mais restritivo.  
  
 Visual Basic passa um parâmetro para o `Set` procedimento durante atribuições de propriedade. Se você não fornecer um parâmetro para `Set`, o ambiente de desenvolvimento integrado (IDE) usa uma parâmetro implícito chamada `value`. Este parâmetro contém o valor a ser atribuído à propriedade. Você normalmente armazena esse valor em uma variável local privada e retorná-lo sempre que o `Get` procedimento é chamado.  
  
## <a name="rules"></a>Regras  
  
-   **Níveis de acesso mistos.** Se você estiver definindo uma propriedade de leitura / gravação, você pode, opcionalmente, especificar um nível de acesso diferentes para qualquer um de `Get` ou o `Set` procedimento, mas não ambos. Se você fizer isso, o nível de acesso do procedimento deve ser mais restritivo do que o nível de acesso da propriedade. Por exemplo, se a propriedade é declarada `Friend`, você pode declarar o `Set` procedimento `Private`, mas não `Public`.  
  
     Se você estiver definindo uma `ReadOnly` ou `WriteOnly` propriedade, o procedimento de propriedade única (`Get` ou `Set`, respectivamente) representa todos os da propriedade. Você não pode declarar um nível de acesso diferentes para procedimento, pois isso configuraria dois níveis de acesso para a propriedade.  
  
-   **Tipo de retorno.** O `Property` instrução pode declarar o tipo de dados do valor que ele retorna. Você pode especificar qualquer tipo de dados ou o nome de uma enumeração, estrutura, classe ou interface.  
  
     Se você não especificar `returntype`, a propriedade retorna `Object`.  
  
-   **Implementação.** Se esta propriedade usa a `Implements` deve ter a palavra-chave, a classe ou estrutura contendo um `Implements` instrução imediatamente após sua `Class` ou `Structure` instrução. O `Implements` instrução deve incluir cada interface especificada em `implementslist`. No entanto, o nome pelo qual uma interface define os `Property` (no `definedname`) não precisa ser o mesmo que o nome da propriedade (em `name`).  
  
## <a name="behavior"></a>Comportamento  
  
-   **Retornando de um procedimento de propriedade.** Quando o `Get` ou `Set` procedimento retorna para o código de chamada, a execução continua com a instrução após a instrução que a invocou.  
  
     O `Exit Property` e `Return` instruções fazem com que uma saída imediata de um procedimento de propriedade. Qualquer número de `Exit Property` e `Return` instruções podem aparecer em qualquer lugar no procedimento, e você pode misturar `Exit Property` e `Return` instruções.  
  
-   **Valor de retorno.** Para retornar um valor de uma `Get` procedimento, você pode atribuir o valor para o nome da propriedade ou incluí-lo em um `Return` instrução. O exemplo a seguir atribui o valor de retorno para o nome da propriedade `quoteForTheDay` e, em seguida, usa o `Exit Property` instrução para retornar.  
  
     [!code-vb[VbVbalrStatements#27](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_1.vb)]  
  
     [!code-vb[VbVbalrStatements#28](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_2.vb)]  
  
     Se você usar `Exit Property` sem atribuir um valor para `name`, o `Get` procedimento retorna o valor padrão para o tipo de dados da propriedade.  
  
     O `Return` instrução ao mesmo tempo atribui o `Get` de valor e finaliza o procedimento de retorno de procedimento. O exemplo a seguir mostra isso.  
  
     [!code-vb[VbVbalrStatements#27](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_1.vb)]  
  
     [!code-vb[VbVbalrStatements#29](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_3.vb)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir declara uma propriedade em uma classe.  
  
 [!code-vb[VbVbalrStatements#51](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_4.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Propriedades Autoimplementadas](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md)  
 [Objetos e Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [Instrução Get](../../../visual-basic/language-reference/statements/get-statement.md)  
 [Instrução Set](../../../visual-basic/language-reference/statements/set-statement.md)  
 [Lista de Parâmetros](../../../visual-basic/language-reference/statements/parameter-list.md)  
 [Padrão](../../../visual-basic/language-reference/modifiers/default.md)
