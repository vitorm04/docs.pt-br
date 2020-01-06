---
title: Resiliência da plataforma Azure
description: Arquitetando aplicativos .NET nativos da nuvem para o Azure | Resiliência de infraestrutura de nuvem com o Azure
ms.date: 06/30/2019
ms.openlocfilehash: 8b33c1cec1633c9fb25ae2b02e51f8be01c22941
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75337384"
---
# <a name="azure-platform-resiliency"></a>Resiliência da plataforma Azure

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Criar um aplicativo confiável na nuvem é diferente do desenvolvimento de aplicativos local tradicional. Embora historicamente você adquiriu um hardware de extremidade superior para escalar verticalmente, em um ambiente de nuvem, você escala horizontalmente. Em vez de tentar evitar falhas, o objetivo é minimizar seus efeitos e manter o sistema estável.

Dito isso, os aplicativos de nuvem confiáveis exibem características distintas:

- Eles são resilientes, recuperam-se normalmente de problemas e continuam a funcionar.
- Eles são altamente disponíveis (HA) e são executados conforme projetados em um estado íntegro sem tempo de inatividade significativo.

Entender como essas características funcionam em conjunto e como elas afetam o custo-é essencial para a criação de um aplicativo de nuvem confiável. Em seguida, veremos como você pode criar resiliência e disponibilidade em seus aplicativos nativos de nuvem aproveitando os recursos da nuvem do Azure.

## <a name="design-with-redundancy"></a>Design com redundância

As falhas variam no escopo do impacto. Uma falha de hardware, como um disco com falha, pode afetar um único nó em um cluster. Um comutador de rede com falha pode afetar um rack de servidor inteiro. Falhas menos comuns, como perda de energia, podem interromper um datacenter inteiro. Raramente, uma região inteira fica indisponível.

