---
title: Registro em log com pilha elástica
description: Registro em log usando Stack elástico, Logstash e Kibana
ms.date: 09/23/2019
ms.openlocfilehash: b3fd3ea30f46914e6513be79f7d949499142b381
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182828"
---
# <a name="logging-with-elastic-stack"></a><span data-ttu-id="16708-103">Registro em log com pilha elástica</span><span class="sxs-lookup"><span data-stu-id="16708-103">Logging with Elastic Stack</span></span> 

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="16708-104">Há muitas boas ferramentas de registro em log centralizadas e elas variam de acordo com as ferramentas gratuitas de software livre, até opções mais caras.</span><span class="sxs-lookup"><span data-stu-id="16708-104">There are many good centralized logging tools and they vary in cost from being free, open-source tools, to more expensive options.</span></span> <span data-ttu-id="16708-105">Em muitos casos, as ferramentas gratuitas são tão boas ou melhores do que as ofertas pagas.</span><span class="sxs-lookup"><span data-stu-id="16708-105">In many cases, the free tools are as good as or better than the paid offerings.</span></span> <span data-ttu-id="16708-106">Uma dessas ferramentas é uma combinação de três componentes de código-fonte aberto: Pesquisa elástica, Logstash e Kibana.</span><span class="sxs-lookup"><span data-stu-id="16708-106">One such tool is a combination of three open-source components: Elastic search, Logstash, and Kibana.</span></span> <span data-ttu-id="16708-107">Coletivamente, essas ferramentas são conhecidas como pilha elástica ou pilha ELK.</span><span class="sxs-lookup"><span data-stu-id="16708-107">Collectively these tools are known as the Elastic Stack or ELK stack.</span></span>

## <a name="what-are-the-advantages-of-elastic-stack"></a><span data-ttu-id="16708-108">Quais são as vantagens da pilha elástica?</span><span class="sxs-lookup"><span data-stu-id="16708-108">What are the advantages of Elastic Stack?</span></span>

<span data-ttu-id="16708-109">A pilha elástica fornece registro em log centralizado de maneira econômica, escalonável e fácil de ser compatível com a nuvem.</span><span class="sxs-lookup"><span data-stu-id="16708-109">Elastic Stack provides centralized logging in a low-cost, scalable, cloud-friendly manner.</span></span> <span data-ttu-id="16708-110">Sua interface do usuário simplifica a análise de dados para que você possa passar o seu tempo coletando informações de seus dados em vez de combater uma interface desajeitado.</span><span class="sxs-lookup"><span data-stu-id="16708-110">Its user interface streamlines data analysis so you can spend your time gleaning insights from your data instead of fighting with a clunky interface.</span></span> <span data-ttu-id="16708-111">Ele dá suporte a uma ampla variedade de entradas, de forma que o aplicativo distribuído se estenda por mais e tipos diferentes de serviços, você pode esperar continuar a poder alimentar o log e os dados de métrica no sistema.</span><span class="sxs-lookup"><span data-stu-id="16708-111">It supports a wide variety of inputs so as your distributed application spans more and different kinds of services, you can expect to continue to be able to feed log and metric data into the system.</span></span> <span data-ttu-id="16708-112">A pilha elástica também dá suporte a pesquisas rápidas mesmo em grandes conjuntos de dados, possibilitando que até mesmo aplicativos grandes registrem dados detalhados e ainda possam ter visibilidade dele de forma eficaz.</span><span class="sxs-lookup"><span data-stu-id="16708-112">The Elastic Stack also supports fast searches even across large data sets, making it possible to for even large applications to log detailed data and still be able to have visibility into it in a performant fashion.</span></span>

## <a name="logstash"></a><span data-ttu-id="16708-113">Logstash</span><span class="sxs-lookup"><span data-stu-id="16708-113">Logstash</span></span>

