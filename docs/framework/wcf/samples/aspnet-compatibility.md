---
title: Compatibilidade ASP.NET
ms.date: 03/30/2017
ms.assetid: c8b51f1e-c096-4c42-ad99-0519887bbbc5
ms.openlocfilehash: f621a3f13fafee67a015d463898a10aaf9104008
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33806215"
---
# <a name="aspnet-compatibility"></a>Compatibilidade ASP.NET
Este exemplo demonstra como habilitar [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] modo de compatibilidade do Windows Communication Foundation (WCF). Serviços em execução [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] participar de modo de compatibilidade totalmente no [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplicativo pipeline e fazer uso de [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] recursos, como a autorização de URL do arquivo, estado de sessão e o <xref:System.Web.HttpContext> classe. O <xref:System.Web.HttpContext> classe permite o acesso a cookies, sessões e outros [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] recursos. Esse modo exige que as associações de usam o transporte HTTP e o próprio serviço deve ser hospedado no IIS.  
  
 Neste exemplo, o cliente é um aplicativo de console (um executável) e o serviço é hospedado no Internet Information Services (IIS).  
  
> [!NOTE]
>  Os procedimentos de instalação e as instruções de compilação para esse exemplo estão localizadas no final deste tópico.  
  
> [!NOTE]
>  Este exemplo requer uma [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] pool de aplicativos para executar. Para criar um novo pool de aplicativos, ou para modificar o pool de aplicativos padrão, siga estas etapas.  
>   
>  1.  Abra **Painel de Controle**.  Abra o **ferramentas administrativas** miniaplicativo sob o **sistema e segurança** título. Abra o **serviços de informações da Internet (IIS) Manager** miniaplicativo.  
> 2.  Expanda o modo de exibição de árvore no **conexões** painel. Selecione o **Pools de aplicativos** nó.  
> 3.  Para definir o pool de aplicativos padrão para usar [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] (que pode causar problemas de incompatibilidade com os sites existentes), com o botão direito do **DefaultAppPool** do item de lista e selecione **configurações básicas...** . Definir o **.Net Framework versão** pull-down até **.Net Framework v4.0.30128** (ou posterior).  
> 4.  Para criar um novo pool de aplicativos que usa [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] (para preservar a compatibilidade para outros aplicativos), com o botão direito do **Pools de aplicativos** nó e selecione **Adicionar Pool de aplicativos...** . Nomeie o novo pool de aplicativos e defina o **.Net Framework versão** pull-down até **.Net Framework v4.0.30128** (ou posterior). Depois de executar a instalação as etapas abaixo, clique com botão direito do **ServiceModelSamples** aplicativo e selecione **gerenciar aplicativo**, **configurações avançadas...** . Definir o **Pool de aplicativos** para o novo pool de aplicativos.  
  
> [!IMPORTANT]
>  Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebHost\ASPNetCompatibility`  
  
 Este exemplo se baseia o [Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md), que implementa um serviço de cálculo. O `ICalculator` contrato foi modificado como o `ICalculatorSession` contrato permitir que um conjunto de operações a serem executadas, mantendo um resultado de execução.  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculatorSession  
{  
    [OperationContract]  
    void Clear();  
    [OperationContract]  
    void AddTo(double n);  
    [OperationContract]  
    void SubtractFrom(double n);  
    [OperationContract]  
    void MultiplyBy(double n);  
    [OperationContract]  
    void DivideBy(double n);  
    [OperationContract]  
    double Result();  
}  
```  
  
 O serviço mantém o estado, usando o recurso para cada cliente, como várias operações de serviço são chamadas para executar um cálculo. O cliente pode recuperar o resultado atual chamando `Result` e pode limpar o resultado como zero chamando `Clear`.  
  
 O serviço usa a [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] sessão para armazenar o resultado para cada sessão de cliente. Isso permite que o serviço manter o resultado de execução para cada cliente em várias chamadas para o serviço.  
  
> [!NOTE]
>  [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] estado da sessão e sessões WCF são coisas muito diferentes.  Consulte o [sessão](../../../../docs/framework/wcf/samples/session.md) para obter detalhes sobre as sessões do WCF.  
  
 O serviço tem uma dependência profunda na [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] estado de sessão e requer [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] modo de compatibilidade para funcionar corretamente. Esses requisitos são expressos declarativamente, aplicando o `AspNetCompatibilityRequirements` atributo.  
  
```  
[AspNetCompatibilityRequirements(RequirementsMode =  
                       AspNetCompatibilityRequirementsMode.Required)]  
public class CalculatorService : ICalculatorSession  
{  
    double Result  
    {  // store result in AspNet Session  
       get {  
          if (HttpContext.Current.Session["Result"] != null)  
             return (double)HttpContext.Current.Session["Result"];  
          return 0.0D;  
       }  
       set  
       {  
          HttpContext.Current.Session["Result"] = value;  
       }  
    }  
    public void Clear()  
    {  
        Result = 0.0D;  
    }  
    public void AddTo(double n)  
    {  
        Result += n;  
    }  
    public void SubtractFrom(double n)  
    {  
        Result -= n;  
    }  
    public void MultiplyBy(double n)  
    {  
        Result *= n;  
    }  
    public void DivideBy(double n)  
    {  
        Result /= n;  
    }  
    public double Result()  
    {  
        return Result;  
    }  
}  
```  
  
 Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console do cliente. Pressione ENTER na janela do cliente para desligar o cliente.  
  
```  
0, + 100, - 50, * 17.65, / 2 = 441.25  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Depois que a solução foi criada, execute bat para configurar o aplicativo ServiceModelSamples em [!INCLUDE[iisver](../../../../includes/iisver-md.md)]. O diretório ServiceModelSamples agora deve aparecer como um [!INCLUDE[iisver](../../../../includes/iisver-md.md)] aplicativo.  
  
4.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Consulte também  
 [Exemplos de persistência e hospedagem de AppFabric](http://go.microsoft.com/fwlink/?LinkId=193961)
