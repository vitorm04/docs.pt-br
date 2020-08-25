---
title: Como registrar em log com a pilha elástica
description: Registro em log usando Stack elástico, Logstash e Kibana
ms.date: 05/13/2020
ms.openlocfilehash: 32d9d0dae175d8d45d48b56d17f133b4cc432363
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811165"
---
# <a name="logging-with-elastic-stack"></a><span data-ttu-id="8e768-103">Como registrar em log com a pilha elástica</span><span class="sxs-lookup"><span data-stu-id="8e768-103">Logging with Elastic Stack</span></span>

<span data-ttu-id="8e768-104">Há muitas boas ferramentas de registro em log centralizadas e elas variam de acordo com as ferramentas gratuitas de software livre, até opções mais caras.</span><span class="sxs-lookup"><span data-stu-id="8e768-104">There are many good centralized logging tools and they vary in cost from being free, open-source tools, to more expensive options.</span></span> <span data-ttu-id="8e768-105">Em muitos casos, as ferramentas gratuitas são tão boas ou melhores do que as ofertas pagas.</span><span class="sxs-lookup"><span data-stu-id="8e768-105">In many cases, the free tools are as good as or better than the paid offerings.</span></span> <span data-ttu-id="8e768-106">Uma dessas ferramentas é uma combinação de três componentes de código-fonte aberto: pesquisa elástica, Logstash e Kibana.</span><span class="sxs-lookup"><span data-stu-id="8e768-106">One such tool is a combination of three open-source components: Elastic search, Logstash, and Kibana.</span></span>

<span data-ttu-id="8e768-107">Coletivamente, essas ferramentas são conhecidas como pilha elástica ou pilha ELK.</span><span class="sxs-lookup"><span data-stu-id="8e768-107">Collectively these tools are known as the Elastic Stack or ELK stack.</span></span>

## <a name="elastic-stack"></a><span data-ttu-id="8e768-108">Pilha elástica</span><span class="sxs-lookup"><span data-stu-id="8e768-108">Elastic Stack</span></span>

