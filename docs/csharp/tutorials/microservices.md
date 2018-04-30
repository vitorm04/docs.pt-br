---
title: Microsserviços hospedados no Docker - C#
description: Aprenda a criar serviços asp.net core que são executados em contêineres do Docker
keywords: .NET, .NET Core, Docker, C#, ASP.NET, Microsserviço
author: BillWagner
ms.author: wiwagn
ms.date: 02/03/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-docker
ms.devlang: csharp
ms.assetid: 87e93838-a363-4813-b859-7356023d98ed
ms.openlocfilehash: 253b622618ef62c28ac13a287c34b9d9049dd066
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="microservices-hosted-in-docker"></a>Microsserviços hospedados no Docker

Este tutorial detalha as tarefas necessárias para compilar e implantar um microsserviço ASP.NET Core em um contêiner do Docker. Durante este tutorial, você aprenderá:

* Como gerar um aplicativo ASP.NET Core usando Yeoman
* Como criar um ambiente de desenvolvimento do Docker
* Como compilar uma imagem do Docker com base em uma imagem existente.
* Como implantar seu serviço em um contêiner do Docker.

Ao longo do caminho, você também verá alguns recursos da linguagem C#:

* Como converter objetos C# em cargas JSON.
* Como compilar Objetos de Transferência de Dados imutáveis
* Como processar solicitações HTTP de entrada e gerar a resposta HTTP
* Como trabalhar com tipos de valor anulável

