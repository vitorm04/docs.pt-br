---
ms.openlocfilehash: 303d6790f1e4a42b021de3a214e3e7b44e1a4320
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70104629"
---
# <a name="contributing"></a>Contribuição

Agradecemos seu interesse em contribuir com a documentação do .NET.

> Estamos no processo de movimentação das nossas diretrizes para um guia de contribuição em todo o site. 
> Para ver as novas diretrizes, acesse a [Visão geral do guia de colaborador do Microsoft Docs](https://docs.microsoft.com/contribute/).

O documento aborda o processo para contribuir para os artigos e exemplos de código hospedados no [site de documentação do .NET](https://docs.microsoft.com/dotnet). As contribuições podem ser tão simples quanto correções de erro de digitação ou tão complexas quanto novos artigos.

- [Processo de contribuição](#process-for-contributing)
- [A experiência interativa em C#](#the-c-interactive-experience)
- [O que FAZER e o que NÃO FAZER](#dos-and-donts)
- [Contrato de Licença do Colaborador](#contributor-license-agreement)

Esse repositório contém a documentação conceitual do .NET. O site de documentação do .NET foi criado com base em vários repositórios, além desse:

- [Exemplos e snippets de código](https://github.com/dotnet/samples)
- [Referência de API](https://github.com/dotnet/dotnet-api-docs)
- [Referência do SDK do .NET Compiler Platform](https://github.com/dotnet/roslyn-api-docs)

Acompanhamos os problemas e as tarefas desses repositórios aqui.

## <a name="process-for-contributing"></a>Processo de contribuição

Você precisa de uma compreensão básica do [Git e do GitHub.com](https://guides.github.com/activities/hello-world/).

**Etapa 1:** Ignore esta etapa para pequenas alterações (por exemplo, se você estiver corrigindo um erro de digitação ou abrindo imediatamente uma solicitação de pull para resolver um problema encontrado nos documentos). Se você estiver interessado em escrever novos conteúdos ou em revisar minuciosamente um conteúdo existente, abra uma [questão](https://github.com/dotnet/docs/issues) descrevendo o que você deseja fazer.
O conteúdo dentro da pasta **docs** é separado em seções organizadas que são refletidas no Índice (TOC). Defina onde o tópico será posicionado no TOC. Obter comentários sobre sua proposta.

-ou-

Também é possível escolher entre as questões existentes, para as quais contribuições da comunidade são bem-vindas. [Projetos para os colaboradores da comunidade do .NET](https://github.com/dotnet/docs/projects/35) lista vários itens de trabalho que estão disponíveis para os colaboradores da comunidade. Dependendo de seus interesses e nível de compromisso, você pode escolher entre questões nas seguintes categorias:

- **Manutenção**. Essa categoria inclui contribuições bastante simples, como corrigir links corrompidos ou incorretos, adicionar exemplos de código ausentes ou abordar problemas de conteúdo limitado. Em alguns casos, essas questões podem envolver grandes quantidades de arquivos. Nesse caso, informe-nos com o que você gostaria de trabalhar antes de começar.

- **Atualizações de conteúdo**. Considerando a enormidade do conjunto de documentos, o conteúdo se torna facilmente desatualizado e precisa de revisão. Além disso, por uma variedade de motivos, certos conteúdos podem ser duplicados ou até mesmo triplicados. A atualização do conteúdo envolve garantir que os tópicos individuais sejam atuais, ou revisar o conteúdo em uma área para eliminar duplicação e se certificar que todo conteúdo exclusivo seja preservado no menor conjunto de documentação.

- **Criação de novo conteúdo**. Se você estiver interessado na criação do seu próprio tópico, estas questões listam tópicos que gostaríamos de adicionar ao nosso conjunto de documentos. Fale conosco antes de começar a trabalhar em um tópico, no entanto. Se você estiver interessado em escrever um tópico que não está listado aqui, abra uma questão. 

Você também pode consultar nossa lista de [questões abertas](https://github.com/dotnet/docs/issues) e se voluntariar para trabalhar naquelas em que está interessado. Usamos o rótulo [up-for-grabs](https://github.com/dotnet/docs/labels/up-for-grabs) (a distribuir) para marcar questões abertas para contribuição. 

**Etapa 2:** Crie fork dos repositórios `dotnet/docs`, `dotnet/samples` ou `dotnet/dotnet-api-docs`, conforme necessário, e crie um branch para as alterações.

Para pequenas alterações, você pode usar a interface da Web do GitHub. Basta clicar em **Editar o arquivo na sua bifurcação deste projeto** no arquivo que você deseja alterar. O GitHub cria o novo branch para você após enviar as alterações.

**Etapa 3:** Faça as alterações nesse novo branch.

Se for um novo tópico, você poderá usar esse [arquivo de modelo](./styleguide/template.md) como ponto de partida. Ele contém as diretrizes de escrita e também explica os metadados necessários para cada artigo, como informações do autor.

Navegue até a pasta que corresponde à localização do Sumário determinado para o seu artigo na etapa 1.
Essa pasta contém os arquivos Markdown para todos os artigos nesta seção.
Se necessário, crie uma pasta para colocar os arquivos do seu conteúdo. O artigo principal desta seção chama-se *index.md*.
Para imagens e outros recursos estáticos, crie uma subpasta chamada **mídia** dentro da pasta que contém seu artigo, se ainda não houver. Dentro da pasta **mídia**, crie uma subpasta com o nome do artigo (exceto para o arquivo de índice).
Inclua exemplos maiores na pasta *exemplos* na raiz do repositório.

Siga a sintaxe de Markdown apropriada. Para saber mais, confira o [guia de estilo](./styleguide/template.md).

### <a name="example-structure"></a>Exemplo de estrutura

```
docs
  /about
  /core
    /porting
      porting-overview.md
      /media
        /porting-overview
            portability_report.png
```

**Etapa 4:** Envie uma PR (solicitação de pull) de seu branch `dotnet/docs/master`.

A PR deve *sempre* ser direcionada ao branch mestre. Você *nunca* deve abrir uma PR direcionada ao branch dinâmico.

Cada PR normalmente deve lidar com uma questão por vez. A PR pode modificar um ou vários arquivos. Se você está abordando várias correções em diferentes arquivos, é preferível usar PRs separadas.

Se a PR estiver resolvendo um problema existente, adicione a palavra-chave `Fixes #Issue_Number` à mensagem de confirmação ou à descrição da PR. Dessa forma, o problema se encerra automaticamente ao mesclar a PR. Para obter mais informações, confira [Closing issues via commit messages](https://help.github.com/articles/closing-issues-via-commit-messages/) (Encerrando problemas por meio de mensagens de confirmação).

A equipe do .NET examinará a PR e informará se outras atualizações/alterações são necessárias para aprová-la.

**Etapa 5:** Faça as atualizações necessárias no branch, conforme discutido com a equipe.

Os mantenedores mesclarão sua PR no branch mestre depois que os comentários forem aplicados e sua alteração for aprovada.

Em um determinado ritmo, efetuaremos push de todas as confirmações do branch mestre para o branch dinâmico e, em seguida, você poderá ver sua colaboração ao vivo em https://docs.microsoft.com/dotnet/.

### <a name="contributing-to-samples"></a>Contribuindo com exemplos

Fazemos a seguinte distinção para o código existente em nosso repositório:

- Exemplos: os leitores podem baixar e executar as amostras. Todas as amostras devem ser aplicativos ou bibliotecas completos. Quando a amostra cria uma biblioteca, ela deve incluir testes de unidade ou um aplicativo que permita aos leitores executar o código.

- Snippets: ilustram um conceito ou tarefa menor. Eles são compilados, mas não são destinados a ser aplicativos completos.

Todos os códigos residem no repositório [dotnet/samples](https://github.com/dotnet/samples). Estamos trabalhando para criar um modelo em que nossa estrutura de pastas de amostras corresponda à nossa estrutura de pastas de documentos. Os padrões que seguimos são:

- A pasta *snippets* de nível superior contém snippets para amostras pequenas e dedicadas.
- Exemplos de referência de API ficam em uma pasta seguindo este padrão: *snippets/\<idioma>/api/\<namespace>/\<nomeapi>* .
- Outras pastas de nível superior correspondem às pastas de nível superior do repositório *docs*. Por exemplo, o repositório docs tem uma pasta *machine-learning/tutorials*, e as amostras para tutoriais de aprendizado por máquina estão na pasta *samples/machine-learning/tutorials*.

Além disso, todas as amostras nas pastas *core* e *standard* devem ser compiladas e executadas em todas as plataformas compatíveis com o .NET Core. Nosso sistema de build de CI força isso. A pasta de nível superior *framework* contém exemplos que só são compilados e validados no Windows.

Podemos expandir esses diretórios conforme seja adicionado conteúdo no repositório docs. Por exemplo, adicionaremos diretórios do Xamarin, como `xamarin-ios` e `xamarin-android`.

Cada amostra completa que você cria deve conter um arquivo *leiame.md*. Esse arquivo deve conter uma breve descrição da amostra (um ou dois parágrafos). O *leiame.md* deve informar aos leitores o que eles aprenderão ao explorar essa amostra. O arquivo *leiame.md* também deve conter um link para o documento ativo no [site de documentação do .NET](https://docs.microsoft.com/dotnet/welcome).
Para definir o local de mapeamento de determinado arquivo no repositório para esse site, substitua `/docs` no caminho do repositório por `https://docs.microsoft.com/dotnet`.

Seu tópico também conterá links para a amostra. Crie um link diretamente para a pasta da amostra no GitHub.

Para saber mais, confira o [Leiame da amostra](https://github.com/dotnet/samples/blob/master/README.md).

## <a name="the-c-interactive-experience"></a>A experiência interativa em C#

Códigos de exemplo curtos em C# podem usar a marcação de linguagem `csharp-interactive` para especificar uma amostra em C# executada no navegador. (Código de exemplos embutidos usam a marcação `csharp-interactive`. Para snippets incluídos da fonte, use a marcação `code-csharp-interactive`.) Esses códigos de exemplo exibem uma janela de código e uma janela de saída no artigo. A janela de saída exibe qualquer resultado da execução do código interativo depois que o usuário tiver executado a amostra. 

A experiência interativa em C# altera o modo como trabalhamos com amostras. Os visitantes podem executar a amostra para ver os resultados. Uma série de fatores ajuda a determinar se a amostra ou o texto correspondente deve incluir informações sobre a saída.

### <a name="when-to-display-the-expected-output-without-running-the-sample"></a>Quando exibir a saída esperada sem executar a amostra

- Artigos direcionados a iniciantes devem fornecer a saída para que os leitores possam comparar a saída do trabalho deles com a resposta esperada.
- Amostras em que a saída é parte integral do tópico devem exibir essa saída. Por exemplo, artigos sobre texto formatado devem mostrar o formato de texto sem executar a amostra.
- Quando a amostra e a saída esperada são curtas, considere mostrar a saída. Isso economiza um pouco de tempo.
- Artigos que explicam como a cultura atual ou a cultura invariável afetam a saída devem explicar a saída esperada. O Interactive REPL (Loop de Leitura-Avaliação-Impressão Interativo) é executado em um host baseado em Linux. A cultura padrão e a cultura invariável produzem uma saída diferente em computadores e sistemas operacionais diferentes. O artigo deve explicar a saída em sistemas Windows, Linux e Mac.

### <a name="when-to-exclude-expected-output-from-the-sample"></a>Quando excluir a saída esperada da amostra 

- Artigos em que a amostra gera uma saída maior não devem incluí-la nos comentários. Isso obscurece o código após a execução da amostra.
- Artigos em que a amostra demonstra um tópico, mas a saída não é fundamental para entendê-lo. Por exemplo, um código que executa uma consulta LINQ para explicar a sintaxe de consulta e, em seguida, exibir cada item da coleção de saída.

## <a name="dos-and-donts"></a>O que FAZER e o que NÃO FAZER

A lista a seguir mostra algumas regras de orientação que você deve considerar ao contribuir para a documentação do .NET:

- **NÃO** nos surpreenda com solicitações de pull grandes. Em vez disso, registre um problema e inicie uma discussão para que possamos concordar sobre o que fazer antes de você gastar muito tempo nisso.
- **FAZER:** leia o [guia de estilo](./styleguide/template.md) e as diretrizes sobre [voz e tom](./styleguide/voice-tone.md).
- **FAZER:** use o arquivo de [modelo](./styleguide/template.md) como o ponto de partida do seu trabalho.
- **FAZER:** crie um branch separado em seu fork antes de trabalhar nos artigos.
- **FAZER:** siga o [fluxo de trabalho do GitHub Flow](https://guides.github.com/introduction/flow/).
- **FAZER:** faça postagem em blogs e no Twitter (ou em outros) sobre suas contribuições, com frequência.

> Observação: você pode observar que, no momento, alguns dos tópicos não estão seguindo todas as diretrizes especificadas aqui e também no [guia de estilo](./styleguide/template.md). Estamos trabalhando para atingir a consistência em todo o site. Verifique a lista de [problemas em aberto](https://github.com/dotnet/docs/issues?q=is%3Aissue+is%3Aopen+label%3Aguidelines-adherence) que estamos acompanhando, no momento, para essa meta específica.

## <a name="contributor-license-agreement"></a>Contrato de licença do colaborador

Você deve assinar o [CLA (Contrato de Licença de Contribuição) da .NET Foundation](https://cla.dotnetfoundation.org) antes de sua solicitação de pull ser mesclada. Isso é um requisito a ser cumprido uma única vez para projetos na .NET Foundation. Você pode ler mais sobre [CLAs (Contratos de Licença de Contribuição)](https://en.wikipedia.org/wiki/Contributor_License_Agreement) na Wikipédia.

O contrato: [net-foundation-contribution-license-agreement.pdf](https://github.com/dotnet/home/blob/master/guidance/net-foundation-contribution-license-agreement.pdf)

Você não precisa assinar o contrato antecipadamente. Você pode clonar sua solicitação de pull, criar fork para ela e enviá-la como de costume. Quando sua solicitação de pull é criada, ela é classificada por um bot do CLA. Se a alteração é simples (por exemplo, se você corrigir um erro de digitação), a solicitação de pull é rotulada com `cla-not-required`. Caso contrário, ela é classificada como `cla-required`. Depois de você assinar o CLA, as solicitações de pull atual e todas as futuras são rotuladas como `cla-signed`.
