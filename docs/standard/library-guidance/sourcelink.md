---
title: Bibliotecas SourceLink e .NET
description: Práticas recomendadas para usar SourceLink para melhorar a depuração para bibliotecas do .NET.
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: fa4af47eaa5dd1510640c2bf0ebb2187b56efae0
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49369675"
---
# <a name="sourcelink"></a>SourceLink

SourceLink é uma tecnologia que permite a depuração de código fonte dos assemblies do .NET do NuGet por desenvolvedores. SourceLink executa ao criar o pacote do NuGet e insere os metadados de controle do código-fonte dentro de módulos (assemblies) e o pacote. Os desenvolvedores que baixar o pacote e tem SourceLink habilitado no Visual Studio podem entrar em seu código-fonte. SourceLink fornece metadados de controle do código-fonte para criar uma ótima experiência de depuração.

## <a name="sourcelink-demo"></a>Demonstração de SourceLink

> [!VIDEO https://www.youtube.com/embed/gyRGhCQPkB4?start=61]

## <a name="using-sourcelink"></a>Usando SourceLink

Instruções sobre como usar SourceLink pode ser encontrado na [dotnet/sourceLink](https://github.com/dotnet/sourcelink/blob/master/README.md) repositório do GitHub.

Você pode usar [Explorador de pacotes NuGet](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) para confirmar que os metadados de SourceLink foi inserido com êxito no pacote. Verifique o `Repository` metadados estão presente com um identificador de comentário e arquivos. PDB estão localizados com. dll de cada nome de destino.

![SourceLink no Explorador de pacotes do NuGet](./media/sourcelink/nuget-package-explorer-sourcelink.png "SourceLink no Explorador de pacotes do NuGet")

**Considere a possibilidade de ✔️** usando SourceLink para adicionar metadados de controle do código-fonte para seus assemblies e o pacote do NuGet.

**Considere a possibilidade de ✔️** incluindo arquivos PDB no pacote NuGet.

>[!div class="step-by-step"]
[Anterior](./dependencies.md)
[Próximo](./publish-nuget-package.md)
