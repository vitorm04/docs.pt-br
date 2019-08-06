---
title: Orientação de migração
ms.date: 03/30/2017
ms.assetid: cb65c132-58c9-4028-b3d4-1efc71d5e60e
ms.openlocfilehash: 45f81b29f63701f690e396de2e9834f9933fd775
ms.sourcegitcommit: bbfcc913c275885381820be28f61efcf8e83eecc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2019
ms.locfileid: "68796806"
---
# <a name="migration-guidance"></a>Orientação de migração
No, [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)]a Microsoft está lançando a segunda versão principal do Windows Workflow Foundation (WF). [!INCLUDE[wf1](../../../includes/wf1-md.md)]foi lançado no WinFX (isso incluiu os tipos em System. Workflow.\* namespaces; agora conhecido como WF3) e aprimorou no [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)]. O [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)]WF3 também faz parte do, mas ele existe junto com a nova tecnologia de fluxo de trabalho (os tipos em System\* . Activities. Namespaces; referido como WF4). Ao considerar quando adotar o WF4, é importante primeiro reconhecer que você controla o tempo.  
  
- O WF3 tem suporte completo do [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)].  
  
- Os aplicativos WF3 são executados no [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] sem alteração e continua tendo suporte total.  
  
- Novos aplicativos WF3 podem ser criados e seus aplicativos existentes podem ser editados no Visual Studio 2012 e têm suporte total.  
  
 Portanto, a decisão de adotar o .NET Framework 4 é dissociada de sua decisão de mudar para WF4 (System. Activities.\*) de WF3 (System. Workflow.\*). Este tópico fornece links para a orientação de migração do WF que fornece informações sobre como trabalhar com WF3 e WF4.  
  
## <a name="wf-migration-whitepapers-and-cookbooks"></a>Artigos e livros de receitas de migração do WF  
 O tópico [visão geral da migração do WF](https://go.microsoft.com/fwlink/?LinkId=153873) fornece uma ampla visão geral da relação entre WF3 e WF4 e estratégias de migração. Os tópicos complementares aprofundam tópicos específicos.  
  
 [Visão geral da migração do WF](https://go.microsoft.com/fwlink/?LinkId=153873)  
 Descreve a relação entre WF3 e WF4, e as opções que você tem como usuário ou usuário potencial da tecnologia de fluxo de trabalho no .NET 4.  
  
 [Migração do WF: Práticas recomendadas para o desenvolvimento de WF3](https://go.microsoft.com/fwlink/?LinkId=153852)  
 Discute como criar os artefatos do WF3 para que eles possam ser migrados mais facilmente para o WF4.  
  
 [Diretrizes do WF: Regras](https://go.microsoft.com/fwlink/?LinkId=153854)  
 Discute como transformar investimentos relacionadas a regras em soluções do [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)].  
  
 [Diretrizes do WF: Computador de estado](https://go.microsoft.com/fwlink/?LinkId=153855)  
 Discute a modelagem do fluxo de controle do WF4 na ausência de uma atividade da máquina de estado.  
  
 Observe que essa orientação somente se aplica a projetos de fluxo de trabalho destinados ao .NET Framework 4. Os fluxos de trabalho da máquina de estado eram adicionados no .NET 4.0.1 com a versão de atualização 1 da plataforma, e foram incluídos como parte do .NET Framework 4.5. Para obter mais informações sobre fluxos de trabalho de máquina de estado no .NET 4.0.1-4.0.3 e .NET Framework 4,5, consulte a [atualização 4.0.1 para recursos do Microsoft .NET Framework 4](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hh290669(v=vs.100)) e [fluxos de trabalho de máquina de estado](state-machine-workflows.md).  
  
 [Manual de migração do WF: Atividades personalizadas](https://go.microsoft.com/fwlink/?LinkId=153856)  
 Fornece exemplos e instruções para recriar as atividades personalizadas do WF3 no WF4.  
  
 [Manual de migração do WF: Atividades personalizadas avançadas](https://go.microsoft.com/fwlink/?LinkId=275560)  
 Fornece orientação para reformatar as atividades personalizadas avançadas do WF3 que usam filas do WF3 e agendar atividades filho como atividades personalizadas do WF4.  
  
 [Manual de migração do WF: Fluxos](https://go.microsoft.com/fwlink/?LinkId=153858)  
 Fornece exemplos e instruções para recriar os fluxos de trabalho do WF3 no WF4.  
  
 [Manual de migração do WF: Hospedagem de fluxo de trabalho](https://go.microsoft.com/fwlink/?LinkId=275561)  
 Fornece orientação para reformatar o código de hospedagem do WF3 como código de hospedagem do WF4. A meta é abranger as principais diferenças na hospedagem de fluxo de trabalho entre WF3 e WF4.  
  
 [Manual de migração do WF: Rastreamento de fluxo de trabalho](https://go.microsoft.com/fwlink/?LinkId=275562)  
 Fornece orientação para reformatar o código de rastreamento e a configuração do WF3 usando o código de rastreamento e a configuração equivalentes do WF4.  
  
 [Diretrizes do WF: Serviços de fluxo de trabalho](https://go.microsoft.com/fwlink/?LinkId=275564)  
 Fornece instruções passo a passo orientadas para exemplos para recriar os fluxos de trabalho que implementam os serviços Web do Windows Communication Foundation (WCF) (geralmente chamado de serviços de fluxo de trabalho) criados no WF3 para usar WF4, para cenários comuns para atividades prontas.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Activities.Statements.Interop>
