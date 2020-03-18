---
title: Portabilidade de bibliotecas para o .NET Core
description: Saiba como realizar a portabilidade de projetos de biblioteca do .NET Framework para o .NET Core.
author: cartermp
ms.date: 12/07/2018
ms.openlocfilehash: 68fe36e543d949dc76bdb0c19ef3482936ad9e79
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79398905"
---
# <a name="port-net-framework-libraries-to-net-core"></a>Portabilidade de bibliotecas do .NET Framework para o .NET Core

Aprenda a portar o código de biblioteca .NET Framework para .NET Core, onde ele é executado em plataforma sinuosa e expande o alcance dos aplicativos que o usam.

## <a name="prerequisites"></a>Pré-requisitos

Este artigo pressupõe que você:

- Está usando o Visual Studio 2017 ou posterior. (.NET Core não é suportado em versões anteriores do Visual Studio.)
- Entenda o [processo de portabilidade recomendado](index.md).
- Resolveu quaisquer problemas com [dependências de terceiros](third-party-deps.md).

Você também deve se familiarizar com o conteúdo dos seguintes artigos:

[.NET Padrão](../../standard/net-standard.md)\
Este artigo descreve a especificação formal das APIs .NET que se destinam a estar disponíveis em todas as implementações .NET.

[Pacotes, Metapacotes e Frameworks](../packages.md)\
Este artigo discute como o .NET Core define e usa pacotes, e como os pacotes dão suporte ao código em execução em várias implementações do .NET.

[Desenvolvendo bibliotecas com ferramentas multiplataformas](../tutorials/libraries.md)\
Este artigo explica como escrever bibliotecas usando o .NET Core CLI.

[Adições ao formato *csproj* para .NET Core](../tools/csproj.md)\
Este artigo descreve as alterações adicionadas aos arquivos de projeto como parte da mudança para *csproj* e o MSBuild.

[Portando para .NET Core - Analisando suas dependências de terceiros](third-party-deps.md)\
Este artigo discute a portabilidade de dependências de terceiros e o que fazer quando uma dependência de pacote NuGet não é executada no .NET Core.

## <a name="retarget-to-net-framework-472"></a>Redirecionar para .NET Framework 4.7.2

Se o seu código não estiver direcionando para o .NET Framework 4.7.2, recomendamos o redirecionamento para o .NET Framework 4.7.2. Isso garante a disponibilidade das alternativas de API mais recentes para casos em que o .NET Standard não dá suporte a APIs existentes.

Para cada um dos projetos que deseja portar, faça o seguinte no Visual Studio:

1. Clique com o botão direito do mouse no projeto e selecione **Propriedades**.
1. Na lista suspensa **Estrutura de Destino**, selecione **.NET Framework 4.7.2**.
1. Recompile o projeto.

Como seus projetos agora são direcionados ao .NET Framework 4.7.2, use essa versão do .NET Framework como sua base de portabilidade de código.

## <a name="determine-portability"></a>Determinar a portabilidade

A próxima etapa é executar o ApiPort (Analisador de Portabilidade de API) para gerar um relatório de portabilidade para análise.

Entenda a [ApiPort (Analisador de Portabilidade de API)](../../standard/analyzers/portability-analyzer.md) e como gerar relatórios de portabilidade para direcionar ao .NET Core. A maneira como você faz isso provavelmente varia de acordo com suas necessidades e preferências pessoais. As seções a seguir detalham algumas abordagens diferentes. Você pode perceber que está combinando etapas dessas abordagens, dependendo de como o código está estruturado.

### <a name="deal-primarily-with-the-compiler"></a>Lidar principalmente com o compilador

Essa abordagem funciona bem para pequenos projetos ou projetos que não usam muitas APIs do Framework .NET. A abordagem é simples:

1. Opcionalmente, execute a ApiPort no seu projeto. Se você executar a ApiPort, saiba mais sobre os problemas que você precisará resolver nos relatórios.
1. Copie todo o códigos para um novo projeto do .NET Core.
1. Ao consultar o relatório de portabilidade (se um for gerado), resolva os erros do compilador até que o projeto seja totalmente compilado.

Embora não seja estruturada, essa abordagem focada em código muitas vezes resolve problemas rapidamente. Um projeto que contém somente os modelos de dados pode ser um candidato ideal para esta abordagem.

### <a name="stay-on-the-net-framework-until-portability-issues-are-resolved"></a>Mantenha-se no Quadro .NET até que os problemas de portabilidade sejam resolvidos

Essa abordagem pode ser a melhor se você preferir que o código seja compilado durante todo o processo. A abordagem é a seguinte:

1. Execute a ApiPort em um projeto.
1. Trate os problemas usando diferentes APIs portáteis.
1. Anote todas as áreas nas quais está impedido de usar uma alternativa direta.
1. Repita as etapas anteriores para todos os projetos que estão passando por portabilidade até ter certeza de que todos estejam prontos para serem copiados em um novo projeto .NET Core.
1. Copie o código em um novo projeto do .NET Core.
1. Solucione os problemas para os quais não exista uma alternativa direta, de acordo com suas anotações.

Essa abordagem cuidadosa é mais estruturada do que simplesmente tratar os erros do compilador, mas ainda é relativamente focada em código e tem a vantagem de sempre ter código que pode ser compilado. A maneira de resolver certos problemas que não puderam ser tratados usando apenas outra API varia muito. Você pode achar que precisa desenvolver um plano mais abrangente para certos projetos, que está coberto na próxima abordagem.

