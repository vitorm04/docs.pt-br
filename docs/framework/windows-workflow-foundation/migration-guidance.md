---
title: Orientação de migração
ms.date: 03/30/2017
ms.assetid: cb65c132-58c9-4028-b3d4-1efc71d5e60e
ms.openlocfilehash: 8abc241331b3d322763ffd67b41ff676ebc680fb
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283206"
---
# <a name="migration-guidance"></a>Orientação de migração

No .NET Framework 4, a Microsoft está lançando a segunda versão principal do Windows Workflow Foundation (WF). o [!INCLUDE[wf1](../../../includes/wf1-md.md)] foi lançado no WinFX (isso incluiu os tipos nos namespaces System. Workflow.\*; agora conhecido como WF3) e aprimorado no .NET Framework 3,5. O WF3 também faz parte do .NET Framework 4, mas ele existe junto com a nova tecnologia de fluxo de trabalho (os tipos nos namespaces System. Activities.\*; referido como WF4). Ao considerar quando adotar o WF4, é importante primeiro reconhecer que você controla o tempo.  
  
- WF3 é uma parte totalmente suportada do .NET Framework 4.  
  
- Os aplicativos WF3 executados no .NET Framework 4 sem modificação e continuam a ser totalmente suportados.  
  
- Novos aplicativos WF3 podem ser criados e seus aplicativos existentes podem ser editados no Visual Studio 2012 e têm suporte total.  
  
 Portanto, a decisão de adotar o .NET Framework 4 é dissociada de sua decisão de mover para WF4 (System. Activities.\*) de WF3 (System. Workflow.\*). Este tópico fornece links para a orientação de migração do WF que fornece informações sobre como trabalhar com WF3 e WF4.  
  
## <a name="wf-migration-whitepapers-and-cookbooks"></a>Artigos e livros de receitas de migração do WF  
 O tópico [visão geral da migração do WF](https://go.microsoft.com/fwlink/?LinkId=153873) fornece uma ampla visão geral da relação entre WF3 e WF4 e estratégias de migração. Os tópicos complementares aprofundam tópicos específicos.  
  
 [Visão geral da migração do WF](https://go.microsoft.com/fwlink/?LinkId=153873)  
 Descreve a relação entre WF3 e WF4, e as opções que você tem como usuário ou usuário potencial da tecnologia de fluxo de trabalho no .NET 4.  
  
 [Migração do WF: práticas recomendadas para o desenvolvimento de WF3](https://go.microsoft.com/fwlink/?LinkId=153852)  
 Discute como criar os artefatos do WF3 para que eles possam ser migrados mais facilmente para o WF4.  
  
 [Diretrizes do WF: regras](https://go.microsoft.com/fwlink/?LinkId=153854)  
 Discute como trazer investimentos relacionados a regras para frente nas soluções .NET Framework 4.  
  
 [Diretrizes do WF: computador de estado](https://go.microsoft.com/fwlink/?LinkId=153855)  
 Discute a modelagem do fluxo de controle do WF4 na ausência de uma atividade da máquina de estado.  
  
 Observe que essa orientação somente se aplica a projetos de fluxo de trabalho destinados ao .NET Framework 4. Os fluxos de trabalho da máquina de estado eram adicionados no .NET 4.0.1 com a versão de atualização 1 da plataforma, e foram incluídos como parte do .NET Framework 4.5. Para obter mais informações sobre fluxos de trabalho de máquina de estado no .NET 4.0.1-4.0.3 e .NET Framework 4,5, consulte a [atualização 4.0.1 para recursos do Microsoft .NET Framework 4](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hh290669(v=vs.100)) e [fluxos de trabalho de máquina de estado](state-machine-workflows.md).  
  
 [Manual de migração do WF: atividades personalizadas](https://go.microsoft.com/fwlink/?LinkId=153856)  
 Fornece exemplos e instruções para recriar as atividades personalizadas do WF3 no WF4.  
  
 [Manual de migração do WF: atividades personalizadas avançadas](https://go.microsoft.com/fwlink/?LinkId=275560)  
 Fornece orientação para reformatar as atividades personalizadas avançadas do WF3 que usam filas do WF3 e agendar atividades filho como atividades personalizadas do WF4.  
  
 [Manual de migração do WF: fluxos de trabalho](https://go.microsoft.com/fwlink/?LinkId=153858)  
 Fornece exemplos e instruções para recriar os fluxos de trabalho do WF3 no WF4.  
  
 [Manual de migração do WF: Hospedagem de fluxo de trabalho](https://go.microsoft.com/fwlink/?LinkId=275561)  
 Fornece orientação para reformatar o código de hospedagem do WF3 como código de hospedagem do WF4. A meta é abranger as principais diferenças na hospedagem de fluxo de trabalho entre WF3 e WF4.  
  
 [Manual de migração do WF: rastreamento de fluxo de trabalho](https://go.microsoft.com/fwlink/?LinkId=275562)  
 Fornece orientação para reformatar o código de rastreamento e a configuração do WF3 usando o código de rastreamento e a configuração equivalentes do WF4.  
  
 [Diretrizes do WF: serviços de fluxo de trabalho](https://go.microsoft.com/fwlink/?LinkId=275564)  
 Fornece instruções passo a passo orientadas para exemplos para recriar os fluxos de trabalho que implementam os serviços Web do Windows Communication Foundation (WCF) (geralmente chamado de serviços de fluxo de trabalho) criados no WF3 para usar WF4, para cenários comuns para atividades prontas.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Activities.Statements.Interop>
