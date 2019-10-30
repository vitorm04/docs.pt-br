---
title: Criar com tipos de referência que permitem valor nulo
description: Este tutorial avançado fornece uma introdução aos tipos de referência que permitem valor nulo. Você aprenderá a expressar sua intenção de design quando os valores de referência puderem ser nulos e ter o compilador obrigatório quando eles não puderem ser nulos.
ms.date: 02/19/2019
ms.technology: csharp-null-safety
ms.custom: mvc
ms.openlocfilehash: 9cb9ac1b292e61d6a8a5f84be29a6a6c323725fc
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039681"
---
# <a name="tutorial-migrate-existing-code-with-nullable-reference-types"></a>Tutorial: migrar código existente com tipos de referência anuláveis

O C# 8 introduz **tipos de referência que permitem valor nulo** que complementam os tipos de referência da mesma maneira que os tipos de valor que permitem valor nulo complementam os tipos de valor. Para declarar que uma variável é um **tipo de referência que permite valor nulo**, anexe um `?` ao tipo. Por exemplo, `string?` representa uma `string` que permite valor nulo. Você pode usar esses novos tipos para expressar mais claramente sua intenção de design: algumas variáveis *devem sempre ter um valor*, outras *podem ter um valor* ausente. Quaisquer variáveis existentes de um tipo de referência seriam interpretadas como um tipo de referência não anulável. 

Neste tutorial, você aprenderá a:

> [!div class="checklist"]
>
> - Habilitar verificações de referência nula enquanto trabalha com o código.
> - Diagnosticar e corrigir avisos diferentes relacionados a valores nulos.
> - Gerenciar a interface entre contextos habilitados para anulável e desabilitados para anulável.
> - Controlar contextos de anotação anuláveis.

## <a name="prerequisites"></a>Prerequisites

Você precisará configurar seu computador para executar o .NET Core, incluindo o C# compilador 8,0. O C# compilador 8 está disponível a partir do [Visual Studio 2019 versão 16,3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) ou do [SDK do .NET Core 3,0](https://dotnet.microsoft.com/download).

Este tutorial pressupõe que você esteja familiarizado com o C# e .NET, incluindo o Visual Studio ou a CLI do .NET Core.

## <a name="explore-the-sample-application"></a>Explorar o aplicativo de exemplo

O aplicativo de exemplo que você migrará é aplicativo Web leitor de feed RSS. Ele lê de um único feed RSS e exibe resumos para os artigos mais recentes. Você pode clicar em qualquer um dos artigos para visitar o site. O aplicativo é relativamente novo, mas foi escrito antes da disponibilização de tipos de referência anuláveis. As decisões de design sobre o aplicativo representam princípios sólidos, mas não aproveitam esse recurso importante de linguagem.

O aplicativo de exemplo inclui uma biblioteca de teste de unidade que valida a funcionalidade principal do aplicativo. Esse projeto facilitará a atualização com segurança, caso você altere qualquer implementação com base nos avisos gerados. Faça o download do código inicial no repositório [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/nullable-reference-migration/start) do GitHub.

Sua meta ao migrar um projeto deve ser aproveitar os novos recursos de linguagem para poder expressar claramente sua intenção sobre a nulidade de variáveis, e fazer isso de forma que o compilador não gere avisos quando o contexto de anotação anulável e o contexto de aviso anulável estiverem definidos como `enabled`.

## <a name="upgrade-the-projects-to-c-8"></a>Atualizar os projetos para C# 8

Primeiro, determine o escopo da tarefa de migração. Comece atualizando o projeto para C# 8.0 (ou mais recente). Adicione o elemento `LangVersion` aos dois arquivos csproj, para o projeto da Web e o projeto de teste de unidade:

```xml
<LangVersion>8.0</LangVersion>
```

A atualização da versão da linguagem seleciona C# 8.0, mas não habilita o contexto de anotação anulável ou o contexto de aviso anulável. Recompile o projeto para garantir que ocorra sem avisos.

Em seguida, ative o contexto de anotação anulável e veja quantos avisos são gerados. Adicione o seguinte elemento aos dois arquivos csproj na solução, diretamente abaixo do elemento `LangVersion`:

```xml
<Nullable>enable</Nullable>
```

Faça uma compilação de teste e observe a lista de avisos. Neste aplicativo pequeno, o compilador gera cinco avisos. Provavelmente, você deixaria o contexto de anotação anulável habilitado e iniciaria a correção de avisos de todo o projeto.

