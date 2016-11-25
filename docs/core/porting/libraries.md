---
title: "Portabilidade para o .NET Core – Bibliotecas"
description: "Portabilidade para o .NET Core – Bibliotecas"
keywords: .NET, .NET Core
author: cartermp
manager: wpickett
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: a0fd860d-d6b6-4659-b325-8a6e6f5fa4a1
translationtype: Human Translation
ms.sourcegitcommit: 46061efa8e33c6a73befa5181eb33b8deb2fa637
ms.openlocfilehash: 503cf3628ee317f701f467bddc4bcb5998b82af4

---

# <a name="porting-to-net-core---libraries"></a>Portabilidade para o .NET Core – Bibliotecas

Com o lançamento do .NET Core 1.0, há a oportunidade de portar código de biblioteca existente para que possa ser executado em plataformas cruzadas.  Este artigo aborda a .NET Standard Library, tecnologias indisponíveis, como lidar com o menor número de APIs disponíveis no .NET Core 1.0, como usar as ferramentas que vem com a Visualização 2 do SDK do .NET Core e as abordagens recomendadas para portar seu código.

A portabilidade é uma tarefa que pode levar tempo, especialmente se você tiver uma grande base de código.  Você também deve estar preparado para adaptar as diretrizes indicadas aqui conforme necessário para melhor adequação ao seu código.  Cada base de código é diferente, por isso esse artigo tenta apresentar as coisas de maneira flexível, porém você pode achar que precisa divergir das diretrizes indicadas.

## <a name="prerequisites"></a>Pré-requisitos

Esse artigo pressupõe que você está usando o Visual Studio 2015 ou posterior no Windows.  Os bits necessários para criar o código do .NET Core não estão disponíveis em versões anteriores do Visual Studio.

Esse artigo também presume que você compreende o [processo recomendado de portabilidade](index.md) e já resolveu possíveis problemas com as [dependências de terceiros](third-party-deps.md).

## <a name="targeting-the-net-standard-library"></a>Direcionamento da .NET Standard Library

A melhor maneira de compilar uma biblioteca de plataforma cruzada para o .NET Core é direcionar para a [.NET Standard Library](../../standard/library.md).  A .NET Standard Library é uma especificação formal de APIs .NET que devem estar disponíveis em todos os tempos de execução do .NET.  Há suporte para ela no tempo de execução do .NET Core.

Isso significa que você terá que fazer uma escolha entre as APIs que você pode usar e plataformas às quais pode dar suporte e escolher a versão do .NET Platform Standard ideal para a compensação que você deseja fazer.

No momento, há 7 versões diferentes a serem considerados: .NET Standard 1.0 a 1.6.  Se você escolher uma versão posterior, obterá acesso a mais APIs, porém às custas de execução em menos destinos.  Se você escolher uma versão inferior, seu código poderá ser executado em mais destinos, porém às custas de menos APIs disponíveis.

Para sua conveniência, veja esta matriz de cada versão do .NET Standard e cada área específica em que é executado:

| Nome da Plataforma | Alias |  |  |  |  |  | | |
| :---------- | :--------- |:--------- |:--------- |:--------- |:--------- |:--------- |:--------- |:--------- |
|.NET Standard | netstandard | 1.0 | 1.1 | 1.2 | 1.3 | 1.4 | 1.5 | 1.6 |
|.NET Core|netcoreapp|&rarr;|&rarr;|&rarr;|&rarr;|&rarr;|&rarr;|1.0|
|.NET Framework|net|&rarr;|4.5|4.5.1|4.6|4.6.1|4.6.2|4.6.3|
|Plataformas Mono/Xamarin||&rarr;|&rarr;|&rarr;|&rarr;|&rarr;|&rarr;|*|
|Plataforma Universal do Windows|uap|&rarr;|&rarr;|&rarr;|&rarr;|10.0|||
|Windows|win|&rarr;|8.0|8.1|||||
|Windows Phone|wpa|&rarr;|&rarr;|8.1|||||
|Windows Phone Silverlight|wp|8.0|||||||

