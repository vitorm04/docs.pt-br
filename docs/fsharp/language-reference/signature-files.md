---
title: Arquivos de assinatura
description: Saiba como usar F# arquivos de assinatura para manter informações sobre as assinaturas públicas de um conjunto de F# elementos de programa, como tipos, namespaces e módulos.
ms.date: 06/15/2018
ms.openlocfilehash: c04ac8bf4ee360a2caa15be8f2bbea41105bd160
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627158"
---
# <a name="signatures"></a>Assinaturas

Um arquivo de assinatura contém informações sobre as assinaturas públicas de um conjunto de elementos de programação de F#, como tipos, namespaces e módulos. Ele pode ser usado para especificar a acessibilidade desses elementos de programa.

## <a name="remarks"></a>Comentários

Para cada F# arquivo de código, você pode ter um *arquivo de assinatura*, que é um arquivo que tem o mesmo nome que o arquivo de código, mas com a extensão. FSI em vez de. FS. Os arquivos de assinatura também podem ser adicionados à linha de comando de compilação se você estiver usando a linha de comando diretamente. Para distinguir entre arquivos de código e arquivos de assinatura, os arquivos de código, às vezes, são chamados de *arquivos de implementação*. Em um projeto, o arquivo de assinatura deve preceder o arquivo de código associado.

Um arquivo de assinatura descreve os namespaces, os módulos, os tipos e os membros no arquivo de implementação correspondente. Você usa as informações em um arquivo de assinatura para especificar quais partes do código no arquivo de implementação correspondente podem ser acessadas do código fora do arquivo de implementação e quais partes são internas ao arquivo de implementação. Os namespaces, os módulos e os tipos incluídos no arquivo de assinatura devem ser um subconjunto dos namespaces, módulos e tipos incluídos no arquivo de implementação. Com algumas exceções mencionadas posteriormente neste tópico, os elementos de idioma que não estão listados no arquivo de assinatura são considerados particulares para o arquivo de implementação. Se nenhum arquivo de assinatura for encontrado no projeto ou na linha de comando, a acessibilidade padrão será usada.

Para obter mais informações sobre a acessibilidade padrão, consulte [controle de acesso](access-control.md).

Em um arquivo de assinatura, você não repete a definição dos tipos e as implementações de cada método ou função. Em vez disso, você usa a assinatura para cada método e função, que atua como uma especificação completa da funcionalidade implementada por um fragmento de módulo ou de namespace. A sintaxe de uma assinatura de tipo é igual à usada em declarações de método abstratas em interfaces e classes abstratas, e também é mostrada pelo IntelliSense F# e pelo intérprete FSI. exe quando exibe a entrada compilada corretamente.

Se não houver informações suficientes na assinatura de tipo para indicar se um tipo é lacrado ou se é um tipo de interface, você deve adicionar um atributo que indique a natureza do tipo ao compilador. Os atributos que você usa para essa finalidade são descritos na tabela a seguir.

|Atributo|Descrição|
|---------|-----------|
|`[<Sealed>]`|Para um tipo que não tem membros abstratos ou que não deve ser estendido.|
|`[<Interface>]`|Para um tipo que é uma interface.|

O compilador produzirá um erro se os atributos não forem consistentes entre a assinatura e a declaração no arquivo de implementação.

Use a palavra `val` -chave para criar uma assinatura para um valor ou valor de função. A palavra `type` -chave apresenta uma assinatura de tipo.

Você pode gerar um arquivo de assinatura usando a `--sig` opção do compilador. Em geral, você não grava arquivos. FSI manualmente. Em vez disso, você gera arquivos. FSI usando o compilador, adiciona-os ao seu projeto, se você tiver um, e editá-los removendo métodos e funções que você não deseja que sejam acessíveis.

Há várias regras para assinaturas de tipo:

- As abreviações de tipo em um arquivo de implementação não devem corresponder a um tipo sem uma abreviação em um arquivo de assinatura.

- Registros e uniões discriminadas devem expor todos ou nenhum dos seus campos e construtores, e a ordem na assinatura deve corresponder à ordem no arquivo de implementação. As classes podem revelar alguns, todos ou nenhum dos seus campos e métodos na assinatura.

- Classes e estruturas que têm construtores devem expor as declarações de suas classes base (a `inherits` declaração). Além disso, as classes e estruturas que têm construtores devem expor todos os seus métodos abstratos e declarações de interface.

- Os tipos de interface devem revelar todos os seus métodos e interfaces.

As regras para as assinaturas de valor são as seguintes:

- Os modificadores para acessibilidade`public`( `internal`, e assim por diante) e `inline` os `mutable` modificadores e na assinatura devem corresponder aos da implementação.

- O número de parâmetros de tipo genérico (implicitamente inferido ou declarado explicitamente) deve corresponder, e os tipos e as restrições de tipo em parâmetros de tipo genérico devem corresponder.

- Se o `Literal` atributo for usado, ele deverá aparecer na assinatura e na implementação, e o mesmo valor literal deverá ser usado para ambos.

- O padrão de parâmetros (também conhecido como *arity*) de assinaturas e implementações deve ser consistente.

- Se os nomes de parâmetro em um arquivo de assinatura forem diferentes do arquivo de implementação correspondente, o nome no arquivo de assinatura será usado em vez disso, o que pode causar problemas durante a depuração ou a criação de perfil. Se você quiser ser notificado sobre tais incompatibilidades, habilite o aviso 3218 em seu arquivo de projeto ou ao invocar o `--warnon` compilador (consulte em [Opções do compilador](compiler-options.md)).

O exemplo de código a seguir mostra um exemplo de um arquivo de assinatura que tem o namespace, módulo, valor de função e assinaturas de tipo junto com os atributos apropriados. Ele também mostra o arquivo de implementação correspondente.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssignatures/snippet9002.fs)]

O código a seguir mostra o arquivo de implementação.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssignatures/snippet9001.fs)]

## <a name="see-also"></a>Consulte também

- [Referência da Linguagem F#](index.md)
- [Controle de Acesso](access-control.md)
- [Opções do Compilador](compiler-options.md)
