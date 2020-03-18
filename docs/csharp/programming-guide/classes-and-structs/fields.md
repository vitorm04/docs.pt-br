---
title: Campos – Guia de Programação em C#
ms.date: 07/20/2015
helpviewer_keywords:
- fields [C#]
ms.assetid: 3cbb2f61-75f8-4cce-b4ef-f5d1b3de0db7
ms.openlocfilehash: 46d4f77a4a490b2acdb5da20b9a477f27c38d410
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77628235"
---
# <a name="fields-c-programming-guide"></a>Campos (Guia de Programação em C#)

Um *campo* é uma variável de qualquer tipo que é declarada diretamente em uma [classe](../../language-reference/keywords/class.md) ou [struct](../../language-reference/builtin-types/struct.md). Os campos são *membros* do tipo que os contém.

Uma classe ou estrutura pode ter campos de ocorrência, campos estáticos ou ambos. Os campos de instância são específicos a uma instância de um tipo. Se você tem uma classe T, com um campo de instância F, você pode criar dois objetos do tipo T e modificar o valor de F em cada objeto sem afetar o valor no outro objeto. Por outro lado, um campo estático pertence à própria classe e é compartilhado entre todas as instâncias dessa classe. Você pode acessar o campo estático apenas usando o nome da classe. Se você acessar o campo estático por um nome de instância, você terá erro de tempo de compilação [cS0176.](../../misc/cs0176.md)

Em geral, você só deve usar campos para variáveis que têm acessibilidade particular ou protegida. Os dados que sua classe expõe ao código do cliente devem ser fornecidos através de [métodos,](./methods.md) [propriedades](./properties.md)e [indexadores.](../indexers/index.md) Usando esses constructos para acesso indireto aos campos internos, você pode proteger contra valores de entrada inválidos. Um campo particular que armazena os dados expostos por uma propriedade pública é chamado de *repositório de backup* ou de *campo de suporte*.

Os campos normalmente armazenam os dados que devem estar acessíveis a mais de um método de classe e devem ser armazenados por mais tempo que o tempo de vida de qualquer método único. Por exemplo, uma classe que representa uma data do calendário pode ter três campos de inteiros: um para o mês, um para o dia e outro para o ano. As variáveis que não são usadas fora do escopo de um método único devem ser declaradas como *variáveis locais* dentro do próprio corpo do método.

Os campos são declarados no bloco de classe, especificando o nível de acesso do campo, seguido pelo tipo do campo e pelo nome do campo. Por exemplo: 

[!code-csharp[csProgGuideObjects#61](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#61)]

Para acessar um campo em um objeto, adicione um ponto após o nome do objeto, seguido pelo nome do campo, como em `objectname.fieldname`. Por exemplo: 

[!code-csharp[csProgGuideObjects#62](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#62)]

Um campo pode receber um valor inicial, usando o operador de atribuição quando o campo é declarado. Para atribuir automaticamente o campo `day` ao `"Monday"`, por exemplo, você poderia declarar `day` como no exemplo a seguir:

[!code-csharp[csProgGuideObjects#63](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#63)]

Os campos são inicializados imediatamente antes do construtor para a instância do objeto ser chamado. Se o construtor atribuir o valor de um campo, ele substituirá qualquer valor fornecido durante a declaração do campo. Para obter mais informações, veja [Usando construtores](./using-constructors.md).

> [!NOTE]
> Um inicializador de campo não pode fazer referência a outros campos de instância.

Os campos podem ser marcados como [públicos,](../../language-reference/keywords/public.md) [privados,](../../language-reference/keywords/private.md) [protegidos,](../../language-reference/keywords/protected.md) [internos,](../../language-reference/keywords/internal.md) [internos](../../language-reference/keywords/protected-internal.md)protegidos ou [protegidos privados.](../../language-reference/keywords/private-protected.md) Esses modificadores de acesso definem como os usuários da classe podem acessar os campos. Para obter mais informações, consulte [Modificadores de Acesso](./access-modifiers.md).

Opcionalmente, um campo pode ser declarado [static](../../language-reference/keywords/static.md). Isso torna o campo disponível para chamadores a qualquer momento, mesmo se não existir nenhuma instância da classe. Para obter mais informações, consulte [Classes Estáticas e Membros de Classe Estática](./static-classes-and-static-class-members.md).

Um campo pode ser declarado [readonly](../../language-reference/keywords/readonly.md). Um valor só pode ser atribuído a um campo somente leitura durante a inicialização ou em um construtor. Um campo `static readonly` é muito semelhante a uma constante, exceto que o compilador C# não tem acesso ao valor de um campo somente leitura estático em tempo de compilação, mas somente em tempo de execução. Para obter mais informações, consulte [Constantes](./constants.md).

## <a name="c-language-specification"></a>especificação da linguagem C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Confira também

- [C# Guia de Programação](../index.md)
- [Classes e structs](./index.md)
- [Usando construtores](./using-constructors.md)
- [Herança](./inheritance.md)
- [Modificadores de acesso](./access-modifiers.md)
- [Classes e membros de classes abstratas e lacradas](./abstract-and-sealed-classes-and-class-members.md)
