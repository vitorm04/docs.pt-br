---
title: Levante e mude os aplicativos .NET existentes para Ozure IaaS (Cloud Infrastructure-Ready)
description: Modernize os aplicativos .NET existentes com contêineres Azure Cloud e Windows.
ms.date: 04/28/2018
ms.openlocfilehash: c7638a034dbb27baea1b097bdb66175bfb5a71f2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73089631"
---
# <a name="lift-and-shift-existing-net-apps-to-azure-iaas-cloud-infrastructure-ready"></a>Levante e mude os aplicativos .NET existentes para Ozure IaaS (Cloud Infrastructure-Ready)

> Visão: Como um primeiro passo, para reduzir seu investimento no local e o custo total de manutenção de hardware e rede, basta rehospedar seus aplicativos existentes na nuvem.

Antes de entrar em *como* migrar seus aplicativos existentes para a infra-estrutura do Azure como uma plataforma de serviço (IaaS), é importante analisar as *razões* pelas quais você gostaria de migrar diretamente para o IaaS no Azure. O cenário nesse nível de maturidade de modernização essencialmente é começar a usar VMs na nuvem, em vez de continuar a usar sua infra-estrutura atual e local.

Outro ponto a ser analisado é *por que* você pode querer migrar para nuvem iaas pura em vez de apenas adicionar serviços gerenciados mais avançados no Azure. Determinar quais casos podem exigir IaaS em primeiro lugar.

Figura 2-1 posiciona aplicações prontas para infraestrutura em nuvem nos níveis de maturidade de modernização:

![Posicionamento de aplicativos prontos para infra-estrutura na nuvem](./media/image2-1.png)

**Figura 2-1.** Posicionamento de aplicativos prontos para infra-estrutura na nuvem

## <a name="why-migrate-existing-net-web-applications-to-azure-iaas"></a>Por que migrar aplicativos web .NET existentes para o Azure IaaS

A principal razão para migrar para a nuvem, mesmo em um nível inicial de IaaS, é conseguir reduções de custos. Usando serviços de infra-estrutura mais gerenciados, sua organização pode reduzir seu investimento em manutenção de hardware, provisionamento e implantação de vm e gerenciamento de infra-estrutura.

Depois que você tomar a decisão de mover seus aplicativos para a nuvem, a principal razão pela qual você pode escolher iaaS em vez de opções mais avançadas como PaaS é simplesmente que o ambiente IaaS será mais familiar. Mudar-se para um ambiente semelhante ao seu ambiente atual, no local, oferece uma curva de aprendizado mais baixa, o que o torna o caminho mais rápido para a nuvem.

No entanto, tomar o caminho mais rápido para a nuvem não significa que você ganhará mais benefícios de ter seus aplicativos rodando na nuvem. Qualquer organização obterá os benefícios mais significativos de uma migração em nuvem nos níveis de maturidade já introduzidos na Nuvem e nativo da nuvem.

Também ficou evidente que os aplicativos são mais fáceis de modernizar e rearquitetar no futuro quando já estão rodando na nuvem, mesmo no IaaS. A migração de dados do aplicativo já foi alcançada. Além disso, sua organização terá adquirido habilidades necessárias para trabalhar na nuvem e fez a mudança para operar em uma "cultura de nuvem".

## <a name="when-to-migrate-to-iaas-instead-of-to-paas"></a>Quando migrar para o IaaS em vez de para o PaaS

As próximas seções discutem aplicativos otimizados para nuvem que são principalmente baseados em plataformas e serviços PaaS. Esses aplicativos dão a você mais benefícios de migrar para a nuvem.

Se seu objetivo é simplesmente mover aplicativos existentes para a nuvem, primeiro, identifique aplicativos existentes que não exigiriam modificações substanciais para serem executados no Azure App Service. Esses aplicativos devem ser os primeiros candidatos para Otimização de Nuvem.

Em seguida, para os aplicativos que ainda não podem se mover para o Windows Containers e PaaS, como O Serviço de Aplicativos ou orquestradores como o Azure Kubernetes Service, migre-os para VMs simples simples (IaaS).

Mas, tenha em mente que a configuração, a segurança e a manutenção correta das VMs requer muito mais tempo e experiência de TI em comparação com o uso de serviços PaaS no Azure. Se você estiver considerando as Máquinas Virtuais do Azure, certifique-se de levar em conta o esforço contínuo de manutenção necessário para corrigir, atualizar e gerenciar seu ambiente VM. Azure Virtual Machines é IaaS.

