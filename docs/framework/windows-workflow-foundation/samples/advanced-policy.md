---
title: Diretiva avançada
ms.date: 03/30/2017
ms.assetid: 75a22c88-5e54-4ae8-84cb-fbb22a612f0a
ms.openlocfilehash: becdc28affd877239474d6f0f007a480297bccb8
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43672834"
---
# <a name="advanced-policy"></a>Diretiva avançada
Este exemplo amplia o exemplo simples de política. Além das regras residenciais de desconto e de desconto de negócio de exemplo simples de política, várias regras novos foram adicionadas.  
  
 Uma regra valioso é adicionada, que fornece desconto maior de pedidos importantes. Recebe um valor de prioridade menor do que as duas regras anteriores de modo que substitui o campo de desconto e tem precedência sobre as regras residenciais e comerciais de desconto.  
  
 Uma regra do total de cálculo também é adicionada, que compute o total com base no nível de desconto. Mostra como referenciar um método definido na atividade de fluxo de trabalho, bem como usar outras ações. Essa regra também demonstra encadeamento o comportamento desde que será avaliado a qualquer momento as alterações do campo de desconto. Além disso, a atribuição do método é mostrada com o RuleWriteAttribute no método de CalculateTotal. Isso faz com que as regras afetados (ErrorTotalRule) a ser reavaliadas sempre que o método é executado.  
  
 A regra mais recente é adicionada uma que detecta erros (neste caso, total menor que 0). Se isso ocorre, a execução de política é interrompida.  
  
 Finalmente, chamadas de `Console.Writeline` são adicionados como ações a cada regra fornecer mais visibilidade em execução de regra, para mostrar que também é possível acessar métodos estáticos em tipos referenciados. Você também pode usar o rastreamento para obter a visibilidade nas regras que são executadas.  
  
 Regras usadas nesse exemplo são:  
  
 **ResidentialDiscountRule:**  
  
 SE OrderValue > 500 E CustomerType = residencial  
  
 ENTÃO desconto = % 5  
  
 **BusinessDiscountRule:**  
  
 SE OrderValue > 10000 E CustomerType = business  
  
 ENTÃO desconto = 10%  
  
 **HighValueDiscountRule:**  
  
 SE OrderValue > 20000  
  
 ENTÃO desconto = 15%  
  
 **TotalRule:**  
  
 SE desconto > 0  
  
 ENTÃO CalculateTotal (OrderValue, desconto)  
  
 Total OUTRO = OrderValue  
  
 **ErrorTotalRule:**  
  
 Se Total \< 0  
  
 ENTÃO erro = “ErrorTotalRule acionado”; Stop  
  
 A avaliação e a execução da regra também podem ser consideradas com o rastreamento e o rastreamento.  
  
### <a name="to-build-the-sample"></a>Para criar o exemplo  
  
1.  Abra a solução em [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Crie a solução. CTRL+SHIFT+B pressionando.  
  
3.  Executar a solução sem depuração pressionando CTRL + f5.  
  
### <a name="to-run-the-sample"></a>Para executar a amostra  
  
-   Na janela do prompt de comando SDK, execute o arquivo .exe no AdvancedPolicy \ bin \ debug (ou na pasta \ bin de AdvancedPolicy para a versão do Visual Basic de exemplo), que está localizado abaixo da pasta principal para o exemplo.  
  
> [!IMPORTANT]
>  Os exemplos podem mais ser instalados no seu computador. Verificar o seguinte diretório (padrão) antes de continuar:  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está no seguinte diretório:  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\Policy\AdvancedPolicy`  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Workflow.Activities.Rules.RuleSet>  
 <xref:System.Workflow.Activities.PolicyActivity>  
 [Política simples](../../../../docs/framework/windows-workflow-foundation/samples/simple-policy.md)
