---
title: Comparar e deslocar aplicativos existentes do Azure IaaS
description: "Modernize aplicativos existentes do .NET com contêineres do Windows e de nuvem do Azure."
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: eed17ad06c138c3a4eb85f5e023427b681488784
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="lift-and-shift-existing-apps-azure-iaas"></a>Comparar e deslocar aplicativos existentes do Azure IaaS

> Visão: como uma primeira etapa, para reduzir o custo de investimento e total de local de hardware e rede de manutenção, simplesmente novo host seus aplicativos existentes na nuvem.

Antes de entrar em *como* para migrar seus aplicativos existentes para a infraestrutura do Azure como uma plataforma de serviço (IaaS), é importante analisar as razões *por* você deseja migrar diretamente para o IaaS no Azure. O cenário neste nível de maturidade modernização é essencialmente começar a usar máquinas virtuais na nuvem, em vez de continuar a usar sua infraestrutura local.

Outro ponto para analisar é *por* deseja migrar para a nuvem de IaaS puro, em vez de apenas adicionar mais avançados de serviços gerenciados no Azure. Você precisa determinar quais casos podem exigir IaaS em primeiro lugar.

Figura 2-1 posiciona aplicativos prontos para nuvem infraestrutura nos níveis de maturidade modernização:

![Aplicativos prontos para nuvem infra-estrutura de posicionamento](./media/image2-1.png)

> **Figura 2-1.** Aplicativos prontos para nuvem infra-estrutura de posicionamento

## <a name="why-migrate-existing-net-web-applications-to-azure-iaas"></a>Por que migrar aplicativos de web existentes do .NET para Azure IaaS 

É o principal motivo para migrar para a nuvem, mesmo em um nível de IaaS inicial reduzir os custos. Usando mais serviços de infraestrutura gerenciada, sua organização pode reduzir o investimento em manutenção de hardware, servidor ou VM provisionamento e implantação e gerenciamento da infraestrutura.

Depois de tomar a decisão de mover seus aplicativos para a nuvem, o principal motivo por que você pode escolher o IaaS, em vez de opções mais avançadas, como PaaS é simplesmente que o ambiente de IaaS será mais familiar. Mover para um ambiente que é semelhante a sua atual, o ambiente local oferece uma curva de aprendizagem inferior, o que torna o caminho mais rápido para a nuvem.

No entanto, o colocando o caminho mais rápido para a nuvem não significa que você obterá o máximo benefício de ter os aplicativos em execução na nuvem. Qualquer organização obterá os benefícios mais importantes de uma migração para a nuvem nos níveis de maturidade (otimização de nuvem) introduzidas já pronta para a nuvem DevOps e PaaS.

Ele também se tornou evidente que os aplicativos são mais fáceis de modernizar e refazer a arquitetura no futuro quando eles já estão em execução na nuvem, mesmo em IaaS. Isso é verdadeiro em parte porque já foi obtida a migração de dados do aplicativo. Além disso, sua organização terá adquirido habilidades necessárias para trabalhar na nuvem e feita a mudança de operando em uma "cultura de nuvem".

## <a name="when-to-migrate-to-iaas-instead-of-to-paas"></a>Quando a migração para o IaaS, em vez de para PaaS

Nas próximas seções, discutiremos aplicativos prontos para nuvem DevOps principalmente com base nas plataformas de PaaS e serviços. Esses aplicativos oferecem os maioria dos benefícios da migração para a nuvem.

Se seu objetivo é simplesmente mover os aplicativos existentes para a nuvem, primeiro, identifique os aplicativos existentes que exigirão modificação significativa para serem executados no serviço de aplicativo do Azure. Esses aplicativos devem ser as primeiras candidatas.

Em seguida, se você não quiser ou ainda não é possível mover a contêineres do Windows e ou orchestrators como o Azure Service Fabric ou Kubernetes, ainda, em seguida, é quando você deseja usar VMs simples (IaaS).

Porém, tenha em mente que corretamente configurar, proteger e manter as VMs requer muito mais tempo e conhecimento de TI comparado a usar os serviços de PaaS no Azure. Se você estiver pensando em máquinas virtuais do Azure, certifique-se de que leva em conta o esforço de manutenção contínua necessário para o patch, atualizar e gerenciar seu ambiente de VM. Máquinas virtuais do Azure é IaaS.

## <a name="use-azure-migrate-to-analyze-and-migrate-your-existing-applications-to-azure"></a>Use a migração do Azure para analisar e migrar seus aplicativos existentes para o Azure

