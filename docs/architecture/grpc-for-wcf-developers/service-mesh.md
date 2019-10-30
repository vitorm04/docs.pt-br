---
title: Malhas de serviço-gRPC para desenvolvedores do WCF
description: Usar uma malha de serviço para rotear e balancear solicitações para serviços gRPC em um cluster kubernetes.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 6bdfa57ba47ba0105092d1c140705599b7023c78
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73090179"
---
# <a name="service-meshes"></a>Malhas de serviço

Uma malha de serviço é um componente de infraestrutura que assume o controle das solicitações de serviço de roteamento em uma rede. As malhas de serviço podem lidar com todos os tipos de preocupações de nível de rede dentro de um cluster kubernetes, incluindo:

- Descoberta de serviço
- Balanceamento de carga
- Tolerância a falhas
- Criptografia
- Monitoramento

As malhas do serviço kubernetes funcionam adicionando um contêiner extra, chamado *proxy sidecar*, a cada pod incluído na malha. O proxy assume o tratamento de todas as solicitações de rede de entrada e saída, permitindo que a configuração e o gerenciamento de rede sejam mantidos separados dos contêineres de aplicativos e, em muitos casos, sem a necessidade de qualquer alteração no código do aplicativo.

Pegue o [exemplo do capítulo anterior](kubernetes.md#testing-the-application), em que as solicitações gRPC do aplicativo Web foram todas roteadas para uma única instância do serviço gRPC. Isso acontece porque o nome de host do serviço é resolvido para um endereço IP e esse endereço IP é armazenado em cache durante o tempo de vida da instância de `HttpClientHandler`. Pode ser possível contornar isso tratando as pesquisas de DNS manualmente ou criando vários clientes, mas isso complicaria consideravelmente o código do aplicativo sem adicionar nenhum valor comercial ou de cliente.

Usando uma malha de serviço, as solicitações do contêiner de aplicativo são enviadas para o proxy sidecar, que pode distribuí-las de forma inteligente em todas as instâncias do outro serviço. A malha também pode:

- Responda de forma direta às falhas de instâncias individuais de um serviço.
- Manipular semânticas de repetição para chamadas com falha ou tempos limite
- Redirecionar solicitações com falha para uma instância alternativa sem retornar ao aplicativo cliente.

A captura de tela a seguir mostra o aplicativo StockWeb em execução com a malha de serviço do Linkerd, sem alterações no código do aplicativo ou até mesmo a imagem do Docker que está sendo usada. A única alteração necessária foi a adição de uma anotação à implantação nos arquivos YAML para os serviços de `stockdata` e `stockweb`.

![StockWeb com malha de serviço](media/service-mesh/stockweb-servicemesh-screenshot.png)

Você pode ver na coluna servidor que as solicitações do aplicativo StockWeb foram roteadas para ambas as réplicas do serviço StockData, apesar de serem originadas de uma única instância de `HttpClient` no código do aplicativo. Na verdade, se você examinar o código, verá que todas as solicitações de 100 para o serviço StockData são feitas simultaneamente usando a mesma instância de `HttpClient`, mas com a malha de serviço, essas solicitações serão balanceadas em todas as instâncias de serviço, no entanto, estão disponíveis.

As malhas de serviço se aplicam somente ao tráfego em um cluster. Para clientes externos, consulte [o próximo capítulo, balanceamento de carga](load-balancing.md).

## <a name="service-mesh-options"></a>Opções de malha de serviço

Há três implementações de malha de serviço de uso geral disponíveis atualmente para uso com kubernetes: İSTİO, Linkerd e Consul Connect. Todos os três fornecem roteamento/proxy de solicitação, criptografia de tráfego, resiliência, autenticação de host para host e controle de tráfego.

Escolher uma malha de serviço depende de vários fatores:

- Os requisitos específicos da organização em relação aos custos, conformidade, planos de suporte pagos e assim por diante.
- A natureza do cluster, seu tamanho, o número de serviços implantados e o volume de tráfego na rede de cluster.
- Facilidade de implantar e gerenciar a malha e usá-la com serviços.

Mais informações sobre cada malha de serviço estão disponíveis em seus respectivos sites.

- [**İSTİO** -İSTİO.Io](https://istio.io)
- [**Linkerd** -linkerd.Io](https://linkerd.io)
- [**Consul** -Consul.Io/mesh.html](https://consul.io/mesh.html)

## <a name="example-add-linkerd-to-a-deployment"></a>Exemplo: Adicionar Linkerd a uma implantação

Neste exemplo, você aprenderá a usar a malha de serviço Linkerd com o aplicativo *StockKube* da [seção anterior](kubernetes.md).
Para seguir este exemplo, você precisará [instalar a CLI do Linkerd](https://linkerd.io/2/getting-started/#step-1-install-the-cli). Os binários do Windows podem ser baixados na seção versões do GitHub; Certifique-se de usar a versão **estável** mais recente e não uma das versões de borda.

Com a CLI do Linkerd instalada, siga as instruções [*introdução* no site da Linkerd] para instalar os componentes do Linkerd no cluster do kubernetes. As instruções são diretas e a instalação deve levar apenas alguns minutos em uma instância de kubernetes local.

### <a name="add-linkerd-to-kubernetes-deployments"></a>Adicionar Linkerd a implantações do kubernetes

A CLI do Linkerd fornece um comando `inject` para adicionar as seções e propriedades necessárias aos arquivos kubernetes. Você pode executar o comando e gravar a saída em um novo arquivo.

```console
linkerd inject stockdata.yml > stockdata-with-mesh.yml
linkerd inject stockweb.yml > stockweb-with-mesh.yml
```

Você pode inspecionar os novos arquivos para ver quais alterações foram feitas. Para objetos de implantação, uma anotação de metadados é adicionada para informar ao Linkerd para injetar um contêiner de proxy sidecar no pod quando ele é criado.

Também é possível canalizar a saída do comando `linkerd inject` para `kubectl` diretamente. Os comandos a seguir funcionarão no PowerShell ou em qualquer shell do Linux.

```console
linkerd inject stockdata.yml | kubectl apply -f -
linkerd inject stockweb.yml | kubectl apply -f -
```

### <a name="inspect-services-in-the-linkerd-dashboard"></a>Inspecionar serviços no painel do Linkerd

Inicie o painel do Linkerd usando a CLI do `linkerd`.

```console
linkerd dashboard
```

O painel fornece informações detalhadas sobre todos os serviços que estão conectados à malha.

![Painel do Linkerd mostrando aplicativos StockKube](media/service-mesh/linkerd-screenshot.png)

Se você aumentar o número de réplicas do serviço StockData gRPC, conforme mostrado no exemplo a seguir, e atualizar a página StockWeb no navegador, verá uma mistura de IDs na coluna servidor, indicando que as solicitações estão sendo atendidas por todas as instâncias disponíveis .

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
  replicas: 2 # Increase the target number of instances
  template:
    metadata:
      annotations:
        linkerd.io/inject: enabled
      creationTimestamp: null
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

>[!div class="step-by-step"]
>[Anterior](kubernetes.md)
>[Próximo](load-balancing.md)