### <a name="develop-a-comprehensive-plan-of-attack"></a>Desenvolva um plano abrangente de ataque

Essa abordagem pode ser a melhor para projetos maiores e mais complexos, nos quais a reestruturação do código ou a recriação completa de determinadas áreas pode ser necessária para dar suporte ao .NET Core. A abordagem é a seguinte:

1. Execute a ApiPort em um projeto.
1. Compreenda os pontos em que cada tipo não portátil está sendo usado e como isso afeta a portabilidade geral.
   - Entenda a natureza desses tipos. Eles são poucos, mas usados com frequência? Eles são muitos, mas usados com pouca frequência? Seu uso é concentrado ou eles são distribuído por todo o código?
   - É fácil isolar o código que não é portátil para lidar com ele mais efetivamente?
   - Você precisa refatorar seu código?
   - Para aqueles tipos que não são portáteis, existem APIs alternativas que realizam a mesma tarefa? Por exemplo, se você <xref:System.Net.WebClient> estiver usando a classe, <xref:System.Net.Http.HttpClient> você pode ser capaz de usar a classe em vez disso.
   - Há diferentes APIs portáteis disponíveis para realizar uma tarefa, mesmo se não for uma substituição exata? Por exemplo, se você <xref:System.Xml.Schema.XmlSchema> estiver usando para analisar xml, mas não precisar de <xref:System.Xml.Linq> descoberta de esquema XML, você pode usar APIs e implementar a análise de si mesmo em vez de confiar em uma API.
1. Se você tiver assemblies que são de difícil portabilidade, vale a pena deixá-los no .NET Framework por enquanto? Estas são algumas coisas que você deve considerar:
   - Você pode ter alguma funcionalidade na sua biblioteca que é incompatível com o .NET Core por ser muito dependente de funcionalidades específicas do .NET Framework ou do Windows. Vale a pena deixar essa funcionalidade para trás por enquanto e liberar uma versão temporária .NET Core da sua biblioteca com menos recursos até que os recursos estejam disponíveis para portar os recursos?
   - Uma refatoração ajudaria?
1. Seria razoável criar sua própria implementação de uma API do .NET Framework indisponível?
   Você pode considerar copiar, modificar e usar o código da fonte de [referência .NET Framework](https://github.com/Microsoft/referencesource). O código-fonte de referência é licenciado sob a [Licença do MIT](https://github.com/Microsoft/referencesource/blob/master/LICENSE.txt), portanto, você tem uma liberdade considerável para usar a fonte como base para seu próprio código. Basta atribuir devidamente a Microsoft em seu código.
1. Repita esse processo conforme necessário para os diferentes projetos.

A fase de análise pode demorar algum tempo dependendo do tamanho de sua base de código. Dedique tempo a essa fase para compreender profundamente o escopo das mudanças necessárias e como desenvolver um plano normalmente economiza tempo em longo prazo, especialmente se você tiver uma base de código complexa.

Seu plano pode envolver alterações significativas na sua base de código enquanto ainda é direcionado para o .NET Framework 4.7.2, tornando essa uma versão mais estruturada da abordagem anterior. A maneira de executar o plano depende de sua base de código.

### <a name="mixed-approach"></a>Abordagem mista

É provável que você combine as abordagens acima para cada projeto. Você deve fazer o que parece ser ideal para você e para sua base de código.

## <a name="port-your-tests"></a>Porto seus testes

A melhor maneira de verificar se tudo está funcionando após portar seu código é testá-lo ao portá-lo para o .NET Core. Para fazer isso, você precisará usar uma estrutura de teste que compilará e executará os testes para .NET Core. No momento, você tem três opções:

- [xUnit](https://xunit.github.io/)
  - [Introdução](https://xunit.github.io/docs/getting-started-dotnet-core.html)
  - [Ferramenta para converter um projeto MSTest em xUnit](https://github.com/dotnet/codeformatter/tree/master/src/XUnitConverter)
- [NUnit](https://nunit.org/)
  - [Introdução](https://github.com/nunit/docs/wiki/Installation)
  - [Postagem no blog sobre a migração de MSTest para NUnit](https://www.florian-rappl.de/News/Page/275/convert-mstest-to-nunit)
- [MSTest](/visualstudio/test/unit-test-basics)

## <a name="recommended-approach"></a>Abordagem recomendada

Por fim, o esforço de portabilidade depende muito de como seu código do .NET Framework está estruturado. Uma boa maneira de portar seu código é começar com a *base* de sua biblioteca, que são os componentes fundamentais do seu código. Ela pode ser os modelos de dados ou alguma outra classe e método fundamental que todos os demais elementos usam direta ou indiretamente.

1. Porte o projeto de teste da camada da sua biblioteca que está sendo portada no momento.
1. Copie a base da sua biblioteca para um novo projeto do .NET Core e selecione a versão do .NET Standard à qual você deseja dar suporte.
1. Faça as alterações necessárias para que o código seja compilado. Uma boa parte disso pode exigir a adição de dependências de pacotes NuGet para o arquivo *csproj*.
1. Execute os testes e faça os ajustes necessários.
1. Selecione a próxima camada de código para portabilidade e repita as etapas anteriores.

Se você começar a partir da base de sua biblioteca, progredir externamente e testar cada camada conforme necessário, a portabilidade será um processo sistemático no qual os problemas ficam isolados a uma camada de código por vez.

## <a name="next-steps"></a>Próximas etapas

>[!div class="nextstepaction"]
>[Organizar projetos para o .NET Core](project-structure.md)
