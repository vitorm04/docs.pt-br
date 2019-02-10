---
title: Portabilidade de bibliotecas para o .NET Core
description: Saiba como realizar a portabilidade de projetos de biblioteca do .NET Framework para o .NET Core.
author: cartermp
ms.date: 12/7/2018
ms.custom: seodec18
ms.openlocfilehash: 8190dcfd3ffed9051c7724752a19d88e7bef4f4d
ms.sourcegitcommit: c6f69b0cf149f6b54483a6d5c2ece222913f43ce
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55904696"
---
# <a name="port-net-framework-libraries-to-net-core"></a>Portabilidade de bibliotecas do .NET Framework para o .NET Core

Saiba como fazer a portabilidade do código da biblioteca do .NET Framework para o .NET Core, a fim de executar em plataformas cruzadas e expandir o alcance dos aplicativos que a utilizam.

## <a name="prerequisites"></a>Pré-requisitos

Este artigo pressupõe que você:

- Está usando o Visual Studio 2017 ou posterior.
  - Não há suporte para o .NET Core em versões anteriores do Visual Studio
- Entenda o [processo de portabilidade recomendado](index.md).
- Resolveu quaisquer problemas com [dependências de terceiros](third-party-deps.md).

Você também deve se familiarizar com o conteúdo dos tópicos a seguir:

[.NET Standard](~/docs/standard/net-standard.md)   
Este tópico descreve a especificação formal de APIs do .NET que devem estar disponíveis em todas as implementações do .NET.

[Pacotes, metapacotes e estruturas](~/docs/core/packages.md)   
Este artigo discute como o .NET Core define e usa pacotes, e como os pacotes dão suporte ao código em execução em várias implementações do .NET.

[Desenvolver bibliotecas com as ferramentas de plataforma cruzada](~/docs/core/tutorials/libraries.md)   
Este tópico explica como escrever bibliotecas para .NET usando ferramentas de CLI de plataforma cruzada.

[Adições ao formato *csproj* para .NET Core](~/docs/core/tools/csproj.md)   
Este artigo descreve as alterações adicionadas aos arquivos de projeto como parte da mudança para *csproj* e o MSBuild.

[Portabilidade para .NET Core – análise de suas dependências de terceiros](~/docs/core/porting/third-party-deps.md)   
Este tópico discute a portabilidade das dependências de terceiros e o que fazer quando uma dependência de pacote do NuGet não é executada no .NET Core.

## <a name="retargeting-your-net-framework-code-to-net-framework-472"></a>Redirecionar seu código do .NET Framework para o .NET Framework 4.7.2

Se o seu código não estiver direcionando para o .NET Framework 4.7.2, recomendamos o redirecionamento para o .NET Framework 4.7.2. Isso garante a disponibilidade das alternativas de API mais recentes para casos em que o .NET Standard não dá suporte a APIs existentes.

Faça o seguinte para cada um dos projetos no Visual Studio que você desejar portar:

1. Clique com o botão direito no projeto e selecione **Propriedades**.
1. Na lista suspensa **Estrutura de Destino**, selecione **.NET Framework 4.7.2**.
1. Recompile seus projetos.

Como seus projetos agora são direcionados ao .NET Framework 4.7.2, use essa versão do .NET Framework como sua base de portabilidade de código.

## <a name="determining-the-portability-of-your-code"></a>Determinar a portabilidade do código

A próxima etapa é executar o ApiPort (Analisador de Portabilidade de API) para gerar um relatório de portabilidade para análise.

Entenda a [ApiPort (Analisador de Portabilidade de API)](../../standard/analyzers/portability-analyzer.md) e como gerar relatórios de portabilidade para direcionar ao .NET Core. A maneira como você faz isso provavelmente varia de acordo com suas necessidades e preferências pessoais. Veja a seguir algumas abordagens diferentes. Você pode perceber que está combinando etapas dessas abordagens, dependendo de como o código está estruturado.

### <a name="dealing-primarily-with-the-compiler"></a>Lidar principalmente com o compilador

Essa abordagem pode ser a melhor para projetos pequenos ou projetos que não usam muitas APIs do .NET Framework. A abordagem é simples:

1. Opcionalmente, execute a ApiPort no seu projeto. Se você executar a ApiPort, saiba mais sobre os problemas que você precisará resolver nos relatórios.
1. Copie todo o códigos para um novo projeto do .NET Core.
1. Ao consultar o relatório de portabilidade (se um for gerado), resolva os erros do compilador até que o projeto seja totalmente compilado.

Embora essa abordagem seja desestruturada, a abordagem centrada em código normalmente agiliza a resolução dos problemas e pode ser a melhor abordagem para bibliotecas ou projetos menores. Um projeto que contém somente os modelos de dados pode ser um candidato ideal para esta abordagem.

### <a name="staying-on-the-net-framework-until-portability-issues-are-resolved"></a>Permanecer no .NET Framework até que os problemas de portabilidade sejam resolvidos

Essa abordagem pode ser a melhor se você preferir que o código seja compilado durante todo o processo. A abordagem é a seguinte:

1. Execute a ApiPort em um projeto.
1. Trate os problemas usando diferentes APIs portáteis.
1. Anote todas as áreas nas quais está impedido de usar uma alternativa direta.
1. Repita as etapas anteriores para todos os projetos que estão passando por portabilidade até ter certeza de que todos estejam prontos para serem copiados em um novo projeto .NET Core.
1. Copie o código em um novo projeto do .NET Core.
1. Solucione os problemas para os quais não exista uma alternativa direta, de acordo com suas anotações.