É importante entender é que **um projeto direcionado a uma versão inferior não pode fazer referência a um projeto direcionado a uma versão superior**.  Por exemplo, um projeto direcionado ao .NET Platform Standard versão 1.2 não pode fazer referência a projetos direcionados ao .NET Platform Standard versão 1.3 ou superior.  No entanto, os projetos **podem** fazer referência a versões anteriores, por isso um projeto direcionado para o .NET Platform Standard 1.3 pode fazer referência a um projeto direcionado para o .NET Platform Standard 1.2 ou inferior.

É recomendável selecionar a versão mais antiga do .NET Standard possível e usá-la em todo o projeto.

Leia mais em [.NET Platform Standard Library](../../standard/library.md).

## <a name="key-technologies-not-yet-available-on-the-net-standard-or-net-core"></a>Principais tecnologias ainda não disponíveis no .NET Standard ou .NET Core

Você pode estar usando algumas tecnologias disponíveis para o .NET Framework que não estão disponíveis no momento para o .NET Core.  Cada subseção a seguir corresponde a uma dessas tecnologias.  Opções alternativas serão listadas se for possível adotá-las.

### <a name="app-domains"></a>Domínios de Aplicativo

AppDomains podem ser usados para diversas finalidades no .NET Framework. Para isolamento de código, é recomendável usar processos separados e/ou contêineres como uma alternativa. Para carregamento dinâmico de assemblies, recomendamos a nova classe @System.Runtime.Loader.AssemblyLoadContext.

### <a name="remoting"></a>Comunicação Remota

