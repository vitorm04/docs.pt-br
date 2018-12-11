---
title: Lift- and -shift de aplicativos .NET existentes para o Azure IaaS (infraestrutura de nuvem pronto)
description: Modernize aplicativos .NET existentes com contêineres do Windows e de nuvem do Azure.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: a6c13ba5bfd28cec87df1c021ed1f303d7d1f4f5
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53154379"
---
# <a name="lift-and-shift-existing-net-apps-to-azure-iaas-cloud-infrastructure-ready"></a>Lift- and -shift de aplicativos .NET existentes para o Azure IaaS (infraestrutura de nuvem pronto)

> Visão: Como uma primeira etapa, para reduzir seu investimento no local e o custo total de hardware e manutenção de rede, simplesmente hospedar novamente seus aplicativos existentes na nuvem.

Antes de abordarmos *como* para migrar seus aplicativos existentes para a infraestrutura do Azure como uma plataforma de serviço (IaaS), é importante analisar as razões *por que* você desejaria migrar diretamente para o IaaS no Azure. O cenário neste nível de maturidade de modernização é, essencialmente começar a usar as VMs na nuvem, em vez de continuar a usar sua infraestrutura local atual.

É outro ponto para analisar *por que* você talvez queira migrar para a nuvem de IaaS puro, em vez de apenas adicionar mais avançado de serviços gerenciados no Azure. Determinar quais casos podem exigir IaaS em primeiro lugar.

Figura 2-1 posiciona aplicativos infraestrutura de nuvem prontos nos níveis de maturidade de modernização:

![Aplicativos de nuvem prontos para infraestrutura de posicionamento](./media/image2-1.png)

> **Figura 2-1.** Aplicativos de nuvem prontos para infraestrutura de posicionamento

## <a name="why-migrate-existing-net-web-applications-to-azure-iaas"></a>Por que migrar aplicativos da web .NET existentes para o Azure IaaS

O principal motivo para migrar para a nuvem, mesmo em um nível inicial de IaaS, é obter redução de custos. Usando mais serviços de infraestrutura gerenciada, sua organização pode reduzir seu investimento na manutenção de hardware, servidor ou o provisionamento da VM e implantação e gerenciamento de infraestrutura.

Depois de tomar a decisão de migrar seus aplicativos para a nuvem, o principal motivo por que você pode escolher o IaaS, em vez de opções mais avançadas, como PaaS é simplesmente que o ambiente de IaaS será mais familiar. Migrando para um ambiente que é semelhante ao seu atual, no ambiente local oferece uma curva de aprendizado mais baixa, o que torna o caminho mais rápido para a nuvem.

No entanto, o levando o caminho mais rápido para a nuvem não significa que você obterá o maior benefício de ter que seus aplicativos em execução na nuvem. Qualquer organização terá vantagens mais significativas de uma migração na nuvem nos níveis de maturidade de otimização para nuvem e nativos da nuvem já foi apresentada.

Ele também tornou-se evidente que os aplicativos são mais fáceis de modernizar e refazer a arquitetura no futuro quando eles já estão em execução na nuvem, mesmo em IaaS. Migração de dados de aplicativo já foi atingida. Além disso, sua organização terá obtidas as habilidades necessárias para trabalhar na nuvem e feita a mudança para operar em uma "cultura de nuvem".

## <a name="when-to-migrate-to-iaas-instead-of-to-paas"></a>Quando migrar para o IaaS, em vez de para PaaS

As seções a seguir discutem aplicativos otimizados para a nuvem se baseiam-se principalmente em serviços e plataformas de PaaS. Esses aplicativos oferecem os maioria dos benefícios de migrar para a nuvem. 

Se seu objetivo é simplesmente mover aplicativos existentes para a nuvem, primeiro, identifique os aplicativos existentes que não exigem modificação significativa para ser executado no serviço de aplicativo do Azure. Esses aplicativos devem ser as primeiras candidatas à otimização de nuvem. 

Em seguida, para os aplicativos que ainda não é possível mover a contêineres do Windows e de PaaS, como o serviço de aplicativo ou orquestradores como o Azure Service Fabric, migrar VMs simples sem formatação (IaaS). 

Mas, lembre-se de que corretamente configurar, proteger e manutenção de VMs exigem muito mais tempo e conhecimento de TI em comparação ao uso de serviços de PaaS no Azure. Se você estiver pensando em máquinas virtuais do Azure, certifique-se de que levam em conta o esforço de manutenção contínua necessário para corrigir, atualizar e gerenciar seu ambiente de VM. Máquinas virtuais do Azure é IaaS.

