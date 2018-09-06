---
title: Provedores de tipos
description: 'Saiba como um provedor de tipos F # é um componente que fornece tipos, propriedades e métodos para uso em seus programas.'
ms.date: 04/02/2018
ms.openlocfilehash: 5fa9de229caa2ec3ba4a248ca5cd1c8aa5adb230
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43891662"
---
# <a name="type-providers"></a>Provedores de tipos

Um provedor de tipos F# é um componente que fornece tipos, propriedades e métodos para uso em seu programa. Provedores de tipos geram o que é conhecido como **fornecidos tipos**, que é gerado pelo compilador do F # e baseiam-se em uma fonte de dados externa.

Por exemplo, um provedor de tipos F # para o SQL pode gerar tipos que representam tabelas e colunas em um banco de dados relacional. Na verdade, isso é o que o [SQLProvider](https://fsprojects.github.io/SQLProvider/) tipo de provedor não.

Fornecidos que tipos dependem de parâmetros de entrada para um provedor de tipo. Essa entrada pode ser uma fonte de dados de exemplo (como um arquivo de esquema JSON), uma URL que aponta diretamente para um serviço externo ou uma cadeia de caracteres de conexão a uma fonte de dados. Um provedor de tipos também pode garantir que grupos de tipos sejam expandidos sob demanda; ou seja, eles serão expandidos se os tipos forem realmente referenciados pelo seu programa. Isso permite a integração direta e sob demanda de espaços de informações em grande escala como mercados de dados online de uma forma fortemente tipada.

## <a name="generative-and-erased-type-providers"></a>Provedores de tipos produtivas e apagado

Provedores de tipos têm duas formas: apagados e produtivas.

Provedores de tipos produtivas produzir tipos que podem ser gravados como tipos do .NET no assembly no qual eles são produzidos. Isso permite que eles para serem consumidos pelo código em outros assemblies. Isso significa que a representação de tipo da fonte de dados geralmente deve ser um que seja viável para representar com tipos .NET.

Apagar provedores de tipos produzir tipos que só podem ser consumidos no assembly ou eles são gerados a partir do projeto. Os tipos são efêmeros; ou seja, eles não são gravados em um assembly e não podem ser consumidos pelo código em outros assemblies. Eles podem conter *atrasada* membros, permitindo que os tipos de uso fornecido de um espaço de informações potencialmente infinito. Eles são úteis para o uso de um pequeno subconjunto de uma fonte de dados grandes e interconectadas.

## <a name="commonly-used-type-providers"></a>Usadas em provedores de tipos

As seguintes bibliotecas usadas contêm provedores de tipos para usos distintos:

- [FSharp](https://fsharp.github.io/FSharp.Data/) inclui provedores de tipos para HTML, XML, CSV e JSON documento formatos e recursos.
- [SQLProvider](https://fsprojects.github.io/SQLProvider/) fornece acesso fortemente tipado para bancos de dados de relação por meio do mapeamento de objeto e F # LINQ consultas em relação a essas fontes de dados.
- [FSharp.Data.SqlClient](https://fsprojects.github.io/FSharp.Data.SqlClient/) tem um conjunto de provedores de tipo para o tempo de compilação verificada incorporação do T-SQL em F #.
- [O provedor de tipo de armazenamento do Azure](https://fsprojects.github.io/AzureStorageTypeProvider/) fornece tipos para Blobs do Azure, tabelas e filas, permitindo que você acesse esses recursos sem a necessidade de especificar nomes de recursos, como cadeias de caracteres em todo o seu programa.
- [FSharp.Data.GraphQL](https://fsprojects.github.io/FSharp.Data.GraphQL/index.html) contém o **GraphQLProvider**, que fornece tipos com base em um servidor GraphQL especificado pela URL.

Quando for necessário, você pode [criar seus próprios provedores de tipo personalizado](creating-a-type-provider.md), ou referenciar provedores de tipos que foram criados por outras pessoas. Por exemplo, suponha que sua organização tenha um serviço de dados que forneça um grande e crescente número de conjuntos de dados nomeados, cada um com seu próprio esquema de dados estáveis. Você pode optar por criar um provedor de tipos que leia os esquemas e apresente os conjuntos de dados mais recentes disponíveis para o programador de uma forma fortemente tipada.

## <a name="see-also"></a>Consulte também

- [Tutorial: Criar um provedor de tipo](creating-a-type-provider.md)
- [Referência da Linguagem F#](../../language-reference/index.md)
- [Visual F#](../../index.md)