<span data-ttu-id="8e768-109">A pilha elástica é uma opção avançada para coletar informações de um cluster kubernetes.</span><span class="sxs-lookup"><span data-stu-id="8e768-109">The Elastic Stack is a powerful option for gathering information from a Kubernetes cluster.</span></span> <span data-ttu-id="8e768-110">O kubernetes dá suporte ao envio de logs para um ponto de extremidade Elasticsearch e, na [maioria das vezes](https://kubernetes.io/docs/tasks/debug-application-cluster/logging-elasticsearch-kibana/), tudo o que você precisa para começar é definir as variáveis de ambiente, conforme mostrado na Figura 7-5:</span><span class="sxs-lookup"><span data-stu-id="8e768-110">Kubernetes supports sending logs to an Elasticsearch endpoint, and for the [most part](https://kubernetes.io/docs/tasks/debug-application-cluster/logging-elasticsearch-kibana/), all you need to get started is to set the environment variables as shown in Figure 7-5:</span></span>

```kubernetes
KUBE_LOGGING_DESTINATION=elasticsearch
KUBE_ENABLE_NODE_LOGGING=true
```

<span data-ttu-id="8e768-111">**Figura 7-5**.</span><span class="sxs-lookup"><span data-stu-id="8e768-111">**Figure 7-5**.</span></span> <span data-ttu-id="8e768-112">Variáveis de configuração para kubernetes</span><span class="sxs-lookup"><span data-stu-id="8e768-112">Configuration variables for Kubernetes</span></span>

<span data-ttu-id="8e768-113">Isso instalará o Elasticsearch no cluster e o destino enviando todos os logs de cluster para ele.</span><span class="sxs-lookup"><span data-stu-id="8e768-113">This will install Elasticsearch on the cluster and target sending all the cluster logs to it.</span></span>

<span data-ttu-id="8e768-114">![Um exemplo de um painel de Kibana mostrando os resultados de uma consulta em relação a logs ingeridos da ](./media/kibana-dashboard.png)
 **figura kubernetes 7-6**.</span><span class="sxs-lookup"><span data-stu-id="8e768-114">![An example of a Kibana dashboard showing the results of a query against logs ingested from Kubernetes](./media/kibana-dashboard.png)
**Figure 7-6**.</span></span> <span data-ttu-id="8e768-115">Um exemplo de um painel de Kibana que mostra os resultados de uma consulta em relação aos logs que são ingeridos do kubernetes</span><span class="sxs-lookup"><span data-stu-id="8e768-115">An example of a Kibana dashboard showing the results of a query against logs that are ingested from Kubernetes</span></span>

## <a name="what-are-the-advantages-of-elastic-stack"></a><span data-ttu-id="8e768-116">Quais são as vantagens da pilha elástica?</span><span class="sxs-lookup"><span data-stu-id="8e768-116">What are the advantages of Elastic Stack?</span></span>

<span data-ttu-id="8e768-117">A pilha elástica fornece registro em log centralizado de maneira econômica, escalonável e fácil de ser compatível com a nuvem.</span><span class="sxs-lookup"><span data-stu-id="8e768-117">Elastic Stack provides centralized logging in a low-cost, scalable, cloud-friendly manner.</span></span> <span data-ttu-id="8e768-118">Sua interface do usuário simplifica a análise de dados para que você possa passar o seu tempo coletando informações de seus dados em vez de combater uma interface desajeitado.</span><span class="sxs-lookup"><span data-stu-id="8e768-118">Its user interface streamlines data analysis so you can spend your time gleaning insights from your data instead of fighting with a clunky interface.</span></span> <span data-ttu-id="8e768-119">Ele dá suporte a uma ampla variedade de entradas, de forma que o aplicativo distribuído se estenda por mais e tipos diferentes de serviços, você pode esperar continuar a poder alimentar o log e os dados de métrica no sistema.</span><span class="sxs-lookup"><span data-stu-id="8e768-119">It supports a wide variety of inputs so as your distributed application spans more and different kinds of services, you can expect to continue to be able to feed log and metric data into the system.</span></span> <span data-ttu-id="8e768-120">A pilha elástica também dá suporte a pesquisas rápidas mesmo em grandes conjuntos de dados, o que possibilita até que aplicativos grandes registrem dados detalhados e ainda possam ter visibilidade dele de forma eficaz.</span><span class="sxs-lookup"><span data-stu-id="8e768-120">The Elastic Stack also supports fast searches even across large data sets, making it possible even for large applications to log detailed data and still be able to have visibility into it in a performant fashion.</span></span>

## <a name="logstash"></a><span data-ttu-id="8e768-121">Logstash</span><span class="sxs-lookup"><span data-stu-id="8e768-121">Logstash</span></span>

<span data-ttu-id="8e768-122">O primeiro componente é [Logstash](https://www.elastic.co/products/logstash).</span><span class="sxs-lookup"><span data-stu-id="8e768-122">The first component is [Logstash](https://www.elastic.co/products/logstash).</span></span> <span data-ttu-id="8e768-123">Essa ferramenta é usada para coletar informações de log de uma grande variedade de fontes diferentes.</span><span class="sxs-lookup"><span data-stu-id="8e768-123">This tool is used to gather log information from a large variety of different sources.</span></span> <span data-ttu-id="8e768-124">Por exemplo, Logstash pode ler logs do disco e também receber mensagens de bibliotecas de log, como [Serilog](https://serilog.net/).</span><span class="sxs-lookup"><span data-stu-id="8e768-124">For instance, Logstash can read logs from disk and also receive messages from logging libraries like [Serilog](https://serilog.net/).</span></span> <span data-ttu-id="8e768-125">O Logstash pode fazer alguma filtragem básica e expansão nos logs à medida que eles chegam.</span><span class="sxs-lookup"><span data-stu-id="8e768-125">Logstash can do some basic filtering and expansion on the logs as they arrive.</span></span> <span data-ttu-id="8e768-126">Por exemplo, se os logs contiverem endereços IP, Logstash poderá ser configurado para fazer uma pesquisa geográfica e obter um país ou até mesmo uma cidade de origem para essa mensagem.</span><span class="sxs-lookup"><span data-stu-id="8e768-126">For instance, if your logs contain IP addresses then Logstash may be configured to do a geographical lookup and obtain a country or even city of origin for that message.</span></span>

<span data-ttu-id="8e768-127">Serilog é uma biblioteca de registro em log para linguagens .NET, que permite o registro em log com parâmetros.</span><span class="sxs-lookup"><span data-stu-id="8e768-127">Serilog is a logging library for .NET languages, which allows for parameterized logging.</span></span> <span data-ttu-id="8e768-128">Em vez de gerar uma mensagem de log textual que incorpore campos, os parâmetros são mantidos separados.</span><span class="sxs-lookup"><span data-stu-id="8e768-128">Instead of generating a textual log message that embeds fields, parameters are kept separate.</span></span> <span data-ttu-id="8e768-129">Isso permite a filtragem e a pesquisa mais inteligentes.</span><span class="sxs-lookup"><span data-stu-id="8e768-129">This allows for more intelligent filtering and searching.</span></span> <span data-ttu-id="8e768-130">Uma configuração de Serilog de exemplo para gravação em Logstash aparece na Figura 7-7.</span><span class="sxs-lookup"><span data-stu-id="8e768-130">A sample Serilog configuration for writing to Logstash appears in Figure 7-7.</span></span>

```csharp
var log = new LoggerConfiguration()
         .WriteTo.Http("http://localhost:8080")
         .CreateLogger();
```

<span data-ttu-id="8e768-131">**Figura 7-7**.</span><span class="sxs-lookup"><span data-stu-id="8e768-131">**Figure 7-7**.</span></span> <span data-ttu-id="8e768-132">Configuração de Serilog para gravar informações de log diretamente no logstash sobre HTTP</span><span class="sxs-lookup"><span data-stu-id="8e768-132">Serilog config for writing log information directly to logstash over HTTP</span></span>

<span data-ttu-id="8e768-133">Logstash usaria uma configuração como a mostrada na Figura 7-8.</span><span class="sxs-lookup"><span data-stu-id="8e768-133">Logstash would use a configuration like the one shown in Figure 7-8.</span></span>

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

<span data-ttu-id="8e768-134">**Figura 7-8**.</span><span class="sxs-lookup"><span data-stu-id="8e768-134">**Figure 7-8**.</span></span> <span data-ttu-id="8e768-135">Uma configuração do Logstash para o consumo de logs do Serilog</span><span class="sxs-lookup"><span data-stu-id="8e768-135">A Logstash configuration for consuming logs from Serilog</span></span>

<span data-ttu-id="8e768-136">Para cenários em que a manipulação de log extensa não é necessária, há uma alternativa ao Logstash conhecido como [batidas](https://www.elastic.co/products/beats).</span><span class="sxs-lookup"><span data-stu-id="8e768-136">For scenarios where extensive log manipulation isn't needed there's an alternative to Logstash known as [Beats](https://www.elastic.co/products/beats).</span></span> <span data-ttu-id="8e768-137">Os batidas são uma família de ferramentas que podem reunir uma grande variedade de dados de logs para dados de rede e informações de tempo de atividade.</span><span class="sxs-lookup"><span data-stu-id="8e768-137">Beats is a family of tools that can gather a wide variety of data from logs to network data and uptime information.</span></span> <span data-ttu-id="8e768-138">Muitos aplicativos usarão Logstash e batidas.</span><span class="sxs-lookup"><span data-stu-id="8e768-138">Many applications will use both Logstash and Beats.</span></span>

<span data-ttu-id="8e768-139">Depois que os logs forem coletados pelo Logstash, ele precisará de algum lugar para colocá-los.</span><span class="sxs-lookup"><span data-stu-id="8e768-139">Once the logs have been gathered by Logstash, it needs somewhere to put them.</span></span> <span data-ttu-id="8e768-140">Embora o Logstash dê suporte a muitas saídas diferentes, um dos mais empolgantes é a pesquisa elástica.</span><span class="sxs-lookup"><span data-stu-id="8e768-140">While Logstash supports many different outputs, one of the more exciting ones is Elastic search.</span></span>

## <a name="elastic-search"></a><span data-ttu-id="8e768-141">Pesquisa elástica</span><span class="sxs-lookup"><span data-stu-id="8e768-141">Elastic search</span></span>

<span data-ttu-id="8e768-142">A pesquisa elástica é um mecanismo de pesquisa poderoso que pode indexar logs à medida que eles chegam.</span><span class="sxs-lookup"><span data-stu-id="8e768-142">Elastic search is a powerful search engine that can index logs as they arrive.</span></span> <span data-ttu-id="8e768-143">Ele faz as consultas em execução nos logs rapidamente.</span><span class="sxs-lookup"><span data-stu-id="8e768-143">It makes running queries against the logs quick.</span></span> <span data-ttu-id="8e768-144">A pesquisa elástica pode lidar com enormes quantidades de logs e, em casos extremos, pode ser dimensionada horizontalmente em vários nós.</span><span class="sxs-lookup"><span data-stu-id="8e768-144">Elastic search can handle huge quantities of logs and, in extreme cases, can be scaled out across many nodes.</span></span>

<span data-ttu-id="8e768-145">As mensagens de log que foram criadas para conter parâmetros ou que tiveram parâmetros divididos por meio deles por meio do processamento de Logstash podem ser consultadas diretamente à medida que Elasticsearch preserva essas informações.</span><span class="sxs-lookup"><span data-stu-id="8e768-145">Log messages that have been crafted to contain parameters or that have had parameters split from them through Logstash processing, can be queried directly as Elasticsearch preserves this information.</span></span>

<span data-ttu-id="8e768-146">Uma consulta que pesquisa as 10 principais páginas visitadas por `jill@example.com` , aparece na figura 7-9.</span><span class="sxs-lookup"><span data-stu-id="8e768-146">A query that searches for the top 10 pages visited by `jill@example.com`, appears in Figure 7-9.</span></span>

```json
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

<span data-ttu-id="8e768-147">**Figura 7-9**.</span><span class="sxs-lookup"><span data-stu-id="8e768-147">**Figure 7-9**.</span></span> <span data-ttu-id="8e768-148">Uma consulta Elasticsearch para localizar as 10 páginas principais visitadas por um usuário</span><span class="sxs-lookup"><span data-stu-id="8e768-148">An Elasticsearch query for finding top 10 pages visited by a user</span></span>

## <a name="visualizing-information-with-kibana-web-dashboards"></a><span data-ttu-id="8e768-149">Visualizando informações com painéis da Web do Kibana</span><span class="sxs-lookup"><span data-stu-id="8e768-149">Visualizing information with Kibana web dashboards</span></span>

<span data-ttu-id="8e768-150">O componente final da pilha é Kibana.</span><span class="sxs-lookup"><span data-stu-id="8e768-150">The final component of the stack is Kibana.</span></span> <span data-ttu-id="8e768-151">Essa ferramenta é usada para fornecer visualizações interativas em um painel da Web.</span><span class="sxs-lookup"><span data-stu-id="8e768-151">This tool is used to provide interactive visualizations in a web dashboard.</span></span> <span data-ttu-id="8e768-152">Os painéis podem ser criados mesmo por usuários que não são técnicos.</span><span class="sxs-lookup"><span data-stu-id="8e768-152">Dashboards may be crafted even by users who are non-technical.</span></span> <span data-ttu-id="8e768-153">A maioria dos dados residentes no índice Elasticsearch pode ser incluída nos painéis do Kibana.</span><span class="sxs-lookup"><span data-stu-id="8e768-153">Most data that is resident in the Elasticsearch index, can be included in the Kibana dashboards.</span></span> <span data-ttu-id="8e768-154">Usuários individuais podem ter diferentes desejos de Dashboard e o Kibana permite essa personalização por meio da permissão de painéis específicos do usuário.</span><span class="sxs-lookup"><span data-stu-id="8e768-154">Individual users may have different dashboard desires and Kibana enables this customization through allowing user-specific dashboards.</span></span>

## <a name="installing-elastic-stack-on-azure"></a><span data-ttu-id="8e768-155">Instalando a pilha elástica no Azure</span><span class="sxs-lookup"><span data-stu-id="8e768-155">Installing Elastic Stack on Azure</span></span>

<span data-ttu-id="8e768-156">A pilha elástica pode ser instalada no Azure de várias maneiras.</span><span class="sxs-lookup"><span data-stu-id="8e768-156">The Elastic stack can be installed on Azure in a number of ways.</span></span> <span data-ttu-id="8e768-157">Como sempre, é possível [provisionar máquinas virtuais e instalar a pilha elástica diretamente](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-elasticsearch)nelas.</span><span class="sxs-lookup"><span data-stu-id="8e768-157">As always, it's possible to [provision virtual machines and install Elastic Stack on them directly](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-elasticsearch).</span></span> <span data-ttu-id="8e768-158">Essa opção é preferida por alguns usuários experientes, pois oferece o mais alto grau de personalização.</span><span class="sxs-lookup"><span data-stu-id="8e768-158">This option is preferred by some experienced users as it offers the highest degree of customizability.</span></span> <span data-ttu-id="8e768-159">A implantação na infraestrutura como um serviço introduz uma sobrecarga de gerenciamento significativa, forçando aqueles que tomam esse caminho para apropriar-se de todas as tarefas associadas à infraestrutura como um serviço, como proteger os computadores e manter-se atualizado com os patches.</span><span class="sxs-lookup"><span data-stu-id="8e768-159">Deploying on infrastructure as a service introduces significant management overhead forcing those who take that path to take ownership of all the tasks associated with infrastructure as a service such as securing the machines and keeping up-to-date with patches.</span></span>

<span data-ttu-id="8e768-160">Uma opção com menos sobrecarga é fazer uso de um dos muitos contêineres do Docker nos quais a pilha elástica já foi configurada.</span><span class="sxs-lookup"><span data-stu-id="8e768-160">An option with less overhead is to make use of one of the many Docker containers on which the Elastic Stack has already been configured.</span></span> <span data-ttu-id="8e768-161">Esses contêineres podem ser descartados em um cluster kubernetes existente e executados junto com o código do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8e768-161">These containers can be dropped into an existing Kubernetes cluster and run alongside application code.</span></span> <span data-ttu-id="8e768-162">O contêiner [sebp/Elk](https://elk-docker.readthedocs.io/) é um contêiner de pilha elástico bem documentado e testado.</span><span class="sxs-lookup"><span data-stu-id="8e768-162">The [sebp/elk](https://elk-docker.readthedocs.io/) container is a well-documented and tested Elastic Stack container.</span></span>

<span data-ttu-id="8e768-163">Outra opção é uma [oferta Elk como serviço anunciada recentemente](https://devops.com/logz-io-unveils-azure-open-source-elk-monitoring-solution/).</span><span class="sxs-lookup"><span data-stu-id="8e768-163">Another option is a [recently announced ELK-as-a-service offering](https://devops.com/logz-io-unveils-azure-open-source-elk-monitoring-solution/).</span></span>

## <a name="references"></a><span data-ttu-id="8e768-164">Referências</span><span class="sxs-lookup"><span data-stu-id="8e768-164">References</span></span>

- [<span data-ttu-id="8e768-165">Instalar pilha elástica no Azure</span><span class="sxs-lookup"><span data-stu-id="8e768-165">Install Elastic Stack on Azure</span></span>](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-elasticsearch)

>[!div class="step-by-step"]
><span data-ttu-id="8e768-166">[Anterior](observability-patterns.md) 
> [Avançar](monitoring-azure-kubernetes.md)</span><span class="sxs-lookup"><span data-stu-id="8e768-166">[Previous](observability-patterns.md)
[Next](monitoring-azure-kubernetes.md)</span></span>