Para comunicação entre processos, mecanismos IPC (comunicação entre processos) podem ser usados como uma alternativa à Comunicação Remota, tais como [Pipes](https://docs.microsoft.com/dotnet/core/api/system.io.pipes) ou [Arquivos de Memória Mapeado](https://docs.microsoft.com/dotnet/core/api/system.io.memorymappedfiles.memorymappedfile).

Entre computadores, você pode usar uma solução baseada em rede como alternativa, preferencialmente um protocolo de texto sem formatação de baixa sobrecarga, como HTTP.  [KestrelHttpServer](https://github.com/aspnet/KestrelHttpServer), o servidor Web usado pelo ASP.NET Core é uma opção aqui.  A geração de proxy remota via [Castle.Core](https://github.com/castleproject/Core) também é considerada.

### <a name="binary-serialization"></a>Serialização binária

Como alternativa à serialização binária, há várias tecnologias de serialização diferentes à sua escolha.  Você deve escolher uma que atenda às suas metas de formatação e espaço.  As opções populares incluem:

* [JSON.NET](http://www.newtonsoft.com/json) para JSON
* @System.Runtime.Serialization.DataContractSerializer para XML e JSON
* @System.Xml.Serialization.XmlSerializer para XML
* [protobuf-net](https://github.com/mgravell/protobuf-net) para Buffers de Protocolo

Consulte os recursos vinculados para saber mais sobre seus benefícios e escolha aqueles que atendem às suas necessidades.  Há muitos outros formatos e tecnologias de serialização, muitas das quais são softwares livres.

### <a name="sandboxes"></a>Áreas restritas

Como uma alternativa às áreas restritas, você pode usar os limites de segurança do sistema operacional fornecidos, como contas de usuário para executar processos com o menor conjunto de privilégios.

## <a name="overview-of-projectjson"></a>Visão geral de `project.json`

O [modelo de projeto do project.json](../tools/project-json.md) é um modelo de projeto que acompanha a Visualização 2 do SDK do .NET Core 1.0.  Ele oferece alguns benefícios que você pode querer aproveitar hoje mesmo:

* Multiplataforma simples em que assemblies específicos de destino podem ser gerados de um único build.
* A capacidade de gerar com facilidade um pacote NuGet com um build do projeto.
* Não é necessário listar os arquivos no seu arquivo de projeto.
* Unificação das dependências de pacotes NuGet e dependências projeto a projeto.

> Embora o `project.json` eventualmente será preterido, ele pode ser usado para criar bibliotecas no .NET Standard atualmente.

### <a name="the-project-file-projectjson"></a>O Arquivo de Projeto: `project.json`

Projetos do .NET Core são definidos por um diretório que contém um arquivo `project.json`.  É nesse arquivo em que os aspectos do projeto são declarados, como as dependências de pacote, configuração do compilador, configuração de tempo de execução e muito mais.

O comando `dotnet restore` lê esse arquivo de projeto, restaura todas as dependências do projeto e gera um arquivo `project.lock.json`.  Esse arquivo contém todas as informações necessárias que o sistema de compilação precisa para compilar o projeto.

Para saber mais sobre o arquivo `project.json`, leia a [referência do project.json](../tools/project-json.md).

### <a name="the-solution-file-globaljson"></a>O Arquivo de Solução: `global.json`

O `global.json` é um arquivo opcional para incluir em uma solução que contém vários projetos.  Ele geralmente reside no diretório raiz de um conjunto de projetos.  Ele pode ser usado para informar o sistema de build sobre diferentes subdiretórios que podem conter projetos.  Isso serve para grandes sistemas compostos por vários projetos.

Por exemplo, você pode organizar seu código em nível superior na pasta `/src` e `/test` dessa forma:

```json
{
    "projects":[ "src", "test" ]
}
```

Você pode então ter vários arquivo `project.json` em suas próprias subpastas dentro de `/src` e `/test`.

### <a name="how-to-multitarget-with-projectjson"></a>Como obter Multiplataformas com `project.json`

Muitas bibliotecas são multiplataforma para terem o alcance mais amplo possível.  Com o .NET Core, a multiplataforma é um “cidadão de primeira classe” o que significa que você pode gerar assemblies específicos à plataforma com facilidade em uma única compilação.

Habilitar a multiplataforma é tão simples quanto adicionar o TFM (Moniker da Estrutura de Destino) ao seu arquivo `project.json` usando as dependências corretas para cada destino (`dependencies` .NET Core e `frameworkAssemblies` para o .NET Framework) e potencialmente usar as diretivas `#if` para compilar condicionalmente o código-fonte para o uso da API específica de plataforma.

Por exemplo, imagine que você está criando uma biblioteca em que deseja executar algumas operações de rede e deseja que a biblioteca seja executada em todas as versões do .NET Framework, um perfil de PCL (Biblioteca de Classes Portátil) e .NET Core.  Para destinos do .NET Core e .NET Framework 4.5+, você pode usar a biblioteca `System.Net.Http` e `async`/`await`.  No entanto, para versões anteriores do .NET Framework, essas APIs não estão disponíveis.

Veja este exemplo de seção `frameworks` para um `project.json` direcionado para o .NET Framework versões 2.0, 3.5, 4.0, 4.5 e .NET Standard 1.6:

```javascript
{
    "frameworks":{
        "net20":{
            "frameworkAssemblies":{
                "System.Net":""
            }
        },
        "net35":{
            "frameworkAssemblies":{
                "System.Net":""
            }
        },
        "net40":{
            "frameworkAssemblies":{
                "System.Net":""
            }
        },
        "net45":{
            "frameworkAssemblies":{
                "System.Net.Http":"",
                "System.Threading.Tasks":""
            }
        },
        ".NETPortable,Version=v4.5,Profile=Profile259": {
            "buildOptions": {
                "define": [ "PORTABLE" ]
             },
             "frameworkAssemblies":{
                 "mscorlib":"",
                 "System":"",
                 "System.Core":"",
                 "System.Net.Http":""
             }
        },
        "netstandard16":{
            "dependencies":{
                "NETStandard.Library":"1.6.0",
                "System.Net.Http":"4.0.1",
                "System.Threading.Tasks":"4.0.11"
            }
        },
    }
}
```

Observe que os destinos PCL são especiais: eles exigem que você especifique uma definição de build para o compilador reconhecer e especifique todos os assemblies que usar, incluindo `mscorlib`.  

O código-fonte poderia então usar as dependências desta maneira:

```csharp
#if (NET20 || NET35 || NET40 || PORTABLE)
using System.Net;
#else
using System.Net.Http;
using System.Threading.Tasks;
#endif
```

Observe que todos os destinos do .NET Framework e .NET Standard têm nomes reconhecidos pelo compilador:

```
.NET Framework 2.0   --> NET20
.NET Framework 3.5   --> NET35
.NET Framework 4.0   --> NET40
.NET Framework 4.5   --> NET45
.NET Framework 4.5.1 --> NET451
.NET Framework 4.5.2 --> NET452
.NET Framework 4.6   --> NET46
.NET Framework 4.6.1 --> NET461
.NET Framework 4.6.2 --> NET462
.NET Standard 1.0    --> NETSTANDARD1_0
.NET Standard 1.1    --> NETSTANDARD1_1
.NET Standard 1.2    --> NETSTANDARD1_2
.NET Standard 1.3    --> NETSTANDARD1_3
.NET Standard 1.4    --> NETSTANDARD1_4
.NET Standard 1.5    --> NETSTANDARD1_5
.NET Standard 1.6    --> NETSTANDARD1_6
```

Conforme mencionado acima, se você estiver direcionando um PCL, terá que especificar uma definição de build que o compilador entenda.  Não há nenhuma definição padrão que o compilador possa usar.

### <a name="using-projectjson-in-visual-studio"></a>Usando `project.json` no Visual Studio

Você tem duas opções para usar `project.json` no Visual Studio:

1. Um novo tipo de projeto xproj.
2. Um projeto PCL redirecionado que dá suporte ao .NET Standard.

Há diferentes vantagens e desvantagens para cada uma.

#### <a name="when-to-pick-an-xproj-project"></a>Quando escolher um projeto Xproj

O novo sistema de projeto Xproj no Visual Studio utiliza os recursos do modelo de projeto baseado em `project.json` para oferecer dois recursos principais com relação aos tipos de projeto existentes: multiplataformas contínuas com a compilação de vários assemblies e a capacidade de gerar um pacote NuGet diretamente no build.

No entanto, isso vem às custas da falta de certos recursos que você pode usar, como:

- Suporte a F # ou Visual Basic
- Geração de assemblies de satélite com cadeias de caracteres de recurso localizado
- Referenciar diretamente um arquivo `.dll` no sistema de arquivos
- A capacidade de fazer referência a um projeto baseado em csproj no Gerenciador de Referências (porém, há suporte dependendo do arquivo `.dll` diretamente)

Se suas necessidades de projeto são relativamente pequenas e você pode tirar proveito dos novos recursos do xproj, escolha-o como seu sistema de projeto.  Isso pode ser feito no Visual Studio dessa forma:

1. Verifique se que você está usando o Visual Studio 2015 ou posterior.
2. Selecione Aquivo | Novo Projeto.
3. Selecione ".NET Core" em Visual C#.
4. Selecione o modelo de "Biblioteca de Classes (.NET Core)". 

#### <a name="when-to-pick-a-pcl-project"></a>Quando escolher um projeto PCL

Você pode direcionar o .NET Core com o sistema de projeto tradicional no Visual Studio criando uma PCL (Biblioteca de Classes Portátil) e selecionando ".NET Core" na caixa de diálogo de configuração do projeto.  Em seguida, você precisará redirecionar o projeto para que ele seja baseado no .NET Standard:

1. Clique com o botão direito do mouse no arquivo de projeto no Visual Studio e selecione Propriedades.
2. Em Compilar, selecione "Converter para .NET Standard".

Se você tiver necessidades do sistema de projeto mais avançadas, essa deverá ser sua escolha.  Observe que se você quiser aplicar multiplataformas gerando assemblies específicos de plataforma, como com o sistema de projeto `xproj`, será necessário criar um PCL "de isca", conforme descrito em [Como fazer bibliotecas de classes portáteis funcionarem para você](https://blogs.msdn.microsoft.com/dsplaisted/2012/08/27/how-to-make-portable-class-libraries-work-for-you/).

## <a name="retargeting-your-net-framework-code-to-net-framework-462"></a>Redirecionar seu código .NET Framework para o .NET Framework 4.6.2

Se seu código não estiver direcionando para o .NET Framework 4.6.2, será recomendável redirecioná-lo.  Isso garante que você possa usar as alternativas de API mais recentes para casos em que o .NET Standard não dá suporte a APIs existentes.

Faça o seguinte para cada um dos projetos no Visual Studio que você desejar portar:

1. Clique com o botão direito do mouse no projeto e selecione Propriedades
2. Na lista suspensa “Estrutura de Destino”, selecione “.NET Framework 4.6.2”.
3. Recompile seus projetos.

E pronto.  Como seus projetos agora são direcionados para o .NET Framework 4.6.2, você pode usar a versão do .NET Framework como sua base de portabilidade de código.

## <a name="determining-the-portability-of-your-code"></a>Determinando a portabilidade do código

A próxima etapa é executar o ApiPort (Analisador de Portabilidade de API) para gerar um relatório de portabilidade que você pode começar a analisar.

Você precisará conhecer a [ApiPort (ferramenta de Portabilidade de API)](https://github.com/Microsoft/dotnet-apiport/blob/master/docs/HowTo/) e poder gerar relatórios de portabilidade para direcionar o .NET Core.  A maneira como você fará isso provavelmente variará dependendo das suas necessidades e preferências pessoais.  Veja a seguir algumas abordagens diferentes. Você pode acabar combinando as abordagens, dependendo de como seu código será estruturado.

### <a name="dealing-primarily-with-the-compiler"></a>Lidando principalmente com o compilador

Essa abordagem pode ser a melhor para projetos pequenos ou projetos que não usam muitas APIs do .NET Framework.  A abordagem é muito simples:

1. Opcionalmente, execute a ApiPort no seu projeto.
2. Se a ApiPort foi executada, dê uma olhada rápida no relatório.
3. Copie todo o códigos para um novo projeto do .NET Core.
4. Resolva os erros de compilador até ele concluir a compilação, consultando o relatório de portabilidade se necessário.
5. Repita conforme necessário.

Embora essa abordagem seja muito desestruturada, uma abordagem centrada em código pode agilizar a resolução dos problemas, podendo ser a melhor abordagem para bibliotecas ou projetos pequenos.  Um projeto que contém somente os modelos de dados pode ser um candidato ideal aqui.

### <a name="staying-on-the-net-framework-until-portability-issues-are-resolved"></a>Permanecer no .NET Framework até que os problemas de portabilidade sejam resolvidos

Essa abordagem pode ser a melhor se você preferir que o código seja compilado durante todo o processo.  A abordagem é a seguinte:

1. Execute a ApiPort em um projeto.
2. Trate os problemas usando diferentes APIs portáteis.
3. Tome nota das áreas nas quais não foi possível usar uma alternativa direta.
4. Repita as etapas 1 a 3 para todos os projetos que estão passando por portabilidade até ter certeza de que todos estejam prontos para serem copiados em um projeto .NET Core.
5. Copie o código em um novo projeto do .NET Core.
6. Trate os problemas anotados.

Essa abordagem cuidadosa é mais estruturada do que simplesmente tratar os erros do compilador, mas ainda é relativamente focada em código e tem a vantagem de sempre ter código que pode ser compilado.  A maneira de resolver certos problemas que não puderam ser tratados usando apenas outra API pode variar muito.  Você pode achar que precisa para desenvolver um plano mas abrangente para certos projetos, o que é tratado como a próxima abordagem.

### <a name="developing-a-comprehensive-plan-of-attack"></a>Desenvolver um plano de ação abrangente

Essa abordagem pode ser a melhor para projetos maiores e mais complexos, nos quais a reestruturação do código ou recriação de determinadas áreas podem ser necessários para dar suporte ao .NET Core.  A abordagem é a seguinte:

1. Execute a ApiPort em um projeto.
2. Compreenda os pontos do seu código em que cada tipo não portátil está sendo usado e como isso afeta a portabilidade geral.

   a.  Entenda a natureza desses tipos.  Eles são poucos, mas usados com frequência?  Eles são muitos, mas usados com pouca frequência?  Seu uso é concentrado ou eles são distribuído por todo o código?
   
   b. É fácil isolar o código que não é portátil para lidar com ele mais facilmente?
   
   c. Você precisaria refatorar seu código?
   
   d. Para esses tipos não portáteis, há APIs alternativas que realizam a mesma tarefa?  Por exemplo, se você estiver usando a classe `WebClient`, poderá usar a classe `HttpClient` em vez disso.
   
   e. Há diferentes APIs portáteis que você poderia usar para realizar uma tarefa, mesmo se não for uma substituição exata?  Por exemplo, se você estiver usando `XmlSchema` para ajudar a analisar o XML, mas não precisar de descoberta de esquema XML, poderá usar as APIs `System.Linq.Xml` e analisar os dados manualmente.

3. Se você tiver assemblies que são de difícil portabilidade, vale a pena deixá-los no .NET Framework por enquanto?  Esses são alguns pontos a considerar:

   a. Você pode ter alguma funcionalidade na sua biblioteca que é incompatível com o .NET Core por ser muito dependente de funcionalidades específicas do .NET Framework ou do Windows.  Vale a pena abandonar essa funcionalidade por enquanto e lançar uma versão .NET Core da sua biblioteca com menos recursos temporariamente?
   
   b. Uma refatoração ajudaria aqui?
   
4. Seria razoável criar sua própria implementação de uma API do .NET Framework indisponível?

   Você pode considerar copiar, modificar e usar código do [.NET Framework Reference Source](https://github.com/Microsoft/referencesource) em vez disso.  Ele é licenciado sob a [Licença MIT](https://github.com/Microsoft/referencesource/blob/master/LICENSE.txt), portanto, você terá grande liberdade ao fazê-lo.  Basta certificar-se de atribuir seu código devidamente à Microsoft.
   
5. Repita esse processo conforme necessário para os diferentes projetos.
6. Depois de elaborar o plano, execute-o.
 
A fase de análise pode demorar algum tempo dependendo do tamanho da sua base de código.  Dedique tempo a essa fase para compreender profundamente o escopo das mudanças necessárias e como desenvolver um plano pode economizar tempo em longo prazo, especialmente se você tiver uma base de código mais complexa.

Seu plano pode envolver alterações significativas na sua base de código enquanto ainda é direcionado para o .NET Framework 4.6.2, tornando essa uma versão mais estruturada da abordagem anterior.  A maneira de executar o plano dependerá da sua base de código.

### <a name="mixing-approaches"></a>Combinando abordagens

É provável que você combine as abordagens acima para cada projeto.  Você deve fazer o que parece ser ideal para você e para sua base de código.

## <a name="porting-your-tests"></a>Portabilidade dos testes

A melhor maneira de verificar se tudo está funcionando após portar seu código é testá-lo ao portá-lo para o .NET Core.  Para fazer isso, você precisará usar uma estrutura de teste que compilará e executará os testes para .NET Core.  No momento, você tem três opções:

* [xUnit](https://xunit.github.io/)
   - [Introdução](http://xunit.github.io/docs/getting-started-dnx.html)
   - [Ferramenta para converter um projeto MSTest em xUnit](https://github.com/dotnet/codeformatter/tree/master/src/XUnitConverter)
* [NUnit](http://www.nunit.org/)
  - [Introdução](https://github.com/nunit/docs/wiki/Installation)
  - [Postagem no blog sobre a migração de MSTest para NUnit](http://www.florian-rappl.de/News/Page/275/convert-mstest-to-nunit)
* [MSTest](https://msdn.microsoft.com/library/ms243147.aspx)

## <a name="recommended-approach-to-porting"></a>Abordagem recomendada para portabilidade

Finalmente, porte o próprio código.  Por fim, o real esforço de portabilidade dependerá muito de como seu código do .NET Framework está estruturado.  Dito isso, veja essa abordagem recomendada que pode funcionar bem com sua base de código.

Uma boa forma de portar seu código é começar pela "base" da sua biblioteca.  Ela pode ser os modelos de dados ou alguma outra classe e método fundamental que todos os demais elementos usam direta ou indiretamente.

1. Porte o projeto de teste da camada da sua biblioteca que está sendo portada no momento.
2. Copie a "base" da sua biblioteca para um novo projeto do .NET Core e selecione a versão do .NET Standard à qual você deseja dar suporte.
3. Faça as alterações necessárias para que o código seja compilado.  Uma boa parte disso pode exigir a adição de dependências de pacotes NuGet para o arquivo `project.json`.
4. Execute testes e faça os ajustes necessários.
5. Selecione a próxima camada de código para ser portada e repita as etapas 2 e 3.

Se você mover metodicamente para fora da base da sua biblioteca e testar cada camada conforme necessário, a portabilidade será um processo sistemático no qual os problemas ficam isolados a uma camada de código por vez.



<!--HONumber=Nov16_HO3-->