Essa estratégia funciona apenas para projetos menores. Para os projetos maiores, o número de avisos gerados com a habilitação do contexto de anotação anulável em toda a base de código dificulta a correção sistemática dos avisos. Para projetos corporativos maiores, convém migrar um projeto de cada vez. Em cada projeto, migre uma classe ou arquivo por vez.

## <a name="warnings-help-discover-original-design-intent"></a>Os avisos ajudam a descobrir a intenção do design original

Há duas classes que geram vários avisos. Comece com a classe `NewsStoryViewModel`. Remova o elemento `Nullable` dos arquivos csproj para que você possa limitar o escopo dos avisos para as seções do código com as quais você está trabalhando. Abra o arquivo *NewsStoryViewModel.cs* e adicione as seguintes diretivas para habilitar o contexto de anotação anulável para `NewsStoryViewModel` e restaure-a seguindo a definição dessa classe:

```csharp
#nullable enable
public class NewsStoryViewModel
{
    public DateTimeOffset Published { get; set; }
    public string Title { get; set; }
    public string Uri { get; set; }
}
#nullable restore
```

Essas duas diretivas ajudam você a concentrar seus esforços de migração. Os avisos anuláveis são gerados para a área do código na qual você está trabalhando ativamente. Deixe-os ativos até que você esteja pronto para ativar os avisos de todo o projeto. Use `restore` em vez do valor `disable` para não desabilitar acidentalmente o contexto após ativar as anotações anuláveis do projeto inteiro. Depois de ativar o contexto de anotação anulável para de todo o projeto, remova todas as pragmas `#nullable` desse projeto.

A classe `NewsStoryViewModel` é um DTO (objeto de transferência de dados) e duas propriedades são cadeias de caracteres de leitura/gravação:

