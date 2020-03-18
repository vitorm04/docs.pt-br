---
title: Sondagem padrão - .NET Core
description: Visão geral do Sistema.Runtime.Loader.AssemblyLoadContext.Default do .NET Core para localizar dependências.
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: 500ee6ee863b1f311970a9e718936f57f7d4efd6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399087"
---
# <a name="default-probing"></a>Sondagem padrão

A <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> instância é responsável por localizar as dependências de um conjunto. Este artigo descreve <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> a lógica de sondagem da instância.

## <a name="host-configured-probing-properties"></a>Propriedades de sondagem configuradas pelo host

Quando o tempo de execução é iniciado, o host de <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> tempo de execução fornece um conjunto de propriedades de sondagem nomeadas que configuram os caminhos do teste.

Cada propriedade de sondagem é opcional. Se presente, cada propriedade é um valor de string que contém uma lista delimitada de caminhos absolutos. O delimitador é ';' no Windows e ':' em todas as outras plataformas.

|Nome da propriedade                 |Descrição  |
|------------------------------|---------|
|`TRUSTED_PLATFORM_ASSEMBLIES`   | Lista de caminhos de arquivos de montagem de plataformas e aplicativos. |
|`PLATFORM_RESOURCE_ROOTS`       | Lista de caminhos de diretório para procurar por conjuntos de recursos de satélite. |
|`NATIVE_DLL_SEARCH_DIRECTORIES` | Lista de caminhos de diretório para procurar bibliotecas não gerenciadas (nativas).        |
|`APP_PATHS`                     | Lista de caminhos de diretório para procurar montagens gerenciadas. |
|`APP_NI_PATHS`                  | Lista de caminhos de diretório para procurar imagens nativas de conjuntos gerenciados. |

### <a name="how-are-the-properties-populated"></a>Como as propriedades são preenchidas?

Existem dois cenários principais para povoar as propriedades, dependendo se o * \<arquivo myapp>.deps.json* existe.

- Quando o * \*arquivo .deps.json* está presente, ele é analisado para preencher as propriedades de sondagem.
- Quando o * \*arquivo .deps.json* não está presente, o diretório do aplicativo é assumido para conter todas as dependências. O conteúdo do diretório é usado para preencher as propriedades de sondagem.

Além disso, os * \*arquivos .deps.json* para quaisquer frameworks referenciados são analisados da mesma forma.

Finalmente, a `ADDITIONAL_DEPS` variável ambiente pode ser usada para adicionar dependências adicionais.

### <a name="how-do-i-see-the-probing-properties-from-managed-code"></a>Como vejo as propriedades de sondagem do código gerenciado?

Cada propriedade está disponível ligando para a <xref:System.AppContext.GetData(System.String)?displayProperty=nameWithType> função com o nome da propriedade na tabela acima.

### <a name="how-do-i-debug-the-probing-properties-construction"></a>Como depurar a construção das propriedades de sondagem?

O host de tempo de execução .NET Core produzirá mensagens de rastreamento úteis quando determinadas variáveis de ambiente estiverem habilitadas:

|Variável de ambiente        |Descrição  |
|----------------------------|---------|
|`COREHOST_TRACE=1`          |Permite o rastreamento.|
|`COREHOST_TRACEFILE=<path>` |Traça para um caminho de `stderr`arquivo em vez do padrão .|
|`COREHOST_TRACE_VERBOSITY`  |Define a verbosidade de 1 (mais baixo) para 4 (mais alto).|

## <a name="managed-assembly-default-probing"></a>Sondagem padrão de montagem gerenciada

Ao sondar para localizar um <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> conjunto gerenciado, os olhares em ordem:

- Arquivos correspondentes a <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> in `TRUSTED_PLATFORM_ASSEMBLIES` (após a remoção de extensões de arquivo).
- Arquivos nativos de `APP_NI_PATHS` montagem de imagens com extensões de arquivo comuns.
- Arquivos de `APP_PATHS` montagem com extensões de arquivo comuns.

## <a name="satellite-resource-assembly-probing"></a>Sondagem de montagem de satélite (recurso)

Para encontrar um conjunto de satélites para uma cultura específica, construa um conjunto de caminhos de arquivos.

Para cada `PLATFORM_RESOURCE_ROOTS` caminho `APP_PATHS`dentro e <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> depois, anexar a seqüência, um separador de diretório, a <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> seqüência e a extensão '.dll'.

Se houver algum arquivo correspondente, tente carregá-lo e devolvê-lo.

## <a name="unmanaged-native-library-probing"></a>Sondagem de biblioteca não gerenciada (nativa)

Ao pesquisar para localizar uma biblioteca `NATIVE_DLL_SEARCH_DIRECTORIES` não gerenciada, os são pesquisados à procura de uma biblioteca correspondente.