Migrar para a nuvem não tem que ser difícil. Mas, muitas organizações têm dificuldade para se familiarizar - para obter visibilidade profunda sobre o ambiente e as total interdependências entre aplicativos, cargas de trabalho e dados. Sem essa visibilidade, pode ser difícil planejar o caminho para a frente. Sem informações detalhadas sobre o que é necessário para uma migração bem-sucedida, você não pode ter as direito conversas dentro de sua organização. Você não sabe o suficiente sobre a possibilidade de custo benefícios, ou se as cargas de trabalho podem apenas levantar shift e ou exigiriam retrabalho significativo para migrar com êxito. Não é surpresa que hesitam muitas organizações.

[Migrar do Azure](https://aka.ms/azuremigrate) é um novo serviço que fornece a orientação, insights e mecanismos necessários para ajudá-lo a migrar para o Azure. Migrar do Azure fornece:

-   Descoberta e avaliação de máquinas virtuais de local

-   Mapeamento de dependência embutidas para descoberta de alta confiabilidade dos aplicativos de várias camadas

-   Rightsizing inteligente para máquinas virtuais do Azure

-   Relatórios com diretrizes para correção de problemas de compatibilidade

-   Integração com o serviço de gerenciamento de banco de dados do Azure para a migração e descoberta de banco de dados

Migrar do Azure proporciona confiança que suas cargas de trabalho podem migrar com mínimo impacto nos negócios e executados conforme esperado no Azure. Orientações e ferramentas, você pode obter o máximo de retorno sobre o investimento, assegurando que críticos de desempenho e confiabilidade necessidades.

Figura 2-2 mostra o mapeamento de dependência internos para todas as conexões de servidor e aplicativo realizado por migrar do Azure.

![Aplicativos prontos para nuvem infra-estrutura de posicionamento](./media/image2-2.png)

> **Figura 2-2.** Aplicativos prontos para nuvem infra-estrutura de posicionamento

## <a name="use-azure-site-recovery-to-migrate-your-existing-vms-to-azure-vms"></a>Usar o Azure Site Recovery para migrar suas VMs existentes para máquinas virtuais do Azure

Como parte de ponta a ponta [migrar do Azure](https://aka.ms/azuremigrate), [do Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview) é uma ferramenta que você pode usar facilmente migrar seus aplicativos web para VMs no Azure. Você pode usar a recuperação de Site para replicar máquinas virtuais de locais e servidores físicos no Azure ou para replicá-los em um local no local secundário. Você mesmo pode replicar uma carga de trabalho em execução em uma VM do Azure com suporte, em um local *Hyper-V* VM, em um *VMware* VM, ou em um servidor físico do Windows ou Linux. A replicação para o Azure elimina o custo e a complexidade de manter um datacenter secundário.

Recuperação de site também é criada especificamente para ambientes híbridos que são parcialmente no local e parcialmente no Azure. Recuperação de site ajuda a garantir a continuidade dos negócios, mantendo seus aplicativos que são executados em máquinas virtuais e físicos servidores locais disponíveis se um site fica inoperante. Ela replica as cargas de trabalho que são executados em máquinas virtuais e servidores físicos para que eles permanecem disponíveis em um local secundário se o site primário não estiver disponível. Recupera as cargas de trabalho para o site primário quando ele está ativo e em execução novamente.

Figura 2-3 mostra a execução de várias migrações de máquina virtual usando o Azure Site Recovery.

![Aplicativos prontos para nuvem infra-estrutura de posicionamento](./media/image2-3.png)

> **Figura 2-3.** Aplicativos prontos para nuvem infra-estrutura de posicionamento

### <a name="additional-resources"></a>Recursos adicionais

-   **Folha de dados de migração do Azure**

    [https://aka.ms/azuremigration\_datasheet](https://aka.ms/azuremigration\_datasheet)

-   **Migrar do Azure**

    [http://azuremigrationcenter.com/](http://azuremigrationcenter.com/)

-   **Migrar para o Azure com a recuperação de Site**

    [https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-to-azure](https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-to-azure)

-   **Visão geral de serviços de recuperação de Site do Azure**

    [https://docs.microsoft.com/azure/site-recovery/site-recovery-overview](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview)

-   **Migração de VMs em AWS em VMs do Azure**

    [https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-aws-to-azure](https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-aws-to-azure)

>[!div class="step-by-step"]
[Anterior](index.md)
[Próximo](migrate-your-relational-databases-to-azure.md)
