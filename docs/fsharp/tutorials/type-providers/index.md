---
title: Provedores de tipos
description: 'Saiba como um provedor de tipos F # é um componente que fornece tipos, propriedades e métodos para uso em seus programas.'
author: cartermp
ms.author: phcart
ms.date: 04/02/2018
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 5b7bae6f960b9cfa91188e8eb80be949cda12b65
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="type-providers"></a>Provedores de tipos

Um provedor de tipos F# é um componente que fornece tipos, propriedades e métodos para uso em seu programa. Provedores de tipos geram o que é conhecido como **tipos fornecidos**, que é gerado pelo compilador F # e é baseado em uma fonte de dados externa.

Por exemplo, um provedor de tipos F # para o SQL pode gerar tipos que representam a tabelas e colunas em um banco de dados relacional. Na verdade, isso é o que o [SQLProvider](https://fsprojects.github.io/SQLProvider/) tipo de provedor não.

Fornecido que tipos dependem de parâmetros de entrada para um provedor de tipos. Essa entrada pode ser uma fonte de dados de exemplo (como um arquivo de esquema JSON), uma URL que aponta diretamente para um serviço externo ou uma cadeia de caracteres de conexão para uma fonte de dados. Um provedor de tipo também pode garantir que os grupos de tipos de somente são expandidos sob demanda; ou seja, eles são expandidos se os tipos, na verdade, são referenciados pelo seu programa. Isso permite a integração direta e sob demanda de espaços de informações em grande escala como mercados de dados online de uma forma fortemente tipada.

## <a name="generative-and-erased-type-providers"></a>Provedores de tipos produtivas e apagados

Provedores de tipos têm duas formas: produtivas e apagados.

Provedores de tipos produtivas produzir tipos que podem ser gravados como tipos do .NET para o assembly no qual eles são produzidos. Isso permite que eles sejam consumidos do código em outros assemblies. Isso significa que a representação de tipo da fonte de dados geralmente deve ser um que seja viável para representar com tipos .NET.

Apagar provedores de tipos produzir tipos que só podem ser consumidos no assembly ou são gerados a partir do projeto. Os tipos são efêmeros; ou seja, eles não são gravados em um assembly e não podem ser consumidos pelo código em outros assemblies. Eles podem conter *atrasada* membros, permitindo que os tipos de uso fornecido de um espaço de informações potencialmente infinito. Eles são úteis para o uso de um pequeno subconjunto de uma fonte de dados grandes e interconectadas.

## <a name="commonly-used-type-providers"></a>Provedores de tipos usados com frequência

As seguintes bibliotecas amplamente usada contêm provedores de tipos para usos diferentes:

- [FSharp.Data](https://fsharp.github.io/FSharp.Data/) inclui provedores de tipos para HTML, XML, CSV e JSON de documento formatos e recursos.
- [SQLProvider](https://fsprojects.github.io/SQLProvider/) fornece acesso fortemente tipado para bancos de dados de relação por meio do mapeamento de objeto e F # LINQ consultas em relação a essas fontes de dados.
- [FSharp.Data.SqlClient](https://fsprojects.github.io/FSharp.Data.SqlClient/) tem um conjunto de provedores de tipo de tempo de compilação verificada incorporação de T-SQL em F #.
- [O provedor de tipo de armazenamento do Azure](https://fsprojects.github.io/AzureStorageTypeProvider/) fornece tipos para Blobs do Azure, tabelas e filas, permitindo que você acesse esses recursos sem a necessidade de especificar nomes de recursos como cadeias de caracteres em todo o programa.
- [FSharp.Data.GraphQL](https://fsprojects.github.io/FSharp.Data.GraphQL/index.html) contém o **GraphQLProvider**, que fornece tipos com base em um servidor GraphQL especificado pela URL.

Quando necessário, você pode [criar seus próprios provedores de tipo personalizado](creating-a-type-provider.md), ou fazer referência a provedores de tipos que foram criados por outros usuários. Por exemplo, suponha que sua organização tenha um serviço de dados que forneça um grande e crescente número de conjuntos de dados nomeados, cada um com seu próprio esquema de dados estáveis. Você pode optar por criar um provedor de tipos que leia os esquemas e apresente os conjuntos de dados mais recentes disponíveis para o programador de uma forma fortemente tipada.

## <a name="see-also"></a>Consulte também
[Tutorial: Criar um provedor de tipos](creating-a-type-provider.md)

[Referência da Linguagem F#](../../language-reference/index.md)

[Visual F#](../../index.md)
