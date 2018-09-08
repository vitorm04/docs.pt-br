---
title: Orientação de migração
ms.date: 03/30/2017
ms.assetid: cb65c132-58c9-4028-b3d4-1efc71d5e60e
ms.openlocfilehash: 93d523c51c45f9b6f6235a7645fa126fcb09b6e5
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44179816"
---
# <a name="migration-guidance"></a>Orientação de migração
No [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], a Microsoft está lançando a segunda versão principal do Windows Workflow Foundation (WF). O [!INCLUDE[wf1](../../../includes/wf1-md.md)] foi liberado no [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] (isso inclui os tipos nos namespaces System.Workflow.*; agora referido como WF3) e aprimorado no [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)]. WF3 também é parte do [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], mas existe ao lado da nova tecnologia de fluxo de trabalho (os tipos em System. Activities.\* namespaces; chamada como WF4). Ao considerar quando adotar o WF4, é importante primeiro reconhecer que você controla o tempo.  
  
-   O WF3 tem suporte completo do [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)].  
  
-   Os aplicativos WF3 são executados no [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] sem alteração e continua tendo suporte total.  
  
-   Os novos aplicativos WF3 podem ser criados e seus aplicativos existentes podem ser editados no [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] e têm suporte total.  
  
 Portanto, a decisão de adotar o .NET Framework 4 é separada da sua decisão de migrar para o WF4 (Activities) do WF3 (Workflow.\*). Este tópico fornece links para a orientação de migração do WF que fornece informações sobre como trabalhar com WF3 e WF4.  
  
## <a name="wf-migration-whitepapers-and-cookbooks"></a>Artigos e livros de receitas de migração do WF  
 O [visão geral da migração de WF](https://go.microsoft.com/fwlink/?LinkId=153873) tópico fornece uma visão geral da relação entre WF3 e WF4 e estratégias de migração. Os tópicos complementares aprofundam tópicos específicos.  
  
 [Visão geral da migração de WF](https://go.microsoft.com/fwlink/?LinkId=153873)  
 Descreve a relação entre WF3 e WF4, e as opções que você tem como usuário ou usuário potencial da tecnologia de fluxo de trabalho no .NET 4.  
  
 [Migração de WF: Práticas recomendadas para desenvolvimento do WF3](https://go.microsoft.com/fwlink/?LinkId=153852)  
 Discute como criar os artefatos do WF3 para que eles possam ser migrados mais facilmente para o WF4.  
  
 [Orientação de WF: regras](https://go.microsoft.com/fwlink/?LinkId=153854)  
 Discute como transformar investimentos relacionadas a regras em soluções do [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)].  
  
 [Orientação de WF: Máquina de estado](https://go.microsoft.com/fwlink/?LinkId=153855)  
 Discute a modelagem do fluxo de controle do WF4 na ausência de uma atividade da máquina de estado.  
  
 Observe que essa orientação somente se aplica a projetos de fluxo de trabalho destinados ao .NET Framework 4. Os fluxos de trabalho da máquina de estado eram adicionados no .NET 4.0.1 com a versão de atualização 1 da plataforma, e foram incluídos como parte do .NET Framework 4.5. Para obter mais informações sobre fluxos de trabalho de máquina de estado no .NET 4.0.1 - 4.0.3 e .NET Framework 4.5, consulte [atualização 4.0.1 para recursos do Microsoft .NET Framework 4](https://msdn.microsoft.com/library/de3297bd-c3e1-4126-95be-2ed7fe2a98fc) e [fluxos de trabalho de máquina de estado](../../../docs/framework/windows-workflow-foundation/state-machine-workflows.md).  
  
 [Livro de receitas de migração de WF: Atividades personalizadas](https://go.microsoft.com/fwlink/?LinkId=153856)  
 Fornece exemplos e instruções para recriar as atividades personalizadas do WF3 no WF4.  
  
 [Livro de receitas de migração de WF: Atividades personalizadas avançadas](https://go.microsoft.com/fwlink/?LinkId=275560)  
 Fornece orientação para reformatar as atividades personalizadas avançadas do WF3 que usam filas do WF3 e agendar atividades filho como atividades personalizadas do WF4.  
  
 [Livro de receitas de migração de WF: fluxos de trabalho](https://go.microsoft.com/fwlink/?LinkId=153858)  
 Fornece exemplos e instruções para recriar os fluxos de trabalho do WF3 no WF4.  
  
 [Livro de receitas de migração de WF: Hospedagem de fluxo de trabalho](https://go.microsoft.com/fwlink/?LinkId=275561)  
 Fornece orientação para reformatar o código de hospedagem do WF3 como código de hospedagem do WF4. A meta é abranger as principais diferenças na hospedagem de fluxo de trabalho entre WF3 e WF4.  
  
 [Livro de receitas de migração de WF: Acompanhamento de fluxo de trabalho](https://go.microsoft.com/fwlink/?LinkId=275562)  
 Fornece orientação para reformatar o código de rastreamento e a configuração do WF3 usando o código de rastreamento e a configuração equivalentes do WF4.  
  
 [Orientação de WF: Serviços de fluxo de trabalho](https://go.microsoft.com/fwlink/?LinkId=275564)  
 Fornece instruções passo a passo orientadas para exemplos para recriar os fluxos de trabalho que implementam os serviços Web do Windows Communication Foundation (WCF) (geralmente chamado de serviços de fluxo de trabalho) criados no WF3 para usar WF4, para cenários comuns para atividades prontas.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Activities.Statements.Interop>
