---
title: SourceLink e bibliotecas do .NET
description: Recomendações de melhores práticas para usar o SourceLink para melhorar a depuração para bibliotecas do .NET.
author: jamesnk
ms.author: mairaw
ms.date: 01/15/2019
ms.openlocfilehash: be97f868e2fcfc6c45e4bbac45b033f8914f4d99
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333532"
---
# <a name="sourcelink"></a>SourceLink

O SourceLink é uma tecnologia que permite a depuração de código-fonte dos assemblies do .NET do NuGet por desenvolvedores. O SourceLink é executado ao criar o pacote do NuGet e insere os metadados de controle do código-fonte dentro de assemblies e do pacote. Os desenvolvedores que baixam o pacote e têm o SourceLink habilitado no Visual Studio podem intervir em seu código-fonte. O SourceLink fornece metadados de controle do código-fonte para criar uma ótima experiência de depuração.

## <a name="sourcelink-demo"></a>Demonstração do SourceLink

> [!VIDEO https://www.youtube.com/embed/gyRGhCQPkB4?start=61]

## <a name="using-sourcelink"></a>Usando o SourceLink

É possível encontrar instruções sobre como usar o SourceLink no repositório GitHub [dotnet/sourceLink](https://github.com/dotnet/sourcelink/blob/master/README.md).

Você pode usar o [Explorador de Pacotes do NuGet](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) para confirmar que os metadados do SourceLink foram inseridos com êxito no pacote. Verifique se os metadados `Repository` estão presentes com um identificador de comentário e se os arquivos .pdb estão localizados com o .dll de cada destino.

![SourceLink no Explorador de Pacotes do NuGet](./media/sourcelink/nuget-package-explorer-sourcelink.png "SourceLink no Explorador de Pacotes do NuGet")

**✔️ CONSIDERE** usar o SourceLink para adicionar metadados de controle do código-fonte aos seus assemblies e pacotes do NuGet.

> [!TIP]
> Você ainda pode aprimorar a experiência de depuração do desenvolvedor com a adição de atributos do depurador aos seus tipos.
> * <xref:System.Diagnostics.DebuggerDisplayAttribute> pode personalizar como uma classe ou campo é exibido nas janelas de variáveis do depurador.
> * <xref:System.Diagnostics.DebuggerStepThroughAttribute> instrui o depurador a depurar o código em vez de intervir nele.
> * <xref:System.Diagnostics.DebuggerBrowsableAttribute> controla se um membro é exibido nas janelas de variáveis do depurador.

**✔️ CONSIDERE** publicar arquivos de símbolo (`*.pdb`).

> Para obter mais informações sobre arquivos de símbolo e pacotes de símbolos, confira [Pacotes de símbolos](./nuget.md#symbol-packages).

>[!div class="step-by-step"]
>[Anterior](dependencies.md)
>[Próximo](publish-nuget-package.md)
