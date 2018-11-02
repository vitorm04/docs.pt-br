---
title: Introdução à criação de bibliotecas do .NET de alta qualidade
description: Introdução à criação de bibliotecas do .NET.
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: 6377e3fe606bf7603b418decdd0e3f9d2de6a510
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50201237"
---
# <a name="get-started"></a>Introdução

## <a name="cross-platform-targetingcross-platform-targetingmd"></a>[Direcionamento de plataforma cruzada](./cross-platform-targeting.md)

Como usar o .NET Standard e multiplataforma para criar bibliotecas de multiplataforma. O .NET é executado em muitos locais e boas bibliotecas do .NET devem buscar dar suporte a tantas plataformas e desenvolvedores quanto possível.

## <a name="strong-namingstrong-namingmd"></a>[Nomenclatura forte](./strong-naming.md)

Saiba mais sobre o nome forte e suas vantagens e desvantagens. Dar um nome forte a uma biblioteca .NET permite que a maioria dos desenvolvedores use-a e é uma prática recomendada.

## <a name="nuget-and-open-source-librariesnugetmd"></a>[Bibliotecas do NuGet e de software livre](./nuget.md)

A melhor maneira de criar pacotes do NuGet para bibliotecas do .NET de código-fonte aberto, incluindo metadados recomendados para todos os pacotes publicamente publicados em NuGet.org.

### <a name="dependenciesdependenciesmd"></a>[Dependências](./dependencies.md)

O NuGet torna fácil usar pacotes existentes ao criar uma biblioteca do .NET. Saiba mais sobre as origens comuns de atrito de dependências do NuGet e como evitá-las.

### <a name="sourcelinksourcelinkmd"></a>[SourceLink](./sourcelink.md)

O SourceLink é uma ótima ferramenta que permite que os usuários da sua biblioteca do .NET intervir em seu código-fonte durante a depuração. Este artigo é uma visão geral do que é SourceLink e por que você deve usá-lo.

### <a name="publishingpublish-nuget-packagemd"></a>[Publicação](./publish-nuget-package.md)

Embora o NuGet.org seja o repositório mais amplamente conhecido e usado, há muitos locais para publicar pacotes do NuGet. Saiba mais sobre os diferentes repositórios de pacote do NuGet disponíveis e práticas recomendadas de segurança para a publicação de uma biblioteca do .NET.

## <a name="versioningversioningmd"></a>[Controle de versão](./versioning.md)

Boas bibliotecas do .NET evoluem ao longo do tempo, adicionando recursos, corrigindo bugs e melhorando o desempenho em versões posteriores. Saiba mais sobre os vários números de versão e como comunicar alterações significativas para os desenvolvedores.

### <a name="breaking-changesbreaking-changesmd"></a>[Alterações significativas](./breaking-changes.md)

É importante que uma biblioteca .NET encontre um equilíbrio entre a estabilidade para usuários existentes e a inovação para o futuro. Saiba mais sobre os diferentes tipos de alterações da falha e estratégias para adição de novos recursos, ao mesmo tempo mantendo a compatibilidade com versões anteriores.

>[!div class="step-by-step"]
[Anterior](./index.md)
[Próximo](./cross-platform-targeting.md)
