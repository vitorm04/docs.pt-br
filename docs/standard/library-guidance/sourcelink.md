---
title: SourceLink e bibliotecas do .NET
description: Recomendações de melhores práticas para usar o SourceLink para melhorar a depuração para bibliotecas do .NET.
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: 3bc72e158a5773b656095f9ce58b442469f91e67
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53128915"
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

**✔️ CONSIDERE** incluir arquivos de símbolo (`*.pdb`) no pacote do NuGet.

> Normalmente, você poderia publicar arquivos de símbolo em um [pacote de símbolos](./nuget.md#symbol-packages). No momento, o principal host público para pacotes de símbolos não é compatível com os arquivos de símbolo portáteis (`*.pdb`) criados por projetos no estilo de SDK e os pacotes de símbolos não são úteis.

>[!div class="step-by-step"]
>[Anterior](dependencies.md)
>[Próximo](publish-nuget-package.md)