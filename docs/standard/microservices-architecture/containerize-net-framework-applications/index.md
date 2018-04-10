---
title: Migrando aplicativos monolíticos herdados do Framework .NET para contêineres do Windows
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Migrando aplicativos monolíticos herdados do Framework .NET para contêineres do Windows
keywords: Docker, Microsserviços, ASP.NET, Contêiner
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c88027156b55829f77357c1fdb1aef01a802b88a
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="migrating-legacy-monolithic-net-framework-applications-to-windows-containers"></a>Migrando aplicativos monolíticos herdados do Framework .NET para contêineres do Windows

*Os contêineres do Windows podem ser usados como uma maneira de melhorar os ambientes de desenvolvimento e teste e para implantar aplicativos baseados em tecnologias herdadas do .NET Framework como Web* *Forms. Usar contêineres para aplicativos herdados dessa maneira é conhecido como um cenário de "lift-and-shift".*

As seções anteriores deste guia defenderam uma arquitetura de microsserviços na qual os aplicativos de negócios são distribuídos entre diferentes contêineres, cada um executando um serviço pequeno e concentrado. Essa meta traz muitos benefícios. No novo desenvolvimento, essa abordagem é altamente recomendável. Os aplicativos críticos para a empresa também serão beneficiados o suficiente para justificar o custo de uma nova arquitetura e de uma reimplementação.

Mas nem todos os aplicativos serão beneficiados o suficiente para justificar o custo. Isso não significa que esses aplicativos não podem ser usados em cenários de contêiner.

Nesta seção, vamos explorar um aplicativo para eShopOnContainers, mostrado na Figura 7-1. Este aplicativo seria usado por membros da equipe corporativa eShopOnContainers para exibir e editar o catálogo de produtos.

![](./media/image1.png)

**Figura 7-1**. Aplicativo Web Forms do ASP.NET (tecnologia herdada) em um contêiner do Windows

Este é um aplicativo Web Forms usado para navegar e modificar as entradas no catálogo. A dependência do Web Forms significa que este aplicativo não será executado no .NET Core, a menos que ele seja reescrito sem o Web Forms e use o ASP.NET Core MVC. Você verá como é possível executar aplicativos como esses em contêineres sem alterações. Você também verá como é possível fazer alterações mínimas para trabalhar em um modo híbrido, no qual algumas funcionalidades são movidas para um microsserviço separado, mas a maior parte das funcionalidades permanece no aplicativo monolítico.

## <a name="benefits-of-containerizing-a-monolithic-application"></a>Benefícios de inserir um aplicativo monolítico em contêineres