## <a name="use-azure-migrate-to-analyze-and-migrate-your-existing-applications-to-azure"></a>Usar as migrações do Azure para analisar e migrar seus aplicativos existentes para o Azure

Migrando para a nuvem não precisa ser difícil. Mas muitas organizações têm dificuldades para começar a usar - para obter visibilidade profunda sobre o ambiente e as forte interdependências entre aplicativos, cargas de trabalho e dados. Sem essa visibilidade, pode ser difícil planejar o caminho para a frente. Sem informações detalhadas sobre o que é necessário para uma migração bem-sucedida, você não pode ter as conversas certas dentro de sua organização. Você não sabe o suficiente sobre os potenciais custos-benefícios, ou se as cargas de trabalho poderia simplesmente lift-and-shift ou exigiriam retrabalho significativo para migrar com êxito. Não é surpresa que muitas organizações hesite em entrar.

[As migrações para Azure](https://aka.ms/azuremigrate) é um novo serviço que fornece a orientação, insights e mecanismos necessários para ajudá-lo a migrar para o Azure. As migrações para Azure fornece:

- Descoberta e avaliação para máquinas virtuais no local

- Mapeamento de dependências embutidas para a descoberta de alta confiabilidade de aplicativos de várias camadas

- Inteligente, o dimensionamento correto para máquinas virtuais do Azure

- Relatório com diretrizes para corrigir possíveis problemas de compatibilidade

- Integração com o serviço de gerenciamento de banco de dados do Azure para a migração e descoberta de banco de dados

As migrações para Azure proporciona confiança que suas cargas de trabalho podem migrar com impacto mínimo nos negócios e executados conforme o esperado no Azure. Com ferramentas e diretrizes, você pode obter o máximo de retorno do investimento, assegurando que o desempenho crítico e necessidades de confiabilidade são atendidas.

Figura 2-2 mostra o mapeamento de dependência internos para todas as conexões de servidor e aplicativo executado pelas migrações para Azure.

![Aplicativos de nuvem prontos para infraestrutura de posicionamento](./media/image2-2.png)

> **Figura 2-2.** Aplicativos de nuvem prontos para infraestrutura de posicionamento

## <a name="use-azure-site-recovery-to-migrate-your-existing-vms-to-azure-vms"></a>Usar o Azure Site Recovery para migrar suas VMs existentes para máquinas virtuais do Azure

Como parte de ponta a ponta [migrações para Azure](https://aka.ms/azuremigrate), [do Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview) é uma ferramenta que você pode usar para migrar facilmente seus aplicativos web para as VMs no Azure. Você pode usar o Site Recovery para replicar VMs locais e servidores físicos no Azure ou para replicá-las para um local secundário local. Você pode até mesmo replicar uma carga de trabalho que está em execução em uma VM do Azure com suporte em um local *Hyper-V* VM, em um *VMware* VM, ou em um servidor físico do Windows ou Linux. Replicação para o Azure elimina o custo e a complexidade de manter um datacenter secundário.

Também é feita a recuperação de site especificamente para ambientes híbridos que são parcialmente localmente e parcialmente no Azure. Site Recovery ajuda a garantir a continuidade dos negócios, mantendo seus aplicativos em execução em VMs locais e servidores físicos disponíveis se um site ficar inativo. Ele replica as cargas de trabalho que são executados em VMs e servidores físicos para que elas permaneçam disponíveis em um local secundário se o site primário não estiver disponível. Ele recupera as cargas de trabalho para o site primário quando ele está ativo e em execução novamente.

Figura 2 a 3 mostra a execução de várias migrações de VM usando o Azure Site Recovery.

![Aplicativos de nuvem prontos para infraestrutura de posicionamento](./media/image2-3.png)

> **Figura 2 a 3.** Aplicativos de nuvem prontos para infraestrutura de posicionamento

### <a name="additional-resources"></a>Recursos adicionais

- **Folha de dados de migrações para Azure**

    [https://aka.ms/azuremigration\_datasheet](https://aka.ms/azuremigration\_datasheet)

- **Migrações para Azure**

    [http://azuremigrationcenter.com/](http://azuremigrationcenter.com/)

- **Migrar para o Azure com o Site Recovery**

    [https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-to-azure](https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-to-azure)

- **Visão geral de serviço do Azure Site Recovery**

    [https://docs.microsoft.com/azure/site-recovery/site-recovery-overview](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview)

- **Migração de VMs no AWS para VMs do Azure**

    [https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-aws-to-azure](https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-aws-to-azure)

>[!div class="step-by-step"]
>[Anterior](index.md)
>[Próximo](migrate-your-relational-databases-to-azure.md)