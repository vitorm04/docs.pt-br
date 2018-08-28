---
title: Modelo de configuração hierárquica
ms.date: 03/30/2017
ms.assetid: 28dcc698-226c-4b77-9e51-8bf45a36216c
ms.openlocfilehash: ce0bc69424495594e0ee9c6b950a5fa9c4d5f993
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43000095"
---
# <a name="hierarchical-configuration-model"></a>Modelo de configuração hierárquica
Este exemplo demonstra como implementar uma hierarquia de arquivos de configuração para serviços. Ele também mostra como associações, comportamentos de serviço e comportamentos de ponto de extremidade são herdados de níveis mais altos na hierarquia.  
  
## <a name="sample-details"></a>Detalhes de exemplo  
 Um dos recursos desenvolvidos para o WCF no [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] é a melhoria no modelo de configuração hierárquica. Um exemplo de um modelo de configuração hierárquica seria aquele definido pelo Machine. config -> Rootweb.config -> Web. config. No [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], essas associações e comportamentos que são definidos em níveis superiores na hierarquia de configuração são adicionados aos seus serviços sem nenhuma configuração explícita. Este exemplo mostra como é possível simplificar sua configuração de serviço em elementos de configuração definidos no computador ou no nível do aplicativo de terceira parte confiável.  
  
 Esse exemplo consiste em nove serviços, definidos em três níveis de hierarquia. `Service1` está na raiz. `Service2` e `Service3` herdam os elementos padrão da `Service1`. `Service4`, `Service5`, `Service6` e `Service7` são definidos em um terceiro nível da hierarquia, herdando os elementos padrão da `Service3`. Por fim `Service10` e `Service11` estão em um quarto nível da hierarquia.  
  
 Todos os serviços de implementam o `IDesc` contrato. A seguir está a definição do `IDesc` interface que mostra os métodos expostos nesta interface. O `IDesc` interface é definida em Service1.cs.  
  
```csharp  
// Define a service contract  
[ServiceContract(Namespace="http://Microsoft.Samples.ConfigHierarchicalModel")]  
public interface IDesc  
{  
    [OperationContract]  
    List<string> ListEndpoints();  
    [OperationContract]  
    List<string> ListServiceBehaviors();  
    [OperationContract]  
    List<string> ListEndpointBehaviors();  
}  
```  
  
 A implementação desses métodos pelos serviços é simples. `ListEndpoints` itera em todos os pontos de extremidade de serviço e retorna uma lista de todos os pontos de extremidade que tem o serviço. `ListServiceBehaviors` itera em todos os comportamentos adicionados ao serviço e retorna a lista de todos os comportamentos de serviço associado ao serviço. `ListEndpointBehaviors` se comporta de forma semelhante ao `ListServiceBehaviors`, mas ele retorna a lista de comportamentos de ponto de extremidade em vez disso.  
  
 Essa implementação permite que o cliente saber quantos pontos de extremidade de serviço está expondo e quais comportamentos de serviço e comportamentos de ponto de extremidade foram adicionados ao serviço. O cliente que foi implementado como parte do exemplo adiciona uma referência de serviço para todos os serviços na solução e mostra esses elementos para cada um dos serviços.  
  
## <a name="to-use-this-sample"></a>Para usar este exemplo  
  
#### <a name="to-run-the-client"></a>Para executar o cliente  
  
1.  Usando [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], abra o arquivo ConfigHierarchicalModel.sln.  
  
2.  O projeto do cliente não já está definido como o projeto de inicialização, siga estas etapas.  
  
    1.  Na **Gerenciador de soluções**, a solução com o botão direito e, em seguida, selecione **propriedades**.  
  
    2.  Na **propriedades comuns**, selecione **projeto de inicialização**e, em seguida, clique em **único projeto de inicialização**.  
  
    3.  Dos **único projeto de inicialização** lista suspensa, selecione **cliente**.  
  
    4.  Clique em **Okey** para fechar a caixa de diálogo.  
  
3.  Para criar o exemplo, pressione CTRL+SHIFT+B.  
  
4.  Para executar o cliente, pressione Ctrl + F5.  
  
> [!NOTE]
>  Se essas etapas não funcionarem, certifique-se de que seu ambiente foi corretamente configurado, usando as seguintes etapas:  
>   
> 1.  Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).  
> 2.  Para criar a solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](building-the-samples.md).  
> 3.  Para executar o exemplo em uma única ou várias configurações de computador, siga as instruções em [executando os exemplos do Windows Communication Foundation](running-the-samples.md).  
  
> [!IMPORTANT]
>  Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigHierarchicalModel`  
  
## <a name="see-also"></a>Consulte também  
 [Exemplos de gerenciamento do AppFabric](http://go.microsoft.com/fwlink/?LinkId=193960)