O aplicativo Catalog.WebForms está disponível no repositório eShopOnContainers do GitHub (<https://github.com/dotnet/eShopOnContainers>). Este aplicativo é um aplicativo Web autônomo que acessa um armazenamento de dados de alta disponibilidade. Mesmo assim, há vantagens de executar o aplicativo em um contêiner. Você cria uma imagem para o aplicativo. A partir desse ponto, cada implantação é executada no mesmo ambiente. Cada contêiner usa a mesma versão do sistema operacional, tem a mesma versão das dependências instaladas, usa a mesma estrutura e é criado usando o mesmo processo. Veja o aplicativo carregado no Visual Studio 2017 na Figura 7-2.

![](./media/image2.png)

**Figura 7-2**. Aplicativo Web Forms de gerenciamento de catálogo no Visual Studio 2017

Além disso, os desenvolvedores podem executar o aplicativo nesse ambiente consistente. Os problemas que só aparecem com determinadas versões aparecerão imediatamente para os desenvolvedores em vez de surgirem em um ambiente de preparo ou de produção. As diferenças entre os ambientes de desenvolvimento entre a equipe de desenvolvimento perdem importância quando os aplicativos passam a ser executados em contêineres.

Finalmente, os aplicativos em contêineres têm uma curva de escala horizontal mais simples. Você já aprendeu como os aplicativos em contêineres permitem mais contêineres em uma VM ou em um computador físico. Isso resulta em maior densidade e menos necessários recursos.

Por esses motivos, considere a possibilidade de executar aplicativos monolíticos herdados em um contêiner de Docker usando uma operação “lift-and-shift”. A frase “lift-and-shift” descreve o escopo da tarefa: você *levanta* todo o aplicativo de um computador físico ou máquina virtual e *coloca-o* em um contêiner. Em situações ideais, não é necessário alterar o código do aplicativo para executá-lo em um contêiner.

## <a name="possible-migration-paths"></a>Caminhos de migração possíveis

Como um aplicativo monolítico, o aplicativo Catalog.Webforms é um único aplicativo Web que contém todo o código, incluindo as bibliotecas de acesso a dados. O banco de dados é executado em um computador separado de alta disponibilidade. Essa configuração é simulada no código de exemplo, usando um serviço de catálogo fictício: você pode executar o aplicativo Catalog.WebForms com esses dados falsos para simular um cenário de lift-and-shift simples. Isso demonstra o caminho de migração mais simples, no qual você move os ativos existentes para serem executados em um contêiner sem nenhuma alteração de código. Esse caminho é adequado para aplicativos que estão completos e que têm uma interação mínima com a funcionalidade que você está movendo para microsserviços.

No entanto, o site eShopOnContainers já está acessando o armazenamento de dados usando microsserviços para cenários diferentes. Podem ser feitas algumas pequenas alterações adicionais no editor de catálogo para aproveitar o microsserviço de catálogo em vez de acessar o armazenamento de dados de catálogo diretamente.

Essas alterações demonstram a continuidade para seus próprios aplicativos. Você pode fazer qualquer coisa como colocar em contêineres um aplicativo existente sem alteração, fazer pequenas alterações para permitir que os aplicativos existentes acessem alguns dos novos microsserviços e reescrever completamente um aplicativo para participar totalmente de uma nova arquitetura baseada em microsserviço. O caminho certo depende do custo de migração e dos benefícios da migração.

## <a name="application-tour"></a>Tour do aplicativo

Você pode carregar a solução Catalog.WebForms e executar o aplicativo como um aplicativo autônomo. Nessa configuração, em vez de um banco de dados do armazenamento persistente, o aplicativo usa um serviço fictício para retornar dados. O aplicativo usa o Autofac (<https://autofac.org/>) como um contêiner de IOC (inversão de controle). Usando a DI (injeção de dependência), você pode configurar o aplicativo para usar os dados fictícios ou o serviço de dados de catálogo ativo. (Explicaremos mais sobre a DI em breve.) O código de inicialização lê uma configuração de useFake dos arquivos web.config e configura o contêiner Autofac para injetar o serviço de dados fictícios ou o serviço de catálogo ativo. Ao executar o aplicativo com useFake definido como false no arquivo web.config, você verá o aplicativo Web Forms exibindo os dados do catálogo.

A maioria das técnicas usadas neste aplicativo é muito familiar para qualquer pessoa que já tenha usado o Web Forms. No entanto, o microsserviço de catálogo apresenta duas técnicas que podem não ser familiares: a DI (injeção de dependência), já mencionada anteriormente e o trabalho com armazenamentos de dados assíncronos no Web Forms.

A DI inverte a estratégia controlada por objeto típica de escrever classes que alocam todos os recursos necessários. Em vez disso, as classes solicitam suas dependências de um contêiner de serviço. A vantagem da DI é que você pode substituir a serviços externos por elementos fictícios (simulações) para dar suporte a ambientes de teste ou outros.

O contêiner de DI usa a configuração appSettings do web.config para controlar se deseja usar os dados do catálogo fictícios ou os dados ativos do serviço em execução. O aplicativo registra um objeto HttpModule que cria o contêiner e registra um manipulador de pré-solicitação para injetar dependências. Você pode ver esse código no arquivo Modules/AutoFacHttpModule.cs, que é semelhante ao exemplo a seguir:

```cs
private static IContainer CreateContainer()
{
  // Configure AutoFac:
  // Register Containers:

  var settings = WebConfigurationManager.AppSettings;
  var useFake = settings["usefake"];
  bool fake = useFake == "true";
  var builder = new ContainerBuilder();

  if (fake)
  {
    builder.RegisterType<CatalogMockService>()
    .As<ICatalogService>();
  }
  else
  {
    builder.RegisterType<CatalogService>()
    .As<ICatalogService>();
    builder.RegisterType<RequestProvider>()
    .As<IRequestProvider>();
  }

  var container = builder.Build();
  return container;
}

private void InjectDependencies()
{
  if (HttpContext.Current.CurrentHandler is Page page)
  {
    // Get the code-behind class that we may have written
    var pageType = page.GetType().BaseType;

    // Determine if there is a constructor to inject, and grab it
    var ctor = (from c in pageType.GetConstructors()
                where c.GetParameters().Length > 0
                select c).FirstOrDefault();

    if (ctor != null)
    {
      // Resolve the parameters for the constructor
      var args = (from parm in ctor.GetParameters()
                  select Container.Resolve(parm.ParameterType))
                  .ToArray();

      // Execute the constructor method with the arguments resolved
      ctor.Invoke(page, args);
    }

    // Use the Autofac method to inject any
    // properties that can be filled by Autofac
    Container.InjectProperties(page);
  }
}
```

As páginas do aplicativo (Default.aspx.cs e EditPage.aspx.cs) definem os construtores que usam essas dependências. Observe que o construtor padrão ainda está presente e acessível. A infraestrutura precisa do código a seguir.

```cs
protected _Default() { }

public _Default(ICatalogService catalog) => this.catalog = catalog;
```

As APIs de catálogo são métodos assíncronos. Agora o Web Forms dá suporte para todos os controles de dados. O aplicativo Catalog.WebForms usa associação de modelos para as páginas de lista e de edição. Os controles nas páginas definem as propriedades UpdateMethod, SelectMethod, InsertMethod e DeleteMethod que especificam operações assíncronas de retorno de tarefa. Os controles do Web Forms entendem quando os métodos associados a um controle são assíncronos. A única restrição encontrada ao usar os métodos de seleção assíncronos é que não há suporte para paginação. A assinatura de paginação requer um parâmetro de saída e os métodos assíncronos não podem ter parâmetros de saída. Essa mesma técnica é usada em outras páginas que exigem dados do serviço de catálogo.

A configuração padrão para aplicativos Web Forms de catálogo usa uma implementação fictícia do serviço catalog.api. Essa implementação fictícia usa um conjunto de dados embutido em código para seus dados, o que simplifica algumas tarefas por remover a dependência do serviço catalog.api em ambientes de desenvolvimento.

## <a name="lifting-and-shifting"></a>Levantando e mudando

O Visual Studio fornece um excelente suporte para colocar um aplicativo em contêineres. Clique com botão direito do mouse no nó do projeto e, em seguida, selecione **Adicionar** e **Suporte ao Docker**. O modelo de projeto do Docker adiciona um novo projeto à solução chamado **docker-compose**. O projeto contém os ativos do Docker que compõem (ou compilam) as imagens necessárias e começa a executar os contêineres necessários, conforme é mostrado na Figura 7-3.

Nos cenários lift-and-shift mais simples, o aplicativo será o único serviço que você usará para o aplicativo Web Forms. O modelo também altera o projeto de inicialização para apontar para o projeto **docker-compose**. Pressionar Ctrl + F5 ou F5 agora cria a imagem do Docker e inicia o contêiner do Docker.

![](./media/image3.png)

**Figura 7-3**. O projeto **docker-compose** na solução do Web Forms

Antes de executar a solução, você deve configurar o Docker para usar contêineres do Windows. Para fazer isso, clique com botão direito do mouse no ícone de barra de tarefas do Docker no Windows e selecione **Alternar para Contêineres do Windows**, conforme é mostrado na Figura 7-4.

![](./media/image4.png)

**Figura 7-4**. Alternando para contêineres do Windows pelo ícone de barra de tarefas do Docker no Windows

Se o item de menu mostrar **Alternar para Contêineres do Linux**, você já estará executando o Docker com contêineres do Windows.

Executar a solução reinicia o host do Docker. Ao compilar, você compila o aplicativo e a imagem do Docker para o projeto do Web Forms. A primeira vez que você fizer isso levará um tempo considerável. Isso ocorre porque o processo de build extrai a imagem base do Windows Server e a imagem adicional do ASP.NET. Os próximos ciclos de build e execução serão muito mais rápidos.

Vamos fazer uma análise mais profunda dos arquivos adicionados pelo modelo de projeto do Docker. Ele criou vários arquivos para você. O Visual Studio usa esses arquivos para criar a imagem do Docker e iniciar um contêiner. Você pode usar os mesmos arquivos da CLI para executar os comandos do Docker manualmente.

O exemplo de Dockerfile a seguir mostra as configurações básicas para compilar uma imagem do Docker com base na imagem do ASP.NET do Windows que executa um site ASP.NET.

```
FROM microsoft/aspnet

ARG source

WORKDIR /inetpub/wwwroot

COPY ${source:-obj/Docker/publish} .
```

Este Dockerfile será muito semelhante ao que é criado para executar um aplicativo ASP.NET Core em contêineres do Linux. No entanto, há algumas diferenças importantes. A diferença mais importante é que a imagem base é microsoft/aspnet, que é a imagem atual do Windows Server que inclui o .NET Framework. Outras diferenças são que os diretórios copiados do seu diretório de origem são diferentes.

Os outros arquivos do projeto **docker-compose** são os ativos do Docker necessários para criar e configurar os contêineres. O Visual Studio coloca os diversos arquivos docker-compose.yml em um único nó para realçar como eles são usados. O arquivo base docker-compose contém as diretivas que são comuns a todas as configurações. O arquivo docker-compose.override.yml contém variáveis de ambiente e as substituições relacionadas para uma configuração de desenvolvedor. As variantes com .vs.debug e .vs.release fornecem configurações de ambiente que permitem que o Visual Studio seja anexado ao contêiner em execução e o gerencie.

Embora a integração do Visual Studio faça parte da adição do suporte ao Docker na sua solução, você também pode criar e executar na linha de comando usando o comando docker-compose up, como você viu nas seções anteriores.

## <a name="getting-data-from-the-existing-catalog-net-core-microservice"></a>Obtendo dados do microsserviço de catálogo existente do .NET Core

Você pode configurar o aplicativo Web Forms para usar o microsserviço de catálogo eShopOnContainers para obter os dados em vez de usar dados fictícios. Para fazer isso, você pode editar o arquivo web.config e definir o valor da chave useFake como false. O contêiner de DI usará a classe que acessa o microsserviço de catálogo ativo em vez da classe que retorna os dados embutidos em código. Nenhuma outra alteração de código será necessária.

Acessar o serviço de catálogo ativo significa que você precisa atualizar o projeto **docker-compose** para compilar a imagem do serviço de catálogo e iniciar o contêiner do serviço de catálogo. O Docker CE para Window dá suporte a contêineres do Linux e contêineres do Windows, mas não para ambos ao mesmo tempo. Para executar o microsserviço de catálogo, você precisa compilar uma imagem que execute o microsserviço de catálogo com base em um contêiner baseado em Windows. Essa abordagem requer um Dockerfile diferente para o projeto microsserviços que você viu nas seções anteriores. O arquivo Dockerfile.windows contém as definições de configuração para compilar a imagem de contêiner da API de catálogo para executar em um contêiner do Windows, por exemplo, para usar uma imagem do Docker do Windows Nano.

O microsserviço de catálogo depende do banco de dados do SQL Server. Portanto, você também precisa usar uma imagem do Docker do SQL Server baseado em Windows.

Após essas alterações, o projeto docker-compose fará algo mais para iniciar o aplicativo. O projeto agora inicia o SQL Server usando a imagem do SQL Server baseado em Windows. Ele inicia o microsserviço de catálogo em um contêiner do Windows. E também inicia o contêiner do editor de catálogo do Web Forms em um contêiner do Windows. Se uma das imagens precisar de build, as imagens serão criadas primeiro.

## <a name="development-and-production-environments"></a>Ambientes de desenvolvimento e produção

Há algumas diferenças entre a configuração de desenvolvimento e uma configuração de produção. No ambiente de desenvolvimento, você executa o aplicativo Web Forms, o microsserviço de catálogo e o SQL Server nos contêineres do Windows, como parte do mesmo host do Docker. Nas seções anteriores, mencionamos que as imagens do SQL Server são implantadas no mesmo host do Docker que os outros serviços baseados em .NET Core em um host do Docker baseado em Linux. A vantagem de executar vários microservices no mesmo host (ou cluster) do Docker é que há menos comunicação de rede e a comunicação entre contêineres tem uma latência menor.

No ambiente de desenvolvimento, você deve executar todos os contêineres no mesmo sistema operacional. O Docker CE para Windows não dá suporte para execução de contêineres baseados em Windows e em Linux ao mesmo tempo. Em produção, você pode decidir se deseja executar o microsserviço de catálogo em um contêiner do Windows em um único host (ou cluster) do Docker ou fazer com que o aplicativo Web Forms se comunique com uma instância de microsserviço de catálogo em execução em um contêiner do Linux em um host do Docker diferente. Isso depende de como você deseja otimizar a latência da rede. Na maioria dos casos, convém que os microsserviços dos quais os aplicativos dependem sejam executado no mesmo host (ou nuvem) do Docker para facilitar a implantação e reduzir a latência de comunicação. Nessas configurações, as únicas comunicações de alto custo são as que ocorrem entre as instâncias de microsserviços e os servidores de alta disponibilidade do armazenamento de dados persistentes.

>[!div class="step-by-step"]
[Previous] (../net-core-single-containers-linux-windows-server-hosts/index.md) [Next] (../multi-container-microservice-net-applications/index.md)