A [redundância](https://docs.microsoft.com/azure/architecture/guide/design-principles/redundancy) é uma maneira de fornecer resiliência do aplicativo. O nível exato de redundância necessário depende de seus requisitos de negócios e afetará o custo e a complexidade do seu sistema. Por exemplo, uma implantação de várias regiões é mais cara e mais complexa para ser gerenciada do que uma implantação de região única. Você precisará de procedimentos operacionais para gerenciar failover e failback. O custo adicional e a complexidade podem ser justificados para alguns cenários de negócios e para outros não.

Para arquitetar a redundância, você precisa identificar os caminhos críticos em seu aplicativo e, em seguida, determinar se há redundância em cada ponto do caminho? Se um subsistema falhar, o aplicativo fará failover para outra coisa? Por fim, você precisa de uma compreensão clara desses recursos incorporados à plataforma de nuvem do Azure que você pode aproveitar para atender aos seus requisitos de redundância. Aqui estão as recomendações para a arquitetura da redundância:

- *Implante várias instâncias de serviços.* Se seu aplicativo depender de uma única instância de um serviço, ele criará um único ponto de falha. O provisionamento de várias instâncias melhora a resiliência e a escalabilidade. Ao hospedar no serviço kubernetes do Azure, você pode configurar declarativamente instâncias redundantes (conjuntos de réplicas) no arquivo de manifesto kubernetes. O valor da contagem de réplicas pode ser gerenciado programaticamente, no portal ou por meio de recursos de dimensionamento automático, que serão discutidos posteriormente.

- *Aproveitando um balanceador de carga.* O balanceamento de carga distribui as solicitações do aplicativo para instâncias de serviço íntegra e remove automaticamente instâncias não íntegras da rotação. Ao implantar no kubernetes, o balanceamento de carga pode ser especificado no arquivo de manifesto kubernetes na seção serviços.

- *Planejar a implantação em multiregião.* Se seu aplicativo for implantado em uma única região e a região ficar indisponível, seu aplicativo também ficará indisponível. Isso pode ser inaceitável nos termos dos contratos de nível de serviço de seu aplicativo. Em vez disso, considere implantar seu aplicativo e seus serviços em várias regiões. Por exemplo, um cluster AKS (serviço de kubernetes do Azure) é implantado em uma única região. Para proteger seu sistema de uma falha regional, você pode implantar seu aplicativo em vários clusters AKS em regiões diferentes e usar o recurso de [regiões emparelhadas](https://buildazure.com/2017/01/06/azure-region-pairs-explained/) para coordenar as atualizações da plataforma e priorizar os esforços de recuperação.

- *Habilite [a replicação geográfica](https://docs.microsoft.com/azure/sql-database/sql-database-active-geo-replication).* A replicação geográfica para serviços, como o banco de dados SQL do Azure e o Cosmos DB criará réplicas secundárias de sua data em várias regiões. Embora os dois serviços repliquem automaticamente os dados na mesma região, a replicação geográfica protege você contra uma interrupção regional, permitindo o failover para uma região secundária. Outra prática recomendada para os centros de replicação geográfica em relação ao armazenamento de imagens de contêiner. Para implantar um serviço no AKS, você precisa armazenar e efetuar pull da imagem de um repositório. O registro de contêiner do Azure integra-se com o AKS e pode armazenar imagens de contêiner com segurança. Para melhorar o desempenho e a disponibilidade, considere a replicação geográfica de suas imagens para um registro em cada região em que você tenha um cluster AKS. Cada cluster AKS, em seguida, efetua pull das imagens de contêiner do registro de contêiner local em sua região, conforme mostrado na Figura 6-6:

![Recursos replicados entre regiões](./media/replicated-resources.png)

**Figura 6-6**. Recursos replicados entre regiões

- *Implemente um balanceador de carga de tráfego DNS.* O [Gerenciador de tráfego do Azure](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview) fornece alta disponibilidade para aplicativos críticos pelo balanceamento de carga no nível do DNS. Ele pode rotear o tráfego para diferentes regiões com base na geografia, no tempo de resposta do cluster e até mesmo na integridade do ponto de extremidade do aplicativo. Por exemplo, o Gerenciador de tráfego do Azure pode direcionar os clientes para a instância de aplicativo e cluster AKS mais próxima. Se você tiver vários clusters AKS em regiões diferentes, use o Gerenciador de tráfego para controlar como o tráfego flui para os aplicativos que são executados em cada cluster. A Figura 6-7 mostra esse cenário.

![AKS e Gerenciador de tráfego do Azure](./media/aks-traffic-manager.png)

**Figura 6-7**. AKS e Gerenciador de tráfego do Azure

## <a name="design-for-scalability"></a>Design para escalabilidade

A nuvem prospera no dimensionamento. A capacidade de aumentar/diminuir os recursos do sistema para lidar com a carga crescente/decrescente do sistema é um princípio fundamental da nuvem do Azure. Mas, para dimensionar um aplicativo com eficiência, você precisa compreender os recursos de dimensionamento de cada serviço do Azure que você inclui em seu aplicativo.  Aqui estão recomendações para implementar efetivamente o dimensionamento em seu sistema.

- *Design para dimensionamento.* Um aplicativo deve ser projetado para dimensionamento. Para iniciar, os serviços devem ser sem estado para que as solicitações possam ser roteadas para qualquer instância. Ter serviços sem estado também significa que a adição ou remoção de uma instância não afeta negativamente os usuários atuais.

- *Cargas de trabalho de partição*. A decomposição de domínios em microserviços independentes e autônomos permite que cada serviço seja dimensionado de forma independente dos outros. Normalmente, os serviços terão necessidades e requisitos de escalabilidade diferentes. O particionamento permite que você dimensione apenas o que precisa ser dimensionado sem o custo desnecessário de dimensionamento de um aplicativo inteiro.

- *Favorecer a expansão.* Os aplicativos baseados em nuvem favorecem a expansão dos recursos em oposição ao dimensionamento. A expansão (também conhecida como escala horizontal) envolve a adição de mais recursos de serviço a um sistema existente para atender e compartilhar um nível de desempenho desejado. O dimensionamento (também conhecido como dimensionamento vertical) envolve a substituição de recursos existentes por hardware mais potente (mais núcleos de disco, memória e processamento). A expansão pode ser invocada automaticamente com os recursos de dimensionamento automático disponíveis em alguns recursos de nuvem do Azure. Escalar horizontalmente em vários recursos também adiciona redundância ao sistema geral. Por fim, a expansão de um único recurso é normalmente mais cara do que escalar horizontalmente em muitos recursos menores. A Figura 6-8 mostra as duas abordagens:

![Escalar verticalmente versus escalar horizontalmente](./media/scale-up-scale-out.png)

**Figura 6-8.** Escalar verticalmente versus escalar horizontalmente

- *Dimensionar proporcionalmente.* Ao dimensionar um serviço, considere em termos de *conjuntos de recursos*. Se você fosse expandir drasticamente um serviço específico, que impacto teria em armazenamentos de dados de back-end, em caches e serviços dependentes? Alguns recursos, como Cosmos DB, podem ser expandidos proporcionalmente, enquanto muitos outros não podem. Você deseja garantir que não expanda um recurso para um ponto em que ele esgotará outros recursos associados.

- *Evite a afinidade.* Uma prática recomendada é garantir que um nó não exija afinidade local, geralmente chamado de *sessão adesiva*. Uma solicitação deve ser capaz de rotear para qualquer instância. Se você precisar manter o estado, ele deve ser salvo em um cache distribuído, como o [cache Redis do Azure](https://azure.microsoft.com/services/cache/).

- *Aproveite os recursos de dimensionamento automático da plataforma.* Use recursos internos de dimensionamento automático sempre que possível, em vez de mecanismos personalizados ou de terceiros. Sempre que possível, use regras de dimensionamento agendadas para garantir que os recursos estejam disponíveis sem um atraso de inicialização, mas adicione o dimensionamento automático reativo às regras conforme apropriado, para lidar com alterações inesperadas na demanda. Para obter mais informações, consulte [diretrizes de dimensionamento](https://docs.microsoft.com/azure/architecture/best-practices/auto-scaling)automático.

- *Escalar horizontalmente de forma agressiva.* Uma prática final seria escalar horizontalmente de forma agressiva para que você possa atender rapidamente a picos imediatos de tráfego sem perder negócios. E, em seguida, reduzir (ou seja, remover instâncias desnecessárias) de forma conservadora para manter o sistema estável. Uma maneira simples de implementar isso é definir o período de resfriamento, que é o tempo de espera entre as operações de dimensionamento, cinco minutos para adicionar recursos e até 15 minutos para remover instâncias.

## <a name="built-in-retry-in-services"></a>Repetição interna em serviços

Incentivamos a prática recomendada de implementar operações de repetição programáticas em uma seção anterior. Tenha em mente que muitos serviços do Azure e seus SDKs de cliente correspondentes também incluem mecanismos de repetição. A lista a seguir resume os recursos de repetição nos muitos dos serviços do Azure que são discutidos neste livro:

- *Azure Cosmos DB.* A classe <xref:Microsoft.Azure.Documents.Client.DocumentClient> da API do cliente desativa automaticamente as tentativas com falha. O número de repetições e o tempo de espera máximo são configuráveis. As exceções geradas pela API do cliente são solicitações que excedem a política de repetição ou erros não transitórios.

- *Cache Redis do Azure.* O cliente Redis StackExchange usa uma classe de Gerenciador de conexões que inclui novas tentativas em tentativas com falha. O número de repetições, a política de repetição específica e o tempo de espera são todos configuráveis.

- *Barramento de serviço do Azure.* O cliente do barramento de serviço expõe uma [classe RetryPolicy](xref:Microsoft.ServiceBus.RetryPolicy) que pode ser configurada com um intervalo de retirada, contagem de repetição e <xref:Microsoft.ServiceBus.RetryExponential.TerminationTimeBuffer%2A>, que especifica o tempo máximo que uma operação pode tomar. A política padrão é de nove tentativas de repetição máximas com um período de retirada de 30 segundos entre as tentativas.

- *Banco de Dados SQL do Azure.* O suporte de repetição é fornecido ao usar a biblioteca de [Entity Framework Core](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency) .

- *Armazenamento do Azure.* A biblioteca de cliente de armazenamento dá suporte a operações de repetição. As estratégias variam em tabelas de armazenamento do Azure, BLOBs e filas. Assim, as repetições alternativas alternam entre locais de serviços de armazenamento primários e secundários quando o recurso de redundância geográfica está habilitado.

- *Hubs de eventos do Azure.* A biblioteca de cliente do hub de eventos apresenta uma propriedade RetryPolicy, que inclui um recurso de retirada exponencial configurável.

>[!div class="step-by-step"]
>[Anterior](application-resiliency-patterns.md)
>[Próximo](resilient-communications.md)
