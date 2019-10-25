---
title: Kubernetes-gRPC para desenvolvedores do WCF
description: Executando ASP.NET Core serviços gRPC em um cluster kubernetes.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 819c761a7a55485612b7fb0c8b392971751d8724
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846635"
---
# <a name="kubernetes"></a>Kubernetes

Embora seja possível executar contêineres manualmente em hosts do Docker, para sistemas de produção confiáveis, é preferível usar um mecanismo de orquestração de contêiner para gerenciar várias instâncias em execução em vários servidores em um cluster. Há vários mecanismos de orquestração de contêiner disponíveis, incluindo kubernetes, Docker Swarm e Apache mesos. Mas desses mecanismos, o kubernetes está longe e distante do mais usado, portanto, será o foco deste capítulo.

O kubernetes inclui a seguinte funcionalidade:

- O **agendamento** executa contêineres em vários nós em um cluster, garantindo o uso equilibrado do recurso disponível, mantendo os contêineres em execução se houver interrupções e manipulando atualizações sem interrupção para novas versões de imagens ou novas configurações.
- As **verificações de integridade** monitoram contêineres para garantir o serviço contínuo.
- O **DNS & descoberta de serviço** manipula o roteamento entre serviços em um cluster.
- A **entrada** expõe os serviços selecionados externamente e geralmente fornece balanceamento de carga entre instâncias desses serviços.
- O **Gerenciamento de recursos** anexa recursos externos, como armazenamento a contêineres.

Este capítulo detalha como implantar um serviço de ASP.NET Core gRPC e um site que consome o serviço em um cluster kubernetes. O aplicativo de exemplo usado está disponível no repositório [dotnet-Architecture/grpc-for-WCF-Developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) no GitHub,

## <a name="kubernetes-terminology"></a>Terminologia do kubernetes

O kubernetes usa a *configuração de estado desejado*: a API é usada para descrever objetos como *pods*, *implantações* e *Serviços*, e o *plano de controle* cuida da implementação do estado desejado em todos os *nós* em um *cluster*. Um cluster kubernetes tem um nó *mestre* que executa a *API kubernetes*, que pode ser comunicada com programaticamente ou usando a ferramenta de linha de comando `kubectl`. `kubectl` pode criar e gerenciar objetos usando argumentos de linha de comando, mas funciona melhor com arquivos YAML que contêm dados de declaração para objetos kubernetes.

### <a name="kubernetes-yaml-files"></a>Arquivos kubernetes YAML

Cada arquivo kubernetes YAML terá pelo menos três propriedades de nível superior.

```yaml
apiVersion: v1
kind: Namespace
metadata:
  # Object properties
```

A propriedade `apiVersion` é usada para especificar qual versão (e qual API) o arquivo se destina. A propriedade `kind` especifica o tipo de objeto que o YAML representa. A propriedade `metadata` contém propriedades de objeto, como `name`, `namespace` ou `labels`.

A maioria dos arquivos kubernetes YAML também terá uma seção `spec` que descreve os recursos e a configuração necessários para criar o objeto.

### <a name="pods"></a>Pods

Pods são as unidades básicas de execução no kubernetes. Eles podem executar vários contêineres, mas também são usados para executar contêineres únicos. O pod também inclui todos os recursos de armazenamento exigidos pelo (s) contêiner (es) e o endereço IP da rede.

### <a name="services"></a>Serviços

Os serviços são metaobjetos que descrevem pods (ou conjuntos de Pods) e fornecem uma maneira de acessá-los no cluster, como o mapeamento de um nome de serviço para um conjunto de endereços IP Pod usando o serviço DNS do cluster.

### <a name="deployments"></a>Implantações

As implantações são os objetos de *estado descritos* para pods. Se você criar um pod manualmente, quando ele for encerrado, ele não será reiniciado. As implantações são usadas para informar ao cluster quais pods e quantas réplicas desses pods devem estar em execução no momento atual.

### <a name="other-objects"></a>Outros objetos