Essa abordagem cuidadosa é mais estruturada do que simplesmente tratar os erros do compilador, mas ainda é relativamente focada em código e tem a vantagem de sempre ter código que pode ser compilado. A maneira de resolver certos problemas que não puderam ser tratados usando apenas outra API varia muito. Você pode achar que precisa para desenvolver um plano mas abrangente para certos projetos, o que é tratado como a próxima abordagem.

### <a name="developing-a-comprehensive-plan-of-attack"></a>Desenvolver um plano de ação abrangente

Essa abordagem pode ser a melhor para projetos maiores e mais complexos, nos quais a reestruturação do código ou a recriação completa de determinadas áreas pode ser necessária para dar suporte ao .NET Core. A abordagem é a seguinte:

1. Execute a ApiPort em um projeto.
1. Compreenda os pontos em que cada tipo não portátil está sendo usado e como isso afeta a portabilidade geral.
   - Entenda a natureza desses tipos. Eles são poucos, mas usados com frequência? Eles são muitos, mas usados com pouca frequência? Seu uso é concentrado ou eles são distribuído por todo o código?
   - É fácil isolar o código que não é portátil para lidar com ele mais efetivamente?
   - Você precisa refatorar seu código?
   - Para esses tipos não portáteis, há APIs alternativas que realizam a mesma tarefa? Por exemplo, se você estiver usando a classe <xref:System.Net.WebClient>, poderá usar a classe <xref:System.Net.Http.HttpClient> em vez disso.
   - Há diferentes APIs portáteis disponíveis para realizar uma tarefa, mesmo se não for uma substituição exata? Por exemplo, se você estiver usando <xref:System.Xml.Schema.XmlSchema> para analisar o XML mas não exigir a descoberta de esquema XML, use APIs <xref:System.Xml.Linq> e implemente a análise por conta própria, em vez de depender de uma API.
1. Se você tiver assemblies que são de difícil portabilidade, vale a pena deixá-los no .NET Framework por enquanto? Esses são alguns pontos a considerar:
   - Você pode ter alguma funcionalidade na sua biblioteca que é incompatível com o .NET Core por ser muito dependente de funcionalidades específicas do .NET Framework ou do Windows. Vale a pena abandonar essa funcionalidade por enquanto e lançar uma versão do .NET Core de sua biblioteca com menos recursos temporariamente, até que os recursos estejam disponíveis para realizar a portabilidade das funcionalidades?
   - Uma refatoração ajudaria?
1. Seria razoável criar sua própria implementação de uma API do .NET Framework indisponível?
   Você pode considerar copiar, modificar e usar código do [.NET Framework Reference Source](https://github.com/Microsoft/referencesource). O código-fonte de referência é licenciado sob a [Licença do MIT](https://github.com/Microsoft/referencesource/blob/master/LICENSE.txt), portanto, você tem uma liberdade considerável para usar a fonte como base para seu próprio código. Basta atribuir devidamente a Microsoft em seu código.
1. Repita esse processo conforme necessário para os diferentes projetos.
 
A fase de análise pode demorar algum tempo dependendo do tamanho de sua base de código. Dedique tempo a essa fase para compreender profundamente o escopo das mudanças necessárias e como desenvolver um plano normalmente economiza tempo em longo prazo, especialmente se você tiver uma base de código complexa.

Seu plano pode envolver alterações significativas na sua base de código enquanto ainda é direcionado para o .NET Framework 4.7.2, tornando essa uma versão mais estruturada da abordagem anterior. A maneira de executar o plano depende de sua base de código.

### <a name="mixing-approaches"></a>Combinação de abordagens

É provável que você combine as abordagens acima para cada projeto. Você deve fazer o que parece ser ideal para você e para sua base de código.

## <a name="porting-your-tests"></a>Portabilidade de seus testes

A melhor maneira de verificar se tudo está funcionando após portar seu código é testá-lo ao portá-lo para o .NET Core. Para fazer isso, você precisará usar uma estrutura de teste que compilará e executará os testes para .NET Core. No momento, você tem três opções:

- [xUnit](https://xunit.github.io/)
  * [Introdução](https://xunit.github.io/docs/getting-started-dotnet-core.html)
  * [Ferramenta para converter um projeto MSTest em xUnit](https://github.com/dotnet/codeformatter/tree/master/src/XUnitConverter)
- [NUnit](https://nunit.org/)
  * [Introdução](https://github.com/nunit/docs/wiki/Installation)
  * [Postagem no blog sobre a migração de MSTest para NUnit](https://www.florian-rappl.de/News/Page/275/convert-mstest-to-nunit)
- [MSTest](https://docs.microsoft.com/visualstudio/test/unit-test-basics)

## <a name="recommended-approach-to-porting"></a>Abordagem recomendada para portabilidade

Por fim, o esforço de portabilidade depende muito de como seu código do .NET Framework está estruturado. Uma boa forma de realizar a portabilidade de seu código é começar com a *base* da biblioteca, que são os componentes fundamentais de seu código. Ela pode ser os modelos de dados ou alguma outra classe e método fundamental que todos os demais elementos usam direta ou indiretamente.

1. Porte o projeto de teste da camada da sua biblioteca que está sendo portada no momento.
1. Copie a base da sua biblioteca para um novo projeto do .NET Core e selecione a versão do .NET Standard à qual você deseja dar suporte.
1. Faça as alterações necessárias para que o código seja compilado. Uma boa parte disso pode exigir a adição de dependências de pacotes NuGet para o arquivo *csproj*.
1. Execute os testes e faça os ajustes necessários.
1. Selecione a próxima camada de código para portabilidade e repita as etapas anteriores.

Se você começar a partir da base de sua biblioteca, progredir externamente e testar cada camada conforme necessário, a portabilidade será um processo sistemático no qual os problemas ficam isolados a uma camada de código por vez.

>[!div class="step-by-step"]
>[Avançar](project-structure.md)
