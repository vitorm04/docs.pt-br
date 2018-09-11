---
title: Implantação do .NET Core Application
description: Implantação de um aplicativo .NET Core.
author: rpetrusha
ms.author: ronpet
ms.date: 09/03/2018
ms.openlocfilehash: 2ef63ebd737739b2c8e671d982c3844135689ab4
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44277145"
---
# <a name="net-core-application-deployment"></a>Implantação de um aplicativo .NET Core

Você pode criar dois tipos de implantações de aplicativos do .NET Core:

- Implantação dependente de estrutura. Como o nome indica, a FDD (implantação dependente de estrutura) se baseia na presença de uma versão compartilhada em todo o sistema do .NET Core no sistema de destino. Como o .NET Core já está presente, seu aplicativo também é portátil entre instalações do .NET Core. Seu aplicativo conterá somente seu próprio código e as dependências de terceiros que estiverem fora de bibliotecas .NET Core. As FDDs contêm arquivos *.dll* que podem ser iniciados por meio do [utilitário dotnet](../tools/dotnet.md) na linha de comando. Por exemplo, `dotnet app.dll` executa um aplicativo chamado `app`.

- Implantação autocontida. Ao contrário da FDD, a SCD (implantação autocontida) não se baseia na presença de componentes compartilhados no sistema de destino. Todos os componentes, inclusive as bibliotecas e o tempo de execução do .NET Core, são incluídos com o aplicativo e isolados de outros aplicativos .NET Core. As SCDs incluem um arquivo executável (como o *app.exe* em plataformas Windows para um aplicativo chamado `app`), que é uma versão renomeada do host específico da plataforma .NET Core, e um arquivo *.dll* (como *app.dll*), que é o aplicativo real.

## <a name="framework-dependent-deployments-fdd"></a>FDD (implantação dependente de estrutura)

Para uma FDD, seu aplicativo é implantado apenas em dependências de terceiros. Você não precisa implantar o .NET Core, pois o aplicativo usará a versão do .NET Core presente no sistema de destino. Esse é o modelo de implantação padrão para aplicativos .NET Core e ASP.NET Core direcionados ao .NET Core.

### <a name="why-create-a-framework-dependent-deployment"></a>Por que criar uma implantação dependente de estrutura?

Implantar uma FDD traz uma série de vantagens:

- Você não precisa definir previamente em quais sistemas operacionais de destino o aplicativo .NET Core será executado. Como o .NET Core usa um formato comum de arquivo PE comum para executáveis e bibliotecas independentemente do sistema operacional, ele pode executar seu aplicativo independentemente do sistema operacional subjacente. Para obter mais informações sobre o formato de arquivo PE, consulte [Formato de Arquivo do Assembly .NET](../../standard/assembly-format.md).

- O tamanho do seu pacote de implantação é pequeno. Você deve implantar apenas o aplicativo e as respectivas dependências, mas não o .NET Core em si.

- Vários aplicativos usam a mesma instalação do .NET Core, o que reduz o uso de memória e espaço em disco nos sistemas host.

Contudo, também há algumas desvantagens:

- Seu aplicativo poderá ser executado somente se a versão do .NET Core de destino, ou uma versão posterior, já estiver instalada no sistema host.

- É possível que o tempo de execução e as bibliotecas do .NET Core sejam alteradas em versões futuras, sem seu conhecimento. Em casos raros, isso pode alterar o comportamento do seu aplicativo.

## <a name="self-contained-deployments-scd"></a>SCD (implantação autocontida)

No caso de uma implantação autocontida, você implanta o aplicativo e as dependências de terceiros necessárias, juntamente com a versão do .NET Core que usou para criar o aplicativo. A criação de uma SCD não inclui as [dependências nativas do .NET Core](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md) de várias plataformas, por isso elas devem estar presentes antes de executar o aplicativo. Para saber mais sobre associação de versão em tempo de execução, confira o artigo sobre [associação de versão no .NET Core](../versions/selection.md).

Começando com o SDK do .NET Core 2.1 (versão 2.1.300), o .NET Core é compatível com *roll forward da versão de patch*. Ao criar uma implantação autocontida, as ferramentas do .NET Core incluem automaticamente o tempo de execução de manutenção mais recente da versão do .NET Core que seu aplicativo utiliza. (O tempo de execução de manutenção mais recente inclui patches de segurança e outras correções de bug.) O tempo de execução de manutenção não precisa estar presente em seu sistema de compilação; ele é baixado automaticamente do NuGet.org. Para saber mais, incluindo instruções sobre como recusar o roll-forward da versão de patch, confira [Roll forward de tempo de execução de implantação autocontida](runtime-patch-selection.md).

Implantações FDD e SCD usam executáveis de host separadas, para que você possa assinar um executável de host para um SCD com sua assinatura do publicador.

### <a name="why-deploy-a-self-contained-deployment"></a>Por que fazer uma implantação autocontida?

Implantar uma implantação autocontida apresenta duas vantagens principais:

- Você tem controle exclusivo sobre a versão do .NET Core que é implantada com seu aplicativo. A manutenção do .NET Core só pode ser feita por você.

- É possível ter certeza de que o sistema de destino pode executar seu aplicativo .NET Core, visto que você está fornecendo a versão do .NET Core na qual ele é executado.

Ela também apresenta algumas desvantagens:

- Como o .NET Core é incluído no seu pacote de implantação, você deve selecionar previamente as plataformas de destino para as quais você criará pacotes de implantação.

- O tamanho do seu pacote de implantação é relativamente grande, visto que você precisa incluir o .NET Core, bem como seu aplicativo e suas dependências de terceiros.

  A partir do .NET Core 2.0, você pode reduzir o tamanho da sua implantação em sistemas Linux em aproximadamente 28 MB usando o [*modo invariável de globalização*](https://github.com/dotnet/corefx/blob/master/Documentation/architecture/globalization-invariant-mode.md) do .NET Core. Normalmente, o .NET Core no Linux se baseia nas [bibliotecas de ICU](https://github.com/dotnet/docs/issues/http%22//icu-project.org) para suporte à globalização. No modo invariável, as bibliotecas não são incluídas na implantação e todas as culturas se comportam como a [cultura invariável](xref:System.Globalization.CultureInfo.InvariantCulture?displayProperty=nameWithType).

- Implantar vários aplicativos .NET Core autocontidos em um sistema pode consumir um volume significativo de espaço em disco, visto que cada aplicativo duplica os arquivos do .NET Core.

## <a name="step-by-step-examples"></a>Exemplos passo a passo

Para obter exemplos passo a passo de como implantar aplicativos .NET Core com ferramentas da CLI, confira o artigo [Implantação de aplicativos .NET Core com ferramentas da CLI](deploy-with-cli.md). Para obter exemplos passo a passo de como implantar aplicativos .NET Core com o Visual Studio, confira o artigo [Implantação de aplicativos .NET Core com o Visual Studio](deploy-with-vs.md). Cada tópico inclui exemplos das seguintes implantações:

- Implantação dependente de estrutura
- Implantação dependente de estrutura com dependências de terceiros
- Implantação autocontida
- Implantação autocontida com dependências de terceiros

## <a name="see-also"></a>Consulte também

* [Implantação de aplicativos .NET Core com ferramentas da CLI](deploy-with-cli.md)
* [Implantação de aplicativos .NET Core com o Visual Studio](deploy-with-vs.md)
* [Pacotes, Metapacotes e Estruturas](../packages.md)
* [Catálogo do Identificador de Tempo de Execução do .NET Core](../rid-catalog.md)