Os pods, serviços e implantações são apenas três dos tipos de objetos mais básicos. Há dezenas de outros tipos de objeto que são gerenciados por um cluster kubernetes. Para obter mais informações, consulte a documentação de [conceitos do kubernetes](https://kubernetes.io/docs/concepts/) .

### <a name="namespaces"></a>Namespaces

Os clusters kubernetes são projetados para serem dimensionados para centenas ou milhares de nós e executam números semelhantes de serviços. Para evitar conflitos entre nomes de objeto, os namespaces são usados para agrupar objetos juntos como parte de aplicativos maiores. Kubernetes próprios serviços executados em um namespace `default`. Todos os objetos de usuário devem ser criados em seus próprios namespaces para evitar possíveis conflitos com objetos padrão ou outros locatários no cluster.

## <a name="get-started-with-kubernetes"></a>Introdução ao kubernetes

Se você estiver executando o Docker desktop para Windows ou macOS, o kubernetes já estará disponível. Basta habilitá-lo na seção kubernetes da janela configurações.

![Habilitar kubernetes no Docker desktop](media/kubernetes/enable-kubernetes-docker-desktop.png)

Para executar um cluster kubernetes local no Linux, examine [minikube](https://github.com/kubernetes/minikube)ou [MicroK8s](https://microk8s.io/) se sua distribuição do Linux oferecer suporte a [snaps](https://snapcraft.io/).

Para verificar se o cluster está em execução e acessível, execute o comando `kubectl version`.

```console
kubectl version
Client Version: version.Info{Major:"1", Minor:"14", GitVersion:"v1.14.6", GitCommit:"96fac5cd13a5dc064f7d9f4f23030a6aeface6cc", GitTreeState:"clean", BuildDate:"2019-08-19T11:13:49Z", GoVersion:"go1.12.9", Compiler:"gc", Platform:"windows/amd64"}
Server Version: version.Info{Major:"1", Minor:"14", GitVersion:"v1.14.6", GitCommit:"96fac5cd13a5dc064f7d9f4f23030a6aeface6cc", GitTreeState:"clean", BuildDate:"2019-08-19T11:05:16Z", GoVersion:"go1.12.9", Compiler:"gc", Platform:"linux/amd64"}
```

Neste exemplo, a CLI do `kubectl` e o servidor kubernetes estão executando a versão 1.14.6. Cada versão do `kubectl` deve dar suporte à versão anterior e à próxima do servidor, de modo que `kubectl` 1,14 também deve funcionar com as versões 1,13 e 1,15 do servidor.

## <a name="run-services-on-kubernetes"></a>Executar serviços no kubernetes

O aplicativo de exemplo tem um diretório `kube` que contém três arquivos YAML. O arquivo de `namespace.yml` declara um namespace personalizado, `stocks`. O arquivo de `stockdata.yml` declara a implantação e o serviço para o aplicativo gRPC, e o arquivo de `stockweb.yml` declara a implantação e o serviço para um aplicativo Web MVC ASP.NET Core 3,0 que consome o serviço gRPC.

Para usar um arquivo de `YAML` com `kubectl`, use o comando `apply -f`.

```console
kubectl apply -f object.yml
```

O comando `apply` verificará a validade do arquivo YAML e exibirá todos os erros recebidos da API, mas não aguardará até que todos os objetos declarados no arquivo tenham sido criados, pois isso pode levar algum tempo. Use o comando `kubectl get` com os tipos de objeto relevantes para verificar a criação de objetos no cluster.

### <a name="the-namespace-declaration"></a>A declaração de namespace

A declaração de namespace é simples e requer apenas a atribuição de um `name`.

```yaml
apiVersion: v1
kind: Namespace
metadata:
  name: stocks
```

Use `kubectl` para aplicar o arquivo de `namespace.yml` e verificar se o namespace foi criado com êxito.

```console
> kubectl apply -f namespace.yml
namespace/stocks created

> kubectl get namespaces
NAME              STATUS   AGE
stocks            Active   2m53s
```

### <a name="the-stockdata-application"></a>O aplicativo StockData

O arquivo `stockdata.yml` declara dois objetos: uma implantação e um serviço.

#### <a name="the-stockdata-deployment"></a>A implantação do StockData

A parte de implantação fornece o `spec` para a implantação em si, incluindo o número de réplicas necessárias e um `template` para os objetos Pod a serem criados e gerenciados pela implantação. Observe que os objetos de implantação são gerenciados com a API do `apps`, conforme especificado em `apiVersion`, em vez da API principal do kubernetes.

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: stockdata
  namespace: stocks
spec:
  selector:
    matchLabels:
      run: stockdata
  replicas: 1
  template:
    metadata:
      labels:
        run: stockdata
    spec:
      containers:
      - name: stockdata
        image: stockdata:1.0.0
        imagePullPolicy: Never
        resources:
          limits:
            cpu: 100m
            memory: 100Mi
        ports:
        - containerPort: 80
```

A propriedade `spec.selector` é usada para fazer a correspondência de pods com a implantação. A propriedade de `metadata.labels` do pod deve corresponder à propriedade `matchLabels` ou a chamada à API falhará.

A seção `template.spec` declara o contêiner a ser executado. Ao trabalhar com um cluster kubernetes local, como o fornecido pela área de trabalho do Docker, você pode especificar imagens que foram criadas localmente, desde que tenham uma marca de versão.

> [!IMPORTANT]
> Por padrão, o kubernetes sempre verificará e tentará efetuar pull de uma nova imagem. Se não conseguir localizar a imagem em nenhum de seus repositórios conhecidos, a criação do pod falhará. Para trabalhar com imagens locais, defina o `imagePullPolicy` como `Never`.

A propriedade `ports` especifica quais portas de contêiner devem ser publicadas no pod.  A imagem de `stockservice` executa o serviço na porta HTTP padrão, portanto, a porta 80 é publicada.

A seção `resources` aplica limites de recursos ao contêiner em execução no pod. Essa é uma prática recomendada, pois impede que um pod individual consuma toda a CPU ou memória disponível em um nó.

> [!NOTE]
> ASP.NET Core 3,0 foi otimizado e ajustado para ser executado em contêineres limitados por recursos, e a imagem do Docker `dotnet/core/aspnet` define uma variável de ambiente para informar ao `dotnet` tempo de execução que ele está em um contêiner.

#### <a name="the-stockdata-service"></a>O serviço StockData

A parte de serviço do arquivo YAML declara o serviço que fornece acesso ao pods dentro do cluster.

```yaml
apiVersion: v1
kind: Service
metadata:
  name: stockdata
  namespace: stocks
spec:
  ports:
  - port: 80
  selector:
    run: stockdata
```

A especificação de serviço usa a propriedade `selector` para corresponder à execução `Pods`, nesse caso, procurando pods com um rótulo `run: stockdata`. Os `port` especificados em pods correspondentes são publicados pelo serviço nomeado. Outros pods em execução no namespace `stocks` podem acessar HTTP nesse serviço usando `http://stockdata` como o endereço. O pods em execução em outros namespaces pode usar o nome de host `http://stockdata.stocks`. Você pode controlar o acesso ao serviço de namespace cruzado usando [as políticas de rede](https://kubernetes.io/docs/concepts/services-networking/network-policies/).

#### <a name="deploy-the-stockdata-application"></a>Implantar o aplicativo StockData

Use `kubectl` para aplicar o arquivo de `stockdata.yml` e verificar se a implantação e o serviço foram criados.

```console
> kubectl apply -f .\stockdata.yml
deployment.apps/stockdata created
service/stockdata created

> kubectl get deployment stockdata --namespace stocks
NAME        READY   UP-TO-DATE   AVAILABLE   AGE
stockdata   1/1     1            1           17s

> kubectl get service stockdata --namespace stocks
NAME        TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)   AGE
stockdata   ClusterIP   10.97.132.103   <none>        80/TCP    33s
```

### <a name="the-stockweb-application"></a>O aplicativo StockWeb

O arquivo de `stockweb.yml` declara a implantação e o serviço para o aplicativo MVC.

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: stockweb
  namespace: stocks
spec:
  selector:
    matchLabels:
      run: stockweb
  replicas: 1
  template:
    metadata:
      labels:
        run: stockweb
    spec:
      containers:
      - name: stockweb
        image: stockweb:1.0.0
        imagePullPolicy: Never
        resources:
          limits:
            cpu: 100m
            memory: 100Mi
        ports:
        - containerPort: 80
        env:
        - name: StockData__Address
          value: "http://stockdata"
        - name: DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT
          value: "true"

---

apiVersion: v1
kind: Service
metadata:
  name: stockweb
  namespace: stocks
spec:
  type: NodePort
  ports:
  - port: 80
  selector:
    run: stockweb
```

#### <a name="environment-variables"></a>Variáveis de ambiente

A seção `env` do objeto de implantação especifica as variáveis de ambiente a serem definidas no contêiner que executa as imagens de `stockweb:1.0.0`.

A variável de ambiente **`StockData__Address`** será mapeada para o parâmetro de configuração `StockData:Address` graças ao provedor de configuração EnvironmentVariables. Essa configuração usa sublinhados duplos entre nomes para separar seções. O endereço usa o nome do serviço do `stockdata`, que está em execução no mesmo namespace kubernetes.

A variável de ambiente **`DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT`** define uma opção <xref:System.AppContext> que permite conexões http/2 não criptografadas para <xref:System.Net.Http.HttpClient>. Essa variável de ambiente é o equivalente à definição da opção no código, como mostrado aqui.

```csharp
AppContext.SetSwitch("System.Net.Http.SocketsHttpHandler.Http2UnencryptedSupport", true);
```

Usar uma variável de ambiente para a opção significa que a configuração pode ser facilmente alterada dependendo do contexto no qual o aplicativo está sendo executado.

#### <a name="service-types"></a>Tipos de serviço

Para tornar o aplicativo Web acessível de fora do cluster, a propriedade `type: NodePort` é usada. Esse tipo de propriedade faz com que o kubernetes publique a porta 80 no serviço em uma porta arbitrária nos soquetes de rede externa do cluster. A porta atribuída pode ser encontrada usando o comando `kubectl get service`.

O serviço de `stockdata` não deve ser acessível de fora do cluster, portanto, ele usou o tipo padrão, `ClusterIP`.

Os sistemas de produção provavelmente usarão um balanceador de carga integrado para expor aplicativos públicos a consumidores externos. Os serviços expostos dessa maneira devem usar o tipo de `LoadBalancer`.

Para obter mais informações sobre tipos de serviço, consulte a documentação de [serviços de publicação do kubernetes](https://kubernetes.io/docs/concepts/services-networking/service/#publishing-services-service-types) .

#### <a name="deploy-the-stockweb-application"></a>Implantar o aplicativo StockWeb

Use `kubectl` para aplicar o arquivo de `stockweb.yml` e verificar se a implantação e o serviço foram criados.

```console
> kubectl apply -f .\stockweb.yml
deployment.apps/stockweb created
service/stockweb created

> kubectl get deployment stockweb --namespace stocks
NAME       READY   UP-TO-DATE   AVAILABLE   AGE
stockweb   1/1     1            1           8s

> kubectl get service stockweb --namespace stocks
NAME       TYPE       CLUSTER-IP     EXTERNAL-IP   PORT(S)        AGE
stockweb   NodePort   10.106.141.5   <none>        80:32564/TCP   13s
```

A saída do comando `get service` mostra que a porta HTTP foi publicada na porta `32564` na rede externa; para o Docker desktop, esse será o localhost. O aplicativo pode ser acessado navegando até `http://localhost:32564`.

### <a name="testing-the-application"></a>Testando o aplicativo

O aplicativo StockWeb exibe uma lista de ações de NASDAQ que são recuperadas de um serviço de solicitação-resposta simples. Para fins de demonstração, cada linha também mostra a ID exclusiva da instância do serviço que a retornou.

![Captura de tela StockWeb](media/kubernetes/stockweb-screenshot.png)

Se o número de réplicas do serviço de `stockdata` foi aumentado, talvez você espere que o valor do **servidor** seja alterado de linha para linha, mas, na verdade, todos os registros 100 sempre são retornados da mesma instância. Se você atualizar a página a cada poucos segundos, a ID do servidor permanecerá a mesma. Por que isso acontece? Há dois fatores em jogo aqui.

Primeiro, o sistema de descoberta de serviço kubernetes usa o balanceamento de carga "Round-Robin" por padrão. Na primeira vez que o servidor DNS for consultado, ele retornará o primeiro endereço IP correspondente para o serviço. Na próxima vez, o próximo endereço IP na lista e assim por diante, até o final, em que ponto ele faz um loop de volta para o início.

Em segundo lugar, o `HttpClient` usado para o cliente gRPC do aplicativo StockWeb é criado e gerenciado pelo [ASP.NET Core HttpClientFactory](../microservices/implement-resilient-applications/use-httpclientfactory-to-implement-resilient-http-requests.md), e uma única instância desse cliente é usada para cada chamada à página. O cliente faz apenas uma pesquisa DNS, de modo que todas as solicitações são roteadas para o mesmo endereço IP. Além disso, como o `HttpClientHandler` é armazenado em cache por motivos de desempenho, várias solicitações em uma rápida sucessão *usarão o* mesmo endereço IP, até que a entrada DNS armazenada em cache expire ou a instância do manipulador seja descartada por algum motivo.

Isso significa que, por padrão, as solicitações para um serviço gRPC não são balanceadas em todas as instâncias desse serviço no cluster. Consumidores diferentes usarão instâncias diferentes, mas isso não garante uma boa distribuição de solicitações e um uso equilibrado de recursos.

O próximo capítulo, [malhas de serviço](service-mesh.md), veremos como resolver esse problema.

>[!div class="step-by-step"]
>[Anterior](docker.md)
>[Próximo](service-mesh.md)
