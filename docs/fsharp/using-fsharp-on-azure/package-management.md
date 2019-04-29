---
title: Usando o gerenciamento de pacotes com F# para o Azure
description: Usar Paket ou Nuget para gerenciar F# dependências do Azure
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: fd9c4a15ab0741d44d6d5cf909b7219d310affb0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61756527"
---
# <a name="package-management-for-f-azure-dependencies"></a>Pacote de gerenciamento para Dependências F# do Azure

Obter pacotes para desenvolvimento do Azure é fácil quando você usa um Gerenciador de pacotes. As duas opções são [Paket](https://fsprojects.github.io/Paket/) e [NuGet](https://www.nuget.org/).

## <a name="using-paket"></a>Usando Paket

Se você estiver usando [Paket](https://fsprojects.github.io/Paket/) como o Gerenciador de dependência, você pode usar o `paket.exe` ferramenta para adicionar dependências do Azure. Por exemplo:

    > paket add nuget WindowsAzure.Storage

Ou, se você estiver usando [Mono](https://www.mono-project.com/) para desenvolvimento de plataforma cruzada do .NET:

    > mono paket.exe add nuget WindowsAzure.Storage

Isso adicionará `WindowsAzure.Storage` ao seu conjunto de dependências do pacote para o projeto no diretório atual, modifique o `paket.dependencies` de arquivo e baixe o pacote. Se você tiver configurado anteriormente dependências ou trabalhando com um projeto em que as dependências foram configuradas por outro desenvolvedor, você pode resolver e instalar dependências localmente como este:

    > paket install

Ou, para desenvolvimento Mono:

    > mono paket.exe install

Você pode atualizar todas as suas dependências de pacote para a versão mais recente, como este:

    > paket update

Ou, para desenvolvimento Mono:

    > mono paket.exe update

## <a name="using-nuget"></a>Usando o Nuget

Se você estiver usando [NuGet](https://www.nuget.org/) como o Gerenciador de dependência, você pode usar o `nuget.exe` ferramenta para adicionar dependências do Azure. Por exemplo:

    > nuget install WindowsAzure.Storage -ExcludeVersion

Ou, para desenvolvimento Mono:

    > mono nuget.exe install WindowsAzure.Storage -ExcludeVersion

Isso adicionará `WindowsAzure.Storage` ao seu conjunto de dependências do pacote para o projeto no diretório atual e o pacote de download. Se você tiver configurado anteriormente dependências ou trabalhando com um projeto em que as dependências foram configuradas por outro desenvolvedor, você pode resolver e instalar dependências localmente como este:

    > nuget restore 

Ou, para desenvolvimento Mono:

    > mono nuget.exe restore

Você pode atualizar todas as suas dependências de pacote para a versão mais recente, como este:

    > nuget update

Ou, para desenvolvimento Mono:

    > mono nuget.exe update

## <a name="referencing-assemblies"></a>Fazendo Referência a Assemblies

Para usar os pacotes em seu F# script, você precisa fazer referência os assemblies incluídos nos pacotes usando uma `#r` diretiva. Por exemplo:

    > #r "packages/WindowsAzure.Storage/lib/net40/Microsoft.WindowsAzure.Storage.dll"

Como você pode ver, você precisará especificar o caminho relativo para a DLL e o nome completo de DLL, que pode não ser exatamente o mesmo que o nome do pacote. O caminho inclui uma versão do framework e, possivelmente, um número de versão do pacote. Para localizar todos os assemblies instalados, você pode usar algo parecido com isso em uma linha de comando do Windows:

    > cd packages/WindowsAzure.Storage
    > dir /s/b *.dll

Ou em um shell do Unix, algo parecido com isto:

    > find packages/WindowsAzure.Storage -name "*.dll"

Isso lhe dará os caminhos para os assemblies instalados. A partir daí, você pode selecionar o caminho correto para a sua versão do framework.
