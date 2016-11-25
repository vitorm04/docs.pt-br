---
title: Modelo de extensibilidade da CLI do .NET Core
description: Modelo de extensibilidade da CLI do .NET Core
keywords: CLI, extensibilidade, comandos personalizados, .NET Core
author: mairaw
manager: wpickett
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 1bebd25a-120f-48d3-8c25-c89965afcbcd
translationtype: Human Translation
ms.sourcegitcommit: aeb199a9aeb1584570ad2a2942e2f22c75a59616
ms.openlocfilehash: 4223f296224c9b62c88b72f0f643c8b8b6fc9f6b

---

# <a name="net-core-cli-extensibility-model"></a>Modelo de extensibilidade da CLI do .NET Core 

## <a name="overview"></a>Visão Geral
Este documento abordará as principais maneiras de estender as ferramentas da CLI e explica os cenários que orientam a cada uma delas. Ele descreverá como consumir as ferramentas, bem como fornecerá breves anotações sobre como compilar ambos os tipos de ferramentas. 

## <a name="how-to-extend-cli-tools"></a>Como estender as ferramentas da CLI
As ferramentas da CLI podem ser estendidas de duas maneiras:

1. Por meio de pacotes NuGet por projeto
2. Por meio do PATH do sistema

Os dois mecanismos de extensibilidade descritos acima não são exclusivos; você pode usar ambos ou apenas um deles. Qual deles escolher depende muito da meta que você está tentando alcançar com a extensão.

## <a name="per-project-based-extensibility"></a>Extensibilidade por projeto
Ferramentas por projeto são [aplicativos de console portátil](../deploying/index.md) que são distribuídos como pacotes NuGet. Ferramentas só estão disponíveis no contexto do projeto que faz referência a eles e para os quais eles são restaurados; a invocação fora do contexto do projeto (por exemplo, fora do diretório que contém o projeto) falhará, pois o comando não poderá ser encontrado.

Essas ferramentas são perfeitas para criar servidores, desde que nada fora do `project.json` seja necessário. O processo de build executa a restauração para o projeto compilado e as ferramentas disponíveis. Projetos de linguagem, como F#, também estão nesta categoria, afinal, cada projeto só pode ser escrito em um idioma específico. 

