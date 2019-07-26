---
title: O .NET Portability Analyzer – .NET
description: Saiba como usar a ferramenta .NET Portability Analyzer para avaliar a portabilidade do seu código entre as várias implementações de .NET, incluindo .NET Core, .NET Standard, UWP e Xamarin.
ms.date: 07/18/2019
ms.technology: dotnet-standard
ms.assetid: 0375250f-5704-4993-a6d5-e21c499cea1e
ms.openlocfilehash: 433936480aa1181370a6ebc2bd2ba9914a50dfa2
ms.sourcegitcommit: 09d699aca28ae9723399bbd9d3d44aa0cbd3848d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/19/2019
ms.locfileid: "68331737"
---
# <a name="the-net-portability-analyzer"></a>O .NET Portability Analyzer

Deseja fazer suas bibliotecas serem compatíveis com multiplataforma? Deseja ver a quantidade de trabalho necessário para tornar o aplicativo compatível com outras implementações do .NET e perfis, incluindo .NET Core, .NET Standard, UWP e Xamarin para iOS, Android e Mac? O [.NET Portability Analyzer](https://github.com/microsoft/dotnet-apiport) é uma ferramenta que fornece um relatório detalhado sobre a flexibilidade do seu programa nas implementações do .NET mediante a análise de assemblies. O Analisador de Portabilidade é oferecido como uma [Extensão do Visual Studio](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer), que analisa assemblies por projeto, e como um [aplicativo de console ApiPort](https://aka.ms/apiportdownload), que analisa assemblies por arquivos ou diretório especificados.

## <a name="common-targets"></a>Destinos comuns

* [.NET Core](../../core/index.md): tem um design modular, utiliza lado a lado e está direcionado a cenários de plataforma cruzada. O lado a lado permite adotar novas versões do .NET Core sem interromper outros aplicativos. Se sua meta é portar seu aplicativo para as plataformas cruzadas compatíveis com o .NET Core, esse é o destino recomendado. 
* .[NET Standard](../../standard/net-standard.md): inclui APIs do .NET Standard disponíveis em todas as implementações do .NET. Se sua meta é fazer sua biblioteca ser executada em todas as plataformas compatíveis com o .NET, esse é o destino recomendado.  
* [ASP.NET Core](/aspnet/core): uma estrutura da Web moderna desenvolvida com base no .NET Core. Se sua meta é portar seu aplicativo Web para o .NET Core para dar suporte a várias plataformas, esse é o destino recomendado.
* .NET Core + [extensões de plataforma](../../core/porting/windows-compat-pack.md): inclui as APIs do .NET Core, além do Pacote de Compatibilidade do Windows, que oferece muitas das tecnologias disponíveis do .NET Framework. Esse é um destino recomendado para portar seu aplicativo do .NET Framework para o .NET Core no Windows.
* .NET Standard + [extensões de plataforma](../../core/porting/windows-compat-pack.md): inclui as APIs do .NET Standard, além do Pacote de Compatibilidade do Windows, que oferece muitas das tecnologias disponíveis do .NET Framework. Esse é um destino recomendado para portar sua biblioteca do .NET Framework para o .NET Core no Windows.

## <a name="how-to-use-the-net-portability-analyzer"></a>Como usar o Analisador de Portabilidade do .NET

Para começar a usar o Analisador de Portabilidade do .NET no Visual Studio, primeiro é necessário baixar e instalar a extensão do [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer). Ele funciona no Visual Studio 2017 e versões posteriores. É possível configurá-la no Visual Studio por meio de **Analisar** > **Configurações do Analisador de Portabilidade** e selecionar as Plataformas de Destino, que são as versões/plataformas do .NET que você deseja avaliar as lacunas de portabilidade, comparando com a plataforma/versão com a qual seu assembly atual foi criado.

![Captura de tela de portabilidade](./media/portability-analyzer/portability-screenshot.png)

Também é possível usar o aplicativo de console ApiPort, baixando-o do [repositório ApiPort](http://aka.ms/apiportdownload). É possível usar a opção de comando `listTargets` para exibir a lista de destino disponível e escolher as plataformas de destino especificando a opção de comando `-t` ou `--target`. 

### <a name="analyze-portability"></a>Analisar portabilidade
Para analisar todo o projeto no Visual Studio, clique com o botão direito do mouse no projeto no **Gerenciador de Soluções** e selecione **Analisar Portabilidade do Assembly**. Caso contrário, acesse o menu **Analyze** e selecione **Analisar Portabilidade do Assembly**. Em seguida, selecione o executável do seu projeto ou DLL.

![Analisador de Portabilidade no Gerenciador de Soluções](./media/portability-analyzer/portability-solution-explorer.png)

Também é possível usar o [aplicativo de console ApiPort](https://aka.ms/apiportdownload). 

* Digite o seguinte comando para analisar o diretório atual: `ApiPort.exe analyze -f .`
* Para analisar uma lista específica de arquivos. dll, digite o seguinte comando: `ApiPort.exe analyze -f first.dll -f second.dll -f third.dll`
* Execute `ApiPort.exe -?` para obter mais ajuda

É recomendável que você inclua todos os arquivos exe e dll relacionados que você tem e que deseje portar e exclua os arquivos do qual seu aplicativo depende, mas que você não tem e não pode portar. Isso fará com que o relatório de portabilidade seja o mais relevante.  

### <a name="view-and-interpret-portability-result"></a>Exibir e interpretar o resultado da portabilidade

Apenas as APIs que não são compatíveis com uma Plataforma de Destino são exibidas no relatório. Após executar a análise no Visual Studio, você verá o link do arquivo do relatório de portabilidade do .NET aparecer. Se você usou o [aplicativo de console ApiPort](https://aka.ms/apiportdownload), o relatório de portabilidade do .NET é salvo como um arquivo no formato especificado. O padrão está em um arquivo Excel ( *.xlsx*) em seu diretório atual.

#### <a name="portability-summary"></a>Resumo de Portabilidade 

![Resumo de Portabilidade](./media/portability-analyzer/portabilitysummary.png)

A seção Resumo de Portabilidade do relatório mostra o percentual de portabilidade para cada assembly incluído na execução. No exemplo anterior, 71,24% das APIs do .NET Framework usadas no aplicativo `svcutil` estão disponíveis no .NET Core + Extensões de plataforma. Se você executar a ferramenta Analisador de Portabilidade do .NET em vários assemblies, cada um deles deverá ter uma linha no relatório Resumo de Portabilidade.

#### <a name="details"></a>Detalhes

![Detalhes da Portabilidade](./media/portability-analyzer/portabilitydetails.png)

A seção Detalhes do relatório lista as APIs ausentes de uma das Plataformas de Destino. 

- Tipo de destino: o tipo tem uma API ausente de uma Plataforma de Destino 
- Membro de destino: o método está ausente de uma Plataforma de Destino 
- Nome do assembly: o assembly do .NET Framework no qual a API ausente reside. 
- Cada uma das Plataformas de Destino selecionada é uma coluna, como “.NET Core”: O valor "Sem suporte" significa que não há suporte para a API nesta Plataforma de Destino. 
- Alterações recomendadas: a API ou a tecnologia recomendada para a qual alterar. No momento, esse campo está vazio ou desatualizado para muitas APIs. Devido ao grande número de APIs, é um grande desafio mantê-las em funcionamento. Estamos examinando soluções alternativas para fornecer informações úteis aos clientes.

#### <a name="missing-assemblies"></a>Assemblies Ausentes

![Detalhes da Portabilidade](./media/portability-analyzer/missingassemblies.png)

Você pode encontrar uma seção Assemblies Ausentes em seu relatório. Ele informa que essa lista de assemblies é referenciada por seus assemblies analisados e não foi analisada. Se for um assembly de sua propriedade, inclua-o na execução do analisador de portabilidade de Api para que você possa obter um relatório de portabilidade detalhado no nível da API para ele. Se for uma biblioteca de terceiros, pesquise se eles têm uma versão mais recente compatível com sua plataforma de destino. Em caso afirmativo, considere migrar para a versão mais recente. Por fim, seria esperado que essa lista incluísse todos os assemblies de terceiros do qual seu aplicativo depende e confirmasse que eles têm uma versão compatível com sua plataforma de destino.  

Para obter mais informações sobre o Analisador de Portabilidade do .NET, acesse a [documentação do GitHub](https://github.com/Microsoft/dotnet-apiport#documentation) e assista ao vídeo [A Brief Look at the .NET Portability Analyzer](https://channel9.msdn.com/Blogs/Seth-Juarez/A-Brief-Look-at-the-NET-Portability-Analyzer) (Uma análise breve do Analisador de Portabilidade do .NET) do Channel 9.
