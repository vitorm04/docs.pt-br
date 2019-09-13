---
title: Investigação padrão-.NET Core
description: Visão geral da lógica de <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> investigação do .NET Core para localizar dependências.
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: 2fa8a13bcb08a767fa965621f95bec8619aea5cc
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926404"
---
# <a name="default-probing"></a>Investigação padrão

A <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> instância é responsável por localizar as dependências de um assembly. Este artigo descreve a <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> lógica de investigação da instância.

## <a name="host-configured-probing-properties"></a>Propriedades de investigação configuradas pelo host

Quando o tempo de execução é iniciado, o host de tempo de execução fornece um conjunto de propriedades <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> de investigação nomeadas que configuram caminhos de investigação.

Cada propriedade de investigação é opcional.  Se houver, cada propriedade será um valor de cadeia de caracteres que contém uma lista delimitada de caminhos absolutos. O delimitador é '; ' no Windows e ': ' em todas as outras plataformas.

|Nome da Propriedade                 |Descrição  |
|------------------------------|---------|
|`TRUSTED_PLATFORM_ASSEMBLIES`   | Lista de caminhos de arquivo de assembly de aplicativo e plataforma. |
|`PLATFORM_RESOURCE_ROOTS`       | Lista de caminhos de diretório para pesquisar por assemblies de recurso satélite. |
|`NATIVE_DLL_SEARCH_DIRECTORIES` | Lista de caminhos de diretório para pesquisar bibliotecas não gerenciadas (nativas).        |
|`APP_PATHS`                     | Lista de caminhos de diretório para pesquisar assemblies gerenciados |
|`APP_NI_PATHS`                  | Lista de caminhos de diretório para pesquisar imagens nativas de assemblies gerenciados. |

### <a name="how-are-the-properties-populated"></a>Como as propriedades são populadas?

Há dois cenários principais para popular as propriedades dependendo se o `<myapp>.deps.json` arquivo existe.

- Quando o `*.deps.json` arquivo estiver presente, ele será analisado para preencher as propriedades de investigação.
- Quando o `*.deps.json` arquivo não está presente, supõe-se que o diretório do aplicativo contenha todas as dependências. O conteúdo do diretório é usado para preencher as propriedades de investigação.

Além disso, `*.deps.json` os arquivos para todas as estruturas referenciadas são analisados de forma semelhante.

Por fim, a `ADDITIONAL_DEPS` variável de ambiente pode ser usada para adicionar outras dependências.

### <a name="how-do-i-see-the-probing-properties-from-managed-code"></a>Como fazer ver as propriedades de investigação do código gerenciado?

Cada propriedade está disponível chamando a <xref:System.AppContext.GetData(System.String)?displayProperty=nameWithType> função com o nome da propriedade da tabela acima.

### <a name="how-do-i-debug-the-probing-properties-construction"></a>Como fazer depurar a construção das propriedades de investigação?

O host de tempo de execução do .NET Core produzirá mensagens de rastreamento úteis quando determinadas variáveis de ambiente estiverem habilitadas:

|Variável de ambiente        |Descrição  |
|----------------------------|---------|
|`COREHOST_TRACE=1`          |Habilita o rastreamento.|
|`COREHOST_TRACEFILE=<path>` |Rastreia um caminho de arquivo em vez do padrão `stderr`.|
|`COREHOST_TRACE_VERBOSITY`  |Define o detalhamento de 1 (menor) para 4 (mais alto).|

## <a name="managed-assembly-default-probing"></a>Investigação padrão do assembly gerenciado

Ao investigar para localizar um assembly gerenciado, o <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> procura na ordem em:

- Arquivos que correspondem <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> ao `TRUSTED_PLATFORM_ASSEMBLIES` (após a remoção de extensões de arquivo).
- Arquivos de assembly de imagem `APP_NI_PATHS` nativa no com extensões de arquivo comuns.
- Arquivos de assembly `APP_PATHS` no com extensões de arquivo comuns.

## <a name="satellite-resource-assembly-probing"></a>Investigação de assembly satélite (recurso)

Para localizar um assembly satélite para uma cultura específica, construa um conjunto de caminhos de arquivo.

Para cada caminho no `PLATFORM_RESOURCE_ROOTS` e, `APP_PATHS`em seguida, <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> acrescente a cadeia de caracteres, um <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> separador de diretório, a cadeia de caracteres e a extensão '. dll '.

Se existir algum arquivo correspondente, tente carregá-lo e retorná-lo.

## <a name="unmanaged-native-library-probing"></a>Investigação de biblioteca não gerenciada (nativa)

Ao investigar para localizar uma biblioteca não gerenciada, o `NATIVE_DLL_SEARCH_DIRECTORIES` é pesquisado procurando por uma biblioteca correspondente,