Por fim, esse modelo de extensibilidade dá suporte à criação de ferramentas que precisam acessar a saída da compilação do projeto. Por exemplo, diversas ferramentas de exibição Razor em aplicativos [ASP.NET](https://www.asp.net/) MVC se enquadram nesta categoria. 

### <a name="consuming-per-project-tools"></a>Consumir ferramentas por projeto
Consumir essas ferramentas requer que você adicione um nó `tools` ao `project.json`. Dentro do nó `tools`, você referenciar o pacote no qual a ferramenta reside. Após executar `dotnet restore`, a ferramenta e suas dependências são restauradas. 

Para ferramentas que precisam carregar a saída do build do projeto para execução, geralmente há outra dependência listada nas dependências regulares no arquivo de projeto. Isso significa que as ferramentas que carregam o código do projeto têm dois componentes: 

1. O invocador principal “ferramentas”
2. Qualquer número de outras ferramentas que contém a lógica para trabalhar com 

Por que as duas coisas? Ferramentas que precisam carregar a saída de build de um projeto precisam ter um gráfico de dependência unificado com o projeto no qual estão trabalhando. Ao adicionar o bit de dependência, permitimos que o NuGet resolva essas dependências como um gráfico unificado. O invocador existe porque ele precisa entender sobre o local, bem como sobre as estruturas da ferramenta de dependência. O invocador pode aceitar todos os argumentos de redirecionamento (`-c`, `-o`, `-b`) que o usuário especifica e localizar a ferramenta de dependência. Ele também pode implementar qualquer política para casos em que existem várias ferramentas de dependência para diversas estruturas (ou seja, ele executa todas elas ou apenas uma) Em geral, a lógica pode ser compartilhada entre essas duas ferramentas do modo que for necessário. 

Vamos examinar um exemplo de como adicionar uma ferramenta única simples a um projeto simples. Dado um exemplo de comando chamado `dotnet-api-search` que permite que você pesquise os pacotes NuGet para a API especificada, veja este arquivo do aplicativo de console `project.json` que usa essa ferramenta:

```json
{
    "version": "1.0.0",
    "compilationOptions": {
        "emitEntryPoint": true
    },
    "dependencies": {
        "Microsoft.NETCore.App": {
            "type": "platform",
            "version": "1.0.0"
        }
    },
    "tools": {
        "dotnet-api-search": {
            "version": "1.0.0",
            "imports": ["dnxcore50"]
        }
    },
    "frameworks": {
        "netcoreapp1.0": {}
    }
}
```

O nó `tools` é estruturado de forma semelhante ao nó `dependencies`. Ele precisa no mínimo da ID do pacote que contém a ferramenta e sua versão. No exemplo acima, podemos ver que há outra instrução, a `imports`. Isso influencia o processo de restauração da ferramenta e especifica que ela também é compatível, além de quaisquer estruturas de destino que as ferramentas tenham, com o destino `dnxcore50`. Para obter mais informações, você pode consultar a [referência project.json](project-json.md).

### <a name="building-tools"></a>Compilando ferramentas
Como mencionado anteriormente, ferramentas são apenas aplicativos de console portáteis. Você poderia compilar uma delas da mesma maneira que qualquer aplicativo de console. Depois de compilá-la, você usaria o comando [`dotnet pack`](dotnet-pack.md) para criar um pacote NuGet (nupkg) que contém o código, as informações sobre suas dependências e assim por diante. O nome do pacote pode ser o que o autor desejar, mas o aplicativo dentro dele, a real ferramenta binária, precisa estar em conformidade com a convenção de `dotnet-<command>` para que `dotnet` consiga invocá-lo. 

Como ferramentas são aplicativos portáteis, o usuário que a consume precisa ter a versão das bibliotecas do .NET Core para as quais a biblioteca foi criada para executar a ferramenta. Qualquer outra dependência que a ferramenta usa e que não está contida em bibliotecas do .NET Core é restaurada e colocada no cache do NuGet. Toda a ferramenta é, portanto, executada usando os assemblies de bibliotecas .NET Core, bem como assemblies do cache do NuGet. 

Esses tipos de ferramentas têm um gráfico de dependência completamente separado do gráfico de dependência do projeto que as utiliza. O processo de restauração restaurará primeiro as dependências do projeto e, em seguida, cada uma das ferramentas e suas dependências. 

Você pode encontrar exemplos mais sofisticados e diferentes combinações disso no [repositório da CLI do .NET Core](https://github.com/dotnet/cli/tree/rel/1.0.0-preview2/TestAssets/TestProjects). Você também pode ver a [implementação das ferramentas utilizadas](https://github.com/dotnet/cli/tree/rel/1.0.0-preview2/TestAssets/TestPackages) no mesmo repositório. 

Compilar ferramentas que carregam as saídas de build do projeto para a execução é um processo ligeiramente diferente. Como mencionado, há dois componentes para esses tipos de ferramentas:

1. Uma ferramenta de dispatcher que o usuário invoca
2. Uma dependência específica de estrutura que contém a lógica sobre como localizar as saídas de build e o que fazer com elas

Um exemplo perfeito disso são os comandos da [EF (Entity Framework)](https://github.com/aspnet/EntityFramework), bem como o comando [`dotnet test`](dotnet-test.md). Em ambos os casos, há uma ferramenta que é referenciada no nó `tools` do `project.json` e é o dispatcher principal. O usuário invoca essa ferramenta na linha de comando. A segunda parte do quebra-cabeça é a dependência que é determinada nas dependências principais do projeto (na raiz ou naquelas específicas de estrutura). Este pacote contém a lógica real da ferramenta. O pacote é uma dependência normal, portanto, ele será restaurado como parte do processo de restauração para o projeto. 

Ao contrário do tipo anterior de ferramentas, na verdade, essas fazem parte do gráfico do projeto que as consome. Isso ocorre porque elas precisam de acesso ao código do projeto e, potencialmente, a todas as suas dependências. Por exemplo, as ferramentas do EF precisam disso porque é necessário verificar os assemblies para encontrar o código exigido, como as migrações.  

Outro motivo pelo qual essa solução dupla existe é para permitir um modelo de invocação mais limpo. A maioria dos comandos da CLI que removem determinados artefatos do disco (por exemplo, `dotnet build`, `dotnet publish`) permitem que os usuários redirecionem as saídas para um caminho diferente usando o argumento `--output`, `--build-base-path` ou `--configuration`. Por exemplo, para ferramentas do EF encontrarem a saída de build do seu projeto, você precisaria fornecer os mesmos argumentos com os mesmos valores para *ambos* o driver `dotnet` e para o comando `ef`. Com o modelo de invocação, os usuários passam argumentos para a ferramenta de dispatcher que pode usá-lo para localizar o binário necessário que contém a lógica nos diretórios de saída. 

Um bom exemplo dessa abordagem pode ser encontrado no [repositório da CLI do .NET Core](https://github.com/dotnet/cli):

* [Arquivo project.json de exemplo](https://github.com/dotnet/cli/blob/rel/1.0.0-preview2/TestAssets/DesktopTestProjects/AppWithDirectDependencyDesktopAndPortable/project.json)
* [Implementação do dispatcher](https://github.com/dotnet/cli/tree/rel/1.0.0-preview2/TestAssets/TestPackages/dotnet-dependency-tool-invoker)
* [Implementação da dependência específica de estrutura](https://github.com/dotnet/cli/tree/rel/1.0.0-preview2/TestAssets/TestPackages/dotnet-desktop-and-portable)


### <a name="path-based-extensibility"></a>Extensibilidade baseada em PATH
A extensibilidade do PATH geralmente é usada para computadores de desenvolvimento em que você precisa de uma ferramenta que abrange conceitualmente mais de um único projeto. A principal desvantagem desse mecanismo de extensões é que ele está vinculado ao computador no qual a ferramenta existe. Se você precisar dela em outro computador, precisará implantá-la.

Esse padrão de extensibilidade do conjunto de ferramentas da CLI é muito simples. Conforme abordado na [Visão geral da CLI do .NET Core](index.md), o driver `dotnet` pode executar qualquer comando nomeado segundo a convenção `dotnet-<command>`. A lógica de resolução padrão primeiro investigará os vários locais e finalmente recairá sobre o PATH do sistema. Se o comando solicitado existir no PATH do sistema e for um binário que pode ser invocado, o driver `dotnet` o invocará. 

O binário pode ser praticamente qualquer coisa que o sistema operacional puder executar. Em sistemas Unix, isso significa tudo que tiver o conjunto de bits execute por meio de `chmod +x`. No Windows, isso significa qualquer coisa que o Windows souber executar. 

Por exemplo, vejamos uma implementação muito simples de um comando `dotnet clean`. Usaremos o `bash` para implementar esse comando. O comando simplesmente excluirá os diretório `bin/` e `obj/` no diretório atual. Se o argumento `--lock` for passado para ele, o arquivo `project.lock.json` também será excluído. Todo o comando é fornecido abaixo. 

```bash
#!/bin/bash

# Delete the bin and obj dirs
rm -rf bin/ obj/

LOCK_FILE=$1
if [[ "$LOCK_FILE" = "--lock" ]]; then
    rm project.lock.json
fi


echo "Cleaning complete..."
```

No macOS, podemos eliminar esse script como `dotnet-clean` e definir o bit executável com `chmod +x dotnet-clean`. Podemos então criar um link simbólico para ele em `/usr/local/bin` usando o comando `ln -s dotnet-clean /usr/local/bin/`. Isso tornará possível invocar o comando limpo usando a sintaxe `dotnet clean`. Você pode testar isso criando um aplicativo, executando o `dotnet build` nele e então executando `dotnet clean`. 

## <a name="conclusion"></a>Conclusão
As ferramentas da CLI do .NET Core permitem dois pontos de extensibilidade principais. As ferramentas por projeto estão contidas no contexto do projeto, mas permitem uma fácil instalação por meio da restauração. Ferramentas baseadas em PATH são boas para ferramentas gerais de vários projetos que são usadas em um único computador. 



<!--HONumber=Nov16_HO3-->


