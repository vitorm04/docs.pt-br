---
title: "Portabilidade para o .NET Core – Bibliotecas"
description: Saiba como realizar a portabilidade de projetos de biblioteca do .NET Framework para o .NET Core.
keywords: .NET, .NET Core
author: cartermp
ms.author: mairaw
ms.date: 07/14/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: a0fd860d-d6b6-4659-b325-8a6e6f5fa4a1
ms.workload:
- dotnetcore
ms.openlocfilehash: 24c74f0396dd7bfdf19fc0e11a29110fdbf27173
ms.sourcegitcommit: cf22b29db780e532e1090c6e755aa52d28273fa6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2018
---
# <a name="porting-to-net-core---libraries"></a>Portabilidade para o .NET Core – Bibliotecas

Este artigo discute a portabilidade do código de biblioteca para .NET Core, de modo que seja executado entre plataformas.

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

## <a name="net-framework-technologies-unavailable-on-net-core"></a>Tecnologias do .NET Framework não disponíveis no .NET Core

Várias tecnologias disponíveis para as bibliotecas do .NET Framework não estão disponíveis para uso com o .NET Core, como AppDomains, Comunicação Remota, CAS (Segurança de acesso do código) e Transparência de segurança. Se suas bibliotecas dependerem de uma ou várias dessas tecnologias, considere as abordagens alternativas descritas abaixo. Se você quiser saber mais sobre compatibilidade de API, a equipe do CoreFX mantém uma [Lista de alterações comportamentais/quebras de compatibilidade e APIs preteridas/herdadas](https://github.com/dotnet/corefx/wiki/ApiCompat) no GitHub.

Só porque uma API ou tecnologia não está implementada no momento, não significa que ela não tem suporte intencionalmente. Registre um problema em [problemas no repositório dotnet/corefx](https://github.com/dotnet/corefx/issues) no GitHub para solicitar APIs e tecnologias específicas. [As solicitações de portabilidade nos problemas](https://github.com/dotnet/corefx/labels/port-to-core) são marcadas com o rótulo `port-to-core`.

### <a name="appdomains"></a>AppDomains

Os AppDomains isolam os aplicativos uns dos outros. Os AppDomains exigem suporte de tempo de execução e geralmente são muito caros. Eles não são implementados no .NET Core. Não pretendemos adicionar esse recurso no futuro. Para isolamento de código, recomendamos como alternativa o uso de processos separados ou contêineres. Para o carregamento dinâmico de assemblies, recomendamos a nova classe <xref:System.Runtime.Loader.AssemblyLoadContext>.

Para facilitar a migração de código do .NET Framework, expomos algumas das APIs <xref:System.AppDomain> exibidas no .NET Core. Algumas das APIs funcionam normalmente (por exemplo, <xref:System.AppDomain.UnhandledException?displayProperty=nameWithType>), alguns membros não fazem nada (por exemplo, <xref:System.AppDomain.SetCachePath%2A>) e alguns geram <xref:System.PlatformNotSupportedException> (por exemplo, <xref:System.AppDomain.CreateDomain%2A>). Verifique os tipos que você usa na [fonte de referência de `System.AppDomain`](https://github.com/dotnet/corefx/blob/master/src/System.Runtime.Extensions/src/System/AppDomain.cs) no [repositório dotnet/corefx do GitHub](https://github.com/dotnet/corefx) selecionando o branch que corresponde à sua versão implementada.

### <a name="remoting"></a>Comunicação Remota

A Comunicação Remota do .NET foi identificada como uma arquitetura problemática. Ela é usada para comunicação entre AppDomains, o que não tem mais suporte. Além disso, a Comunicação Remota exige suporte de tempo de execução, o que é caro para manter. Por esses motivos, a Comunicação Remota do .NET não tem suporte no .NET Core, e não planejamos adicionar suporte para ela no futuro.

Para comunicação entre processos, considere mecanismos IPC (comunicação entre processos) como uma alternativa à Comunicação Remota, tais como a classe <xref:System.IO.Pipes> ou <xref:System.IO.MemoryMappedFiles.MemoryMappedFile>.

Entre computadores, use uma solução baseada em rede como alternativa. De preferência, use um protocolo de texto sem formatação de sobrecarga baixa, como HTTP. O [servidor Web Kestrel](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel), o servidor Web usado pelo ASP.NET Core, é uma opção. Considere também o uso de <xref:System.Net.Sockets> para cenários entre computadores baseados em rede. Para ter mais opções, veja [.NET Open Source Developer Projects: Messaging](https://github.com/Microsoft/dotnet/blob/master/dotnet-developer-projects.md#messaging).

### <a name="code-access-security-cas"></a>CAS (Segurança de Acesso do Código)

A área restrita, que depende do tempo de execução ou da estrutura para restringir quais recursos um aplicativo gerenciado ou biblioteca usa ou executa, [não tem suporte no .NET Framework](~/docs/framework/misc/code-access-security.md) e, portanto, também não tem suporte no .NET Core. Acreditamos que há muitos casos no .NET Framework e no tempo de execução nos quais uma elevação de privilégios ocorre a fim de continuar a tratar CAS como um limite de segurança. Além disso, a CAS complica mais a implementação e geralmente tem implicações de desempenho de exatidão em aplicativos que não pretendem usá-la.

Use limites de segurança fornecidos pelo sistema operacional, como virtualização, contêineres ou contas de usuário para executar processos com o conjunto mínimo de privilégios.

### <a name="security-transparency"></a>Transparência de Segurança

Assim como a CAS, a Transparência de Segurança permite a separação do código em área restrita do código crítico de segurança de uma forma declarativa, mas [não têm mais suporte como um limite de segurança](~/docs/framework/misc/security-transparent-code.md). Esse recurso é amplamente usado pelo Silverlight. 

Use limites de segurança fornecidos pelo sistema operacional, como virtualização, contêineres ou contas de usuário para executar processos com o conjunto mínimo de privilégios.

### <a name="globaljson"></a>global.json

O arquivo *global.json* é um arquivo opcional que permite a definição da versão das ferramentas do .NET Core de um projeto. Se você estiver usando compilações noturnas do .NET Core e quiser definir uma versão específica do SDK, especifique a versão com um arquivo *global.json*. Ele geralmente está no diretório de trabalho atual ou em um de seus diretórios pai. 

```json
{
  "sdk": {
    "version": "2.1.0-preview1-006491"
  }
}
```

## <a name="converting-a-pcl-project"></a>Converter um projeto de PCL

Você pode converter os destinos de um projeto de PCL para .NET Standard carregando a biblioteca no Visual Studio 2017 e executando as seguintes etapas:

1. Clique com o botão direito do mouse no arquivo do projeto e selecione **Propriedades**.
1. Em **Biblioteca**, selecione **Direcionar .NET Platform Standard**.

Se os seus pacotes derem suporte a NuGet 3.0, o projeto será redirecionado para o .NET Standard.

Se os seus pacotes não derem suporte a NuGet 3.0, você receberá uma caixa de diálogo do Visual Studio solicitando a desinstalação dos pacotes atuais. Se você receber esse aviso, execute as seguintes etapas:

1. Clique com o botão direito do mouse no projeto e escolha **Gerenciar Pacotes NuGet**.
1. Anote os pacotes do projeto.
1. Desinstale os pacotes um por um.
1. Talvez seja necessário reiniciar o Visual Studio para concluir o processo de desinstalação. Nesse caso, um botão **Reiniciar** será apresentado na janela **Gerenciador de Pacotes NuGet**.
1. Quando o projeto é recarregado, ele é direcionado para o .NET Standard. Adicione os pacotes que você precisou desinstalar.

## <a name="retargeting-your-net-framework-code-to-net-framework-462"></a>Redirecionar seu código do .NET Framework para o .NET Framework 4.6.2

Se o seu código não estiver direcionando para o .NET Framework 4.6.2, recomendamos o redirecionamento para o .NET Framework 4.6.2. Isso garante a disponibilidade das alternativas de API mais recentes para casos em que o .NET Standard não dá suporte a APIs existentes.

Faça o seguinte para cada um dos projetos no Visual Studio que você desejar portar:

1. Clique com o botão direito do mouse no projeto e selecione Propriedades.
1. Na lista suspensa **Estrutura de Destino**, selecione **.NET Framework 4.6.2**.
1. Recompile seus projetos.

Como seus projetos agora são direcionados ao .NET Framework 4.6.2, use essa versão do .NET Framework como sua base de portabilidade de código.

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

Seu plano pode envolver alterações significativas na sua base de código enquanto ainda é direcionado para o .NET Framework 4.6.2, tornando essa uma versão mais estruturada da abordagem anterior. A maneira de executar o plano depende de sua base de código.

### <a name="mixing-approaches"></a>Combinação de abordagens

É provável que você combine as abordagens acima para cada projeto. Você deve fazer o que parece ser ideal para você e para sua base de código.

## <a name="porting-your-tests"></a>Portabilidade de seus testes

A melhor maneira de verificar se tudo está funcionando após portar seu código é testá-lo ao portá-lo para o .NET Core. Para fazer isso, você precisará usar uma estrutura de teste que compilará e executará os testes para .NET Core. No momento, você tem três opções:

- [xUnit](https://xunit.github.io/)
  * [Introdução](http://xunit.github.io/docs/getting-started-dotnet-core.html)
  * [Ferramenta para converter um projeto MSTest em xUnit](https://github.com/dotnet/codeformatter/tree/master/src/XUnitConverter)
- [NUnit](http://www.nunit.org/)
  * [Introdução](https://github.com/nunit/docs/wiki/Installation)
  * [Postagem no blog sobre a migração de MSTest para NUnit](http://www.florian-rappl.de/News/Page/275/convert-mstest-to-nunit)
- [MSTest](https://docs.microsoft.com/visualstudio/test/unit-test-basics)

## <a name="recommended-approach-to-porting"></a>Abordagem recomendada para portabilidade

Por fim, o esforço de portabilidade depende muito de como seu código do .NET Framework está estruturado. Uma boa forma de realizar a portabilidade de seu código é começar com a *base* da biblioteca, que são os componentes fundamentais de seu código. Ela pode ser os modelos de dados ou alguma outra classe e método fundamental que todos os demais elementos usam direta ou indiretamente.

1. Porte o projeto de teste da camada da sua biblioteca que está sendo portada no momento.
1. Copie a base da sua biblioteca para um novo projeto do .NET Core e selecione a versão do .NET Standard à qual você deseja dar suporte.
1. Faça as alterações necessárias para que o código seja compilado. Uma boa parte disso pode exigir a adição de dependências de pacotes NuGet para o arquivo *csproj*.
1. Execute os testes e faça os ajustes necessários.
1. Selecione a próxima camada de código para portabilidade e repita as etapas anteriores.

Se você começar a partir da base de sua biblioteca, progredir externamente e testar cada camada conforme necessário, a portabilidade será um processo sistemático no qual os problemas ficam isolados a uma camada de código por vez.
