---
title: Instrução Property (Visual Basic)
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
ms.openlocfilehash: 2c3e417aad404171a43342dc92773615ec350ef5
ms.sourcegitcommit: 8b8dd14dde727026fd0b6ead1ec1df2e9d747a48
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71332744"
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

- `attributelist`

  Opcional. Lista de atributos que se aplicam a esta propriedade ou ao procedimento `Get` ou `Set`. Consulte a [lista de atributos](attribute-list.md).

- `Default`

  Opcional. Especifica que essa propriedade é a propriedade padrão para a classe ou estrutura na qual ela está definida. As propriedades padrão devem aceitar parâmetros e podem ser definidas e recuperadas sem especificar o nome da propriedade. Se você declarar a propriedade como `Default`, não poderá usar `Private` na propriedade ou em qualquer um dos seus procedimentos de propriedade.

- `accessmodifier`

  Opcional na instrução `Property` e em no máximo uma das instruções `Get` e `Set`. Pode ser um dos seguintes:

  - [Público](../modifiers/public.md)

  - [Protegido](../modifiers/protected.md)

  - [Friend](../modifiers/friend.md)

  - [Privado](../modifiers/private.md)

  - [Amigo Protegido](../modifiers/protected-friend.md)

  - [Particular Protegido](../modifiers/private-protected.md)

  Consulte [níveis de acesso em Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).

- `propertymodifiers`

  Opcional. Pode ser um dos seguintes:

  - [Sobrecargas](../modifiers/overloads.md)

  - [Substituições](../modifiers/overrides.md)

  - [Substituível](../modifiers/overridable.md)

  - [NotOverridable](../modifiers/notoverridable.md)

  - [MustOverride](../modifiers/mustoverride.md)

  - `MustOverride Overrides`

  - `NotOverridable Overrides`

- `Shared`

  Opcional. Consulte [compartilhado](../modifiers/shared.md).

- `Shadows`

  Opcional. Consulte [Shadows](../modifiers/shadows.md).

- `ReadOnly`

  Opcional. Consulte [ReadOnly](../modifiers/readonly.md).

- `WriteOnly`

  Opcional. Consulte [WriteOnly](../modifiers/writeonly.md).

- `Iterator`

  Opcional. Consulte [iterador](../modifiers/iterator.md).

- `name`

  Necessário. Nome da propriedade. Consulte [nomes de elementos declarados](../../programming-guide/language-features/declared-elements/declared-element-names.md).

- `parameterlist`

  Opcional. Lista de nomes de variáveis locais que representam os parâmetros dessa propriedade e possíveis parâmetros adicionais do procedimento `Set`. Consulte a [lista de parâmetros](parameter-list.md).

- `returntype`

  Necessário se `Option Strict` for `On`. Tipo de dados do valor retornado por essa propriedade.

- `Implements`

  Opcional. Indica que essa propriedade implementa uma ou mais propriedades, cada uma definida em uma interface implementada por essa propriedade que contém a classe ou a estrutura. Consulte a [instrução Implements](implements-statement.md).

- `implementslist`

  Necessário se `Implements` for fornecido. Lista de propriedades que estão sendo implementadas.

  `implementedproperty [ , implementedproperty ... ]`

  Cada `implementedproperty` tem a seguinte sintaxe e partes:

  `interface.definedname`

  |Parte|Descrição|
  |---|---|
  |`interface`|Necessário. Nome de uma interface implementada por essa propriedade que contém a classe ou a estrutura.|
  |`definedname`|Necessário. Nome pelo qual a propriedade é definida em `interface`.|

- `Get`

  Opcional. Obrigatório se a propriedade estiver marcada `ReadOnly`. Inicia um procedimento de propriedade `Get` que é usado para retornar o valor da propriedade.  A instrução `Get` não é usada com [Propriedades implementadas automaticamente](../../programming-guide/language-features/procedures/auto-implemented-properties.md).

- `statements`

  Opcional. Bloco de instruções a serem executadas dentro do procedimento `Get` ou `Set`.

- `End Get`

  Encerra o procedimento de propriedade `Get`.

- `Set`

  Opcional. Obrigatório se a propriedade estiver marcada `WriteOnly`. Inicia um procedimento de propriedade `Set` que é usado para armazenar o valor da propriedade.  A instrução `Set` não é usada com [Propriedades implementadas automaticamente](../../programming-guide/language-features/procedures/auto-implemented-properties.md).

- `End Set`

  Encerra o procedimento de propriedade `Set`.

- `End Property`

  Encerra a definição desta propriedade.

## <a name="remarks"></a>Comentários

