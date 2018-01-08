---
title: "Pacote de distribuição do .NET Core"
description: "Aprenda a empacotar, nomear e controlar a versão do .NET Core para distribuição."
keywords: .NET, .NET core, fonte, build
author: bleroy
ms.author: mairaw
ms.date: 06/28/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 71b9d722-c5a8-4271-9ce1-d87e7ae2494d
ms.workload: dotnetcore
ms.openlocfilehash: 9f5cd2f7c4fec553dfdfaf1765663b6896b3061d
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="net-core-distribution-packaging"></a>Pacote de distribuição do .NET Core

À medida que o .NET Core fica disponível em mais plataformas, é muito útil saber como empacotar, nomear e controlar a versão dele. Dessa forma, os mantenedores do pacote podem ajudar a garantir uma experiência consistente, independentemente de onde os usuários escolhem executar o .NET.

## <a name="net-core-components"></a>Componentes do .NET Core

O .NET Core é composto por três partes principais que precisam ser empacotadas:

1. **O host** (também conhecido como o "muxer") tem duas funções distintas: ativar um tempo de execução para iniciar um aplicativo e ativar um SDK para enviar comandos a ele. O host é um executável nativo (`dotnet.exe`) e suas bibliotecas de política de suporte (instalados em `host/fxr`). Ele é compilado do código no repositório [`dotnet/core-setup`](https://github.com/dotnet/core-setup/). Normalmente, há apenas um host em um computador específico, embora isso não seja um requisito restrito.
2. **A estrutura** é composta por um tempo de execução e por bibliotecas gerenciadas de suporte. A estrutura pode ser instalada como parte de um aplicativo, ou como uma estrutura compartilhada em um local central que pode ser reutilizado por vários aplicativos. Pode haver qualquer quantidade de estruturas compartilhadas instaladas em um determinado computador. Estruturas compartilhadas ativas em `shared/Microsoft.NETCore.App/<version>`. O host efetua o roll forward em versões do patch. Se um aplicativo é direcionado ao `Microsoft.NETCore.App` 1.0.0, e somente o 1.0.4 estiver presente, o aplicativo será iniciado no 1.0.4.
3. **O SDK** (também conhecido como "as ferramentas") é um conjunto de ferramentas gerenciadas que pode ser usado para escrever e compilar bibliotecas e aplicativos do .NET Core. O SDK inclui a CLI, MSBuild e tarefas de compilação e direcionamentos associados, o NuGet, novos modelos de projeto etc. É possível ter vários SDKs em um computador (por exemplo, para compilar projetos que exigem explicitamente uma versão mais antiga), mas a recomendação é usar as ferramentas mais recente.

## <a name="recommended-package-names"></a>Nomes de pacote recomendados

As diretrizes a seguir são nossa recomendação para nomes de pacote. O mantenedor do pacote poderá divergir delas por vários motivos, por exemplo, uma tradição diferente da distribuição específica direcionada.

### <a name="minimum-package-set"></a>Conjunto mínimo de pacote

* `dotnet-runtime-[major].[minor]`: uma estrutura compartilhada com a versão especificada (apenas a versão de patch mais recente para uma determinada combinação de principal+secundário deve estar disponível no gerenciador de pacote). **dependências**: `dotnet-host`
* `dotnet-sdk`: o SDK mais recente. **dependências**: o `dotnet-sdk-[major].[minor]` mais recente.
* `dotnet-sdk-[major].[minor]`: o SDK com a versão especificada. A versão especificada é a versão mais recente incluída das estruturas compartilhadas incluídas, para que os usuários possam relacionar facilmente um SDK a uma estrutura compartilhada. **dependências**: `dotnet-host`, um ou mais `dotnet-runtime-[major].[minor]` (um dos tempos de execução é usado pelo próprio código do SDK, os outros servem para compilação e execução dos usuários).
* `dotnet-host`: o host mais recente.

#### <a name="preview-versions"></a>Versões prévias

Os mantenedores do pacote podem decidir incluem as versões prévias da estrutura compartilhada e do SDK. Eles nunca devem ser incluídos no pacote do `dotnet-sdk` sem controle de versão, mas podem ser lançados como pacotes com controle de versão com um marcador de prévia adicional anexado às seções de versão principal e secundária do nome. Por exemplo, pode haver um pacote `dotnet-sdk-2.0-preview-final`.

### <a name="optional-additional-packages"></a>Pacotes adicionais opcionais

Alguns mantenedores podem optar por fornecer pacotes adicionais, como:

* `dotnet-lts`: a versão mais recente de LTS (Suporte de longo prazo) da estrutura compartilhada. [As séries da Versão Atual e de LTS](~/docs/core/versions/lts-current.md) correspondem a cadências diferentes de lançamento do .NET Core. Os usuários têm a opção de adotar uma ou a outra, com base na frequência com que estão dispostos a atualizar. Este é um conceito que também está ligado aos níveis de suporte, portanto pode ou não fazer sentido dependendo da distribuição que está sendo considerada.

## <a name="disk-layout"></a>Layout de disco

Ao instalar os pacotes do .NET Core, o posicionamento relativo dos destinos de direcionamento no disco é importante.
O host `dotnet.exe` deve ser colocado ao lado das pastas `sdk` e `shared` que contêm o conteúdo com controle de versão dos pacotes do SDK `dotnet-sdk`, e os pacotes da estrutura compartilhada `dotnet-runtime`.

O layout de disco de arquivos e diretórios dentro dos pacotes tem controle de versão. Isso significa que a atualização para a versão mais recente de `dotnet-runtime` instala a nova versão lado a lado com as versões anteriores, reduzindo a possibilidade de interrupção dos aplicativos existentes ao atualizar o pacote. As atualizações de pacote não devem remover as versões anteriores.

## <a name="update-policies"></a>Políticas de atualização

Quando um `update` é executado, o comportamento de cada pacote ocorre da seguinte forma:

* `dotnet-runtime-[major].[minor]`: as novas versões de patch atualizam o pacote, mas novas versões principais ou secundárias são pacotes separados.
* `dotnet-sdk`: `update` efetua o roll forward das versões principal, secundária e de patch.
* `dotnet-sdk-[major].[minor]`: as novas versões de patch atualizam o pacote, mas novas versões principais ou secundárias são pacotes separados.
* `dotnet-lts`: `update` efetua o roll forward das versões principal, secundária e de patch.

Este tópico apresentou nossas recomendações para empacotar o .NET Core. No entanto, cada distribuição é livre para escolher quais versões oferecer e quando. Por exemplo, uma distribuição que valoriza mais a estabilidade do que a atualização pode optar por lançar somente versões que se ajustam à versão de treinamento do LTS.