## <a name="use-azure-migrate-to-analyze-and-migrate-your-existing-applications-to-azure"></a>Use o Azure Migrate para analisar e migrar seus aplicativos existentes para o Azure

Migrar para a nuvem não precisa ser difícil. Mas muitas organizações lutam para começar - para obter uma visibilidade profunda sobre o ambiente e as interdependências apertadas entre aplicativos, cargas de trabalho e dados. Sem essa visibilidade, pode ser difícil planejar o caminho a seguir. Sem informações detalhadas sobre o que é necessário para uma migração bem-sucedida, você não pode ter as conversas certas dentro de sua organização. Você não sabe o suficiente sobre os benefícios de custo potenciais, ou se as cargas de trabalho poderiam apenas levantar e mudar ou exigiria um retrabalho significativo para migrar com sucesso. Não é à toa que muitas organizações hesitam.

[O Azure Migrate](https://aka.ms/azuremigrate) é um novo serviço que fornece a orientação, insights e mecanismos necessários para ajudá-lo a migrar para o Azure. As Migrações para Azure fornecem:

- Descoberta e avaliação de máquinas virtuais locais

- Mapeamento de dependência incorporada para a descoberta de alta confiança de aplicativos multiníveis

- Dimensionamento direito inteligente para máquinas virtuais Azure

- Relatórios de compatibilidade com diretrizes para remediar possíveis problemas

- Integração com o Azure Database Management Service para detecção e migração de banco de dados

O Azure Migrate lhe dá confiança de que suas cargas de trabalho podem migrar com o mínimo de impacto para os negócios e funcionar como esperado no Azure. Com as ferramentas e orientações certas, você pode obter o máximo retorno sobre o investimento, garantindo que as necessidades críticas de desempenho e confiabilidade sejam atendidas.

A Figura 2-2 mostra o mapeamento de dependência incorporado para todas as conexões de servidor e aplicativos realizadas pelo Azure Migrate.

![Posicionamento de aplicativos prontos para infra-estrutura na nuvem](./media/image2-2.png)

**Figura 2-2.** Posicionamento de aplicativos prontos para infra-estrutura na nuvem

## <a name="use-azure-site-recovery-to-migrate-your-existing-vms-to-azure-vms"></a>Use a recuperação do site do Azure para migrar suas VMs existentes para As VMs do Azure

Como parte do [Azure Migrate](https://aka.ms/azuremigrate)de ponta a ponta, [o Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview) é uma ferramenta que você pode usar para migrar facilmente seus aplicativos web para VMs no Azure. Você pode usar o Site Recovery para replicar VMs e servidores físicos no local para o Azure ou para replicá-los em um local secundário no local. Você pode até replicar uma carga de trabalho que está sendo executado em uma VM Azure suportada, em um *Hiper-V VM* no local, em uma *VMM VMware* ou em um servidor físico Windows ou Linux. A replicação no Azure elimina o custo e a complexidade de manter um data center secundário.

A Recuperação do Site também é feita especificamente para ambientes híbridos que são parcialmente no local e em parte no Azure. A recuperação do site ajuda a garantir a continuidade dos negócios mantendo seus aplicativos que estão sendo executados em VMs e servidores físicos locais disponíveis se um site for derrubado. Ele replica cargas de trabalho que estão sendo executados em VMs e servidores físicos para que eles permaneçam disponíveis em um local secundário se o site principal não estiver disponível. Ele recupera as cargas de trabalho para o site primário quando ele está ativo e em execução novamente.

A Figura 2-3 mostra a execução de várias migrações de VM usando o Azure Site Recovery.

![Posicionamento de aplicativos prontos para infra-estrutura na nuvem](./media/image2-3.png)

**Figura 2-3.** Posicionamento de aplicativos prontos para infra-estrutura na nuvem

### <a name="additional-resources"></a>Recursos adicionais

- **Folha de dados do Azure Migrate**

    <https://aka.ms/azuremigration\_datasheet>

- **Azure Migrar**

    <https://aka.ms/azuremigrate>

- **Centro de migração Azure**

    <https://azure.microsoft.com/migration/>

- **Migrar para o Azure com recuperação de site**

    <https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-to-azure>

- **Visão geral do serviço de recuperação do site do Azure**

    <https://docs.microsoft.com/azure/site-recovery/site-recovery-overview>

- **Migrando VMs em AWS para VMs azure**

    <https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-aws-to-azure>

>[!div class="step-by-step"]
>[Próximo](index.md)
>[anterior](migrate-your-relational-databases-to-azure.md) <!-- Next Chapter -->
