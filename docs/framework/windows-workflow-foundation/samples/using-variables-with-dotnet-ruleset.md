---
title: Usando variáveis com o.NET Framework 3.5 Ruleset
ms.date: 03/30/2017
ms.assetid: 27b56249-22fe-4252-840f-74c0d6c7a6b3
ms.openlocfilehash: 9fa6eaf58aaddc4673f08ec9a9001647a494877d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33516849"
---
# <a name="using-variables-with-a-net-framework-35-ruleset"></a>Usando variáveis com o.NET Framework 3.5 Ruleset
Este exemplo demonstra como criar um fluxo de trabalho que usa a atividade de <xref:System.Activities.Statements.Interop> para integrar uma atividade personalizado escrito em [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] que use a diretiva e regras. O fluxo de trabalho passar dados personalizado pela atividade variáveis de associação às propriedades de dependência exposta pela atividade personalizado.  
  
## <a name="sample-walkthrough"></a>Passo a passo de exemplo  
  
#### <a name="to-examine-travelrulelibrary"></a>Para examinar TravelRuleLibrary  
  
1.  Usando o Visual Studio, abra o arquivo de solução de InteropWith35RuleSet.sln.  
  
2.  Abra o TravelRuleSet.cs no designer de fluxo de trabalho.  
  
     Uma atividade sequencial personalizado que contém <xref:System.Workflow.Activities.PolicyActivity> é exibida.  
  
3.  Clique duas vezes na atividade de política de DiscountPolicy para examinar as regras.  
  
     Os PNF do editor das regras até mostram as regras.  
  
4.  Clique com botão direito do `DiscountPolicy` e selecione o **Exibir código** permite que você examine o código ao lado de código c# para a atividade.  
  
     Observe a configuração da propriedade de dependência para `DiscountLevel`. Isso é equivalente a argumentos em [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)]. Para obter mais informações sobre os argumentos, consulte [variáveis e argumentos](../../../../docs/framework/windows-workflow-foundation/variables-and-arguments.md).  
  
## <a name="interopwith35ruleset"></a>InteropWith35RuleSet  
 Este é um projeto sequencial de fluxo de trabalho que usa a atividade de <xref:System.Activities.Statements.Interop> para integrar com o conjunto de regra personalizada criado no projeto de `TravelRuleLibrary` . As variáveis são criados na atividade de alto nível <xref:System.Activities.Statements.Sequence> . A atividade de <xref:System.Activities.Statements.Interop> é usada para integrar-se a atividade de `TravelRuleSet` . Variáveis que são declarados em <xref:System.Activities.Statements.Sequence> são usados para associar a propriedades de dependência.  
  
## <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Usando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], abra o arquivo de solução de InteropWith35RuleSet.sln.  
  
2.  Para criar a solução, pressione CTRL+SHIFT+B.  
  
3.  Para executar a solução, pressione CTRL+F5.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\InteropWith35RuleSet`