A instrução `Property` apresenta a declaração de uma propriedade. Uma propriedade pode ter um procedimento `Get` (somente leitura), um procedimento `Set` (somente gravação) ou ambos (leitura-gravação). Você pode omitir o `Get` e o procedimento `Set` ao usar uma propriedade implementada automaticamente. Para obter mais informações, consulte [Propriedades autoimplementadas](../../programming-guide/language-features/procedures/auto-implemented-properties.md).

Você pode usar `Property` somente no nível de classe. Isso significa que o *contexto de declaração* para uma propriedade deve ser uma classe, estrutura, módulo ou interface e não pode ser um arquivo de origem, namespace, procedimento ou bloco. Para obter mais informações, consulte [Contextos de declaração e níveis de acesso padrão](declaration-contexts-and-default-access-levels.md).

Por padrão, as propriedades usam acesso público. Você pode ajustar o nível de acesso de uma propriedade com um modificador de acesso na instrução `Property` e, opcionalmente, pode ajustar um de seus procedimentos de propriedade para um nível de acesso mais restritivo.

Visual Basic passa um parâmetro para o procedimento `Set` durante as atribuições de propriedade. Se você não fornecer um parâmetro para `Set`, o ambiente de desenvolvimento integrado (IDE) usará um parâmetro implícito denominado `value`. Esse parâmetro contém o valor a ser atribuído à propriedade. Normalmente, você armazena esse valor em uma variável local privada e retorna-o sempre que o procedimento `Get` for chamado.

## <a name="rules"></a>Regras

- **Níveis de acesso misto.** Se você estiver definindo uma propriedade de leitura/gravação, você pode opcionalmente especificar um nível de acesso diferente para o procedimento `Get` ou `Set`, mas não ambos. Se você fizer isso, o nível de acesso do procedimento deverá ser mais restritivo do que o nível de acesso da propriedade. Por exemplo, se a propriedade for declarada `Friend`, você poderá declarar o procedimento `Set` `Private`, mas não `Public`.

  Se você estiver definindo uma propriedade `ReadOnly` ou `WriteOnly`, o procedimento de propriedade única (`Get` ou `Set`, respectivamente) representará toda a propriedade. Você não pode declarar um nível de acesso diferente para tal procedimento, pois isso definiria dois níveis de acesso para a propriedade.

- **Tipo de retorno.** A instrução `Property` pode declarar o tipo de dados do valor que ele retorna. Você pode especificar qualquer tipo de dados ou o nome de uma enumeração, estrutura, classe ou interface.

  Se você não especificar `returntype`, a propriedade retornará `Object`.

- **Implementação.** Se essa propriedade usar a palavra-chave `Implements`, a classe contendo ou a estrutura deverá ter uma instrução `Implements` imediatamente após sua instrução `Class` ou `Structure`. A instrução `Implements` deve incluir cada interface especificada em `implementslist`. No entanto, o nome pelo qual uma interface define o `Property` (em `definedname`) não precisa ser o mesmo que o nome dessa propriedade (em `name`).

## <a name="behavior"></a>Comportamento

- **Retornando de um procedimento de propriedade.** Quando o procedimento `Get` ou `Set` retorna ao código de chamada, a execução continua com a instrução após a instrução que o invocou.

  As instruções `Exit Property` e `Return` causam uma saída imediata de um procedimento de propriedade. Qualquer número de instruções `Exit Property` e `Return` pode aparecer em qualquer lugar no procedimento, e você pode misturar instruções `Exit Property` e `Return`.

- **Valor de retorno.** Para retornar um valor de um procedimento `Get`, você pode atribuir o valor ao nome da propriedade ou incluí-lo em uma instrução `Return`. O exemplo a seguir atribui o valor de retorno ao nome da propriedade `quoteForTheDay` e, em seguida, usa a instrução `Exit Property` para retornar.

  [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]

  [!code-vb[VbVbalrStatements#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#28)]

  Se você usar `Exit Property` sem atribuir um valor a `name`, o procedimento `Get` retornará o valor padrão para o tipo de dados da propriedade.

  A instrução `Return` ao mesmo tempo atribui o valor de retorno do procedimento `Get` e sai do procedimento. O exemplo a seguir mostra isso.

  [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]

  [!code-vb[VbVbalrStatements#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#29)]

## <a name="example"></a>Exemplo

O exemplo a seguir declara uma propriedade em uma classe.

[!code-vb[VbVbalrStatements#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#51)]

## <a name="see-also"></a>Consulte também

- [Propriedades Autoimplementadas](../../programming-guide/language-features/procedures/auto-implemented-properties.md)
- [Objetos e Classes](../../programming-guide/language-features/objects-and-classes/index.md)
- [Instrução Get](get-statement.md)
- [Instrução Set](set-statement.md)
- [Lista de Parâmetros](parameter-list.md)
- [Padrão](../modifiers/default.md)