Você pode [exibir ou baixar o aplicativo de exemplo](https://github.com/dotnet/samples/tree/master/csharp/getting-started/WeatherMicroservice) deste tópico. Para obter instruções de download, consulte [Exemplos e tutoriais](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

### <a name="why-docker"></a>Por que o Docker?

O Docker facilita a criação de imagens de máquina padrão para hospedar seus serviços em um data center ou na nuvem pública. O Docker permite que você configure a imagem e replique-a conforme o necessário para dimensionar a instalação de seu aplicativo.

Todo o código neste tutorial funcionará em qualquer ambiente .NET Core.
As tarefas adicionais para uma instalação do Docker funcionarão para um aplicativo ASP.NET Core. 

## <a name="prerequisites"></a>Pré-requisitos
Você precisará configurar seu computador para executar o .NET Core. Você encontrará as instruções de instalação na página do [.NET Core](https://www.microsoft.com/net/core).
Você pode executar esse aplicativo no Windows, Ubuntu Linux, macOS ou em um contêiner do Docker. Será necessário instalar o editor de código de sua preferência. As descrições a seguir usam o [Visual Studio Code](https://code.visualstudio.com/), que é uma software livre, no editor de plataforma. No entanto, você pode usar quaisquer ferramentas que esteja familiarizado.

Também precisará instalar o mecanismo Docker. Consulte a [página Instalação de Docker](http://www.docker.com/products/docker) para obter instruções para sua plataforma.
O Docker pode ser instalado em muitas distribuições do Linux, macOS ou Windows. A página mencionada acima contém seções para cada uma das instalações disponíveis.

A maioria das instalações dos componentes é realizada por um gerenciador de pacotes. Se o gerenciador de pacotes do node.js `npm` estiver instalado, ignore esta etapa. Caso contrário, instale o NodeJs mais recente do [nodejs.org](https://nodejs.org), que instalará o gerenciador de pacotes npm. 

Aqui, você precisará instalar uma série de ferramentas de linha de comando que oferecem suporte ao desenvolvimento em ASP.NET Core. Os modelos de linha de comando usam Yeoman, Bower, Grunt e Gulp. Se você os tiver instalado, ótimo, caso contrário, digite o seguinte em seu shell favorito:

`npm install -g yo bower grunt-cli gulp`

A opção `-g` indica que é uma instalação global, e essas ferramentas estão disponíveis em todo o sistema. (Uma instalação local define o escopo do pacote para um único projeto). Após a instalação dessas ferramentas básicas, você precisará instalar os geradores de modelo ASP.NET do Yeoman:

`npm install -g generator-aspnet`

## <a name="create-the-application"></a>Criar o aplicativo

Agora que você instalou todas as ferramentas, crie um novo aplicativo ASP.NET Core. Para usar o gerador de linha de comando, execute o seguinte comando yeoman no shell de sua preferência:

`yo aspnet`

Esse comando solicita a seleção do Tipo de aplicativo que você deseja criar. Para este microsserviço, convém ter o aplicativo Web mais simples e mais leve possível, portanto, selecione 'Aplicativo Web Vazio'. O modelo solicitará um nome. Selecione 'WeatherMicroservice'. 

O modelo cria oito arquivos para você:

* Um .gitignore, personalizado para aplicativos ASP.NET Core.
* Um arquivo Startup.cs. Contém a base do aplicativo.
* Um arquivo Program.cs. Contém o ponto de entrada do aplicativo.
* Um arquivo WeatherMicroservice.csproj. Esse é o arquivo de compilação do aplicativo.
* Um dockerfile. Esse script cria uma imagem do Docker para o aplicativo.
* Um README.md. Contém links para outros recursos do ASP.NET Core.
* Um arquivo web.config. Contém informações básicas de configuração.
* Um arquivo runtimeconfig.template.json. Contém as configurações de depuração usadas pelos IDEs.

Agora você pode executar o aplicativo gerado pelo modelo. Isso é feito usando uma série de ferramentas na linha de comando. O comando `dotnet` executa as ferramentas necessárias para desenvolvimento em .NET. Cada verbo executa um comando diferente

A primeira etapa é restaurar todas as dependências:

```console
dotnet restore
```

A restauração do dotnet usa o gerenciador de pacotes do NuGet para instalar todos os pacotes necessários no diretório do aplicativo. Ele também gera um arquivo project.json.lock. Esse arquivo contém informações sobre cada pacote referenciado. Depois de restaurar todas as dependências, compile o aplicativo:

```console
dotnet build
```
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

E, depois de compilar o aplicativo, execute-o na linha de comando:

```console
dotnet run
```

A configuração padrão escuta `http://localhost:5000`. Abra um navegador, navegue até a página e veja uma mensagem "Hello World!" .

### <a name="anatomy-of-an-aspnet-core-application"></a>Anatomia de um aplicativo ASP.NET Core

Agora que você criou o aplicativo, vamos analisar como essa funcionalidade é implementada. Há dois dos arquivos gerados que são particularmente interessantes neste ponto: project.json e Startup.cs. 

Project.json contém informações sobre o projeto. Os dois nós com os quais você trabalhará com frequência são 'dependências' e 'estruturas'. O nó dependências lista todos os pacotes necessários para este aplicativo.
No momento, este é um nó pequeno que precisa apenas dos pacotes que executam o servidor Web.

O nó 'estruturas' especifica as versões e as configurações da estrutura .NET que executará esse aplicativo.

O aplicativo é implementado em Startup.cs. Esse arquivo contém a classe de inicialização.

Os dois métodos são chamados pela infraestrutura do ASP.NET Core para configurar e executar o aplicativo. O método `ConfigureServices` descreve os serviços que são necessários para este aplicativo. Você está compilando um microsserviço enxuto, portanto, não precisa configurar dependências. O método `Configure` configura os manipuladores para solicitações HTTP de entrada. O modelo gera um manipulador simples que responde a qualquer solicitação com o texto "Hello World!".

## <a name="build-a-microservice"></a>Criar um microsserviço

O serviço criado fornecerá relatórios meteorológicos de qualquer lugar do mundo. Em um aplicativo de produção, você chamaria algum serviço para obter os dados meteorológicos. Em nosso exemplo, geraremos uma previsão do tempo aleatória. 

Há várias tarefas que você precisará executar para implementar nosso serviço meteorológico aleatório:

* Analise a solicitação de entrada para ler a latitude e a longitude.
* Gere alguns dados de previsão aleatórios.
* Converta esses dados de previsão aleatórios de objetos C# para pacotes JSON.
* Defina o cabeçalho de resposta para indicar que o serviço retorna JSON.
* Escreva a resposta.

As próximas seções orientarão você por cada uma dessas etapas.

### <a name="parsing-the-query-string"></a>Análise da cadeia de caracteres de consulta.

Você começará pela análise de cadeia de caracteres de consulta. O serviço aceitará os argumentos 'lat' e 'long' na cadeia de consulta nesta forma:

`http://localhost:5000/?lat=-35.55&long=-12.35`  

Todas as alterações que você precisa fazer estão na expressão lambda definida como o argumento `app.Run` em sua classe de inicialização.

O argumento na expressão lambda é o `HttpContext` para a solicitação. Uma de suas propriedades é o objeto `Request`. O objeto `Request` tem uma propriedade `Query` que contém um dicionário com todos os valores na cadeia de consulta da solicitação. A primeira adição serve para encontrar os valores de latitude e longitude:

[!code-csharp[ReadQueryString](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#ReadQueryString "read variables from the query string")]

Os valores de dicionário de Consulta são do tipo `StringValue`. Esse tipo pode conter uma coleção de cadeias de caracteres. Para o serviço meteorológico, cada valor é uma cadeia de caracteres única. É por isso que há a chamada para `FirstOrDefault()` no código acima. 

Em seguida, você precisa converter as cadeias de caracteres em doubles. O método que você usará para converter a cadeia de caracteres em um double é `double.TryParse()`:

```csharp
bool TryParse(string s, out double result);
```

Esse método utiliza parâmetros C# para indicar se a cadeia de caracteres de entrada pode ser convertida em um double. Se a cadeia de caracteres for uma representação válida de um double, o método retornará true, e o argumento `result` conterá o valor. Se a cadeia de caracteres não representar um double válida, o método retornará false.

Adapte essa API com o uso de um *método de extensão* que retorna um *double anulável*. O *tipo de valor anulável* é um tipo que representa algum tipo de valor e também pode apresentar um valor ausente ou nulo. Um tipo que permite valor nulo é representado por meio do acréscimo do caractere `?` à declaração de tipo. 

Métodos de extensão são métodos definidos como estáticos, mas ao adicionar o modificador `this` no primeiro parâmetro é possível chamá-los como se fossem membros dessa classe. Os métodos de extensão só podem ser definidos em classes estáticas. Confira aqui a definição da classe que contém o método de extensão para análise:

[!code-csharp[TryParseExtension](../../../samples/csharp/getting-started/WeatherMicroservice/Extensions.cs#TryParseExtension "try parse to a nullable")]

A expressão `default(double?)` retorna o valor padrão para o tipo `double?`. O valor padrão é o valor nulo (ou ausente).

Use esse método de extensão para converter os argumentos da cadeia de caracteres de consulta no tipo double:

[!code-csharp[UseTryParse](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#UseTryParse "Use the try parse extension method")]

Para testar o código de análise com facilidade, atualize a resposta para incluir os valores dos argumentos:

[!code-csharp[WriteResponse](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#WriteResponse "Write the output response")]

Neste ponto, você pode executar o aplicativo Web e verificar se o código de análise está funcionando. Adicione valores à solicitação da Web em um navegador e você verá os resultados atualizados.

### <a name="build-a-random-weather-forecast"></a>Compilar uma previsão do tempo aleatória

A próxima tarefa é compilar uma previsão do tempo aleatória. Vamos começar com um contêiner de dados com os valores que você gostaria para uma previsão do tempo:

```csharp
public class WeatherReport
{
    private static readonly string[] PossibleConditions = new string[]
    {
        "Sunny",
        "Mostly Sunny",
        "Partly Sunny",
        "Partly Cloudy",
        "Mostly Cloudy",
        "Rain"
    };

    public int HiTemperature { get; }
    public int LoTemperature { get; }
    public int AverageWindSpeed { get; }
    public string Conditions { get; }
}
```

Em seguida, compile um construtor que define aleatoriamente os valores. Este construtor usa os valores de latitude e longitude para propagar o Gerador de número aleatório. Isso significa que a previsão para o mesmo local é a mesma. Se você alterar os argumentos para a latitude e longitude, obterá uma previsão diferente (porque começou com uma propagação diferente.)

[!code-csharp[WeatherReportConstructor](../../../samples/csharp/getting-started/WeatherMicroservice/WeatherReport.cs#WeatherReportConstructor "Weather Report Constructor")]

Agora você pode gerar a previsão de cinco dias em seu método de resposta:

[!code-csharp[GenerateRandomReport](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#GenerateRandomReport "Generate a random weather report")]

### <a name="build-the-json-response"></a>Compile a resposta JSON.

A tarefa de código final no servidor é converter a matriz WeatherReport em um pacote JSON e enviá-lo de volta ao cliente. Vamos começar criando o pacote JSON. Você adicionará o Serializador de JSON da NewtonSoft à lista de dependências. Faça isso usando a CLI `dotnet`:

```
dotnet add package Newtonsoft.Json
```

Em seguida, use a classe `JsonConvert` para gravar o objeto em uma cadeia de caracteres:

[!code-csharp[ConvertToJson](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#ConvertToJSON "Convert objects to JSON")]

O código acima converte o objeto de previsão (uma lista de `WeatherForecast` objetos) em um pacote JSON. Após a construção do pacote de resposta, defina o tipo de conteúdo como `application/json` e grave a cadeia de caracteres.

Agora, o aplicativo é executado e retorna previsões aleatórias.

## <a name="build-a-docker-image"></a>Criar uma imagem do Docker

Nossa tarefa final é executar o aplicativo no Docker. Vamos criar um contêiner do Docker que executa uma imagem do Docker que representa nosso aplicativo.

Uma ***imagem do Docker*** é um arquivo que define o ambiente para execução do aplicativo.

Um ***Contêiner do Docker*** representa uma instância em execução de uma imagem do Docker.

Por analogia, você pode considerar a *imagem do Docker* como uma *classe* e o *Contêiner do Docker* como um objeto ou uma instância dessa classe.  

O Dockerfile criado pelo modelo ASP.NET servirá para nossos objetivos. Vamos analisar o conteúdo.

A primeira linha especifica a imagem de origem:

```
FROM microsoft/dotnet:1.1-sdk-msbuild
```

O Docker permite que você configure uma imagem de máquina com base em um modelo de origem. Isso significa que não é necessário fornecer todos os parâmetros da máquina ao iniciar, você só precisa fornecer as alterações. As alterações feitas aqui servem para incluir nosso aplicativo.

Neste primeiro exemplo, usaremos a versão `1.1-sdk-msbuild` da imagem do dotnet. Essa é a maneira mais fácil de criar um ambiente funcional do Docker. Essa imagem inclui o tempo de execução do dotnet core e o SDK do dotnet. Isso facilita o início e a compilação, mas cria uma imagem maior.

As próximas cinco linhas configuram e compilam seu aplicativo:

```
WORKDIR /app

# copy csproj and restore as distinct layers

COPY WeatherMicroservice.csproj .
RUN dotnet restore 

# copy and build everything else

COPY . .

# RUN dotnet restore
RUN dotnet publish -c Release -o out
```

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Isso copiará o arquivo de projeto do diretório atual para a VM do Docker e restaurará todos os pacotes. Usar a CLI do dotnet significa que a imagem do Docker deve incluir o SDK do .NET Core. Depois disso, o restante de seu aplicativo será copiado e o comando publish do dotnet compilará e empacotará seu aplicativo.

A linha final do arquivo executa o aplicativo:

```
ENTRYPOINT ["dotnet", "out/WeatherMicroservice.dll", "--server.urls", "http://0.0.0.0:5000"]
```

Essa porta configurada é referenciada no argumento `--server.urls` para `dotnet` na última linha do Dockerfile. O comando `ENTRYPOINT` informa ao Docker qual comando e quais opções de linha de comando iniciarão o serviço. 

## <a name="building-and-running-the-image-in-a-container"></a>Crie e execute a imagem em um contêiner.

Vamos compilar uma imagem e executar o serviço dentro de um contêiner do Docker. Você não quer que todos os arquivos de seu diretório local sejam copiados na imagem. Em vez disso, compile o aplicativo no contêiner. Você criará um arquivo `.dockerignore` para especificar os diretórios que não são copiados na imagem. Você não que copiar nenhum ativo de compilação. Especifique os diretórios de compilação e publicação no arquivo `.dockerignore`:

```
bin/*
obj/*
out/*
```

Crie a imagem usando o comando `docker build`. Execute o seguinte comando no diretório que contém seu código.

```console
docker build -t weather-microservice .
```

Esse comando compila a imagem do contêiner com base em todas as informações de seu Dockerfile. O argumento `-t` fornece uma marca, ou nome, para essa imagem de contêiner. Na linha de comando acima, a marca usada para o contêiner do Docker é `weather-microservice`. Quando esse comando for concluído, você terá um contêiner pronto para executar seu novo serviço. 

Execute o seguinte comando para iniciar o contêiner e também o serviço:

```console
docker run -d -p 80:5000 --name hello-docker weather-microservice
```

A opção `-d` representa a execução do contêiner desanexado do terminal atual. Isso significa que você não verá a saída do comando em seu terminal. A opção `-p` indica o mapeamento de porta entre o serviço e o host. Aqui ela informa que qualquer solicitação de entrada na porta 80 deve ser encaminhada para a porta 5000 no contêiner. 5000 corresponde à porta na qual o serviço está escutando a partir dos argumentos de linha de comando especificados no Dockerfile acima. O argumento `--name` nomeia o contêiner em execução. É um nome conveniente que você pode usar para trabalhar com esse contêiner. 

É possível ver se a imagem está sendo executada verificando o comando:

```console
docker ps
```

Se o contêiner estiver em execução, você verá uma linha que o lista nos processos em execução. (Pode ser o único).

Teste seu serviço abrindo um navegador, navegando até localhost e especificando uma latitude e longitude:

```
http://localhost/?lat=35.5&long=40.75
```

## <a name="attaching-to-a-running-container"></a>Anexar um contêiner em execução

Quando você executa o serviço em uma janela de comando, pode ver informações de diagnóstico impressas para cada solicitação. Você não vê essas informações quando o contêiner está sendo executado no modo desconectado. O comando attach do Docker permite que você anexe a um contêiner em execução para que você possa ver as informações de log.  Execute este comando a partir de uma janela de comando:

```console
docker attach --sig-proxy=false hello-docker
```

O argumento `--sig-proxy=false` significa que os comandos `Ctrl-C` não são enviados ao processo do contêiner, mas, em vez disso, interrompem o comando `docker attach`. O argumento final é o nome fornecido ao contêiner no comando `docker run`. 

> [!NOTE]
> Use também a ID de contêiner atribuída pelo Docker para se referir a qualquer contêiner. Se você não tiver especificado um nome para seu contêiner no `docker run`, use a id do contêiner.

Abra um navegador e navegue até seu serviço. Você verá as mensagens de diagnóstico nas janelas de comando do contêiner anexado em execução.

Pressione `Ctrl-C` para interromper o processo de conexão.

Quando você terminar de trabalhar com seu contêiner, interrompa-o:

```console
docker stop hello-docker
```

O contêiner e a imagem ainda estão disponíveis para a reinicialização.  Se você quiser remover o contêiner do seu computador, use este comando:

```console
docker rm hello-docker
```

Se você quiser remover imagens não usadas do seu computador, use este comando:

```console
docker rmi weather-microservice
```

## <a name="conclusion"></a>Conclusão 

Neste tutorial, você criou um microsserviço do ASP.NET Core e adicionou alguns recursos simples.

Você criou uma imagem de contêiner do Docker para o serviço e executou o contêiner no computador. Você anexou uma janela de terminal ao serviço e viu as mensagens de diagnóstico de seu serviço.

Durante o tutorial, você viu vários recursos da linguagem C# em ação.