<span data-ttu-id="16708-114">O primeiro componente é [Logstash](https://www.elastic.co/products/logstash).</span><span class="sxs-lookup"><span data-stu-id="16708-114">The first component is [Logstash](https://www.elastic.co/products/logstash).</span></span> <span data-ttu-id="16708-115">Essa ferramenta é usada para coletar informações de log de uma grande variedade de fontes diferentes.</span><span class="sxs-lookup"><span data-stu-id="16708-115">This tool is used to gather log information from a large variety of different sources.</span></span> <span data-ttu-id="16708-116">Por exemplo, Logstash pode ler logs do disco e também receber mensagens de bibliotecas de log, como [Serilog](https://serilog.net/).</span><span class="sxs-lookup"><span data-stu-id="16708-116">For instance, Logstash can read logs from disk and also receive messages from logging libraries like [Serilog](https://serilog.net/).</span></span> <span data-ttu-id="16708-117">O Logstash pode fazer alguma filtragem básica e expansão nos logs à medida que eles chegam.</span><span class="sxs-lookup"><span data-stu-id="16708-117">Logstash can do some basic filtering and expansion on the logs as they arrive.</span></span> <span data-ttu-id="16708-118">Por exemplo, se os logs contiverem endereços IP, Logstash poderá ser configurado para fazer uma pesquisa geográfica e obter um país ou até mesmo uma cidade de origem para essa mensagem.</span><span class="sxs-lookup"><span data-stu-id="16708-118">For instance, if your logs contain IP addresses then Logstash may be configured to do a geographical lookup and obtain a country or even city of origin for that message.</span></span> 

<span data-ttu-id="16708-119">Serilog é uma biblioteca de registro em log para linguagens .NET, que permite o registro em log com parâmetros.</span><span class="sxs-lookup"><span data-stu-id="16708-119">Serilog is a logging library for .NET languages, which allows for parameterized logging.</span></span> <span data-ttu-id="16708-120">Em vez de gerar uma mensagem de log textual que incorpore campos, os parâmetros são mantidos separados.</span><span class="sxs-lookup"><span data-stu-id="16708-120">Instead of generating a textual log message that embeds fields, parameters are kept separate.</span></span> <span data-ttu-id="16708-121">Isso permite a filtragem e a pesquisa mais inteligentes.</span><span class="sxs-lookup"><span data-stu-id="16708-121">This allows for more intelligent filtering and searching.</span></span> <span data-ttu-id="16708-122">Uma configuração de Serilog de exemplo para gravação em Logstash aparece na Figura 7-2.</span><span class="sxs-lookup"><span data-stu-id="16708-122">A sample Serilog configuration for writing to Logstash appears in Figure 7-2.</span></span>

```csharp
var log = new LoggerConfiguration()   
         .WriteTo.Http("http://localhost:8080")
         .CreateLogger();
```

<span data-ttu-id="16708-123">**Figura 7-2** Configuração de Serilog para gravar informações de log diretamente no logstash sobre HTTP</span><span class="sxs-lookup"><span data-stu-id="16708-123">**Figure 7-2** Serilog config for writing log information directly to logstash over HTTP</span></span>

<span data-ttu-id="16708-124">Logstash usaria uma configuração como a mostrada na Figura 7-3.</span><span class="sxs-lookup"><span data-stu-id="16708-124">Logstash would use a configuration like the one shown in Figure 7-3.</span></span> 

```
input {
    http {
        #default host 0.0.0.0:8080
        codec => json
    }
}

output {
    elasticsearch {
        hosts => "elasticsearch:9200"
        index=>"sales-%{+xxxx.ww}"
    }
}
```

<span data-ttu-id="16708-125">**Figura 7-3** -uma configuração de Logstash para consumir logs de Serilog</span><span class="sxs-lookup"><span data-stu-id="16708-125">**Figure 7-3** - A Logstash configuration for consuming logs from Serilog</span></span>

<span data-ttu-id="16708-126">Para cenários em que a manipulação de log extensa não é necessária, há uma alternativa ao Logstash conhecido como [batidas](https://www.elastic.co/products/beats).</span><span class="sxs-lookup"><span data-stu-id="16708-126">For scenarios where extensive log manipulation isn't needed there's an alternative to Logstash known as [Beats](https://www.elastic.co/products/beats).</span></span> <span data-ttu-id="16708-127">Os batidas são uma família de ferramentas que podem reunir uma grande variedade de dados de logs para dados de rede e informações de tempo de atividade.</span><span class="sxs-lookup"><span data-stu-id="16708-127">Beats is a family of tools that can gather a wide variety of data from logs to network data and uptime information.</span></span> <span data-ttu-id="16708-128">Muitos aplicativos usarão Logstash e batidas.</span><span class="sxs-lookup"><span data-stu-id="16708-128">Many applications will use both Logstash and Beats.</span></span>

<span data-ttu-id="16708-129">Depois que os logs forem coletados pelo Logstash, ele precisará de algum lugar para colocá-los.</span><span class="sxs-lookup"><span data-stu-id="16708-129">Once the logs have been gathered by Logstash, it needs somewhere to put them.</span></span> <span data-ttu-id="16708-130">Embora o Logstash dê suporte a muitas saídas diferentes, um dos mais empolgantes é a pesquisa elástica.</span><span class="sxs-lookup"><span data-stu-id="16708-130">While Logstash supports many different outputs, one of the more exciting ones is Elastic search.</span></span>

## <a name="elastic-search"></a><span data-ttu-id="16708-131">Pesquisa elástica</span><span class="sxs-lookup"><span data-stu-id="16708-131">Elastic search</span></span>

<span data-ttu-id="16708-132">A pesquisa elástica é um mecanismo de pesquisa poderoso que pode indexar logs à medida que eles chegam.</span><span class="sxs-lookup"><span data-stu-id="16708-132">Elastic search is a powerful search engine that can index logs as they arrive.</span></span> <span data-ttu-id="16708-133">Ele faz as consultas em execução nos logs rapidamente.</span><span class="sxs-lookup"><span data-stu-id="16708-133">It makes running queries against the logs quick.</span></span> <span data-ttu-id="16708-134">A pesquisa elástica pode lidar com enormes quantidades de logs e, em casos extremos, pode ser dimensionada horizontalmente em vários nós.</span><span class="sxs-lookup"><span data-stu-id="16708-134">Elastic search can handle huge quantities of logs and, in extreme cases, can be scaled out across many nodes.</span></span> 

<span data-ttu-id="16708-135">As mensagens de log que foram criadas para conter parâmetros ou que tiveram parâmetros divididos por meio deles por meio do processamento de Logstash podem ser consultadas diretamente à medida que Elasticsearch preserva essas informações.</span><span class="sxs-lookup"><span data-stu-id="16708-135">Log messages that have been crafted to contain parameters or that have had parameters split from them through Logstash processing, can be queried directly as Elasticsearch preserves this information.</span></span>

<span data-ttu-id="16708-136">Uma consulta que pesquisa as 10 principais páginas visitadas por `jill@example.com`, aparece na Figura 7-4.</span><span class="sxs-lookup"><span data-stu-id="16708-136">A query that searches for the top 10 pages visited by `jill@example.com`, appears in Figure 7-4.</span></span>

```
"query": {
    "match": {
      "user": "jill@example.com"
    }
  },
  "aggregations": {
    "top_10_pages": {
      "terms": {
        "field": "page",
        "size": 10
      }
    }
  }
```

<span data-ttu-id="16708-137">**Figura 7-4** -uma consulta Elasticsearch para localizar as 10 páginas principais visitadas por um usuário</span><span class="sxs-lookup"><span data-stu-id="16708-137">**Figure 7-4** - An Elasticsearch query for finding top 10 pages visited by a user</span></span>

## <a name="visualizing-information-with-kibana-web-dashboards"></a><span data-ttu-id="16708-138">Visualizando informações com painéis da Web do Kibana</span><span class="sxs-lookup"><span data-stu-id="16708-138">Visualizing information with Kibana web dashboards</span></span>

<span data-ttu-id="16708-139">O componente final da pilha é Kibana.</span><span class="sxs-lookup"><span data-stu-id="16708-139">The final component of the stack is Kibana.</span></span> <span data-ttu-id="16708-140">Essa ferramenta é usada para fornecer visualizações interativas em um painel da Web.</span><span class="sxs-lookup"><span data-stu-id="16708-140">This tool is used to provide interactive visualizations in a web dashboard.</span></span> <span data-ttu-id="16708-141">Os painéis podem ser criados mesmo por usuários que não são técnicos.</span><span class="sxs-lookup"><span data-stu-id="16708-141">Dashboards may be crafted even by users who are non-technical.</span></span> <span data-ttu-id="16708-142">A maioria dos dados residentes no índice Elasticsearch pode ser incluída nos painéis do Kibana.</span><span class="sxs-lookup"><span data-stu-id="16708-142">Most data that is resident in the Elasticsearch index, can be included in the Kibana dashboards.</span></span> <span data-ttu-id="16708-143">Usuários individuais podem ter diferentes desejos de Dashboard e o Kibana permite essa personalização por meio da permissão de painéis específicos do usuário.</span><span class="sxs-lookup"><span data-stu-id="16708-143">Individual users may have different dashboard desires and Kibana enables this customization through allowing user-specific dashboards.</span></span> 

## <a name="installing-elastic-stack-on-azure"></a><span data-ttu-id="16708-144">Instalando a pilha elástica no Azure</span><span class="sxs-lookup"><span data-stu-id="16708-144">Installing Elastic Stack on Azure</span></span>

<span data-ttu-id="16708-145">A pilha elástica pode ser instalada no Azure de várias maneiras.</span><span class="sxs-lookup"><span data-stu-id="16708-145">The Elastic stack can be installed on Azure in a number of ways.</span></span> <span data-ttu-id="16708-146">Como sempre, é possível [provisionar máquinas virtuais e instalar a pilha elástica diretamente](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-elasticsearch)nelas.</span><span class="sxs-lookup"><span data-stu-id="16708-146">As always, it's possible to [provision virtual machines and install Elastic Stack on them directly](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-elasticsearch).</span></span> <span data-ttu-id="16708-147">Essa opção é preferida por alguns usuários experientes, pois oferece o mais alto grau de personalização.</span><span class="sxs-lookup"><span data-stu-id="16708-147">This option is preferred by some experienced users as it offers the highest degree of customizability.</span></span> <span data-ttu-id="16708-148">A implantação na infraestrutura como um serviço introduz uma sobrecarga de gerenciamento significativa, forçando aqueles que tomam esse caminho para apropriar-se de todas as tarefas associadas à infraestrutura como um serviço, como proteger os computadores e manter-se atualizado com os patches.</span><span class="sxs-lookup"><span data-stu-id="16708-148">Deploying on infrastructure as a service introduces significant management overhead forcing those who take that path to take ownership of all the tasks associated with infrastructure as a service such as securing the machines and keeping up-to-date with patches.</span></span> 

<span data-ttu-id="16708-149">Uma opção com menos sobrecarga é fazer uso de um dos muitos contêineres do Docker nos quais a pilha elástica já foi configurada.</span><span class="sxs-lookup"><span data-stu-id="16708-149">An option with less overhead is to make use of one of the many Docker containers on which the Elastic Stack has already been configured.</span></span> <span data-ttu-id="16708-150">Esses contêineres podem ser descartados em um cluster kubernetes existente e executados junto com o código do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="16708-150">These containers can be dropped into an existing Kubernetes cluster and run alongside application code.</span></span> <span data-ttu-id="16708-151">O contêiner [sebp/Elk](https://elk-docker.readthedocs.io/) é um contêiner de pilha elástico bem documentado e testado.</span><span class="sxs-lookup"><span data-stu-id="16708-151">The [sebp/elk](https://elk-docker.readthedocs.io/) container is a well-documented and tested Elastic Stack container.</span></span>

<span data-ttu-id="16708-152">Outra opção é uma [oferta Elk como serviço anunciada recentemente](https://devops.com/logz-io-unveils-azure-open-source-elk-monitoring-solution/).</span><span class="sxs-lookup"><span data-stu-id="16708-152">Another option is a [recently announced ELK-as-a-service offering](https://devops.com/logz-io-unveils-azure-open-source-elk-monitoring-solution/).</span></span>

## <a name="references"></a><span data-ttu-id="16708-153">Referências</span><span class="sxs-lookup"><span data-stu-id="16708-153">References</span></span>

- [<span data-ttu-id="16708-154">Instalar pilha elástica no Azure</span><span class="sxs-lookup"><span data-stu-id="16708-154">Install Elastic Stack on Azure</span></span>](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-elasticsearch)

>[!div class="step-by-step"]
><span data-ttu-id="16708-155">[Anterior](observability-patterns.md)
>[Próximo](monitoring-azure-kubernetes.md)</span><span class="sxs-lookup"><span data-stu-id="16708-155">[Previous](observability-patterns.md)
[Next](monitoring-azure-kubernetes.md)</span></span>
