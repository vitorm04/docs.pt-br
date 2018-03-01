---
title: 'Usando o gerenciamento de pacotes com F # para o Azure'
description: "Use Paket ou Nuget para gerenciar as dependências de F # do Azure"
keywords: "o Visual f #, f #, funcional programação .NET, .NET Core, o Azure"
author: sylvanc
ms.author: phcart
ms.date: 09/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: dd32ef9c-5416-467e-9fa3-c9ee3bb08456
ms.openlocfilehash: d1a807053f5c4c45492f206739922aacdf6d4122
ms.sourcegitcommit: 655fd4f78741967f80c409cef98347fdcf77857d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2018
---
# <a name="package-management-for-f-azure-dependencies"></a>Pacote de gerenciamento para Dependências F# do Azure

Obter pacotes para o desenvolvimento do Azure é fácil quando você usa um Gerenciador de pacotes. As duas opções são [Paket](https://fsprojects.github.io/Paket/) e [NuGet](https://www.nuget.org/).

## <a name="using-paket"></a>Usando Paket

Se você estiver usando [Paket](https://fsprojects.github.io/Paket/) como seu gerente de dependência, você pode usar o `paket.exe` ferramenta para adicionar dependências do Azure. Por exemplo:

    > paket add nuget WindowsAzure.Storage

Ou, se você estiver usando [Mono](https://www.mono-project.com/) para desenvolvimento de plataforma cruzada do .NET:

    > mono paket.exe add nuget WindowsAzure.Storage

Isso adicionará `WindowsAzure.Storage` seu conjunto de dependências do pacote para o projeto no diretório atual, modifique o `paket.dependencies` de arquivo e baixar o pacote. Se você tiver configurado anteriormente dependências ou trabalha com um projeto em que as dependências foram definidas por outro desenvolvedor, você pode resolver e instalar dependências localmente como este:

    > paket install

Ou, para desenvolvimento Mono:

    > mono paket.exe install

Você pode atualizar todas as suas dependências de pacote para a versão mais recente assim:

    > paket update

Ou, para desenvolvimento Mono:

    > mono paket.exe update

## <a name="using-nuget"></a>Usando o Nuget

Se você estiver usando [NuGet](https://www.nuget.org/) como seu gerente de dependência, você pode usar o `nuget.exe` ferramenta para adicionar dependências do Azure. Por exemplo:

    > nuget install WindowsAzure.Storage -ExcludeVersion

Ou, para desenvolvimento Mono:

    > mono nuget.exe install WindowsAzure.Storage -ExcludeVersion

Isso adicionará `WindowsAzure.Storage` seu conjunto de dependências do pacote para o projeto no diretório atual e o pacote de download. Se você tiver configurado anteriormente dependências ou trabalha com um projeto em que as dependências foram definidas por outro desenvolvedor, você pode resolver e instalar dependências localmente como este:

    > nuget restore 

Ou, para desenvolvimento Mono:

    > mono nuget.exe restore

Você pode atualizar todas as suas dependências de pacote para a versão mais recente assim:

    > nuget update

Ou, para desenvolvimento Mono:

    > mono nuget.exe update

## <a name="referencing-assemblies"></a>Fazendo Referência a Assemblies

Para usar seus pacotes em seu script F #, você precisa referenciar os assemblies incluídos nos pacotes usando um `#r` diretiva. Por exemplo:

    > #r "packages/WindowsAzure.Storage/lib/net40/Microsoft.WindowsAzure.Storage.dll"

Como você pode ver, você precisará especificar o caminho relativo para a DLL e o nome completo de DLL, que pode não ser exatamente o mesmo que o nome do pacote. O caminho inclui uma versão do framework e, possivelmente, um número de versão do pacote. Para localizar todos os assemblies instalados, você pode usar algo como em uma linha de comando do Windows:

    > cd packages/WindowsAzure.Storage
    > dir /s/b *.dll

Ou, em um shell do Unix, algo parecido com:

    > find packages/WindowsAzure.Storage -name "*.dll"

Isso lhe dará os caminhos para os assemblies instalados. A partir daí, você pode selecionar o caminho correto para a sua versão do framework.
