---
title: Migrando aplicativos WPF para .NET Core 3.0
description: Saiba como migrar um aplicativo da Windows Presentation Foundation (WPF) para o .NET Core 3.0.
author: mjrousos
ms.date: 09/12/2019
ms.author: mikerou
ms.openlocfilehash: f52005e7c8a6312b8c4e09a950f1f635af1894e4
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "82071307"
---
# <a name="migrating-wpf-apps-to-net-core"></a>Migrando aplicativos WPF para .NET Core

Este artigo abrange as etapas necessárias para migrar um aplicativo do Windows Presentation Foundation (WPF) do .NET Framework para .NET Core 3.0. Se você não tem um aplicativo WPF em mãos para portar, mas gostaria de experimentar o processo, você pode usar o aplicativo de exemplo **Bean Trader** disponível no [GitHub](https://github.com/dotnet/windows-desktop/tree/master/Samples/BeanTrader). O aplicativo original (alvo .NET Framework 4.7.2) está disponível na pasta NetFx\BeanTraderClient. Primeiro explicaremos os passos necessários para portar aplicativos em geral, e depois vamos passar pelas alterações específicas que se aplicam à amostra do **Bean Trader.**

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

Para migrar para o .NET Core, você deve primeiro:

01. Entenda e atualize as dependências do NuGet:

    01. Atualize as dependências `<PackageReference>` do NuGet para usar o formato.
    01. Revise as dependências de NuGet de nível superior para compatibilidade .NET Core ou .NET Standard.
    01. Atualize os pacotes NuGet para versões mais recentes.
    01. Use o [Analisador de Portabilidade .NET](../../standard/analyzers/portability-analyzer.md) para entender as dependências .NET.

01. Migre o arquivo do projeto para o novo formato estilo SDK:

    01. Escolha se deve segmentar o .NET Core e o .NET Framework ou apenas o .NET Core.
    01. Copie propriedades e itens relevantes do arquivo do projeto para o novo arquivo do projeto.

01. Corrigir problemas de compilação:

    01. Adicione uma referência ao pacote [Microsoft.Windows.Compatibilidade.](https://www.nuget.org/packages/Microsoft.Windows.Compatibility/)
    01. Encontre e corrija diferenças de nível de API.
    01. Remover *seções app.config* diferentes `appSettings` ou `connectionStrings`.
    01. Regenerar código gerado, se necessário.

01. Teste em tempo de execução:

    01. Confirme se o aplicativo portado funciona conforme o esperado.
    01. Cuidado com <xref:System.NotSupportedException> exceções.

## <a name="about-the-sample"></a>Sobre o exemplo

Este artigo faz referência ao [aplicativo de exemplo Bean Trader](https://github.com/dotnet/windows-desktop/tree/master/Samples/BeanTrader) porque ele usa uma variedade de dependências semelhantes às que os aplicativos WPF do mundo real podem ter. O aplicativo não é grande, mas é feito para ser um passo acima de 'Hello World' em termos de complexidade. O aplicativo demonstra alguns problemas que os usuários podem encontrar ao portar aplicativos reais. O aplicativo se comunica com um serviço WCF, então para que ele seja executado corretamente, você também precisará executar o projeto BeanTraderServer (disponível no mesmo repositório do GitHub) e certifique-se de que a configuração beanTraderClient aponta para o ponto final correto. (Por padrão, a amostra assume que o servidor *http://localhost:8090*está sendo executado na mesma máquina em , o que será verdade se você iniciar o BeanTraderServer localmente.)

Tenha em mente que este aplicativo de amostra é destinado a demonstrar desafios e soluções de portação .NET Core. Não é para demonstrar as melhores práticas da WPF. Na verdade, ele deliberadamente inclui alguns anti-padrões para garantir que você se deparar com pelo menos alguns desafios interessantes durante a portação.

## <a name="getting-ready"></a>Preparando-se

O principal desafio de migrar um aplicativo .NET Framework para o .NET Core é que suas dependências podem funcionar de forma diferente ou não. A migração é muito mais fácil do que costumava ser; muitos pacotes NuGet agora têm como alvo o .NET Standard. Começando com o .NET Core 2.0, as áreas de superfície .NET Framework e .NET Core tornaram-se semelhantes. Mesmo assim, algumas diferenças (tanto no suporte de pacotes NuGet quanto nas APIs disponíveis .NET) permanecem. O primeiro passo para migrar é rever as dependências do aplicativo e certificar-se de que as referências estão em um formato que é facilmente migrado para o .NET Core.

### <a name="upgrade-to-packagereference-nuget-references"></a>Atualize `<PackageReference>` para referências NuGet

Projetos mais antigos do .NET Framework normalmente listam suas dependências do NuGet em um arquivo *packages.config.* O novo formato de arquivo de projeto no estilo [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) SDK faz referência aos pacotes NuGet como elementos no próprio arquivo csproj, em vez de em um arquivo de configuração separado.

Ao migrar, há duas vantagens em usar `<PackageReference>`referências de estilo:

- Este é o estilo de referência NuGet que é necessário para o novo arquivo de projeto .NET Core. Se você já `<PackageReference>`estiver usando, esses elementos de arquivo do projeto podem ser copiados e colados diretamente no novo projeto.
- Ao contrário de um arquivo `<PackageReference>` packages.config, os elementos referem-se apenas às dependências de nível superior que seu projeto depende diretamente. Todos os outros pacotes NuGet transitivos serão determinados no momento da restauração e gravados no arquivo obj\project.assets.json gerado automaticamente. Isso torna muito mais fácil determinar quais dependências seu projeto tem, o que é útil ao determinar se as dependências necessárias funcionarão no .NET Core ou não.

O primeiro passo para migrar um aplicativo .NET Framework para `<PackageReference>` .NET Core é atualizá-lo para usar referências NuGet. Visual Studio torna isso simples. Basta clicar com o botão direito do mouse no arquivo *packages.config* do projeto no Visual Studio's **Solution Explorer**e, em seguida, selecione **Migrate packages.config to PackageReference**.

![Atualizando para o PackageReference](./media/convert-project-from-net-framework/package-reference-migration.png)

Um diálogo aparece mostrando dependências de NuGet de alto nível calculadas e perguntando quais outros pacotes NuGet devem ser promovidos para o nível superior. Nenhum desses outros pacotes precisa ser de alto nível para a amostra bean trader, para que você possa desmarcar todas essas caixas. Em seguida, clique **em Ok** e o `<PackageReference>` arquivo *packages.config* é removido e elementos são adicionados ao arquivo do projeto.

`<PackageReference>`-referências de estilo não armazenam pacotes NuGet localmente em uma pasta de pacotes. Em vez disso, eles são armazenados globalmente como uma otimização. Após a migração concluída, edite o arquivo `<Analyzer>` csproj e remova quaisquer elementos referentes aos analisadores que anteriormente vinham do *.. \diretório de pacotes.* Não se preocupe, ele vai ficar bem. uma vez que você ainda tem as referências do pacote NuGet, os analisadores serão incluídos no projeto. Você só precisa limpar os pacotes antigos.elementos estilo `<Analyzer>` config.

### <a name="review-nuget-packages"></a>Revisar pacotes NuGet

Agora que você pode ver os pacotes NuGet de alto nível dos quais o projeto depende, você pode rever se esses pacotes estão disponíveis no .NET Core. Você pode determinar se um pacote suporta .NET Core olhando para suas dependências em [nuget.org](https://www.nuget.org/). O site [de fuget.org](https://www.fuget.org/) criado pela comunidade mostra essas informações com destaque na parte superior da página de informações do pacote.

Ao direcionar o .NET Core 3.0, qualquer pacote direcionado ao .NET Core ou ao .NET Standard deve funcionar (uma vez que o .NET Core implementa a área de superfície padrão .NET). Em alguns casos, a versão específica de um pacote usado não terá como alvo o .NET Core ou o .NET Standard, mas as versões mais recentes. Neste caso, você deve considerar a atualização para a versão mais recente do pacote.

Você pode usar pacotes direcionados ao .NET Framework, também, mas isso introduz algum risco. As dependências do .NET Core para .NET Framework são permitidas porque as áreas de superfície do .NET Core e do .NET Framework são semelhantes o suficiente para que essas dependências *funcionem frequentemente.* No entanto, se o pacote tentar usar uma API .NET que não esteja presente no .NET Core, você encontrará uma exceção de tempo de execução. Por causa disso, você só deve consultar pacotes .NET Framework quando não houver outras opções disponíveis e entender que fazê-lo impõe uma carga de teste.

Se houver pacotes referenciados que não tenham como alvo o .NET Core ou o .NET Standard, você terá que pensar em outras alternativas:

- Existem outros pacotes semelhantes que podem ser usados em vez disso? Às vezes, os autores do NuGet publicam separadamente. As versões do Core de suas bibliotecas têm como alvo especificamente o .NET Core. Os pacotes da Biblioteca Corporativa são um exemplo da publicação comunitária". Alternativas netcore" Em outros casos, SDKs mais novos para um determinado serviço (às vezes com nomes de pacotes diferentes) estão disponíveis para .NET Standard. Se não houver alternativas disponíveis, você pode continuar usando os pacotes direcionados ao .NET Framework, tendo em mente que você precisará testá-los completamente uma vez que seja executado no .NET Core.

A amostra bean trader tem as seguintes dependências nuGet de nível superior:

- [**Castle.Windsor, versão 4.1.1**](https://www.castleproject.org/projects/windsor/)  

  Este pacote tem como alvo o .NET Standard 1.6, por isso funciona no .NET Core.

- [**Microsoft.CodeAnalysis.FxCopAnalyzers, versão 2.6.3**](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.6.3)  
  Este é um meta-pacote, por isso não é imediatamente óbvio quais plataformas ele suporta, mas a [documentação](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisfxcopanalyzers) indica que sua versão mais recente (2.9.2) funcionará tanto para .NET Framework quanto .NET Core.

- [**Nito.AsyncEx, versão 4.0.1**](https://www.nuget.org/packages/Nito.AsyncEx/4.0.1)  

  Este pacote não tem como alvo o .NET Core, mas a versão 5.0 mais recente sim. Isso é comum ao migrar porque muitos pacotes NuGet adicionaram suporte ao .NET Standard recentemente, mas as versões mais antigas do projeto só terão como alvo o .NET Framework. Se a diferença de versão é apenas uma pequena diferença de versão, muitas vezes é fácil atualizar para a versão mais recente. Como esta é uma grande mudança de versão, você precisa ser cauteloso com a atualização, pois pode haver mudanças no pacote. Há um caminho a seguir, porém, o que é bom.

- [**MahApps.Metro, versão 1.6.5**](https://www.nuget.org/packages/MahApps.Metro/1.6.5)  

  Este pacote também não tem como alvo o .NET Core, mas tem uma nova pré-lançamento (2.0-alfa) que tem. Mais uma vez, você tem que olhar para a quebra de mudanças, mas o pacote mais novo é encorajador.

As dependências nuGet da amostra do Bean Trader têm como alvo o .NET Standard/.NET Core ou têm versões mais recentes que o fazem, portanto, é improvável que haja problemas de bloqueio aqui.

### <a name="upgrade-nuget-packages"></a>Atualizar pacotes NuGet

Se possível, seria bom atualizar as versões de quaisquer pacotes que visam apenas .NET Core ou .NET Standard com versões mais recentes neste momento (com o projeto ainda visando .NET Framework) para descobrir e resolver quaisquer alterações de quebra mais cedo.

Se você preferir não fazer nenhuma alteração material na versão existente do .NET Framework do aplicativo, isso pode esperar até que você tenha um novo arquivo de projeto direcionado ao .NET Core. No entanto, atualizar os pacotes Do NuGet para versões compatíveis com o .NET Core com antecedência torna o processo de migração ainda mais fácil quando você cria o novo arquivo de projeto e reduz o número de diferenças entre as versões .NET Framework e .NET Core do aplicativo.

Com a amostra do Bean Trader, todos os upgrades necessários podem ser feitos facilmente (usando o gerenciador de pacotes NuGet do Visual Studio) com uma exceção: a atualização do **MahApps.Metro 1.6.5** para **o 2.0** revela alterações de quebra relacionadas às APIs de gerenciamento de tema e sotaque.

Idealmente, o aplicativo seria atualizado para usar a versão mais recente do pacote (já que é mais provável que funcione no .NET Core). Em alguns casos, porém, isso pode não ser viável. Nesses casos, não atualize **o MahApps.Metro** porque as alterações necessárias não são triviais e este tutorial se concentra em migrar para o .NET Core 3, não para **MahApps.Metro 2.** Além disso, esta é uma dependência de baixo risco .NET Framework porque o aplicativo Bean Trader exerce apenas uma pequena parte do **MahApps.Metro**. É claro que isso exigirá testes para garantir que tudo esteja funcionando assim que a migração estiver concluída. Se este fosse um cenário real, seria bom apresentar um problema para acompanhar o trabalho para mudar para **mahapps.Metro** versão 2.0 já que não fazer a migração agora deixa para trás alguma dívida técnica.

Uma vez que os pacotes NuGet `<PackageReference>` sejam atualizados para versões recentes, o grupo de itens no arquivo de projeto da amostra bean trader deve ser assim.

```xml
<ItemGroup>
  <PackageReference Include="Castle.Windsor">
    <Version>4.1.1</Version>
  </PackageReference>
  <PackageReference Include="MahApps.Metro">
    <Version>1.6.5</Version>
  </PackageReference>
  <PackageReference Include="Microsoft.CodeAnalysis.FxCopAnalyzers">
    <Version>2.9.2</Version>
  </PackageReference>
  <PackageReference Include="Nito.AsyncEx">
    <Version>5.0.0</Version>
  </PackageReference>
</ItemGroup>
```

### <a name="net-framework-portability-analysis"></a>.NET Framework portability analysis analysis

Uma vez que você entenda o estado das dependências nuGet do seu projeto, a próxima coisa a considerar são as dependências da API .NET Framework. A ferramenta [.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) é útil para entender quais das APIs .NET que seu projeto usa estão disponíveis em outras plataformas .NET.

A ferramenta vem como um [plugin Visual Studio](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer), uma [ferramenta de linha de comando,](https://github.com/Microsoft/dotnet-apiport/releases)ou envolto em uma [GUI simples,](https://github.com/Microsoft/dotnet-apiport-ui)o que simplifica suas opções. Você pode ler mais sobre como usar o .NET Portability Analyzer (API Port) usando a GUI nos [aplicativos de área de trabalho porting para posta](https://devblogs.microsoft.com/dotnet/porting-desktop-apps-to-net-core/) no blog .NET Core. Se preferir usar a linha de comando, as etapas necessárias são:

1. Baixe o [Analisador de Portabilidade .NET](https://github.com/Microsoft/dotnet-apiport/releases) se você ainda não o tiver.
1. Certifique-se de que o aplicativo .NET Framework a ser portado seja criado com sucesso (essa é uma boa ideia antes da migração, independentemente).
1. Execute a porta API com uma linha de comando como esta.

    ```console
    ApiPort.exe analyze -f <PathToBeanTraderBinaries> -r html -r excel -t ".NET Core"
    ```

    O `-f` argumento especifica o caminho que contém os binários a serem analisados. O `-r` argumento especifica qual formato de arquivo de saída você deseja. O `-t` argumento especifica qual plataforma .NET analisará o uso da API contra. Neste caso, você quer .NET Core.

Quando você abrir o relatório HTML, a primeira seção listará todos os binários analisados e qual porcentagem das APIs .NET que eles usam estão disponíveis na plataforma-alvo. A porcentagem não é significativa por si só. O que é mais útil é ver as APIs específicas que estão faltando. Para fazer isso, selecione um nome de montagem ou role até os relatórios para assembléias individuais.

Concentre-se nas assembléias para as quais você possui o código fonte. No relatório Bean Trader ApiPort, por exemplo, há muitos binários listados, mas a maioria deles pertence a pacotes NuGet. `Castle.Windsor`mostra que depende de algumas APIs do System.Web que estão faltando no .NET Core. Isso não é uma preocupação porque `Castle.Windsor` você verificou anteriormente que suporta .NET Core. É comum que os pacotes NuGet tenham binários diferentes para uso com diferentes plataformas .NET, portanto, se a versão .NET Framework de `Castle.Windsor` usa ou não o System.Web APIs é irrelevante, desde que o pacote também tenha como alvo o .NET Standard ou o .NET Core (o que ele faz).

Com a amostra bean trader, o único binário que você precisa considerar é **beanTraderClient** e `System.ServiceModel.ClientBase<T>.Close` `System.ServiceModel.ClientBase<T>.Open`o relatório mostra que apenas duas APIs .NET estão faltando: e .

![Relatório de portabilidade do BeanTraderClient](./media/convert-project-from-net-framework/portability-report.png)

É improvável que sejam problemas de bloqueio porque as APIs do Cliente WCF são (principalmente) suportadas no .NET Core, portanto, deve haver alternativas disponíveis para essas APIs centrais. Na verdade, `System.ServiceModel`olhando para a área <https://apisof.net>de superfície do .NET Core (usando), você vê que há alternativas assíncronas no .NET Core.

Com base neste relatório e na análise anterior da dependência do NuGet, parece que não deve haver grandes problemas migrando a amostra do Bean Trader para o .NET Core. Você está pronto para o próximo passo em que você realmente vai começar a migração.

## <a name="migrating-the-project-file"></a>Migrando o arquivo de projeto

Se o aplicativo não estiver usando o novo [formato de arquivo de projeto no estilo SDK,](../../core/tools/csproj.md)você precisará de um novo arquivo de projeto para segmentar o .NET Core. Você pode substituir o arquivo csproj existente ou, se preferir manter o projeto existente intocado em seu estado atual, você pode adicionar um novo arquivo csproj direcionado ao .NET Core. Você pode criar versões do aplicativo para .NET Framework e .NET Core com um único `<TargetFrameworks>` arquivo de projeto no estilo SDK com vários [alvos](../../standard/library-guidance/cross-platform-targeting.md) (especificando vários alvos).

Para criar o novo arquivo de projeto, você pode criar `dotnet new wpf` um novo projeto WPF no Visual Studio ou usar o comando em um diretório temporário para gerar o arquivo do projeto e, em seguida, copiá-lo/renomeá-lo para o local correto. Há também uma ferramenta criada pela comunidade, [CsprojToVs2017,](https://github.com/hvanbakel/CsprojToVs2017)que pode automatizar parte da migração de arquivos do projeto. A ferramenta é útil, mas ainda precisa de um humano para revisar os resultados para ter certeza de que todos os detalhes da migração estão corretos. Uma área específica que a ferramenta não lida de forma ideal é migrar pacotes NuGet de *arquivos packages.config.* Se a ferramenta for executada em um arquivo de projeto que ainda usa um arquivo `<PackageReference>` *packages.config* para referenciar pacotes NuGet, ele migrará para elementos automaticamente, mas adicionará `<PackageReference>` elementos para todos *os* pacotes em vez de apenas os de nível superior. Se você já migrou para`<PackageReference>` elementos com o Visual Studio (como você fez nesta amostra), então a ferramenta pode ajudar com o resto da conversão. Como Scott Hanselman recomenda em [seu blog sobre migração de arquivos csproj](https://www.hanselman.com/blog/UpgradingAnExistingNETProjectFilesToTheLeanNewCSPROJFormatFromNETCore.aspx), portando à mão é educacional e dará melhores resultados se você tiver apenas alguns projetos para portar. Mas se você está portando dezenas ou centenas de arquivos de projeto, então uma ferramenta como [CsprojToVs2017] pode ser uma ajuda.

Para criar um novo arquivo de projeto `dotnet new wpf` para a amostra Bean Trader, execute em um diretório temporário e mova o arquivo *.csproj* gerado para a pasta *BeanTraderClient* e renomeie-o **beanTraderClient.Core.csproj**.

Como o novo formato de arquivo de projeto inclui automaticamente arquivos C#, arquivos *resx* e arquivos XAML que ele encontra em ou sob seu diretório, o arquivo do projeto já está quase completo! Para concluir a migração, abra os arquivos de projeto antigos e novos lado a lado e olhe através do antigo para ver se alguma informação que ele contém precisa ser migrada. No caso da amostra bean trader, os seguintes itens devem ser copiados para o novo projeto:

- As `<RootNamespace>` `<AssemblyName>`propriedades `<ApplicationIcon>` devem ser todas copiadas.

- Você também precisa `<GenerateAssemblyInfo>false</GenerateAssemblyInfo>` adicionar uma propriedade ao novo arquivo de projeto, uma vez `[AssemblyTitle]`que a amostra bean trader inclui atributos de nível de montagem (like) em um arquivo AssemblyInfo.cs. Por padrão, novos projetos no estilo SDK irão gerar automaticamente esses atributos com base em propriedades no arquivo csproj. Como você não quer que isso aconteça neste caso (os atributos autogerados entrariam em `<GenerateAssemblyInfo>`conflito com os de AssemblyInfo.cs), você desativa os atributos gerados automaticamente com .

- Embora os arquivos *resx* sejam automaticamente `<Resource>` incluídos como recursos incorporados, outros itens como imagens não são. Então, copie `<Resource>` os elementos para incorporar arquivos de imagem e ícone. Você pode simplificar as referências de png a uma única linha usando o `<Resource Include="**\*.png" />`suporte do novo formato de arquivo de projeto para padrões de globbing: .

- Da mesma `<None>` forma, os itens são incluídos automaticamente, mas não são copiados para o diretório de saída, por padrão. Como o projeto Bean `<None>` Trader inclui um item *copiado* para `PreserveNewest` o diretório de saída (usando `<None>` comportamentos), você precisa atualizar o item preenchido automaticamente para esse arquivo, como este.

  ```xml
  <None Update="BeanTrader.pfx">
    <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>
  </None>
  ```

- A amostra do Bean Trader inclui um arquivo XAML (Default.Accent.xaml) como `Content` (e não como um `Page`) porque os temas e acentos definidos neste arquivo são carregados do XAML do arquivo em tempo de execução, em vez de serem incorporados no próprio aplicativo. O novo sistema de projeto inclui `<Page>`automaticamente este arquivo como um , no entanto, uma vez que é um arquivo XAML. Então, você precisa remover o arquivo XAML`<Page Remove="**\Default.Accent.xaml" />`como uma página ( ) e adicioná-lo como conteúdo.

  ```xml
  <Content Include="Resources\Themes\Default.Accent.xaml">
      <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>
  </Content>
  ```

- Finalmente, adicione as referências NuGet copiando o `<ItemGroup>` com todos os `<PackageReference>` elementos. Se você não tivesse atualizado anteriormente os pacotes NuGet para versões compatíveis com o .NET Core, você poderia fazer isso agora que as referências do pacote estão em um projeto específico do .NET Core.

Neste ponto, deve ser possível adicionar o novo projeto à solução BeanTrader e abri-lo no Visual Studio. O projeto deve parecer correto `dotnet restore BeanTraderClient.Core.csproj` no Solution **Explorer**e deve restaurar com sucesso pacotes (com dois avisos esperados relacionados à versão MahApps.Metro que você está usando como alvo .NET Framework).

Embora seja possível manter os dois arquivos do projeto lado a lado (e pode até ser desejável se você quiser continuar construindo o projeto antigo exatamente como era), isso complica o processo de migração (os dois projetos tentarão usar as mesmas pastas bin e obj) e geralmente não é necessário. Se você quiser construir para ambos os alvos .NET Core `<TargetFramework>netcoreapp3.0</TargetFramework>` e .NET Framework, `<TargetFrameworks>netcoreapp3.0;net472</TargetFrameworks>` você pode substituir a propriedade no novo arquivo de projeto por. Para a amostra bean trader, exclua o arquivo de projeto antigo (BeanTraderClient.csproj) já que ele não é mais necessário. Se você preferir manter ambos os arquivos do projeto, certifique-se de que eles sejam construídos para diferentes caminhos de saída e saída intermediárias.

## <a name="fix-build-issues"></a>Corrigir problemas de compilação

O terceiro passo do processo de portação é fazer com que o projeto seja construído. Alguns aplicativos já serão criados com sucesso assim que o arquivo do projeto for convertido em um projeto no estilo SDK. Se esse é o caso do seu aplicativo, parabéns! Você pode ir para o passo 4. Outros aplicativos precisarão de algumas atualizações para fazê-los construir para o .NET Core. Se você tentar `dotnet build` executar no projeto de amostra bean trader agora, por exemplo, (ou construí-lo no Visual Studio), haverá muitos erros, mas você os corrigirá rapidamente.

### <a name="systemservicemodel-references-and-microsoftwindowscompatibility"></a>Referências do System.ServiceModel e Microsoft.Windows.Compatibilidade

Uma fonte comum de erros está faltando referências para APIs que estão disponíveis para .NET Core, mas não automaticamente incluídas no metapacote do aplicativo .NET Core. Para resolver isso, você `Microsoft.Windows.Compatibility` deve referenciar o pacote. O pacote de compatibilidade inclui um amplo conjunto de APIs que são comuns em aplicativos de desktop do Windows, como cliente WCF, serviços de diretório, registro, configuração, APIs de ACLs e muito mais.

Com a amostra bean trader, a maioria dos <xref:System.ServiceModel> erros de compilação são devido a tipos ausentes. Estes podem ser endereçados fazendo referência aos pacotes WCF NuGet necessários. As APIs de clientes WCF estão entre as `Microsoft.Windows.Compatibility` presentes no pacote, porém, fazer referência ao pacote de compatibilidade é uma solução ainda melhor (uma vez que também aborda quaisquer problemas relacionados a APIs, bem como soluções para os problemas de WCF que o pacote de compatibilidade disponibiliza). O `Microsoft.Windows.Compatibility` pacote ajuda na maioria dos cenários de portação do .NET Core 3.0 WPF e WinForms. Depois de adicionar a `Microsoft.Windows.Compatibility`referência NuGet a , apenas um erro de compilação permanece!

### <a name="cleaning-up-unused-files"></a>Limpeza de arquivos não utilizados

Um tipo de problema de migração que surge muitas vezes diz respeito a arquivos C# e XAML que não foram incluídos anteriormente na compilação sendo captadas pelos novos projetos no estilo SDK que incluem *todas as* fontes automaticamente.

O próximo erro de compilação que você vê na amostra Bean Trader refere-se a uma implementação de interface ruim em *OldUnusedViewModel.cs*. O nome do arquivo é uma dica, mas na inspeção, você verá que este arquivo de origem está incorreto. Ele não causou problemas anteriormente porque não estava incluído no projeto original .NET Framework. Os arquivos de origem que estavam presentes no disco, mas não estão incluídos no *csproj* antigo, estão incluídos automaticamente agora.

Para problemas pontuais como este, é fácil comparar com o *csproj* anterior para confirmar que `<Compile Remove="" />` o arquivo não é necessário, e então ou ele ou, se o arquivo de origem não for mais necessário em qualquer lugar, exclua-o. Neste caso, é seguro apenas *excluíOldUnusedViewModel.cs*.

Se você tiver muitos arquivos de origem que precisariam ser excluídos dessa forma, `<EnableDefaultCompileItems>` você pode desativar a inclusão automática de arquivos C# definindo a propriedade como falsa no arquivo do projeto. Em seguida, `<Compile Include>` você pode copiar itens do arquivo de projeto antigo para o novo, a fim de construir apenas fontes que você pretendia incluir. Da mesma `<EnableDefaultPageItems>` forma, pode ser usado para desativar a `<EnableDefaultItems>` inclusão automática de páginas XAML e pode controlar ambos com uma única propriedade.

### <a name="a-brief-aside-on-multi-pass-compilers"></a>Um breve lado em compiladores multi-pass

Depois de remover o arquivo ofensivo da amostra Bean Trader, você pode reconstruir e obterá quatro erros. Você não tinha um antes? Por que o número de erros aumentou? O compilador C# é um [compilador multi-pass](https://docs.microsoft.com/archive/blogs/ericlippert/how-many-passes). Isso significa que ele passa por cada arquivo de origem duas vezes. Primeiro, o compilador apenas olha para metadados e declarações em cada arquivo de origem e identifica quaisquer problemas de nível de declaração. Esses são os erros que você corrigiu. Em seguida, ele passa pelo código novamente para construir a fonte C# em IL; esses são o segundo conjunto de erros que você está vendo agora.

> [!NOTE]
> O compilador C# faz [mais do que apenas duas passagens,](https://docs.microsoft.com/archive/blogs/ericlippert/how-many-passes)mas o resultado final é que erros de compilador para grandes mudanças de código como esta tendem a vir em duas ondas.

### <a name="third-party-dependency-fixes-castlewindsor"></a>Correções de dependência de terceiros (Castle.Windsor)

Outra classe de problema que surge em alguns cenários de migração são as diferenças de API entre as versões .NET Framework e .NET Core de dependências. Mesmo que um pacote NuGet tenha como alvo o .NET Framework e o .NET Standard ou o .NET Core, pode haver bibliotecas diferentes para uso com diferentes alvos .NET. Isso permite que os pacotes suportem muitas plataformas .NET diferentes, o que pode exigir implementações diferentes. Isso também significa que pode haver pequenas diferenças de API nas bibliotecas ao direcionar diferentes plataformas .NET.

O próximo conjunto de erros que você verá na `Castle.Windsor` amostra bean trader está relacionado a APIs. O projeto .NET Core Bean Trader `Castle.Windsor` usa a mesma versão do projeto direcionado ao .NET Framework (4.1.1), mas as implementações para essas duas plataformas são ligeiramente diferentes.

Neste caso, você verá os seguintes problemas que precisam ser corrigidos:

1. `Castle.MicroKernel.Registration.Classes.FromThisAssembly`não está disponível no .NET Core. Há, no entanto, `Classes.FromAssemblyContaining` a API semelhante disponível, `Classes.FromThisAssembly()` para `Classes.FromAssemblyContaining(t)`que `t` possamos substituir ambos os usos por chamadas para , onde está o tipo que faz a chamada.
1. Da mesma *Bootstrapper.cs*forma, `Castle.Windsor.Installer.FromAssembly`em Bootstrapper.cs , . Isso não está disponível no .NET Core. Em vez disso, essa `FromAssembly.Containing(typeof(Bootstrapper))`chamada pode ser substituída por .

### <a name="updating-wcf-client-usage"></a>Atualizando o uso do cliente WCF

Tendo corrigido `Castle.Windsor` as diferenças, o último erro de compilação restante `BeanTraderServiceClient` no projeto `DuplexClientBase`.NET Core Bean Trader é que (que deriva de ) não tem um `Open` método. Isso não é surpreendente, uma vez que esta é uma API que foi destacada pelo .NET Portability Analyzer no início deste processo de migração. Olhar `BeanTraderServiceClient` para chama a atenção para um problema maior, no entanto. Este cliente WCF foi gerado automaticamente pela ferramenta [Svcutil.exe.](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)

**Os clientes WCF gerados pela Svcutil são destinados a serem usados no .NET Framework.**

As soluções que usam clientes WCF gerados por svcutil precisarão regenerar clientes compatíveis com o .NET Standard para uso com o .NET Core. Uma das principais razões pelas quais os clientes antigos não funcionam é que eles dependem da configuração do aplicativo para definir vinculações e pontos finais do WCF. Como as APIs padrão .NET podem funcionar entre plataformas (onde as APIs de configuração do System.configuration não estão disponíveis), os clientes WCF para cenários .NET Core e .NET Standard devem definir vinculações e pontos finais de forma programática em vez de na configuração.

Na verdade, qualquer uso do cliente `<system.serviceModel>` WCF que dependa da seção app.config (seja criado com Svcutil ou manualmente) precisará ser alterado para trabalhar no .NET Core.

Existem duas maneiras de gerar automaticamente clientes WCF compatíveis com o .NET Padrão:

- A `dotnet-svcutil` ferramenta é uma ferramenta .NET que gera clientes WCF de forma semelhante à forma como o Svcutil trabalhou anteriormente.
- O Visual Studio pode gerar clientes WCF usando a opção [wcf web service reference](../../core/additional-tools/wcf-web-service-reference-guide.md) de seu recurso Connected Services.

Qualquer abordagem funciona bem. Alternativamente, é claro, você poderia escrever o código do cliente WCF você mesmo. Para esta amostra, escolhi usar o recurso Visual Studio Connected Service. Para isso, clique com o botão direito do mouse no projeto *BeanTraderClient.Core* no explorador de soluções do Visual Studio e selecione **Adicionar** > **serviço conectado**. Em seguida, escolha o provedor de referência de serviços web WCF. Isso trará um diálogo onde você pode especificar o endereço do`localhost:8080` serviço web do Backend Bean Trader (se você estiver executando o servidor localmente) e o namespace que os tipos gerados devem usar **(BeanTrader.Service,** por exemplo).

![Diálogo de serviço conectado de referência do serviço web wcf](./media/convert-project-from-net-framework/connected-service-dialog.png)

Depois de selecionar o botão **Concluir,** um novo nó Serviços conectados é adicionado ao projeto e um arquivo Reference.cs é adicionado sob esse nó contendo o novo cliente .NET Standard WCF para acessar o serviço Bean Trader. Se você olhar `GetEndpointAddress` `GetBindingForEndpoint` para os métodos ou métodos nesse arquivo, você verá que as vinculações e os pontos finais agora são gerados programáticamente (em vez de via configuração de aplicativo). O recurso 'Adicionar serviços conectados' também pode adicionar referências a alguns pacotes System.ServiceModel no arquivo do projeto, que não são necessários, uma vez que todos os pacotes WCF necessários estão incluídos via Microsoft.Windows.Compatibilidade. Verifique o csproj para ver se `<PackageReference>` algum item extra do System.ServiceModel foi adicionado e, se for o caso, remova-os.

Nosso projeto tem novas classes de clientes WCF agora (em *Reference.cs),* mas também ainda tem as antigas (em BeanTrader.cs). Há duas opções neste momento:

- Se você quiser ser capaz de construir o projeto original .NET Framework (ao lado do `<Compile Remove="BeanTrader.cs" />` novo .NET Core-targeted), você pode usar um item no arquivo csproj do projeto .NET Core para que as versões .NET Framework e .NET Core do aplicativo usem diferentes clientes WCF. Isso tem a vantagem de deixar o projeto .NET Framework existente inalterado, mas tem a desvantagem de que o código que usa os clientes WCF gerados `#if` pode precisar ser ligeiramente diferente no caso .NET Core do que no projeto .NET Framework, então você provavelmente precisará usar diretivas para compilar condicionalmente algum uso de cliente wcf (criando clientes, por exemplo) para trabalhar de uma maneira quando construído para .NET Core e outra maneira quando construído para .NET Framework.

- Se, por outro lado, algum churn de código no projeto .NET Framework existente for aceitável, você poderá remover *BeanTrader.cs* todos juntos. Como o novo cliente WCF foi construído para o .NET Standard, ele funcionará tanto nos cenários .NET Core quanto no .NET Framework. Se você estiver construindo para o .NET Framework, além do .NET Core (seja por vários alvos ou por ter dois arquivos csproj), você pode usar este novo arquivo *Reference.cs* para ambos os alvos. Essa abordagem tem a vantagem de que o código não precisará bifurcar para suportar dois clientes WCF diferentes; o mesmo código será usado em todos os lugares. A desvantagem é que envolve alterar o projeto .NET Framework (presumivelmente estável).

No caso da amostra bean trader, você pode fazer pequenas alterações no projeto original se facilitar a migração, então siga estas etapas para conciliar o uso do cliente WCF:

01. Adicione o novo arquivo Reference.cs ao projeto .NET Framework *BeanTraderClient.csproj* usando o menu de contexto 'Adicionar item existente' do explorador de soluções. Certifique-se de adicionar 'como link' para que o mesmo arquivo seja usado por ambos os projetos (em vez de copiar o arquivo C#). Se você estiver construindo para o .NET Core e o .NET Framework com um único csproj (usando multi-targeting), então essa etapa não é necessária.

01. Excluir *BeanTrader.cs*.

01. O novo cliente WCF é semelhante ao antigo, mas vários namespaces no código gerado são diferentes. Por causa disso, é necessário atualizar o projeto para que os tipos de clientes WCF sejam usados a partir do BeanTrader.Service (ou qualquer nome de namespace que você escolheu) em vez de BeanTrader.Model ou sem um namespace. O Building *BeanTraderClient.Core.csproj* ajudará a identificar onde essas alterações precisam ser feitas. Correções serão necessárias tanto em C# quanto em arquivos de origem XAML.

01. Finalmente, você descobrirá que há um erro na *BeanTraderServiceClientFactory.cs* porque `BeanTraderServiceClient` os construtores disponíveis para o tipo mudaram. Costumava ser possível fornecer `InstanceContext` um argumento (que foi `CallbackHandler` criado `Castle.Windsor` usando um recipiente de IoC). Os novos construtores `CallbackHandler`criam novos s. Há, no entanto, `BeanTraderServiceClient`construtores do tipo base que correspondem ao que você quer. Uma vez que o código de cliente WCF gerado automaticamente existe em classes parciais, você pode facilmente ampliá-lo. Para fazer isso, crie um novo arquivo chamado *BeanTraderServiceClient.cs* e crie uma classe parcial com esse mesmo nome (usando o namespace beanTrader.Service). Em seguida, adicione um construtor ao tipo parcial como mostrado aqui.

    ```csharp
    public BeanTraderServiceClient(System.ServiceModel.InstanceContext callbackInstance) :
        base(callbackInstance, EndpointConfiguration.NetTcpBinding_BeanTraderService)
            { }
    ```

Com essas alterações feitas, a amostra bean trader agora estará usando um novo cliente WCF `Open` compatível com o `await OpenAsync` .NET Standard e você pode fazer a correção final de alterar a chamada em *TradingService.cs* usar em seu lugar.

Com os problemas do WCF resolvidos, a versão .NET Core da amostra Bean Trader agora é construída de forma limpa!

## <a name="runtime-testing"></a>Teste de tempo de execução

É fácil esquecer que o trabalho de migração não é feito assim que o projeto se constrói de forma limpa contra o .NET Core. É importante deixar tempo para testar o aplicativo portado, também. Uma vez que as coisas se construam com sucesso, certifique-se de que o aplicativo seja executado e funcione como esperado, especialmente se você estiver usando quaisquer pacotes direcionados ao .NET Framework.

Vamos tentar lançar o aplicativo Bean Trader portado e ver o que acontece. O aplicativo não vai longe antes de falhar com a seguinte exceção.

```output
System.Configuration.ConfigurationErrorsException: 'Configuration system failed to initialize'

Inner Exception
ConfigurationErrorsException: Unrecognized configuration section system.serviceModel.
```

Isso faz sentido, é claro. Lembre-se que o WCF não usa mais a configuração do aplicativo, então a seção old system.serviceModel do arquivo app.config precisa ser removida. O cliente WCF atualizado inclui todas as mesmas informações em seu código, de modo que a seção de configuração não é mais necessária. Se você quisesse que o ponto final do WCF fosse configurável no app.config, você poderia adicioná-lo como uma configuração de aplicativo e atualizar o código cliente WCF para recuperar o ponto final do serviço WCF da configuração.

Depois de remover a seção system.serviceModel do *app.config,* o aplicativo é iniciado com outra exceção quando um usuário faz o sinal.

```output
System.PlatformNotSupportedException: 'Operation is not supported on this platform.'
```

A API sem `Func<T>.BeginInvoke`suporte é . Como explicado em [dotnet/corefx#5940](https://github.com/dotnet/corefx/issues/5940), .NET `BeginInvoke` Core `EndInvoke` não suporta os métodos e métodos sobre tipos de delegados devido a dependências de remoção subjacentes. Este problema e sua correção são explicados com mais detalhes no Post de blog [Dom Migrando.BeginInvoke Calls for .NET Core,](https://devblogs.microsoft.com/dotnet/migrating-delegate-begininvoke-calls-for-net-core/) mas a essência é que `BeginInvoke` e `EndInvoke` as chamadas devem ser substituídas por `Task.Run` (ou alternativas assíncronas, se possível). Aplicando a solução geral `BeginInvoke` aqui, a chamada `Invoke` pode `Task.Run`ser substituída por uma chamada lançada por .

```csharp
Task.Run(() =>
{
    return userInfoRetriever.Invoke();
}).ContinueWith(result =>
{
    // BeginInvoke's callback is replaced with ContinueWith
    var task = result.ConfigureAwait(false);
    CurrentTrader = task.GetAwaiter().GetResult();
}, TaskScheduler.Default);
```

Depois de `BeginInvoke` remover o uso, o aplicativo Bean Trader é executado com sucesso no .NET Core!

![Bean Trader em execução no .NET Core](./media/convert-project-from-net-framework/running-on-core.png)

Todos os aplicativos são diferentes, então as etapas específicas necessárias para migrar seus próprios aplicativos para o .NET Core variam. Mas espero que a amostra do Bean Trader demonstre o fluxo de trabalho geral e os tipos de problemas que podem ser esperados. E, apesar do comprimento deste artigo, as mudanças reais necessárias na amostra do Bean Trader para fazê-lo funcionar no .NET Core foram bastante limitadas. Muitos aplicativos migram para o .NET Core da mesma forma; com mudanças limitadas ou mesmo sem mudanças de código necessárias.
