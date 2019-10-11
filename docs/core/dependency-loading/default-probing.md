---
title: Investigação padrão-.NET Core
description: Visão geral da lógica de investigação System. Runtime. Loader. AssemblyLoadContext. padrão do .NET Core para localizar dependências.
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: 500ee6ee863b1f311970a9e718936f57f7d4efd6
ms.sourcegitcommit: 10db6551ea3c971470cf5d2cc21ba1cbcefe5c55
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/08/2019
ms.locfileid: "72031832"
---
# <a name="default-probing"></a>Investigação padrão

A instância <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> é responsável por localizar as dependências de um assembly. Este artigo descreve a lógica de investigação da instância do @no__t 0.

## <a name="host-configured-probing-properties"></a>Propriedades de investigação configuradas pelo host

Quando o tempo de execução é iniciado, o host de tempo de execução fornece um conjunto de propriedades de investigação nomeadas que configuram caminhos de investigação <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType>.

Cada propriedade de investigação é opcional. Se houver, cada propriedade será um valor de cadeia de caracteres que contém uma lista delimitada de caminhos absolutos. O delimitador é '; ' no Windows e ': ' em todas as outras plataformas.

|Nome da Propriedade                 |Descrição  |
|------------------------------|---------|
|`TRUSTED_PLATFORM_ASSEMBLIES`   | Lista de caminhos de arquivo de assembly de aplicativo e plataforma. |
|`PLATFORM_RESOURCE_ROOTS`       | Lista de caminhos de diretório para pesquisar por assemblies de recurso satélite. |
|`NATIVE_DLL_SEARCH_DIRECTORIES` | Lista de caminhos de diretório para pesquisar bibliotecas não gerenciadas (nativas).        |
|`APP_PATHS`                     | Lista de caminhos de diretório para pesquisar assemblies gerenciados. |
|`APP_NI_PATHS`                  | Lista de caminhos de diretório para pesquisar imagens nativas de assemblies gerenciados. |

### <a name="how-are-the-properties-populated"></a>Como as propriedades são populadas?

Há dois cenários principais para popular as propriedades dependendo se o arquivo *\<myapp >. deps. JSON* existe.

- Quando o arquivo de *\*. deps. JSON* estiver presente, ele será analisado para preencher as propriedades de investigação.
- Quando o arquivo *\*. deps. JSON* não está presente, supõe-se que o diretório do aplicativo contenha todas as dependências. O conteúdo do diretório é usado para preencher as propriedades de investigação.

Além disso, os arquivos *\*. deps. JSON* para todas as estruturas referenciadas são analisados de forma semelhante.

Por fim, a variável de ambiente `ADDITIONAL_DEPS` pode ser usada para adicionar outras dependências.

### <a name="how-do-i-see-the-probing-properties-from-managed-code"></a>Como fazer ver as propriedades de investigação do código gerenciado?

Cada propriedade está disponível chamando a função <xref:System.AppContext.GetData(System.String)?displayProperty=nameWithType> com o nome da propriedade da tabela acima.

### <a name="how-do-i-debug-the-probing-properties-construction"></a>Como fazer depurar a construção das propriedades de investigação?

O host de tempo de execução do .NET Core produzirá mensagens de rastreamento úteis quando determinadas variáveis de ambiente estiverem habilitadas:

|Variável de ambiente        |Descrição  |
|----------------------------|---------|
|`COREHOST_TRACE=1`          |Habilita o rastreamento.|
|`COREHOST_TRACEFILE=<path>` |Rastreia para um caminho de arquivo em vez do padrão `stderr`.|
|`COREHOST_TRACE_VERBOSITY`  |Define o detalhamento de 1 (menor) para 4 (mais alto).|

## <a name="managed-assembly-default-probing"></a>Investigação padrão do assembly gerenciado

Ao investigar para localizar um assembly gerenciado, o <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> procura na ordem em:

- Arquivos que correspondem ao <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> em `TRUSTED_PLATFORM_ASSEMBLIES` (após a remoção das extensões de arquivo).
- Arquivos de assembly de imagem nativa no `APP_NI_PATHS` com extensões de arquivo comuns.
- Arquivos de assembly em `APP_PATHS` com extensões de arquivo comuns.

## <a name="satellite-resource-assembly-probing"></a>Investigação de assembly satélite (recurso)

Para localizar um assembly satélite para uma cultura específica, construa um conjunto de caminhos de arquivo.

Para cada caminho em `PLATFORM_RESOURCE_ROOTS` e, em seguida, `APP_PATHS`, acrescente a cadeia de caracteres <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType>, um separador de diretório, a cadeia de caracteres <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> e a extensão '. dll '.

Se existir algum arquivo correspondente, tente carregá-lo e retorná-lo.

## <a name="unmanaged-native-library-probing"></a>Investigação de biblioteca não gerenciada (nativa)

Ao investigar para localizar uma biblioteca não gerenciada, o `NATIVE_DLL_SEARCH_DIRECTORIES` será pesquisado procurando por uma biblioteca correspondente.