[!code-csharp[InitialViewModel](~/samples/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/ViewModels/NewsStoryViewModel.cs#StarterViewModel)]

Essas duas propriedades causam `CS8618`, "Propriedade não anulável não inicializada". Está bem claro: as duas propriedades `string` têm o valor padrão de `null` quando um `NewsStoryViewModel` é construído. O importante é descobrir como os objetos `NewsStoryViewModel` são construídos. Examinando essa classe, não é possível determinar se o valor `null` faz parte do design, ou se esses objetos são definidos como valores não nulos sempre que um é criado. As histórias de notícias são criadas no método `GetNews` da classe `NewsService`:

[!code-csharp[StarterCreateNewsItem](~/samples/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/Services/NewsService.cs#CreateNewsItem)]

Há muita coisa acontecendo no bloco de código anterior. Esse aplicativo usa o pacote NuGet [AutoMapper](https://automapper.org/) para construir um item de notícias a partir de um `ISyndicationItem`. Você descobriu que os itens de notícias são construídos, e as propriedades são definidas nessa instrução. Isso significa que o design do `NewsStoryViewModel` indica que essas propriedades nunca devem ter o valor `null`. Essas propriedades devem ser **tipos de referência não anuláveis**. Isso expressa melhor a intenção do design original. Na verdade, qualquer `NewsStoryViewModel` *é* corretamente instanciada com valores não nulos. Isso torna o código de inicialização a seguir uma correção válida:

```csharp
public class NewsStoryViewModel
{
    public DateTimeOffset Published { get; set; }
    public string Title { get; set; } = default!;
    public string Uri { get; set; } = default!;
}
```

A atribuição de `Title` e `Uri` a `default`, que é `null` para o tipo `string`, não altera o comportamento de tempo de execução do programa. O `NewsStoryViewModel` ainda é construído com valores nulos, mas agora o compilador não retorna avisos. O **operador que tolera valores nulos**, o caractere `!` logo após a expressão `default` informa ao compilador que a expressão anterior não é nula. Essa técnica pode ser adequada quando outras alterações forçam alterações muito maiores em uma base de código, mas nesse aplicativo há uma solução relativamente rápida e melhor: tornar o `NewsStoryViewModel` um tipo imutável em que todas as propriedades são definidas no construtor. Faça estas alterações em `NewsStoryViewModel`:

[!code-csharp[FinishedViewModel](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/ViewModels/NewsStoryViewModel.cs#FinishedViewModel)]

Depois disso, atualize o código que configura o AutoMapper, para que ele use o construtor em vez de definir propriedades. Abra `NewsService.cs` e procure o seguinte código na parte inferior do arquivo:

[!code-csharp[StarterAutoMapper](~/samples/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/Services/NewsService.cs#ConfigureAutoMapper)]

O código mapeia as propriedades do objeto `ISyndicationItem` para as propriedades `NewsStoryViewModel`. Em vez disso, você deseja que o AutoMapper forneça o mapeamento usando um construtor. Substitua o código acima pela seguinte configuração do automapper:

[!code-csharp[FinishedViewModel](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Services/NewsService.cs#ConfigureAutoMapper)]

Note que como essa classe é pequena, e você examinou cuidadosamente, ative a diretiva `#nullable enable` acima dessa declaração de classe. A alteração no construtor poderia ter quebrado algo, portanto, vale a pena executar todos os testes e testar o aplicativo antes de prosseguir.

O primeiro conjunto de alterações mostrou como descobrir quando o design original indicou que as variáveis não devem ser definidas como `null`. A técnica é conhecida como **corrigir pela construção**. Você declara que um objeto e suas propriedades não podem ser `null` quando ele é construído. A análise de fluxo do compilador fornece garantia de que essas propriedades não são definidas como `null` após a construção. Observe que esse construtor é chamado pelo código externo, e que o código é **indiferente ao anulável**. A nova sintaxe não fornece uma verificação de tempo de execução. O código externo pode enganar a análise de fluxo do compilador. 

Outras vezes, a estrutura de uma classe fornece dicas sobre diferentes sobre a intenção. Abra o arquivo *Error.cshtml.cs* na pasta *Páginas*. O `ErrorViewModel` contém o seguinte código:

[!code-csharp[StarterErrorModel](~/samples/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/Pages/Error.cshtml.cs#StartErrorModel)]

Adicione a diretiva `#nullable enable` antes da declaração de classe e uma diretiva `#nullable restore` depois dela. Você receberá um aviso de que `RequestId` não foi inicializado. Ao examinar a classe, você deve decidir que a propriedade `RequestId` deve ser nula em alguns casos. A existência da propriedade `ShowRequestId` indica que é possível faltar valores. Como `null` é válido, adicione o `?` no tipo `string` para indicar que a propriedade `RequestId` é um *tipo de referência anulável*. A classe final se parece com o seguinte exemplo:

[!code-csharp[FinishedErrorModel](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Pages/Error.cshtml.cs#ErrorModel)]

Verifique os usos da propriedade, e você verá que na página associada, a propriedade passa por uma verificação de valor nulo antes da renderização na marcação. Esse é um uso seguro de um tipo de referência anulável, portanto, você concluiu essa classe.

## <a name="fixing-nulls-causes-change"></a>Corrigir nulos causa alteração

Com frequência, a correção para um conjunto de avisos cria novos avisos no código relacionado. Vamos ver os avisos em ação corrigindo a classe `index.cshtml.cs`. Abra o arquivo `index.cshtml.cs` e examine o código. Esse arquivo contém o código por trás da página de índice:

[!code-csharp[StarterIndexModel](~/samples/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/Pages/Index.cshtml.cs#IndexModelStart)]

Adicione a diretiva `#nullable enable` e você verá dois avisos. Nem a propriedade `ErrorText`, ou a propriedade `NewsItems` é inicializada. Um exame dessa classe o levaria a acreditar que ambas as propriedades devem ser tipos de referência anuláveis: ambas têm setters privados. Exatamente um é atribuído no método `OnGet`. Antes de fazer alterações, examine os consumidores das duas propriedades. Na própria página, o `ErrorText` é verificado em relação ao valor nulo antes de gerar a marcação dos erros. A coleção `NewsItems` é verificada com relação a `null` e verificada para garantir que a coleção tenha itens. Uma correção rápida seria transformar as duas propriedades em tipos de referência anuláveis. Uma correção melhor seria transformar a coleção em um tipo de referência não anulável e adicionar itens à coleção existente ao recuperar notícias. A primeira correção é adicionar o `?` ao tipo `string` para o `ErrorText`:

[!code-csharp[UpdateErrorText](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Pages/Index.cshtml.cs#UpdateErrorText)]

Essa alteração não se propagará pelo outro código, pois qualquer acesso à propriedade `ErrorText` já foi protegida por verificações de valor nulo. Em seguida, inicialize a lista `NewsItems` e remova a propriedade setter, tornando-a uma propriedade somente leitura:

[!code-csharp[InitializeNewsItems](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Pages/Index.cshtml.cs#InitializeNewsItems)]

Isso corrigiu o aviso, mas introduziu um erro. Agora, a lista `NewsItems` foi **corrigida pela construção**, mas o código que define a lista no `OnGet` deve ser alterado para coincidir com a nova API. Em vez de uma atribuição, chame `AddRange` para adicionar os itens de notícias à lista existente:

[!code-csharp[AddRange](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Pages/Index.cshtml.cs#AddRange)]

Usar `AddRange` em vez de uma atribuição significa que o método `GetNews` pode retornar um `IEnumerable` em vez de um `List`. Isso salva uma alocação. Altere a assinatura do método e remova a chamada a `ToList`, conforme mostra o exemplo de código a seguir:

[!code-csharp[GetNews](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Services/NewsService.cs#GetNewsFinished)]

A alteração da assinatura também interrompe testes de uma das opções. Abra o arquivo `NewsServiceTests.cs` na pasta `Services` do projeto `SimpleFeedReader.Tests`. Navegue até o teste `Returns_News_Stories_Given_Valid_Uri` e altere o tipo da variável `result` para `IEnumerable<NewsItem>`. A alteração do tipo significa que a propriedade `Count` não está mais disponível. Portanto, substitua a propriedade `Count` no `Assert` com uma chamada para `Any()`:

[!code-csharp[FixTests](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader.Tests/Services/NewsServiceTests.cs#FixTestSignature)]

Você também precisará adicionar uma instrução `using System.Linq` ao início do arquivo.

Esse conjunto de alterações destaca uma consideração especial ao atualizar o código que inclui instanciações genéricas. Tanto a lista quanto os elementos na lista de tipos não anuláveis. Um deles ou ambos podem ser tipos anuláveis. Todas as declarações a seguir são permitidas:

- `List<NewsStoryViewModel>`: lista não anulável de modelos de exibição não anuláveis.
- `List<NewsStoryViewModel?>`: lista não anulável de modelos de exibição anuláveis.
- `List<NewsStoryViewModel>?`: lista anulável de modelos de exibição não anuláveis.
- `List<NewsStoryViewModel?>?`: lista anulável de modelos de exibição anuláveis.

## <a name="interfaces-with-external-code"></a>Interfaces com código externo

Você fez alterações na classe `NewsService`, então, ative a anotação `#nullable enable` para essa classe. Isso não gerará avisos novos. No entanto, um exame cuidadoso da classe ajuda a ilustrar algumas das limitações da análise de fluxo do compilador. Examine o construtor:

[!code-csharp[ServiceConstructor](~/samples/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Services/NewsService.cs#ServiceConstructor)]

O parâmetro `IMapper` é tipado como uma referência não anulável. Ele é chamado pelo código de infraestrutura do ASP.NET Core, portanto, o compilador não sabe que o `IMapper` nunca será nulo. O contêiner de DI (injeção de dependência) do ASP.NET Core padrão gera uma exceção se não puder resolver um serviço necessário, para que o código fique correto. O compilador não consegue validar todas as chamadas para suas APIs públicas, mesmo que seu código seja compilado com contextos de anotação anuláveis habilitados. Além disso, suas bibliotecas podem ser consumidas por projetos que ainda não aceitaram o uso de tipos de referência anuláveis. Valide as entradas para APIs públicas, mesmo que você as tenha declarado como tipos não anuláveis.

## <a name="get-the-code"></a>Obter o código

Você corrigiu os avisos identificados na compilação de teste inicial, portanto, agora você pode ativar o contexto de anotação anulável para os dois projetos. Recompile os projetos; o compilador não relatará nenhum aviso. Você pode obter o código do projeto concluído no repositório do GitHub [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/nullable-reference-migration/finished).

Os novos recursos que dão suporte aos tipos de referência anuláveis ajudam você a encontrar e corrigir possíveis erros no modo de manipulação de valores `null` em seu código. A habilitação do contexto de anotação anulável permite que você expresse sua intenção de design: algumas variáveis nunca devem ser nulas, outras variáveis podem conter valores nulos. Esses recursos facilitam a declaração de sua intenção de design. Da mesma forma, o contexto de aviso anulável instrui o compilador a emitir avisos quando você violar essa intenção. Esses avisos servirão como orientação para criar atualizações que tornem seu código mais resiliente e menos propensa a lançar uma `NullReferenceException` durante a execução. Você pode controlar o escopo desses contextos para se concentrar na migração de áreas locais do código, enquanto a base de código restante permanece inalterada. Na prática, você pode tornar essa tarefa de migração uma parte da manutenção regular das suas classes. Este tutorial demonstrou o processo para migrar um aplicativo a fim de usar tipos de referência anuláveis. Você pode explorar um exemplo real maior desse processo examinando a solicitação de pull feita por [Jon Skeet](https://github.com/jskeet) para incorporar tipos de referência anuláveis em [NodaTime](https://github.com/nodatime/nodatime/pull/1240/commits).
