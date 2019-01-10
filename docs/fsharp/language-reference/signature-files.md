---
title: Arquivos de assinatura
description: Saiba como usar F# arquivos de assinatura para manter informações sobre as assinaturas públicas de um conjunto de F# elementos, como tipos, namespaces e módulos do programa.
ms.date: 06/15/2018
ms.openlocfilehash: 88938309a7c2bd12428f06ba8088141fd5349e80
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53613408"
---
# <a name="signatures"></a>Assinaturas

Um arquivo de assinatura contém informações sobre as assinaturas públicas de um conjunto de elementos de programação de F#, como tipos, namespaces e módulos. Ele pode ser usado para especificar a acessibilidade desses elementos de programa.

## <a name="remarks"></a>Comentários

Para cada F# arquivo de código, você pode ter um *arquivo de assinatura*, que é um arquivo que tem o mesmo nome que o arquivo de código, mas com o. FSI de extensão em vez de. FS. Arquivos de assinatura também podem ser adicionados à compilação de linha de comando se você estiver usando a linha de comando diretamente. Para distinguir entre arquivos de código e arquivos de assinatura, arquivos de código são às vezes chamados de *arquivos de implementação*. Em um projeto, o arquivo de assinatura deve preceder o arquivo de código associado.

Um arquivo de assinatura descreve os namespaces, módulos, tipos e membros no arquivo de implementação correspondente. Use as informações em um arquivo de assinatura para especificar quais partes do código na implementação correspondente arquivo pode ser acessado pelo código fora do arquivo de implementação e quais partes são internos ao arquivo de implementação. Os namespaces, módulos e tipos que são incluídos no arquivo de assinatura devem ser um subconjunto dos namespaces, módulos e tipos que são incluídos no arquivo de implementação. Com algumas exceções indicadas neste tópico, os elementos de linguagem que não estão listados no arquivo de assinatura são considerados particulares para o arquivo de implementação. Se nenhum arquivo de assinatura for encontrado no projeto ou na linha de comando, a acessibilidade padrão será usada.

Para obter mais informações sobre a acessibilidade padrão, consulte [controle de acesso](access-control.md).

Em um arquivo de assinatura, você não se repetem a definição dos tipos e as implementações de cada método ou função. Em vez disso, você deve usar a assinatura para cada método e a função, que atua como uma especificação completa da funcionalidade que é implementada por um fragmento de um módulo ou namespace. A sintaxe para uma assinatura de tipo é o mesmo usado em declarações de método abstrato em interfaces e classes abstratas e também é mostrada pelo IntelliSense e pelo F# interpretador fsi.exe quando ela for exibida corretamente compilado de entrada.

Se não há informações suficientes na assinatura de tipo para indicar se um tipo seja selado ou se ele é um tipo de interface, você deve adicionar um atributo que indica a natureza do tipo para o compilador. Atributos que você pode usar para essa finalidade são descritos na tabela a seguir.

|Atributo|Descrição|
|---------|-----------|
|`[<Sealed>]`|Um tipo que não tem nenhum membro abstrato, ou que não deve ser estendido.|
|`[<Interface>]`|Um tipo que é uma interface.|

O compilador produz um erro se os atributos não são consistentes entre a assinatura e a declaração no arquivo de implementação.

Use a palavra-chave `val` para criar uma assinatura para um valor ou o valor da função. A palavra-chave `type` apresenta uma assinatura de tipo.

Você pode gerar um arquivo de assinatura usando o `--sig` opção de compilador. Em geral, você não gravar arquivos. FSI manualmente. Em vez disso, você pode gerar arquivos. FSI, usando o compilador, adicioná-los ao seu projeto, se você tiver um e editá-los, removendo os métodos e as funções que você não deseja ser acessível.

Há várias regras para assinaturas de tipo:

- Abreviações de tipo em um arquivo de implementação não devem corresponder a um tipo sem uma abreviação em um arquivo de assinatura.

- Registros e uniões discriminadas devem expor todos ou nenhum dos seus construtores e campos, e a ordem em que a assinatura deve corresponder à ordem no arquivo de implementação. As classes podem revelar alguns, todos ou nenhum dos seus campos e métodos na assinatura.

- Classes e estruturas que têm construtores devem expor as declarações de suas classes base (o `inherits` declaração). Além disso, classes e estruturas que têm construtores devem expor todos os seus métodos abstratos e declarações de interface.

- Tipos de interface devem revelar todos os seus métodos e interfaces.

As regras para assinaturas de valor são da seguinte maneira:

- Modificadores de acessibilidade (`public`, `internal`e assim por diante) e o `inline` e `mutable` modificadores na assinatura devem corresponder na implementação.

- O número de parâmetros de tipo genérico (ou inferido implicitamente ou explicitamente declarado) deve corresponder ao, e os tipos e as restrições de tipo em parâmetros de tipo genérico devem corresponder.

- Se o `Literal` atributo é usado, ele deverá aparecer na assinatura do e a implementação e o mesmo valor literal deve ser usado para ambos.

- O padrão de parâmetros (também conhecido como o *arity*) de assinaturas e implementações devem ser consistentes.

- Se os nomes de parâmetro em um arquivo de assinatura forem diferentes do arquivo de implementação correspondente, o nome no arquivo de assinatura será usado em vez disso, que pode causar problemas ao depurar ou criação de perfil. Se você quiser ser notificado sobre tais incompatibilidades, habilitar 3218 de aviso no arquivo de projeto ou ao invocar o compilador (consulte `--warnon` sob [opções do compilador](compiler-options.md)).

O exemplo de código a seguir mostra um exemplo de um arquivo de assinatura que tem o namespace, módulo, o valor de função e as assinaturas de tipo junto com os atributos apropriados. Ele também mostra o arquivo de implementação correspondente.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssignatures/snippet9002.fs)]

O código a seguir mostra o arquivo de implementação.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssignatures/snippet9001.fs)]

## <a name="see-also"></a>Consulte também

- [Referência da Linguagem F#](index.md)
- [Controle de Acesso](access-control.md)
- [Opções do Compilador](compiler-options.md)
